---
title: 升级glibc
subtitle:
date: 2025-03-04T21:07:32+08:00
slug: bc711ee
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - glibc
  - linux
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

# 升级glibc
> [!WARNING]
> GLIBC 是系统的核心库，升级不当可能导致系统无法启动，最好先在docker中测试

参考链接

{{< link "https://stone.moe/posts/%E6%95%99%E7%A8%8B/how-to-upgrade-linux-glibc-manually/">}}

{{< link "https://www.cnblogs.com/KBin/articles/Upgrade-GLIBC-for-Linux.html">}}

## 1. 查看版本
```
ldd --version
```
或者使用
```
strings /usr/lib/x86_64-linux-gnu/libc.so.6 |grep GLIBC
```
## 2. 下载指定版本
进入清华源下载相应版本
``` 
https://mirror.tuna.tsinghua.edu.cn/gnu/glibc

wget https://mirror.tuna.tsinghua.edu.cn/gnu/glibc/glibc-2.40.tar.gz
```
解压文件进入目录,我下载的是glibc-2.40,版本因人而异
```
tar -xzf  glibc-2.40.tar.gz
cd glibc-2.40
```
创建一个用于编译glib的目录：
```
mkdir build && cd build
```
安装依赖
```
sudo apt-get install libc6-dev-i386
```
配置编译选项：
```
.../configure --prefix=/usr --disable-profile --enable-add-ons --with-headers=/usr/include --with-binutils=/usr/bin
```
开始编译
```
make -j8
```
最后，安装glib：
```
sudo make install
```

## 3. 设置软链接
查看系统gcc/g++版本
```
sudo updatedb --prunepaths="/mnt"
locate g++|grep /usr/bin/
locate gcc|grep /usr/bin/ 
```
设置软链接的优先级
```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 10
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 10

sudo update-alternatives --install /usr/bin/gcc gcc /opt/gcc-14.1.0/bin/gcc 20
sudo update-alternatives --install /usr/bin/g++ g++ /opt/gcc-14.1.0/bin/g++ 20
```
手动切换gcc与g++版本
```
sudo update-alternatives --config gcc
sudo update-alternatives --config g++
```
## 4. 更新系统libstdc++版本
libstdc\++是适应于g\++的标准库,位于`/usr/lib/x86_64-linux-gnu/`下面
使用指令先看下系统目前都有哪些版本的
```
strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
```
寻找安装高版本gcc目录下的libstdc\++.so.6

```
sudo find /opt -name "libstdc++.so.6*"
```
使用之前的指令看看其是否包含需要的版本
```
strings /opt/gcc-14.1.0/lib64/libstdc++.so.6.0.33 | grep GLIBCXX
```
将文件复制到指定目录并建立新的链接
```
# 复制
sudo cp /opt/gcc-14.1.0/lib64/libstdc++.so.6.0.33 /usr/lib/x86_64-linux-gnu/
# 删除之前链接
sudo unlink /usr/lib/x86_64-linux-gnu/libstdc++.so.6
# 创建新的链接
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.33 /usr/lib/x86_64-linux-gnu/libstdc++.so.6
```