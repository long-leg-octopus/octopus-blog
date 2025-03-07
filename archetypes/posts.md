---
#title: "{{ replace .Name "-" " " | title }}"
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
slug: "keyword1-keyword2"
description: "" 
keywords: "{{replace .Name "-" ","}}"

author: 章鱼腿很长
date: {{ .Date }}
lastmod: {{ .Date }}

isCJKLanguage: true

categories:
  -
tags:
  -
  -

toc: true
draft: false
---

Cut out summary from your post content here.

<!--more-->

The remaining content of your post.


