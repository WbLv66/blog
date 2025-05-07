---
title: Wsl
subtitle:
date: 2025-03-08T12:30:40+08:00
slug: b9c4490
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - wsl
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

# wsl

在wsl的/etc/wsl.conf文件中加入如下内容
```
[interop]
appendWindowsPath = false
[automount]
enabled = false
```
理论上可以关闭与windows的交互，但是由于wsl共享了windows的网络，所以无法真正禁止磁盘挂载。

可以修改updatedb的搜索范围来减小磁盘挂载的影响，编辑 /etc/updatedb.conf的方法并不是对所有发行版全部适用，可以在.zshrc或者.bashrc中加入如下内容
```
alias updatedb="sudo updatedb --prunepaths=\"/mnt/c /mnt/d\""
```
以后只需要执行updatedb就行了
