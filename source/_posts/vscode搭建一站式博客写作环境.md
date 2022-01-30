---
title: vscode搭建一站式博客写作环境
top: true
cover: true
coverImg: /medias/coverImg/coverImg2.jpg
toc: true
mathjax: true
date: 2021-12-28 13:37:50
update: 
img: https://s2.loli.net/2021/12/24/qy6eWLDFU9aTBE8.png
password: 
summary: 
categories: 博客建设
tags: 
- vscode
- Hexo
- PicGo
- markdown
---

## 前言
使用 Github page 和 Hexo 搭建的个人博客，每次写博客时需要在博客根目录下打开`Git Bash Here`，在命令窗口输入新建命令`hexo n`，然后去文件管理器找到新建的`md`文件，再用`markdown编辑器`进行书写，最后书写完需要回到命令窗口输入命令进行预览和部署。这一过程基本需要在三个界面来回切换，相当繁琐。为了更方便的书写，避免来回切换界面，我尝试了在 vscode 中配置一个完整的 Hexo 博客写作环境，即在 vscode 内完成上述所有操作。

主要内容：
- 安装`Markdown Preview Enhanced`插件
- 在vscode终端里添加`Git Bash`终端
- 安装`PicGo`插件
- 开启markdown代码补全功能，通过代码补全快速插入博客文章的`Front matter`。

## 配置markdown环境
vscode 默认是支持 markdown 的，但语法支持以及扩展功能较少，因此需要安装插件来获得更好的书写体验，有两个插件：`Markdown All in One`和`Markdown Preview Enhanced`。

### 1. 安装
这里推荐安装`Markdown Preview Enhanced`插件，简称`MPE`。打开 vscode 编辑器，在插件页搜索 markdown-preview-enhanced，接着点击 Install 按钮。
![](https://s2.loli.net/2021/12/27/rPTNOsdaRSi9nCU.png)

### 2. 使用
MPE 支持一边写一边实时渲染，markdown 基本语法可参考[markdown中文网](http://markdown.p2hp.com/)，MPE插件使用技巧可参考[MPE简介](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)，我这只简单介绍一下基本使用和更换主题。
![](https://s2.loli.net/2021/12/27/SFjHtbvM4gXwPks.png)

预览窗口上`右键-->Preview Theme`更换主题，推荐将主题更换为`vue.css`，因为这个主题的样式基本与Hexo博客渲染出来的效果一致，这样我们在书写时看到的效果就和发布到个人博客网站上看到的效果一样，基本可以省去使用`hexo s -g`进行本地部署预览。
![](https://s2.loli.net/2021/12/27/zi62mBQS1MZnudO.png)

## 配置Git Bash终端
vscode 的终端默认不支持 Git bash，为了直接在 vscode 中打开 Git Bash 终端，需要做以下配置：

### 1. 打开vscode
`文件->首选项->设置`，打开设置，搜索`shell windows`
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211222111931.png)

### 2. 添加配置
打开`settings.json`，在最后一个花括号前输入代码：
```json
// 设置终端默认为git bash
"terminal.integrated.profiles.windows": {
  "gitBash": {
    "path": "D:\\Program Files\\Git\\bin\\bash.exe",//这里是的的bash路径
  }
},
"terminal.integrated.defaultProfile.windows": "gitBash"
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211222112158.png)

### 3. 重启生效
保存重启 vscode，按`ctrl+~`键打开终端，测试是否成功。
![](https://s2.loli.net/2021/12/27/k3hVBpofNt5sugT.png)

## 配置自动上传图床
平时写博客插入图片时，需要切换到图床网站或 PicGo 上传图片，再拷贝连接回来，非常麻烦。而通过 PicGo 插件可以实现直接复制图片到 vscode 中，图片会自动上传到配置好的图床，并在文档内转换为图片链接地址。支持的图床有：`微博`，`七牛图床`，`腾讯云COS`，`又拍云`，`github`，`阿里云OSS`，`imgur`和`SM.MS`。

### 安装PicGo插件
![](https://s2.loli.net/2021/12/27/YP7KIoCWqDvcanx.png)

### 配置Token
我这里使用的是`SM.MS`图床，因此只需要配置 Token 就可以。如果使用的是其它的图床，需要添加对应的配置项。

1. 在 PicGo 插件上`右键-->扩展设置`

找到 `Smms：Token`，填入自己的 Token值。
![](https://s2.loli.net/2021/12/27/tCLp2GoQ94jfbvI.png)

2. 使用

需要插入图片时，使用快捷键上传。
![](https://s2.loli.net/2021/12/27/rDNomitYnh1CQIH.png)

例如：我是windows系统，选中要插入的图片右键复制，在文档中按`ctrl+alt+u`自动上传，上传成功后文档中插入图片的地方返回图片链接。
![](https://s2.loli.net/2021/12/27/HfcgTuaIApjMxQN.png)

默认是`![图片名](图片地址)`的格式，并且会自动以上传时间命名图片。如果不想自动填入图片名称，可以将扩展设置里的`Custom Output Format`修改为如下：
![](https://s2.loli.net/2021/12/27/d6wIPqSBOsjno1A.png)

效果：
![](https://s2.loli.net/2021/12/27/dmLuDsrZ1coPF3N.png)

可以看到`[]`内不再自动填入上传时间。
> 附：
> [PicGo插件配置官方文档](https://picgo.github.io/PicGo-Core-Doc/zh/guide/config.html#%E9%BB%98%E8%AE%A4%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)
> [PicGo搭建图床](https://cfxin.github.io/picgo-pei-zhi-tu-chuang.html)

## 配置博客文件模板
我们知道用`hexo n`命令新建文档会自动根据模板文件插入`Front matter`的内容，而在vscode中直接通过右键新建文件是没有`Front matter`的，需要手动一项一项写书，比较麻烦。为了书写方便，我们可以自定义代码片段，然后利用代码补全功能实现快速插入`Front matter`内容。

### 1. 打开设置
选择左下角`设置 -->用户代码片段`
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227105506.png)

### 2. 打开配置文件
搜索框输入`markdown`，打开`markdown.json`文件
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227105922.png)
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227110412.png)
> `Print to console`：表示代码片段名称；
> `prefix`：表示呼出代码片段时的快捷方式；
> `body`：代码块内容；换行使用\r\n；
> `description`：说明内容，输入快捷方式时VSCode显示的内容；
> `$1,$2,$0`：指定代码模块生成后，编辑光标出现位置; 使用Tab键进行切换(编辑光标按$1,$2,$3...$0的顺序跳转)，$0是光标最后可切换位置。

### 3. 添加模板代码
在文件内输入以下内容：
```json
"Front matter": {
		"prefix": "frm", //输入frm时会提示补全
		"body": [
			"---",
			"title: $TM_FILENAME_BASE", // 读取当前文件名，不带后缀
			"top: false",
			"cover: false",
			"toc: true",
			"mathjax: true",
			"date: $CURRENT_YEAR-$CURRENT_MONTH-$CURRENT_DATE $CURRENT_HOUR:$CURRENT_MINUTE:$CURRENT_SECOND",
			"update: ",
			"img: ",
			"password: ",
			"summary: ",
			"categories: $1", // 光标位置1，补全代码片段后光标会停留在这里
			"tags: ",
			"- $2", // 光标位置2，按tab键光标会切换到这里
			"---",
			"$0", // 光标位置0，最后的位置
		],
		"description": "插入文章的front mater" // 用户输入后智能提示的内容
	}
```
> 内置参数
> `$TM_FILENAME_BASE`：当前文件名，不带后缀
> `$CURRENT_YEAR`：年
> `$CURRENT_MONTH`：月
> `$CURRENT_DATE`：日
> `$CURRENT_HOUR`：时
> `$CURRENT_MINUTE`：分
> `$CURRENT_SECOND`：秒

### 4. 开启markdown的提示功能
vscode默认没有开启markdown的代码补全功能，开启方式：
1. ​`ctrl+shifi+p`打开命令面板，搜索`settings.json`并打开。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227120430.png)

在最后的花括号前添加以下内容，注意在上一条语句后面加逗号`,`​
```json
"[markdown]": {
            "editor.quickSuggestions": true
}
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227120914.png)

2. 重启vscode进行测试
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227121214.png)

可以看到当输入`frm`后出现了代码补全提示，按下`tab或回车键`即可补全代码。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211227121933.png)

此时，在`光标位置1`输入分类名，按`tab键`条到`光标位置2`输入标签名，再按`tab键`跳到`光标位置0`开始正文书写。

## 整体效果
至此，我们就可以只打开vscode完成博客写作，所有的操作在如下图一个界面内均可完成，不需要来回切换界面。
![](https://s2.loli.net/2021/12/27/OIpJgvMnX6zikSL.png)

第一次使用时的流程：打开vscode-->文件-->打开文件夹-->找到博客根目录-->ctrl+~打开终端。vscode会记住上次退出时的工作区，因此下次需要写博客文章时只需要打开vscode就可以了。如果打开后工作环境不是博客写作工作区，那只需要在`最近打开的文件`中切换一下就好。
