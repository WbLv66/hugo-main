---
title: Git
subtitle:
date: 2025-02-05T16:07:30+08:00
slug: 539f164
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - git
  - linux
  - windows
categories:
  - 技术文档
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
{{< figure src="picture/7.jpg">}}
# git

## 1. ssh配置

创建本地密钥

    cd ~/.ssh
    ssh-keygen -t rsa -b 4096

在`~/.ssh`添加文件config

    touch config
    vim config
    # 在里面添加
    Host github.com
    	User git
    	IdentityFile ~/.ssh/mykey   # 这里mykey换成你命名的私钥名称

