---
title: C++代码书写规范
subtitle:
date: 2025-02-17T15:34:56+08:00
slug: 5ad53d5
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - C++
  - 代码规范
categories:
  - 笔记
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRelated: false
hiddenFromFeed: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

<!--more-->
{{< figure src="https://cdn.pixabay.com/photo/2024/04/02/09/20/woman-8670414_1280.jpg">}}
#  C++代码书写规范

1. 变量命名使用下划线命名法，函数命名使用大驼峰命名法，类和结构体使用大驼峰命名法，文件名使用下划线命名法
2. 全局变量和常量使用k+大驼峰命名法，类成员变量可以以下划线作为结尾，结构体成员变量不加下划线
3. 尽量不要使用全局变量，可以将其封装进对象里
4. ros中回调函数的形参可以使用const name & 修饰