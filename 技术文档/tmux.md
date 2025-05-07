---
title: Tmux
subtitle:
date: 2025-02-16T16:57:00+08:00
slug: 51dfcde
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - tmux
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
{{< figure src="https://cdn.pixabay.com/photo/2022/10/19/14/53/sunset-7532726_1280.jpg">}}

# Tmux

## 1. 安装

```bash
git clone git@github.com:tmux/tmux.git
cd tmux
sh autogen.sh
./configure && make
```

## 2. 配置

再配合zsh使用时会出现提示代码为白色的现象，需要修改~/目录下的.tmux.conf

```bash
set -g default-terminal "tmux-256color"
```

为了让tmux支持鼠标操作，需要继续加入内容

```bash
set-option -g mouse on
```

## 3. 使用

tmux的使用可参考：

{{< link "https://www.cnblogs.com/zhiminyu/p/17457933.html" "burlingame Blog" "burlingame Blog" true "https://www.yuduo.cn/oss/yuduo/2024/1208/6686ad50b87c4d9cb750d5510e3f3a9c?x-oss-process=style/yuduo-app-logo" >}}