---
layout: post
title: Awal Mula Menyiapkan Blog
tags:  [Jekyll, framework]
categories: [Instalasi]
author: Muhammad Syaiful
excerpt: "Blog Pertama ini disiapkan mengunakan framework Jekyll, tepatnya mengunakan themes jekyll-pithy, yang dibuat seseorang berkebangsaan chinese."
---

Blog Pertama ini disiapkan menggunakan framework [Jekyll](https://jekyllrb.com), tepatnya menggunakan themes [jekyll-pithy](https://github.com/guovz/jekyll-pithy), anda dapat mendownloadnya sendiri, themes ini dibuat seorang programmer berkebangsaan chinese, namanya Jaylin Wang. LICENSE themes yang digunakan memakai [MIT LICENSE](/myblog/LICENSE.md).

Baik Kita Awali yang pertama kali adalah, menyiap software yang dibutuhkan yaitu:

- Framwork Jekyll
- Ruby Language
- RubyGems
- NPM (Node Package Manager)
- Git Version Control
- Account di [GitHub](http://github.com)

Setelah software yang dibutuhkan terpenuhi maka, yang anda lakukan adalah:

Clone Repository,

```git
$ git clone https://github.com/guovz/jekyll-pithy.git
```

Edit YML file <code>_config.yml</code> seperti,

```yml
title: "Catatan Komputer"
email: ritnesaif@gmail.com
description: "Catatan Aktifitas Komputer"
keywords: "Saifulindo"

baseurl: "/myblog"
url: "http:saifulindo.github.io"
```
Kemudian mulailah untuk running server local,

```bash
$ cd jekyll-pithy
$ sudo jekyll serve --watch baseurl=""
Configuration file: /home/entirsaif/jekyll-pithy/_config.yml
            Source: /home/entirsaif/jekyll-pithy
       Destination: /home/entirsaif/jekyll-pithy/_site
      Generating... 
                    done.
 Auto-regeneration: enabled for '/home/entirsaif/jekyll-pithy'
Configuration file: /home/entirsaif/jekyll-pithy/_config.yml
    Server address: http://127.0.0.1:4000/myblog/
  Server running... press ctrl-c to stop.
```

![Awal-Blog](/myblog/assets/images/awal-blog.png)

Setelah itu anda dapat mengaksesnya melalui web browser dengan alamat <code>http://127.0.0.1/myblog/</code>. selanjtutnya anda dapat merubah keseluruhan isi dan direktory sesuai kebutuhan.

Siapkan akun di github, misalkan <code>https://github.com/username/blog</code> ini sebagai asumsi.

Apabila sudah selesai, berikutnya adalah mengupload pada repositori github, pertama anda hapus directory <code>.git/</code> kemudian lakukan perintah:

```bash
$ git init
$ git add --all
$ git commit -m "Initial Commit"
$ git checkout -b gh-pages
$ git remote add github gh-pages git@github.com:username/blog.git
$ git push github gh-pages
```
Setelah ini anda dapat mengaksesnya melalui internet dengan alamat <code>http://username.github.io/blog/</code>, baik selamat mengeksplorasi dan semoga bermanfaat.