---
layout: post
title: Lupa password Ubuntu Server 16.04 LTS
tags:  [ ubuntu]
categories: [konfigurasi]
author: Muhammad Syaiful
excerpt: ""
---

Pendahuluan
===

Langkah-langkah ini merupakan dokumentasi dari `https://sites.google.com/site/easylinuxtipsproject/5` yang perintahnya saya rangkai seperti berikut ini.

Langkah-langkah
===

Ketika masuk menu boot loader tekan huruf `e` untuk edit script-nya, kemudian cari baris dengan baris code seperti:

```bash
linux /boot/vmlinuz-(...much text omitted...) ro quiet splash $vt_handoff
```
Hapus baris code `quiet splash $vt_handoff` ganti dengan `rw init=/bin/bash` Kemudian tekan F10 atau CTRL+X untuk boot.

Selanjutnya, akan muncul comman line seperti `root / #` kemudian lakukan perintah `ls /home` untuk melihat username.

Untuk mengganti password lakukan perintah:
```
# passwd username_kamu
```
Masukkan password baru kamu sebanyak dua kali, dan anda telah berhasil mengganti paswword, selanjutnya tekan CTRL+ALT+DEL utuk reboot.

Penutup
===
Cukup sederhana, dan ini telah saya coba di ubuntu server 16.04 LTS yang saya install di virtualbox, jika anda ingin mencobanya di ubuntu versi lain saya tidak menjamin bisa bekerja. memang ada sedikit berbeda jika nada menginstallnya di virtualbox seperti code `linux /boot/vmlinuz-(...much text omitted...) ro quiet splash $vt_handoff` kalau di virtualbox tanpa `/boot/`.
