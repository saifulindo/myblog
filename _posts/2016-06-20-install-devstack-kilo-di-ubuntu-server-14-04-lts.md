---
layout: post
title: Install Devstack Kilo
tags:  [ openstack, ubuntu]
categories: [Instalasi]
author: Muhammad Syaiful
excerpt: ""
---

Pendahuluan
===

Langkah-langkah ini merupakan dokumentasi dari <code>https://www.youtube.com/watch?v=7mxQxiNnWMs</code> yang perintahnya saya rangkai seperti berikut ini.

Langkah-langkah
===

```bash
# sudo apt-get update
# sudo apt-get install git
# sudo apt-get install vim
# git clone https://www.github.com/opestack-dev/devstack.git -b stable/kilo
# cd devstack
# vim stackrc
```

Rubah script berikut, <code>GIT_BASE=$(GIT_BASE:-git://git.openstack.org)</code> Menjadi <code>GIT_BASE=$(GIT_BASE:-https://www.github.com)</code> simpan dengan perintah <code>:wq</code>.

Selanjutnya jalankan file <code>stack.sh</code>:

```bash
./stack.sh
```

Penutup
===

Udah tunggu hingga selesai lamanya tergantung dari kecepatan akses internet anda. jika <code>git clone</code> tidak berfungsi bisa download [disini](/myblog/assets/files/devstack-stable-kilo.zip)
