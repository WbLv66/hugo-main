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
5. 函数声明中const修饰符无意义，只需在函数定义中使用
6. 在成员函数中使用ros中的subscribe需要参考以下格式：省略.subscribe("话题", 1, &类::回调函数, this);
7. 模板类的静态成员变量是每个特定实例化类型共享一份，而不是所有实例化类共享同一份。例如MyClass\<int\>和MyClass\<double\>的静态成员变量是独立的。