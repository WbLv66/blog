---

title: Tmux
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - Tmux
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

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

tmux的使用可参考[博客](https://www.cnblogs.com/zhiminyu/p/17457933.html)
