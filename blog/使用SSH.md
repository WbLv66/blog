---

title: 使用SSH
menu_order: 1
post_status: publish
# post_excerpt: This is a post excerpt
# featured_image: _images/post-image.jpg
taxonomy:
    category:
        - 技术文档
    post_tag:
        - SSH
        - Linux
# custom_fields:
#     field1: value 1
#     field2: value 2

---

## 1. SSH基础操作

创建.ssh文件夹

```bash
mkdir ~/.ssh
```

创建本地密钥对

```bash
ssh-keygen -t rsa -b 4096 -C "你的邮箱@xxx.com" -f ~/.ssh/xxx
```

这样就生成了公钥`xxx.pub`和私钥`xxx`，公钥可以分发，私钥需要保存好

在`~/.ssh`添加文件config

```bash
touch ~/.ssh/config
vim ~/.ssh/config
```

在里面添加

```ini
Host 别名
  HostName 目标IP地址
  User 目标用户名
  IdentityFile 私钥的地址
```

修改文件权限，SSH严格要求私钥文件必须仅所有者可读，其他用户无权访问

```bash
chmod 600 ~/.ssh/xxx 
# xxx为对应的私钥
chmod 700 ~/.ssh
```

## 2. 使用SSH连接远程服务器

远程服务器访问人数较多，所以在本地生成密钥对，将公钥传到服务器上，将私钥保存在本地

### 2.1 本地生成SSH密钥对

请参考SSH基础操作

### 2.2 上传公钥到服务器

```bash
ssh-copy-id -i ~/.ssh/xxx.pub username@server_ip
```

如果`ssh-copy-id`不可用，可以手动将公钥内容添加到服务器的`~/.ssh/authorized_keys`文件中

### 2.3 配置SSH远程服务器

先通过SSH密码认证连接远程服务器

```bash
ssh username@server_ip
```

然后输入密码，并在远程服务器的终端中修改SSH配置

[warning] 警告

此操作将修改全局SSH配置，会影响到其他用户
[/warning]

```bash
sudo vim /etc/ssh/sshd_config
```

```ini
PubkeyAuthentication yes           # 启用公钥认证
PasswordAuthentication no          # 禁用密码认证
AuthorizedKeysFile .ssh/authorized_keys # 指定公钥文件路径
```

### 2.4 配置SSH本地客户端

请参考SSH基础操作

使用密钥连接

```bash
ssh xxx
#xxx为Host的值
```
