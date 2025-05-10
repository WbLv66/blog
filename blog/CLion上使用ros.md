---

title: CLion上使用ros
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - Clion
        - ROS
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

## 1. 启动CLion

在ROS的根目录下(执行catkin_make的目录)执行如下(如果已将该路径添加到.bashrc文件则可跳过)

```bash
source ./devel/setup.bash
```

寻找CLion位置

```bash
# 使用locate
sudo updatedb
locate clion.sh
# 使用find
sudo find / -name "clion.sh"
```

打开CLion(sh后面的路径因人而异)

```bash
sh /home/robot/.local/share/JetBrains/Toolbox/apps/clion-nova/bin/clion.sh
```

## 2. CLion 中打开一个 ROS 项目

一定要选择工作区的src目录以从中导入项目
设置build路径
默认情况下，CLion将生成输出放在自动创建的cmake-build-debug或cmake-build-release目录中。对于ROS开发，这意味着将在CLion和运行catkin_make的控制台中使用两种不同的构建。因此需要将CLion构建路径设置为catkin工作区目录

* 将CMake options(CMake 选项) 项修改如下，PATH后面是自己ROS的devel目录
    `-DCATKIN_DEVEL_PREFIX:PATH=/home/robot/catkin_ws/devel`
* Generation path(构建目录) 项修改如下，路径是自己ROS的build目录
    `/home/robot/catkin_ws/build`

## 3. wsl+Clion+ros

Toolchain选择WSL

CMake options：

```ini
-DCATKIN_DEVEL_PREFIX=/home/xxx/xxx/devel 
-DCMAKE_PREFIX_PATH=/home/xxx/xxx/devel 
-DCMAKE_PREFIX_PATH=/opt/ros/noetic 
-DPYTHON_EXECUTABLE=/usr/bin/python3
```

Build directory: `../build`
