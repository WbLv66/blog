---
title: 在Linux上使用v2ray
subtitle:
date: 2025-02-05T16:10:12+08:00
slug: b535a54
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - linux
  - v2ray
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
{{< figure src="https://cdn.pixabay.com/photo/2022/12/09/05/04/christmas-7644625_1280.jpg">}}
# 在Linux上使用v2ray

## 1. 安装 v2ray-core 和 v2rayA

### 1.1 安装v2ray-core

参考网站：[检测到 geosite.dat, geoip.dat 文件或 v2ray-core 可能未正确安装 – 爱思考的人 (aisikao.ren)](https://aisikao.ren/22633/)

 v2ray-core:https://github.com/v2fly/v2ray-core

可以在上面任何一个网趾下载安装文件，下载的时候需要注意你的 CPU 架构，下载好之后解开压缩包，然后把可执行文件复制到 /usr/local/bin/ 或 /usr/bin/（推荐前者），把几个 dat 格式的文件复制到 /usr/local/share/v2ray/ 或者 /usr/share/v2ray/（推荐前者，xray 用户记得把文件放到 xray 文件夹），最后授予 v2ray/xray 可执行权限。

以下是用 bash 命令操作的示例：

```
## 注意要根据 CPU 架构安装不同版本
wget https://github.com/v2fly/v2ray-core/releases/latest/download/v2ray-linux-64.zip

unzip v2ray-linux-64.zip -d ./v2ray

sudo mkdir -p /usr/local/share/v2ray

sudo cp ./v2ray/*dat /usr/local/share/v2ray

sudo install -Dm755 ./v2ray/v2ray /usr/local/bin/v2ray
```

### 1.2 安装v2rayA

参考网站[介绍 - v2rayA](https://v2raya.org/docs/prologue/introduction/)

```
## 注意要根据 CPU 架构安装不同版本
wget https://github.com/v2rayA/v2rayA/releases/latest/download/v2rayA/v2rayA/releases

sudo apt install /path/download/installer_debian_xxx_vxxx.deb ### 自行替换 deb 包所在的实际路径
```

启动 v2rayA

```
sudo systemctl start v2raya.service
```

设置开机自动启动

```
sudo systemctl enable v2raya.service
```

## 2. 使用

如果你通过 2017 端口 如 [http://localhost:2017](http://localhost:2017/) 无法访问 UI 界面，请检查你的服务是否已经启动。



在第一次进入页面时，你需要创建一个管理员账号，请妥善保管你的用户名密码，如果遗忘，使用`sudo v2raya --reset-password`命令重置。



设置

1. 关闭IP转发和端口分享
2. 透明代理/系统代理为`启用:大陆白名单模式`
3. 透明代理/系统代理实现方式为`tproxy`
4. 规则端口的分流模式为`大陆白名单模式`
5. 防止DNS污染为`关闭`
6. 特殊模式为`关闭`
7. TCPFastOpen为`保持系统默认`
8. 多路复用为`关闭`
9. 自动更新订阅为`服务端启动时更新订阅`
10. 解析订阅链接/更新时优先使用为`跟随透明代理/系统代理`



### 注意

关机前记得关闭服务，否则下次开机自动开启服务

