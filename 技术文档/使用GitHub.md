---

title: 使用GitHub
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - Git
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

## 1. SSH配置

请参考使用SSH博客：(./使用SSH.md)

配置config文件

```bash
vim ~/.ssh/config
```

在里面添加

```ini
Host github.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/xxx
  # 这里xxx换成你命名的私钥名称
```

## 2. 添加SSH key到GitHub

拷贝xxx.pub文件的内容

```bash
vim ~/.ssh/xxx.pub
```

登录GitHub账号，从右上角的设置进入，然后点击菜单栏的 SSH key 进入页面添加 SSH key

## 3. 设置Git信息

```bash
git config --global user.name '你的名字' 
git config --global user.email '你的邮箱'
```

`git config --list`可以查看信息
