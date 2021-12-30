---
title: git连接GitHub报错port 22 Connection timed out
top: false
cover: false
toc: true
mathjax: true
date: 2021-12-28 11:01:25
update: 
img: https://s2.loli.net/2021/12/24/1xYTHXJLykSuRPE.jpg
password: 
summary: 
categories: 软件与工具
tags: 
- Git
- Github
---
## 前言
使用Git提交代码时，发现报错Connection timed out，然后使用`ssh -T git@github.com`检查连接GitHub，报错：

![](https://s2.loli.net/2021/12/28/QieGVSZPuBDNUyn.png)

## 解决方法
在存放公钥私钥(`id_rsa` 和 `id_rsa.pub`)的同级文件夹中，例如我的是Windows系统，路径为：`C:\Users\2cc\.ssh`。在该文件夹新建`config文本`，内容如下：
```bash
Host github.com
User cfxin@163.com
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
```
> User 后面写的是登录Github的账号;
该配置文件目的是将原来的22端口改为443端口。

再次执行`ssh -T git@github.com`检查，输入yes，可以看到连接成功。

![](https://s2.loli.net/2021/12/28/bkZoPA8LQ5Yifcz.png)
