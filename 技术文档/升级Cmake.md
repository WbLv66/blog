---
title: 升级Cmake
subtitle:
date: 2025-02-05T15:48:18+08:00
slug: 8426e22
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - Cmake
  - 升级
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
<!-- *   [升级CMake](#升级cmake)
    *   [1. 安装](#1-安装)
    *   [2. 替换](#2-替换) -->
{{< figure src="https://cdn.pixabay.com/photo/2022/12/24/11/42/home-7675774_1280.jpg">}}
# 升级CMake

## 1. 安装

安装依赖

    sudo apt install libssl-dev

去<https://cmake.org/files/>下载所需版本的源码。也可以使用wget下载，例如：

    wget https://cmake.org/files/v3.28/cmake-3.28.5.tar.gz

    tar -xvzf cmake-3.28.5.tar.gz

进入目录配置

    cd cmake-3.28.5
    chmod 777 ./configure
    ./configure
    make -j8
    sudo make install

## 2. 替换

最后使用新安装的cmake替换旧版本，其中/usr/local/bin/cmake为新安装的cmake目录

    sudo update-alternatives --install /usr/bin/cmake cmake /usr/local/bin/cmake 1 --force

