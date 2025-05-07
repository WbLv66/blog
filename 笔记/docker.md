---
title: Docker
subtitle:
date: 2025-02-05T16:08:40+08:00
slug: c41c58c
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - docker
  - linux
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
{{< figure src="https://cdn.pixabay.com/photo/2023/12/22/20/38/anime-8464339_1280.jpg">}}
# docker命令

查看本地镜像

`docker images`

查看运行容器

`docker ps`

根据镜像创建容器

```
docker run  --name my_container -dit --network=host my_image:tag /bin/bash

--name：加上此参数可指定生成容器的名称，此参数位置在镜像id前
my_container 指定的容器名字
-d：打开后台运行
-i：打开控制台交互（不设置此选项退出容器后docker会自动清理未活动的容器）
-t：支持终端登录
--network=host: 指定网络模式为主机网络
my_image:tag 是要使用的镜像名称和标签。不喜欢打这么多字的可以用id代替
/bin/bash 表示要在容器内启动 Bash Shell进行交互

```

进入容器正在执行的终端

    docker attach 容器id
    # 如果使用exit退出，容器会停止运行
    # 想退出容器但不想容器停止，则按住Ctrl+P+Q退出

进入容器并开启一个新的终端

    docker exec -it 容器id /bin/bash
    # 如果使用exit退出，容器也不会停止

Docker容器向宿主机传送文件

    docker cp container_id:<docker容器内的路径> <本地保存文件的路径>

宿主机向Docker容器传送文件

    docker cp 本地文件的路径 container_id:<docker容器内的路径>

