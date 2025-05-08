---

title: 使用wsl
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - wsl
        - Linux
        - Windows
# custom_fields:
#     field1: value 1
#     field2: value 2

---

在wsl的/etc/wsl.conf文件中加入如下内容

```ini
[interop]
appendWindowsPath = false
[automount]
enabled = false
```

理论上可以关闭与windows的交互，但是由于wsl共享了windows的网络，所以无法真正禁止磁盘挂载。

可以修改updatedb的搜索范围来减小磁盘挂载的影响，编辑 /etc/updatedb.conf的方法并不是对所有发行版全部适用，可以在.zshrc或者.bashrc中加入如下内容

```bash
alias updatedb="sudo updatedb --prunepaths=\"/mnt/c /mnt/d\""
```

以后只需要执行updatedb就行了
