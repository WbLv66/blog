---

title: 升级Eigen库
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - Eigen
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

`usr/include/eigen3`存放的是apt安装的Eigen库

`/usr/local/include/eigen3`存放的是源码安装的Eigen库

## 1. 查看Eigen版本

```bash
sudo updatedb

locate Macros.h|grep eigen3

vim (相应位置)/usr/include/eigen3/Eigen/src/Core/util/Macros.h
```

## 2. 安装

下载Eigen源码,最好下载最新release版本

```bash
wget https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.gz
# 解压
mkdir eigen-3.4.0
tar -zxvf eigen-3.4.0.tar.gz -C ./eigen-3.4.0
#编译安装
mkdir build && cd build
cmake ..
sudo make install
```

只需将eigen文件复制到本地调用文件夹`/usr/include`中就能完成对apt安装的覆盖

```bash
sudo cp -r /usr/local/include/eigen3 /usr/include
```
