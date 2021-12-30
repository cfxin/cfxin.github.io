---
title: Mysql 8.0以上重置初始密码的方法(Win10)
date: 2021-12-15 19:51:18
update: 
img: 
top: false
cover: false
toc: true
mathjax: true
summary: 
tags: 
- Mysql
categories: 
- 软件与工具
---

网上大部分的方法都是通过在`My.ini`或是`My_default.ini`中添加`–skip-grant-tables`的方法来实现跳过Mysql密码来连接数据库，并更改密码，然而都没有成功。
> **以下命令行代码均在管理员模式下操作**

### 第一步：关闭Mysql服务
首先，确保自己已经关闭了Mysql的服务
```bash
cd "d:\Program Files\mysql8\bin"(此处输入自己的Mysql安装地址)
net stop mysql
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211215195648.png)

### 第二步：跳过Mysql密码验证
关闭Mysql服务之后，继续在 d:\Program Files\mysql8\bin 目录下进行操作，输入命令
```bash
mysqld --console --skip-grant-tables --shared-memory 
```
在输入这行代码之后，我们就已经成功跳过Mysql的密码登录了
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211215195732.png)

### 第三步：无密码方式进入Mysql
在上述步骤之后，再打开一个管理员模式运行的cmd.exe。

进入 mysql 下的 bin 目录后，直接登录mysql。

在命令行中输入以下代码
```bash
cd "d:\Program Files\mysql8\bin"(此处输入自己的Mysql安装地址)
mysql -u root -p
```

此时会显示让你输入密码，直接回车，就可以成功连接Mysql

### 第四步：将登陆密码设置为空
输入代码，将密码设置为空（此时还不能直接修改密码，必须先设置为空，否则会报错）。
```bash
use mysql; (使用mysql数据表)
update user set authentication_string='' where user='root';（将密码置为空）
quit; (然后退出Mysql)
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211215195806.png)

### 第五步：更改自己的登陆密码
这里分为两个部分

1. 关闭第一个cmd窗口(一定要关闭！)
2. 在第二个窗口中输入代码
```bash
net stop mysql (关闭mysql服务, 虽然会显示没有开启服务，但是以防万一)
net start mysql (再打开mysql服务)
mysql -u root -p
```

此处会显示输入密码，直接回车就好了，第四步我们已经将他置为空了

```bash
ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';（更改密码）
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211215195829.png)

### 最后一步：验证密码是否修改成功
```bash
quit（退出mysql）
mysql -u root -p 
(输入新密码，再次登录)
```
