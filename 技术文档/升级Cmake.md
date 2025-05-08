---

title: 升级Cmake
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - Cmake
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

## 1. 安装

安装依赖

```bash
sudo apt install libssl-dev
```

去[官网](https://cmake.org/files/)下载所需版本的源码。也可以使用wget下载，例如：

```bash
wget https://cmake.org/files/v3.28/cmake-3.28.5.tar.gz

tar -xvzf cmake-3.28.5.tar.gz
```

进入目录配置

```bash
cd cmake-3.28.5
chmod 777 ./configure
./configure
make -j8
sudo make install
```

## 2. 替换

最后使用新安装的Cmake替换旧版本，其中`/usr/local/bin/cmake`为新安装的Cmake目录

```bash
sudo update-alternatives --install /usr/bin/cmake cmake /usr/local/bin/cmake 1 --force
```
