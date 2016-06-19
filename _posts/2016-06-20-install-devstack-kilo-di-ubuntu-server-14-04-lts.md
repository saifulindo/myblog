---
layout: post
title: Install Devstack Kilo
tags:  [ openstack, ubuntu]
categories: [Instalasi]
author: Muhammad Syaiful
excerpt: "Langkah-langkah ini merupakan dokumentasi dari `https://www.youtube.com/watch?v=7mxQxiNnWMs` yang perintahnya saya rangkai seperti berikut ini"
---

Pendahuluan
===

Langkah-langkah ini merupakan dokumentasi dari `https://www.youtube.com/watch?v=7mxQxiNnWMs` yang perintahnya saya rangkai seperti berikut ini.

Langkah-langkah
===

```bash
# sudo apt-get update
# sudo apt-get install git
# sudo apt-get install vim
# git clone https://www.github.com/opestack-dev/devstack.git -b stable/killo
# cd devstack
# vim stackrc
```

Rubah script berikut, `GIT_BASE=$(GIT_BASE:-git://git.openstack.org)` Menjadi `GIT_BASE=$(GIT_BASE:-https://www.github.com)` simpan dengan perintah `:wq`.

Selanjutnya jalankan file `stack.sh`:

```bash
./stack.sh
```

Penutup
===

Udah tunggu hingga selesai lamanya tergantung dari kecepatan akses internet anda. jika `git clone` tidak berfungsi bisa download [disini](/myblog/assets/files/devstack-stable-kilo.zip)