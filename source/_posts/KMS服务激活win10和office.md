---
title: KMS服务激活win10和office
date: 2021-12-08 12:51:18
update: 
img: 
top: false
cover: false
toc: true
mathjax: true
summary: 
tags: 
- win10激活
categories: 
- 软件与工具
---
## 服务器
服务器地址：[http://kms.03k.org](http://kms.03k.org/)([点击检查是否可用](https://03k.org/go/kmscheck.html))；
服务作用：在线激活windows和office
适用对象：VOL版本的windows和office
适用版本：截止到win10和office2016的所有版本
公开地址有：
> [kms.loli.best](https://moe.best/kms.html)
[kms.cangshui.net](https://kms.cangshui.net/)
[kms.kuretru.com](https://blog.kuretru.com/kms/)

## 激活win10：

1. 一般来说，只要确保的下载的是VL批量版本并且没有手动安装过任何key，你只需要**使用管理员权限运行cmd**执行一句命令就足够：


```bash
slmgr /skms kms.03k.org
```

这句命令的意思是，把kms服务器地址设置（set kms）[为kms.03k.org](https://link.zhihu.com/?target=http%3A//%25E4%25B8%25BAkms.03k.org)，设置成功如下：

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211208124943.png)

2. 然后一句命令手动激活：


```bash
slmgr /ato
```

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211208125022.png)

## 激活office

1. 首先你的office必须是vol版本，否则无法激活。

找到你的office安装目录，比如C:\Program Files (x86)\Microsoft Office\Office16
> 64位的就是C:\Program Files\Microsoft Office\Office16
> office16是office2016，office15就是2013，office14就是2010.

然后目录对的话，该目录下面应该有个OSPP.VBS。

2. 接下来我们就cd到这个目录下面，例如（请更改为自己的实际安装目录）：


```bash
cd "C:\Program Files (x86)\Microsoft Office\Office16"
```

如果你不知道你的office装在哪个目录，可以打开一个程序比如word，然后用打开任务管理员右键选择“打开文件所在的位置”。


3. 然后执行注册kms服务器地址：


```bash
cscript ospp.vbs /sethst:kms.03k.org
```

> /sethst参数就是指定kms服务器地址。


一般ospp.vbs可以拖进去cmd窗口，所以也可以这么弄：

```bash
cscript "C:\Program Files (x86)\Microsoft Office\Office16\OSPP.VBS" /sethst:kms.03k.org
```

一般来说，“一句命令已经完成了”，但一般office不会马上连接kms服务器进行激活，所以我们额外补充一条手动激活命令：

```bash
cscript ospp.vbs /act
```

如果提示看到successful的字样，那么就是激活成功了，重新打开office就好。
