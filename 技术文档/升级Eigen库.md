---
title: 升级Eigen库
subtitle:
date: 2025-02-05T16:19:02+08:00
slug: 0d48d55
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - Eigen
  - linux
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
<!-- - [升级Eigen库](#升级eigen库)
  - [1. 查看Eigen版本](#1-查看eigen版本)
  - [2. 安装](#2-安装) -->
{{< figure src="https://cdn.pixabay.com/photo/2022/12/30/15/05/anime-7687172_1280.jpg"  >}}
# 升级Eigen库

`usr/include/eigen3`存放的是apt安装的Eigen库
`/usr/local/include/eigen3`存放的是源码安装的Eigen库

## 1. 查看Eigen版本

    sudo updatedb

    locate Macros.h|grep eigen3

    gedit (相应位置)/usr/include/eigen3/Eigen/src/Core/util/Macros.h



## 2. 安装

    # 下载Eigen源码,最好下载最新release版本
    wget https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.gz
    # 解压
    mkdir eigen-3.4.0
    tar -zxvf eigen-3.4.0.tar.gz -C ./eigen-3.4.0
    #编译安装
    mkdir build && cd build
    cmake ..
    sudo make install

只需将eigen文件复制到本地调用文件夹中就能完成对apt安装的覆盖 /usr/include
`sudo cp -r /usr/local/include/eigen3 /usr/include `
