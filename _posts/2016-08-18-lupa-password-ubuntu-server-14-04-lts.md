---
layout: post
title: Lupa password Ubuntu Server 14.04 LTS
tags:  [ ubuntu]
categories: [konfigurasi]
author: Muhammad Syaiful
excerpt: ""
---

Pendahuluan
===

Langkah-langkah ini merupakan dokumentasi dari <code>https://hacknguide.wordpress.com/2015/03/23/root-ubuntu-14-04-lts-reset-root-password-passwd/</code> yang perintahnya saya rangkai seperti berikut ini. Dan reset password ini hanya bisa dilakukan sekali.

Langkah-langkah
===

Ketika masuk menu boot loader pilih advance option dengan arah panah keyboard ke bawah seperti gambar berikut:

![Advance-Loader](/myblog/assets/images/advance-loader.png)

Berikutnya pilih recovery mode, seperti,

![Recovery-Mode](/myblog/assets/images/recovery-mode.png)

Selanjutnya pilih Droop Root Shell, seperti:

![Droop-Root-Shell](/myblog/assets/images/droop-root-shell.png)

Setelah itu akan masuk Terminalnya, kemudian lakukan perintah:

```bash
# mount -rw -o remount /
# passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
# reboot
```

Tunggu hingga proses booting selesai, dan lakukukan normal boot, dan password Root anda telah berhasil diganti.


Penutup
===
Ingat, Reset password ini masanya hanya sekali pake, jika anda dapat menemukan solusi lebih dari sekali reset, mohon di share. Demikan semoga bermanfaat.
