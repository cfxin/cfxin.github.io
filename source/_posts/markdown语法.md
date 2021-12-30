---
title: markdown语法
top: false
cover: false
toc: true
mathjax: true
date: 2021-12-27 21:44:46
update: 
img: https://s2.loli.net/2021/12/24/qy6eWLDFU9aTBE8.png
password: 
summary: 
categories: 软件与工具
tags: 
- markdown
---

## 基础语法
### 标题
在文字前面加`#`表示标题，`#`的个数代表标题级数，一个`#`是一级标题，最多6个`#`。
例如：
```markdown
# 一级标题
## 二级标题
### 三级标题
···
###### 六级标题
```
> 注意：#号后面需要一个空格才生效

### 换行
现在大多数 markdown 编辑器都支持直接`按回车键`换行，例如Typora、Markdown Preview Enhanced插件等。若直接`按回车键`不能换行，需以`2个或多个空格`结束一行，然后再`按回车键`，则会另起一行。

### 分段
使用`空白行`分隔一行或多行文本。
```markdown
这是第一段
这还是第一段

这是第二段
```

### 强调
- 加粗：在需要加粗的地方前后添加`2个*号`
- 斜体：在需要斜体的地方前后添加`1个*号`
- 粗斜体：在需要粗斜体的地方前后添加`3个*号`
- 横线删除：在需要删除的地方前后添加`2个~号`

```markdown
**我是粗体**
*我是斜体*
***我是粗斜体***
~~我会被横线删除~~
```
![](https://s2.loli.net/2021/12/28/vq6LjFYyktcxh3w.png)

### 引用
在需要引用的句子或段落前添加1个`>空格`。

- 块引用可以包含多个段落。在段落之间的空白行上添加一个`>`。
- 需要嵌套块引用时，在段落前面添加1个`>>空格`。

```markdown
> 第一段引用
> 
> 第二段引用
>> 第二段引用中的引用
```
![](https://s2.loli.net/2021/12/28/Q1fCRdbAlXYvP6o.png)

### 列表
- 无序列表：在条目前添加1个`-空格`。
- 有序列表：在条目前添加`数字.空格`或`字母.空格`。
- 嵌套列表，在条目前先添加`2个或多个空格`，再写列表。

```markdown
- 条目
- 条目
  - 条目
  - 条目
1. 条目1
2. 条目2
  a. 条目2.1
  b. 条目2.2
```
![](https://s2.loli.net/2021/12/28/oHvPzs56uatRErQ.png)

### 链接
用`[链接名](网址)`插入链接，如果需要连接名则使用`<网址>`的形式。若需要鼠标悬停在链接上时显示提示，则在网址后用引号`' '`添加提示信息。
```markdown
[首页](https://cfxin.github.io)
<https://cfxin.github.io>
[首页](https://cfxin.github.io '提示信息')
```
![](https://s2.loli.net/2021/12/28/tcKyrPkY3E8IxOd.png)

### 图片
用`![图片描述](图片路径或url)`插入图片, 若不需要图片描述，则方括号内空着即可。
```markdown
![图1](https://s2.loli.net/2021/12/27/HfcgTuaIApjMxQN.png)
![图2](/images/2.png)
```

### 代码
- 行内代码：用``括起来。
- 代码块：用一对` ``` `围起来。
  - 在第一个` ``` `后指定语言可语法高亮

![](https://s2.loli.net/2021/12/28/KTmjZ9ilnR4GJpQ.png)

### 分割线
在单独一行上使用3个`-`可插入分割线。
```markdown
水平线上

---

水平线下
```

### 表格
使用如下形式，默认左对齐，`-`相当于`:-`表示左对齐，`-:`表示右对齐，`:-:`表示居中对齐。
```markdown
|表头|表头|
|-|-|
|单元格|单元格|
|单元格|单元格|
```
![](https://s2.loli.net/2021/12/28/eIzKbXZxtDlkp95.png)

> 参考资料：[Markdown中文网](http://markdown.p2hp.com/index.html)、[MPE插件简介](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)
