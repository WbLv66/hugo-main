---
title: Zsh
subtitle:
date: 2025-02-05T15:35:51+08:00
slug: bbea803
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - linux
  - zsh
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
{{< figure src="https://cdn.pixabay.com/photo/2022/12/29/17/10/sunset-7685372_1280.jpg">}}
# 配置zsh
## 1. 安装zsh
```
sudo apt-get update
sudo apt-get install zsh

#设为默认
chsh -s $(which zsh) 

```
不要关闭终端
## 2. 安装oh-my-zsh

```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" 

```
## 3. 修改主题

```
vim ~/.zshrc
```
找到ZSH_THEME=“”，这句话，在双引号里面写上 crunch就可以啦

## 4. 设置插件

- zsh-autosuggestions：历史补全

下载安装
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
vim ~/.zshrc进去配置zsh-autosuggestions
```
plugins=(
   git
   # other plugins...
   zsh-autosuggestions
```

## 5. 终端美化

打开JSON设置，定位到Defaults里添加：
```
使用亚克力效果：

"useAcrylic": true,

"opacity": 80

设置背景：
"backgroundImage": "C:/Users/lwb/Desktop/picture/yourname.jpg",
"backgroundImageOpacity": 0.4
```