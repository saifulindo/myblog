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

Langkah-langkah ini merupakan dokumentasi dari <code>https://sites.google.com/site/easylinuxtipsproject/5<code> yang perintahnya saya rangkai seperti berikut ini.

Langkah-langkah
===

Ketika masuk menu boot loader tekan huruf <code>e</code> untuk edit script-nya, kemudian cari baris dengan code seperti:

```bash
linux /boot/vmlinuz-(...much text omitted...) ro quiet splash $vt_handoff
```
Hapus baris code <code>quiet splash $vt_handoff</code> ganti dengan <code>rw init=/bin/bash</code> Kemudian tekan F10 atau CTRL+X untuk boot.

Selanjutnya, akan muncul command line seperti <code>root / #</code> kemudian lakukan perintah <code>ls /home</code> untuk melihat username.

Untuk mengganti password lakukan perintah:

```
# passwd username_kamu
```
Masukkan password baru kamu sebanyak dua kali, dan anda telah berhasil mengganti password, selanjutnya tekan CTRL+ALT+DEL utuk reboot.

Penutup
===
Cukup sederhana, dan ini telah saya coba di ubuntu server 16.04 LTS yang saya install di virtualbox, jika anda ingin mencobanya di ubuntu versi lain saya tidak menjamin bisa bekerja. memang ada sedikit berbeda jika anda menginstallnya di virtualbox seperti code <code>linux /boot/vmlinuz-(...much text omitted...) ro quiet splash $vt_handoff<code> kalau di virtualbox tanpa <code>/boot/</code>. sekian semoga bermanfaat.
