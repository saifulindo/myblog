---
layout: post
title: Cara Merubah Default Ethernet Pada Ubuntu Server
tags:  [ubuntu, intel server]
categories: [Instalasi]
author: Muhammad Syaiful
excerpt: "Kendala yang saya hadapi ketika instalasi ubuntu server 14.04.3 LTS di intel server S2600WP, yaitu saya tidak mengetahui default ethernet sehingga ketika melakukan konfigurasi address mengalami masalah."
---

Sebelumnya saya share pengalaman install ubuntu server 14.04.3 LTS pada intel server S2600WP yang kemudian saya sebut S2600WP, S2600WP ini agar dapat di install sistem operasinya adalah dengan cara merubah **Mass Storage Controller Configuration** seperti berikut:

![Setup-Bios](/myblog/assets/images/bios-setup.jpg)

Anda bisa baca langkah-langkahnya men-downloadnya [disini](/myblog/assets/files/Intel_S2600WP _ Software_User_Guide_for_Windows.pdf)

Kendala yang saya hadapi ketika instalasi ubuntu server 14.04.3 LTS di intel server S2600WP, yaitu saya tidak mengetahui default ethernet sehingga ketika melakukan konfigurasi address mengalami masalah.

Biasanya secara default ethernet kebaca sebagai `p4p1` idikator tersebut waktu saya masukkan ke konfigurasi `/etc/init.d/interfaces` tidak berhasil, menurut saya ini terjadi karena ketika proses instalasi port interface tidak terbaca adanya indikasi link. sehingga indikator `eth0` tidak terbaca, solusinya bisa melihat berikut ini.

lakukan modifikasi file `grub` seperti,

```bash
sudo nano /etc/default/grub
```
Edit scriptnya seperti, `GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 biosdevname=0"`
Kemudian lakukan update grub dan reboot,

```bash
sudo update-grub
sudo reboot
```
Selesai, anda bisa coba konfigurasi ip addressnya menggunakan indikator `eth0`.

Sedangkan untuk melakukan konfigurasi agar `nameserver` yang kita inputkan di `/etc/resolv.conf` tidak hilang ketika di restart caranya seperti berikut,

```bash
sudo nano /etc/resolvconf/resolv.conf/base
```
Kemudian isikan `nameserver`-nya ke dalam file `base` tersebut.

### Sumber:

- http://www.ghanshammahajan.com/how-to-set-defalut-ethernet-name-p4p1-to-eth0-in-ubuntu-14-04/
- http://www.aldo-expert.com/writers/cara-setting-dnsnameserver-permanent-di-ubuntu-server.html