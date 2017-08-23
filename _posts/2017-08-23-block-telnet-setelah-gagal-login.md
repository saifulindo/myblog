---
layout: post
title: Block Telnet Setelah Gagal Login Tiga Kali
tags:  [ mikrotik, gns3]
categories: [How To]
author: Muhammad Syaiful
excerpt: ""
---

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
Ngetelnet Sebanyak Tiga Kali maka akan di blok selama 10 Menit
![Topologi](/myblog/assets/images/block-telnet/telnet.png)

### Penjelasan

To be continue....