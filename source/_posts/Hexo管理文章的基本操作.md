---
title: Hexo管理文章的基本操作
date: 2021-12-20 11:06:18
update: 
img: 
top: true
cover: true
coverImg: /medias/coverImg/coverImg4.jpg
toc: true
mathjax: true
summary: 
tags: 
- Hexo
categories: 
- 博客建设
---

## 1. 创建md文件

Hexo 使用 Markdown 解析文章，md文件也就是Markdown文件，通过以下命令创建：
```bash
hexo n <title>
# 例如
hexo n "Hexo管理文章的基本操作"
```

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220111012.png)

这里可以看到创建了一个Hexo管理文章的基本操作.md，保存在`\source\_posts`文件夹下。打开该文件，使用Markdown语法即可书写文章内容。

## 2. 三种布局
创建md文件时，我们可以指定布局，Hexo布局有三种：post（文章）、draft（草稿）、page（页面）。

&nbsp;
在新建文件时，Hexo 会根据 `scaffolds` 文件夹内相对应的文件（可以理解为模板）来建立md文件：

- 如果没有指定布局类型，则为默认布局post，即`hexo n = hexo n post`。
- 当我们创建不同布局的md文件时，它们会存储在不同路径：

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220130338.png)

> 对于page，Hexo会创建一个以标题为名的文件夹，并在该文件夹下生成一个index.md文件，page布局顾名思义就是用来DIY我们博客页面的。

&nbsp;
**draft**：
draft这种布局在创建时会被保存到`\source\_drafts`文件夹中，但不会显示在页面上，如果我们不想某一篇文章显示在页面上，那么就可以把它移动到_drafts文件夹中。
- 可在启动服务器时加上 --draft 参数来查看草稿。`hexo s --draft`
- 可以在站点配置文件中把 render_drafts 参数设为 true 来预览草稿。
- 可以通过 publish 命令将草稿发布文章或者页面，它将会被移动到指定的文件夹。`hexo publish [layout] <title>`

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211220131544.png)

## 3. Front-matter
当我们创建一个md文件后，打开后会看到一些内容，这些称为Front-matter，它是文件最上方以 `---` 分隔的区域，用于指定个别文件的变量，举例来说：

```yaml
---
title: Hexo管理文章的基本操作 # 文章标题，也就是创建时指定的名字
date: 2021-12-20 11:06:18 # 创建时间
tags: # 标签
---
```

> 在Typora中我们在md文件的首行（必须是第一行）输入`---` ，然后按回车就可以插入Front-matter了。
> 注意：参数的`:`后面有一个空格。

- **Front-matter预定义参数**

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211223145713.png)

> **注意**:
> 1. 如果 `img` 属性不填写的话，文章特色图会根据文章标题的 `hashcode` 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图**各有特色**。
> 1. `date` 的值尽量保证每篇文章是唯一的，因为本主题中 `Gitalk` 和 `Gitment` 识别 `id` 是通过 `date` 的值来作为唯一标识的。
> 1. 如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 `_config.yml` 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：[chahuo](http://encode.chahuo.com/)。

最简示例：
```yaml
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
---
```
最全示例：
```yaml
---
title: Hexo管理文章的基本操作
date: 2021-12-20 14:33:20
author: cfxin
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /medias/images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容
categories: Markdown
tags:
  - Typora
  - Markdown
---
```

- **添加分类与标签**
只有文章（post布局）支持分类和标签，需要在Front-matter中设置。分类有层级关系，标签没有。例如：

```yaml
categories:
- 个人博客 #（第一层级）
- Hexo博客 #（第二层级）
tags:
- Hexo
- 博客
```

添加多个分类：

```yaml
categories:
- [日常, 生活]
- [日常, 随想]
```

## 4. 基本操作
- 清除缓存：`hexo clean`
- 生成静态文件：`hexo generate`可简写为`hexo g`
- 启动服务器：`hexo server`简写为`hexo s`，常用参数：`-p`重设端口
- 部署：`hexo deploy`简写为`hexo d`，用于将网站部署到服务器上。常用参数：-g，`hexo d -g`部署前预先生成静态文件。

&nbsp;
一般发布文章或者修改博客后需要这些操作：清除缓存>生成静态文件>启动服务器，测试没问题后再部署。

```bash
hexo clean && hexo s -g # 清除缓存>生成静态文件>启动服务器
hexo d # 部署
```
> 更多操作查看：[Hexo官方文档](https://hexo.bootcss.com/docs/)

