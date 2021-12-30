---
title: PicGo配置图床
top: false
cover: false
toc: true
mathjax: true
date: 2021-12-24 13:36:46
update:
img: https://s2.loli.net/2021/12/24/2aVbRGrFwugK6nv.png
password:
summary:
tags:
- PicGo
- 图床
categories: 软件与工具
---
## PicGo+Gitee搭建个人图床
### 1. PicGo下载安装
进入[PicGo官方地址](https://github.com/Molunerfinn/PicGo/releases)下载所需要的安装包。

安装好后，在软件的插件设置里安装上传gitee所需要的插件，我这里使用的是`gitee-smart 1.1.7`。

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211224135031.png)

### 2. Gitee上创建存放图片的仓库
1. 打开[Gitee官网](https://gitee.com/)创建仓库，如果没注册的先自行注册账号，Gitee免费提供5G的存储空间。

新建仓库时注意：
- 设置为开源
- Readme文件初始化

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211224140258.png)

2. 创建私人令牌

`个人头像-->设置-->私人令牌-->生成新令牌`
> 注意: 令牌生成后只能看见一次, 记得复制粘贴保存下来, 关闭之后就看不到了.

3. 私人令牌权限设置

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211224141514.png)

### 3. 配置PicGo
1. 进入PicGo软件, 选择图床设置, 找到gitee
2. gitee配置如下:

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211224143035.png)

> repo: 用户名/仓库名, 可以在刚创建的仓库里进行复制
> branch: 分支, 创建仓库时选择了master单分支, 所以这里填master
> token: 填刚在Gitee上创建的私人令牌
> path: 图片在仓库中的存储路径，我这里存储在image下
> customPath：默认即可
> customURL: 默认即可


## PicGo配置SM.MS公共图床
### 1. 获得SM.MS的密令Token
SM.MS是一个老牌公共图床, 永久存储免注册，图片链接支持https，可以删除上传的图片，提供多种图片链接格式. 单张图片最大5M，每分钟最多上传10张, 有5G免费空间.

进入[SM.MS官网](https://sm.ms/)注册账号, 点击`User-->Login`注册登录，登录后点击相同的位置，进入Dashboard. 左侧菜单栏找到`API Token`, 创建Token.

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211224145857.png)

### 2. PicGo中配置
在PicGo中配置SM.MS非常简单, PicGO默认支持上传SM.MS图床, 不需要额外安装插件,  只需要填入密令Token即可.

![](https://s2.loli.net/2021/12/24/NehaJXuBEYivjsr.png)

> 附：[PicGo官方指南](https://picgo.github.io/PicGo-Doc/zh/guide/)
