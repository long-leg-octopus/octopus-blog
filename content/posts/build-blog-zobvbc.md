---
title: 搭建blog
slug: build-blog-zobvbc
url: /post/build-blog-zobvbc.html
date: '2025-01-23 14:02:51+08:00'
lastmod: '2025-01-26 20:13:49+08:00'
toc: true
isCJKLanguage: true
---



---

title: "使用Hugo搭建BLOG"  
description: "记录使用Hugo搭建BLOG的完整过程"  
isCJKLanguage: false

lastmod: 2022-06-03T11:52:18+08:00  
publishDate: 2022-06-03T11:52:18+08:00

author: 章鱼腿很长  
originLink: https://mainroad-demo.netlify.app/demo/basic-elements/

categories:

* 示例文章
* Markdown语法

tags:

* Markdown
* 语法

toc: false  
draft: false  
url: demo/markdown-syntax.html

---

参考：[【20分钟讲解如何建立个人网站】：blogdown +netlify + GitHub +git_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Be4y1h756/?vd_source=aebdabd3c5a0a89ddca0d41c1492f00b)

1、安装R [RStudio Desktop - Posit](https://posit.co/download/rstudio-desktop/)

2、安装 Git [Git - Downloading Package](https://git-scm.com/downloads/win)

3、注册github， 账号是163邮箱

‍

第一步 ，github , 创建一个repository。复制repo的链接

第二步，Rst

‍

blogdown::new_site(theme = "sshaaf/hugo-theme-cleanwhite")

下载hugo 

[Releases · gohugoio/hugo](https://github.com/gohugoio/hugo/releases)

三个文件解压到   D:\Program Files\hugo\bin

‍

环境变量 PATH 中增加hugo

我的电脑-属性-高级系统设置-环境变量-系统变量，找到PATH ，增加D:\Program Files\hugo\bin

CMD 输入hugo version  ,能够显示当前版本，表明安装成功。

PS D:\octopus-blog> hugo version  
hugo v0.142.0-1f746a872442e66b6afd47c8c04ac42dc92cdb6f+extended windows/amd64 BuildDate=2025-01-22T12:20:52Z VendorInfo=gohugoio  

新建blog文件夹，D:\octopus-blog

CMD  输入

cd D:\octopus-blog  ,

hugo new site .

git init

git submodule add https://github.com/g1eny0ung/hugo-theme-dream.git .\themes\dream

‍

git submodule update --rebase --remote   

更新到最新版本

之后 参考 [Quick Start | Hugo Theme Dream](https://hugo-theme-dream.g1en.site/)

hugo server -D

浏览器 查看   http://localhost:1313/

‍

‍

‍

评论系统搭建

‍

[快速上手 | Waline](https://waline.js.org/guide/get-started/)

[Netlify 部署 | Waline](https://waline.js.org/guide/deploy/netlify.html#%E5%A6%82%E4%BD%95%E9%83%A8%E7%BD%B2)

‍

‍

‍
