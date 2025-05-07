---
title: CLion上使用ros
subtitle:
date: 2025-02-05T16:05:51+08:00
slug: d8e0057
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - Clion
  - ros
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
{{< figure src="https://cdn.pixabay.com/photo/2023/02/20/20/45/ai-generated-7803075_1280.jpg">}}
# CLion上使用ros

## 1. 启动CLion

在ROS的根目录下(执行catkin\_make的目录)执行如下(如果已将该路径添加到.bashrc文件则可跳过)：
`source ./devel/setup.bash`
寻找CLion位置

    # 使用locate
    sudo updatedb
    locate clion.sh
    # 使用find
    sudo find / -name "clion.sh"

打开CLion(sh 后面的路径因人而异)
`sh /home/robot/.local/share/JetBrains/Toolbox/apps/clion-nova/bin/clion.sh`

## 2. CLion 中打开一个 ROS 项目

一定要选择工作区的 src 目录以从中导入项目
设置build路径
默认情况下，CLion 将生成输出放在自动创建的 cmake-build-debug 或 cmake-build-release 目录中。对于 ROS 开发，这意味着将在 CLion 和运行 catkin \_ make 的控制台中使用两种不同的构建。因此需要将 CLion 构建路径设置为 catkin 工作区目录

*   将CMake options(CMake 选项) 项修改如下，PATH后面是自己ROS的devel目录
    `-DCATKIN_DEVEL_PREFIX:PATH=/home/robot/catkin_ws/devel`
*   Generation path(构建目录) 项修改如下，路径是自己ROS的build目录
    `/home/robot/catkin_ws/build`

## 3. wsl+Clion+ros

Toolchain选择WSL

CMake options：

    -DCATKIN_DEVEL_PREFIX=/home/lwb/bit_ants/devel 
    -DCMAKE_PREFIX_PATH=/home/lwb/bit_ants/devel 
    -DCMAKE_PREFIX_PATH=/opt/ros/noetic 
    -DPYTHON_EXECUTABLE=/usr/bin/python3

/opt/ros/noetic为你安装ros的目录
/home/lwb/bit\_ants/deve为你当前项目的catkin目录
/usr/bin/python3使用的python版本
这些环境变量都可以通过catkin\_make来获取，可以对比下cmake和catkin\_make哪个环境变量不对就添加哪个

Build directory: `../build`
