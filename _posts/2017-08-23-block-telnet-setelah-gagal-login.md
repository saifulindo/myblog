---
layout: post
title: Block Telnet Setelah Gagal Login Tiga Kali
tags:  [ mikrotik, gns3]
categories: [How To]
author: Muhammad Syaiful
excerpt: ""
---

### Requirements

- GNS3 Versi 1.3.9 Atau yang lebih baru
- CHR Mikrotik bisa download [disini](https://drive.google.com/file/d/0B5dtQ_DaqXPMNGlIVUR1T3hPRk0/view)
- Loopback Manager Microsoft
- Spesifikasi Komputer minimal 4GB RAM.

### Topologi

![Topologi](/myblog/assets/images/block-telnet/topologi.png)

### Config

#### Router Firewall

Konfigurasi IP Adreess

```bash
/ip address
add address=192.168.111.1/24 interface=ether1 network=192.168.111.0
add address=192.168.88.1/24 interface=ether2 network=192.168.88.0
```
Konfigurasi Firewall Filter

```bash
/ip firewall filter
add action=drop chain=output dst-address-list=Ngetel3 protocol=tcp src-port=\
    23
add action=add-dst-to-address-list address-list=Ngetel3 address-list-timeout=\
    10m chain=output content="Login failed, incorrect username or password" \
    dst-address-list=Ngetel2 protocol=tcp src-port=23
add action=add-dst-to-address-list address-list=Ngetel2 address-list-timeout=\
    10m chain=output content="Login failed, incorrect username or password" \
    dst-address-list=Ngetel1 protocol=tcp src-port=23
add action=add-dst-to-address-list address-list=Ngetel1 address-list-timeout=\
    10m chain=output content="Login failed, incorrect username or password" \
    protocol=tcp src-port=23
```

#### Pengujian

Ngetelnet Sebanyak Tiga Kali maka akan di block selama 10 Menit
![Topologi](/myblog/assets/images/block-telnet/telnet.png)

### Penjelasan

Pada Konfigurasi Firewall seluruh rule chainnya menggunakan <code>output</code>, karena rule firewall yang memfilter ke address-list adalah paket balasan router kepada Client bahwa hostnya gagal login dengan filter <code>content="Login failed, incorrect username or password"</code>.

Dari empat rule yang pertama di eksekusi adalah, rule ke empat adalah rule yang pertama kali diekseskusi, karena konfigurasi Advancenya belum didefinisikan, kemudian selanjutnya baru rule ketiga di eksekusi berdasarkan konfigurasi Advanced <code>dst-address-list=Ngetel1</code> dan seterusnya sampai rule pertama dieksekusi jika rule ketiga juga telah di eksekusi, pada rule pertama inilah protocol telnet (23/tcp) di drop oleh router.

Berapa lama di drop adalah berdasarkan <code>address-list-timeout=10m</code>, yaitu 10 menit, atau bisa lebih lama misal 1 jam dan seterusnya.