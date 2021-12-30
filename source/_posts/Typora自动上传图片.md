---
title: Typora自动上传图片
date: 2021-12-20 10:35:18
update: 
img: 
top: false
cover: false
toc: true
mathjax: true
summary: 
tags: 
- Typora
categories: 
- 软件与工具
---

## 配合PicGo自动上传图片

1. **下载配置PicGo**

我这里以上传到gitee为例：

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220100720.png)

2. **设置typora和PicGo关联**

文件-->偏好设置-->图像

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220101432.png)

然后开启自动上传：
格式-->图像-->当插入本地图片时-->上传图像

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220101657.png)

## 设置图片居左显示
Typora默认图片是居中显示，通过修改主题样式.css文件可实现默认居左显示。

1. **打开所使用的主题样式文件**

文件-->偏好设置-->外观-->打开主题文件夹

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220102727.png)

2. **打开主题的css文件，在后面添加代码**
```css
p .md-image:only-child{
    width: auto;
    text-align: left;
}
```

3. **重启Typora即可生效**。
