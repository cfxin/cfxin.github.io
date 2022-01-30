---
title: Hexo搭建博客详解
top: true
cover: true
coverImg: /medias/coverImg/coverImg3.jpg
toc: true
mathjax: true
date: 2022-01-02 13:28:16
update: 
img: https://s2.loli.net/2021/12/24/cwnsS7r42JyMQId.png
password: 
summary: 
categories: 博客建设
tags: 
- Hexo
- Matery
---

## 前言
本文是针对新手使用 <font color=#f86b1d>Hexo</font> 搭建个人博客的详细教程，涉及所需要的基础工具的安装与使用，从零定制自己的主题，因此篇幅较长。

使用 <font color=#f86b1d>github pages</font> 服务搭建博客的好处：

- 免费，注册 GitHub 账号可以免费创建个人主页
- 可以随意绑定自己的域名
- 全是静态文件，访问速度快
- 博客内容可以轻松打包、转移、发布到其它平台

> 使用的主题是[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery)，配置过程也参考了该主题[作者的博客](https://blinkfox.github.io/)。

## 1 准备工作
### 1.1 安装Git
Git 是版本控制工具，使用Git把本地的文件上传到 GitHub。在[Git官网](https://git-scm.com/)下载需要的版本，安装选项全部默认即可。在最后一步添加路径时选择`Use Git from the Windows Command Prompt`，这样可以直接在命令提示符里打开 git。安装完成后在命令提示符中输入`git --version`验证是否安装成功。
![](https://s2.loli.net/2021/12/30/wsBKuMpT7CDoXjf.png)

> Windows 系统命令行：win+R 打开 cmd

### 1.2 安装Node.js
Hexo 是基于 <font color=#f86b1d>Node.js</font> 的，Node.js 下载地址：[Download | Node.js](https://nodejs.org/zh-cn/download/) 。下载自己需要的版本，安装 Node.js 会包含环境变量及 npm 的安装，安装选项全部默认即可。安装后，打开命令提示符，输入`node -v`和`npm -v`，如果出现版本号，那么就安装成功了。
![](https://s2.loli.net/2021/12/30/2cEDaU8GpyQzueF.png)

> 可以使用阿里的国内镜像进行加速​
> `npm config set registry https://registry.npm.taobao.org`

### 1.3 创建仓库
登录到 GitHub，如果没有 GitHub 帐号，使用你的邮箱注册 GitHub 帐号：[Sing up](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)。建议用户名用简短的英文小写，方便以后输入个人主页地址。

1. 新建一个名为你的用户名.github.io的仓库
比如说，github 用户名是 test，那么就新建 `test.github.io` 的仓库（必须是你的用户名，其它名称无效），将来网站访问地址就是 `https://test.github.io` 了。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219150755.png)
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219151611.png)

> **注意**：新版 GitHub 默认分支已改为 main，本教程使用的 master 分支，建议先点击 setings 修改为master 再创建。默认 main 分支也可以，只是需要自行修改一些配置。

2. 开启 GitHub Pages
进入仓库，点击`Settings`，向下拉到最后找到 `GitHub Pages`。启用成功后如下，显示的链接即为个人主页地址。    
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219152900.png)

### 1.4 绑定Git和GitHub账号
1. 在任意文件夹下右键打开git bash here，然后输入下面命令：

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

2. 生成ssh密钥文件

```bash
ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```

3. 查看密钥

```bash
cat ~/.ssh/id_rsa.pub
```

4. 打开 github，在头像下面点击 <font color=#f86b1d>settings</font>，再点击 <font color=#f86b1d>SSH and GPG keys</font>，新建一个 SSH，名字随便。将上一步输出的内容复制到框中，点击确定保存。输入`ssh -T git@github.com`，若出现你的用户名说明连接成功。

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219154933.png)
> 如果提示Are you sure you want to continue connecting (yes/no)?，输入yes。

## 2 安装Hexo
### 2.1 Hexo简介
Hexo是一个简单、快速、强大的基于 Github Pages 的博客发布工具，支持 Markdown 格式，有众多优秀插件和主题。官网： [http://hexo.io](http://hexo.io/)，github: [https://github.com/hexojs/hexo](https://github.com/hexojs/hexo)。

由于 github pages 存放的都是静态文件，博客存放的不只是文章内容，还有文章列表、分类、标签、翻页等动态内容，假如每次写完一篇文章都要手动更新博文目录和相关链接信息，那非常麻烦，所以 Hexo 所做的就是将这些 md 文件都放在本地，每次写完文章后调用写好的命令来批量完成相关页面的生成，然后再将有改动的页面提交到 github。

### 2.2 Hexo常用命令
```bash
hexo new "postName" # 新建文章
hexo new page "pageName" # 新建页面
hexo generate # 生成静态页面至public目录
hexo server # 开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy # 部署到GitHub
hexo help  # 查看帮助
hexo version  # 查看Hexo的版本

# 缩写
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy

# 组合命令
hexo s -g # 生成并本地预览
hexo d -g # 生成并上传

# 关闭服务
ctrl+c
```

### 2.3 使用源代码搭建
这种方式适用于想快速搭建好一个漂亮的博客，只需要做好上面的准备工作，然后下载源代码，稍微修改几个配置信息就好了。例如：使用我的配置完成后的博客源文件[Blog-matery](https://github.com/cfxin/Blog-matery)，通过下面的几步操作即可快速获得一个风格类似的博客网站。

1. 打开命令行窗口，输入`npm i hexo-cli -g`安装 Hexo。安装完后输入`hexo -v`验证是否安装成功。

2. 新建一个存放博客的文件夹，在该文件下右键打开`Git Bash Here`，输入命令下载我的博客源码到本地。

```bash
git clone git@github.com:cfxin/Blog-matery.git
```

3. 进入下载的文件内，解压 <font color=#f86b1d>node_modules.zip</font>，然后删除 <font color=#f86b1d>node_modules.zip</font> 和 <font color=#f86b1d>.git</font> 文件夹。

4. 在博客根目录(Blog-matery/)下的`_config.yml`配置文件里修改基本信息

```yaml
title: 网站标题	
subtitle: 网站副标题
description: 简介，这里启用了打字效果
keywords: 网站关键字，便于搜索引擎收录，分类
author: 你的名字
url: 你的博客首页网址，（如：https://xxx.github.io）
repository: 你的仓库地址
```
![](https://s2.loli.net/2021/12/30/uNUmWF1nycqgtfX.png)

5. 在主题目录下的`_config.yml`配置文件里修改基本信息

```yaml
dream: 设置你想展示的文字
favicon:  浏览器标签页里显示的图标，位置：hexo-theme-matery/source/favicon.png
logo: 博客名字旁的图标，位置：hexo-theme-matery/source/medias/logo.png
indexbtn: url为Github个人主页
socialLink: 修改为你自己的社交链接信息，空着表示不启用。
reward: 替换为你自己的二维码图片
profile: 关于页面的个人信息
mySkills: 关于页面的个人技能信息
subtitle:  启用打字效果所显示的文字
githubLink: url为Github个人主页
```

6. 在博客根目录下打开 git bash，使用下面命令生成并浏览博客页面，此时就可以得到一个和源代码作者一样的博客。

```bash
hexo g  # 生成博客网页文件
hexo s  # 本地预览博客
```
![](https://s2.loli.net/2022/01/02/RQwrv61U3JuhPoL.png)
> 到这里已经可以使用 Hexo 写博客，在本地浏览。上传到 GitHub 个人主页仓库的过程后面再详细介绍。

### 2.4 从零开始搭建
这种方式适用于自己从头开始慢慢自定义主题，学习完整的博客搭建过程。

1. 新建一个文件夹，用于存放自己的博客文件，比如 `E:\project\blog`。在该目录下右键点击 Git Bash Here，打开 git 的控制台窗口，以后所有的操作都在 git 控制台进行。输入`npm i hexo-cli -g`安装Hexo。安装完后输入`hexo -v`验证是否安装成功。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219172853.png)

2. 初始化网站，输入`hexo init`初始化文件夹，接着输入`npm install`安装必备的组件。这样本地的网站配置也弄好了，文件夹下也会生成许多文件。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219173722.png)

> node_modules：依赖包
> public：存放生成的页面
> scaffolds：文章模板文件
> source：用来存放你的文章
> themes：存放安装的主题
> _config.yml：博客的配置文件

3. 输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器，然后浏览器打开`http://localhost:4000`，就可以看到我们的博客啦，效果如下：
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219173950.png)

4. 打开博客根目录下的 `_config.yml` 文件，这是博客的配置文件，在这里你可以修改与博客相关的各种信息。修改最后一行的配置，用于连接到之前创建的个人主页仓库。

```yaml
deploy:
  type: 'git'
  repository: git@github.com:用户名/用户名.github.io.git # 之前创建的个人主页仓库地址
  branch: master
```

5. 在博客根目录下右键打开git bash，安装一个扩展`npm i hexo-deployer-git`。输入`hexo new post "文章标题"`，新建一篇文章。然后打开 `E:\project\blog\source\_posts` 的目录，可以发现下面多了一个 `.md` 文件，这个文件就是你的文章文件。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219174541.png)
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219174615.png)

6. 编写完 markdown 文件后，根目录下输入`hexo g`生成静态网页，然后输入`hexo s`可以本地预览效果，最后输入`hexo d`上传到 github 上。这时打开你的 github.io 主页就能看到发布的文章。
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211219181551.png)

> hexo d上传报错的话，可以在这里[链接](https://www.zhihu.com/question/38219432)找找解决方法。

## 3 个性化设置
### 更换主题（matery主题）
主题的原地址在这里：[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery)，该主题作者的博客地址：[闪烁之狐](http://blinkfox.com/2018/09/28/qian-duan/hexo-bo-ke-zhu-ti-zhi-hexo-theme-matery-de-jie-shao/)。按照作者的说明文档进行安装即可。

1. **下载**
在 Hexo 根目录下的 `themes` 文件夹下打开 `Git Bash Here`, 使用 `Git clone` 命令来下载:

```bash
git clone https://github.com/blinkfox/hexo-theme-matery.git
```

2. **切换主题**
修改 Hexo 根目录下的 `_config.yml` 的 `theme` 的值：`theme: hexo-theme-matery`

`_config.yml` 文件的修改建议:
- 修改 `title` 的值为你的博客名字，如`xxxの博客`。
- 修改 `_config.yml` 的 `url` 的值为你的网站主 `URL`，如：`http://xxx.github.io`。
- 建议修改两个 `per_page` 的分页条数值为 `6` 的倍数，如：`12`、`18` 等，这样文章列表在各个屏幕下都能较好的显示。
- 中文用户，则建议修改`language`的值为 `zh-CN`。

> _config.yml 配置文件的[官方详细介绍文档](https://hexo.io/zh-cn/docs/configuration)

### 新建分类 categories 页
`categories` 页是用来展示所有分类的页面，如果在你的博客 `source` 目录下还没有 `categories/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "categories"
```

编辑你刚刚新建的页面文件 `/source/categories/index.md`，至少需要以下内容：
```yaml
---
title: categories
date: 2021-12-20 15:32:02
type: "categories"
layout: "categories"
---
```

### 新建标签 tags 页
`tags` 页是用来展示所有标签的页面，如果在你的博客 `source` 目录下还没有 `tags/index.md` 文件，那么你就需要新建一个，命令如下：
```bash
hexo new page "tags"
```

编辑你刚刚新建的页面文件 `/source/tags/index.md`，至少需要以下内容：
```yaml
---
title: tags
date: 2021-12-20 15:37:36
type: "tags"
layout: "tags"
---
```

### 新建关于我 about 页
about 页是用来展示关于我和我的博客信息的页面，如果在你的博客 source 目录下还没有 `about/index.md` 文件，那么你就需要新建一个，命令如下：
```bash
hexo new page "about"
```

编辑你刚刚新建的页面文件 `/source/about/index.md`，至少需要以下内容：
```yaml
---
title: about
date: 2021-12-20 15:40:00
type: "about"
layout: "about"
---
```

### 新建友情连接 friends 页
friends 页是用来展示友情连接信息的页面，如果在你的博客 source 目录下还没有 `friends/index.md` 文件，那么你就需要新建一个，命令如下：
```bash
hexo new page "friends"
```

编辑你刚刚新建的页面文件 `/source/friends/index.md`，至少需要以下内容：
```yaml
---
title: friends
date: 2021-12-20 15:43:18
type: "friends"
layout: "friends"
---
```

如需添加友情连接，则在你的博客 `source` 目录下新建 `_data` 目录，在 `_data` 目录中新建 `friends.json` 文件，文件内容填写示例：
```json
[{
    "avatar": "http://blinkfox.com/medias/avatar.jpg",
    "name": "闪烁之狐",
    "introduction": "现实的抽象是语言, 语言的抽象是程序, 程序的抽象是数理逻辑, 数理逻辑的抽象是超越认知的真理",
    "url": "http://blinkfox.com/",
    "title": "前去学习"
}, {
    "avatar": "https://cfxin.github.io/medias/avatar.png",
    "name": "程不懂",
    "introduction": "一只程序猿的冒险之路",
    "url": "https://cfxin.github.io/",
    "title": "前去学习"
}]
```

### 代码高亮
由于 Hexo 自带的代码高亮主题显示不好看，所以主题中使用到了 [hexo-prism-plugin](https://github.com/ele828/hexo-prism-plugin) 的 Hexo 插件来做代码高亮，安装命令如下：
```bash
npm i -S hexo-prism-plugin
```

然后，修改 Hexo 根目录下 `_config.yml` 文件中 `highlight.enable` 的值为 `false`，并新增 `prism` 插件相关的配置，主要配置如下：
```yaml
highlight:
  enable: false

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css:
```

若更换之后花括号`{}`无法正常显示，而显示为`&#123;`和`&#125;`，则在博客根目录下找到`node_modules\hexo-prism-plugin\src\index.js`文件，将文件内`map{ }`内容改为如下：
```javascript
const map = {
  '&#39;': '\'',
  '&amp;': '&',
  '&gt;': '>',
  '&lt;': '<',
  '&quot;': '"',
  '&#123;': '{',
  '&#125;': '}'
};
```

### 添加搜索
本主题中还使用到了 [hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 的 Hexo 插件来做内容搜索，安装命令如下：
```bash
npm install hexo-generator-search --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：
```yaml
search:
  path: search.xml
  field: post
```

### 中文链接转拼音
如果你的文章名称是中文的，那么 Hexo 默认生成的永久链接也会有中文，这样不利于 `SEO`，且 gitment 评论对中文链接也不支持。我们可以用 [hexo-permalink-pinyin Hexo](https://github.com/viko16/hexo-permalink-pinyin) 插件使在生成文章时生成中文拼音的永久链接。安装命令如下：
```bash
npm i hexo-permalink-pinyin --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：
```yaml
permalink_pinyin:
  enable: true
  separator: '-' # default: '-'
```

> 除了此插件外，[hexo-abbrlink](https://github.com/rozbo/hexo-abbrlink) 插件也可以生成非中文的链接。

### 文章字数统计插件
如果你想要在文章中显示文章字数、阅读时长信息，可以安装 [hexo-wordcount](https://github.com/willin/hexo-wordcount)插件。安装命令如下：
```bash
npm i --save hexo-wordcount
```

然后在本主题下的 `_config.yml` 文件中，激活以下配置项即可：
```yaml
wordCount:
  enable: false # 将这个值设置为 true 即可.
  postWordCount: true
  min2read: true
  totalCount: true
```

### 修改页脚
页脚信息可以做定制化的修改，需要自己去修改和加工。修改的地方在主题文件夹下的`/layout/_partial/footer.ejs` 文件中，包括站点、使用的主题、访问量等。

### 修改社交链接
在主题的 `_config.yml` 文件中，默认支持 `QQ`、`GitHub` 和`邮箱`的配置，你可以在主题文件的 `/layout/_partial/social-link.ejs`文件中，新增、修改你需要的社交链接地址，增加链接可参考如下代码：
```html
<a href="https://github.com/blinkfox" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
    <i class="fa fa-github"></i>
</a>
```

其中，社交图标（如：`fa-github`）你可以在 [Font Awesome](https://fontawesome.com/icons) 中搜索找到。以下是常用社交图标的标识，供你参考：

- Facebook: fa-facebook
- Twitter: fa-twitter
- Google-plus: fa-google-plus
- Linkedin: fa-linkedin
- Tumblr: fa-tumblr
- Medium: fa-medium
- Slack: fa-slack
- 新浪微博: fa-weibo
- 微信: fa-wechat
- QQ: fa-qq

> 注意: 本主题中使用的 Font Awesome 版本为 4.7.0。

### 修改打赏的二维码图片
在主题文件的 `source/medias/reward` 文件中，你可以替换成你的的微信和支付宝的打赏二维码图片。

### 文章头设置
为了方便新建文章，建议将`/scaffolds/post.md`修改为如下代码，这样就不用自己写头信息，只需要修改信息即可。
```yaml
---
title: {{ title }}
top: false
cover: false
toc: true
mathjax: true
date: {{ date }}
update:
img:
password:
summary:
tags:
categories:
---
```

### 设置动态标签页标题
打开博客主题文件夹，路径：`themes\hexo-theme-matery\layout\layout.ejs`，添加如下代码：
```javascript
<script type="text/javascript">
        var OriginTitile = document.title,
            st;
        document.addEventListener("visibilitychange", function () {
            document.hidden ? (document.title = "🙈看不见我~🙈", clearTimeout(st)) : (document.title =
                "😛被发现了~😘", st = setTimeout(function () {
                    document.title = OriginTitile
                }, 3e3))
        })
</script>
```
![](https://s2.loli.net/2021/12/30/7GgObjxqecPwEnJ.png)
![](https://s2.loli.net/2021/12/30/ZPowMNdtpUasqi3.png)

### 文章生成永久链接
`hexo`编译的站点打开文章的url默认是：`sitename/year/mounth/day/title`四层的结构. 这种结构, 当我们更新文章后会导致文章地址发生改变. 此外, 也不利于网站的SEO优化.

- 方法一: 

我们可以将`url`直接改成`sitename/title`的形式，在博客根目录`_config.yml`文件里修改`permalink`如下：
```yaml
url: https://cfxin.github.io/
root: /
permalink: :title.html
permalink_defaults:
```
> 这种方式不需要额外安装插件, 只要不修改文章标题, 链接就不会改变.

- 方法二:

安装`hexo-abbrlink`插件, 它将原来的URL地址重新进行了进制转换和再编码。
```bash
npm install hexo-abbrlink --save
```

配置博客根目录下的`_config.yml`文件。
```yaml
permalink: archives/:abbrlink.html # 此处可以自己设置，也可以直接使用 :/abbrlink
abbrlink:
  alg: crc32  # 使用的加密算法
  rep: hex    # 十六进制
```
> 这种方式可以保证在我们修改了博客标题或博客发生更新之后都不会改变链接地址。

### 添加Emoji表情支持
为了使我们的博客文章可以显示`Emoji`表情，需要安装[hexo-filter-github-emojis](https://npmmirror.com/package/hexo-filter-github-emojis)插件。该插件可以把用markdown emoji语法（:smile:）解析成对应的表情。
![](https://s2.loli.net/2021/12/30/1VAbpEBRfLGl2ej.png)
安装命令：
```bash
npm install hexo-filter-github-emojis --save
```

然后，在 Hexo 博客根目录下的`_config.yml`文件中，添加配置项：
```yaml
githubEmojis:
  enable: true
  className: github-emoji
  inject: true
  styles:
  customEmojis:
```
> 如果你用的微软输入法，那使用快捷`win+.`或`右键-->表情符号`，可以调出Emoji表情符号。直接输入这些表情，hexo博客文章里也是能正常显示的，不需要安装上面的插件。
> [Emoji词典](https://www.emojiall.com/zh-hans)

### 图片懒加载
图片懒加载是用于优化网站加载速度的，它的原理是当你翻到图片的时候再加载那张图片，而不是以下将本页面的所有图片都加载完。需要用到`hexo-lazyload-image`插件，安装命令：
```bash
npm install hexo-lazyload-image --save
```

然后，在 Hexo 博客根目录下的`_config.yml`文件中，添加配置项：
```yaml
lazyload:
  enable: true
  onlypost: true
  loadingImg: /medias/loading.gif # 图片地址
```

分享一个我使用的动图：
![](https://s2.loli.net/2021/12/30/ZpycPsXoVzuTd3w.gif)

> - `onlypost`：是否仅文章中的图片做懒加载，如果为 false，则主题中的其他图片，也会做懒加载，如头像，logo 等任何图片。
> - `loadingImg`：图片未加载时的代替图，不填写使用默认加载图片，如果需要自定义，添填入 loading 图片地址，如果是本地图片，不要忘记把图片添加到你的主题目录下。 matery 主题可以将图片放到 \hexo-theme-matery\source\medias 目录下，然后引用时：loadingImg: /medias/图片文件名

`注意`：使用图片懒加载可能会出现点击文章内图片放大查看时，全部显示为loading加载图。我使用的matery主题出现了该问题，解决方法是修改主题文件下的`\source\js\matery.js`，在 108 行左右添加以下代码：
```javascript
$(document).find('img[data-original]').each(function(){
    $(this).parent().attr("href", $(this).attr("data-original"));
});
```

### 修改统计图的开始时间
在关于页面内，文章发布统计图的开始时间默认是：当前年-月减一年，例如，我是2021年12月开始搭建博客发布文章，统计图的开始时间就是2020年12月。
![](https://s2.loli.net/2021/12/30/MaJykhIDmoRNjKG.png)

这个开始时间设置的代码在`themes/matery/layout/_widget/post-charts.ejs`中，大约在 39 行左右，源代码为：
```javascript
var startDate = moment().subtract(1, 'years').startOf('month');
```

其中，`subtract(1, 'years')`表示的就是当前时间减`1年`，数字的取值范围是`0-10`之间。我将其改为从上个月开始，即当前时间减`1个月`，修改后代码如下：
```javascript
var startDate = moment().subtract(1, 'months').startOf('month');
```
![](https://s2.loli.net/2021/12/30/zNrgABwE4omybD3.png)

### 修改字体
我这里以思源宋体为例。

- 在主题目录下的`source`文件夹内创建一个名为`font`的文件夹，用来统一存放你要用到的字体。
- 将要用到的字体放入创建的文件夹内，如 `matery/source/font/SourceHanSerif.ttc`
- 找到主题文件夹下的`my.css`文件，路径为`/themes/matery/source/css/my.css`，填入下面的代码：

```css
@font-face{
    font-family: 'SourceHanSerif';
    src: url('../font/SourceHanSerif.ttc');
}
body{
    font-family: 'SourceHanSerif';
}
```

### 添加自己的导航页
给博客添加一个导航页，用于放一些自己经常访问的网站。

- 首先，新建一个`页面(page)`，执行下面的命令：

```bash
hexo new page navigate
```

- `navigate`目录下的`index.md`写入以下内容：

```yaml
---
title: navigate
date: 2021-12-30 20:52:28
type: "navigate"
layout: "navigate"
---
```

- 在主题目下的`_config.yml`配置文件中`menu:`选项里添加导航页

```yaml
导航:
    url: /navigate
    icon: fas fa-location-arrow
```

- `/layout`下新建`navigate.ejs`，写入以下代码，其中导航链接根据自己的需要修改：

```html
<div class="navi-height bg-cover pd-header "><div class=" link-box container"><!--搜索框--><div class="baidu baidu-2 large-screen"><form name="f"action="https://www.baidu.com/"target="_blank"><div id="Select-2"><div class="Select-box-2"id="baidu"><ul style="height: 46px;"><li class="this_s">百度</li><!--<li class="bing_s">必应</li>--><li class="google_s">谷歌</li><li class="baidu_s">百度</li></ul></div><input name="wd"id="kw-2"maxlength="100"autocomplete="off"type="text"></div><div class="qingkong"id="qingkong"title="清 除"style="display: none;">X</div><input value="搜 索"id="su-2"type="submit"><ul class="keylist"></ul></form></div><!--链接--><div class="row tags-posts "><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">📺娱乐📺</div><ul class="jj-list-con"><li><a href="https://cupfox.app/"class="link-3"target="_blank">茶杯狐</a><li><a href="https://www.playm3u8.cn/jiexi.php?url="class="link-3"target="_blank">Playm3u8解析</a></li><li><a href="https://www.zhihu.com/explore"class="link-3"target="_blank">知乎</a></li></li><li><a href="https://v.qq.com/"class="link-3"target="_blank">腾讯视频</a></li><li><a href="http://www.iqiyi.com/"class="link-3"target="_blank">爱奇艺</a></li><li><a href="https://www.bilibili.com/"class="link-3"target="_blank">哔哩哔哩</a></li><li><a href="https://piaofang.maoyan.com/dashboard"class="link-3"target="_blank">猫眼电影</a></li><li><a href="https://book.douban.com/"class="link-3"target="_blank">豆瓣读书</a></li><li><a href="https://www.douyu.com/directory/all"class="link-3"target="_blank">斗鱼</a></li></ul></div></div><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">🧰工具🧰</div><ul class="jj-list-con"><li><a href="https://tools.pdf24.org/zh/"class="link-3"target="_blank">PDF24 Tools</a></li><li><a href="https://tool.lu/"class="link-3"target="_blank">在线工具箱</a></li><li><a href="https://sm.ms/"class="link-3"target="_blank">SM.MS图床</a></li><li><a href="https://www.fococlipping.com/"class="link-3"target="_blank">去除图像背景</a></li><li><a href="https://uutool.cn/gif-edit/"class="link-3"target="_blank">GIF图片修改</a></li><li><a href="https://docsmall.com/"class="link-3"target="_blank">图片压缩</a></li><li><a href="https://trace.moe/"class="link-3"target="_blank">动漫场景搜索</a></li><li><a href="https://getavataaars.com/"class="link-3"target="_blank">Q版头像生成器</a></li><li><a href="https://cowtransfer.com/"class="link-3"target="_blank">奶牛快传</a></li></ul></div></div><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">👨‍💻编程👨‍💻</div><ul class="jj-list-con"><li><a href="https://www.dotcpp.com/run/"class="link-3"target="_blank">CPP在线编译</a></li><li><a href="https://mofanpy.com/"class="link-3"target="_blank">莫烦Python</a></li><li><a href="https://leetcode-cn.com/"class="link-3"target="_blank">力扣</a></li><li><a href="https://visualgo.net/zh"class="link-3"target="_blank">算法可视化</a></li><li><a href="http://deeprl.neurondance.com/"class="link-3"target="_blank">强化学习实验室</a></li><li><a href="https://c.runoob.com/"class="link-3"target="_blank">菜鸟工具</a></li><li><a href="https://github.com/"class="link-3"target="_blank">Github</a></li><li><a href="https://r2coding.com/#/"class="link-3"target="_blank">吾爱破解</a></li><li><a href="https://my.openwrite.cn/"class="link-3"target="_blank">Road To Coding</a></li></ul></div></div><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">🙆‍♂️资源🙆‍♂️</div><ul class="jj-list-con"><li><a href="https://wall.alphacoders.com/?lang=Chinese"class="link-3"target="_blank">高清壁纸</a></li><li><a href="https://www.100font.com/"class="link-3"target="_blank">免费字体</a></li><li><a href="https://www.flaticon.com/"class="link-3"target="_blank">免费图标</a></li><li><a href="https://www.emojiall.com/zh-hans"class="link-3"target="_blank">Emoji字典</a></li><li><a href="https://fontawesome.com/"class="link-3"target="_blank">Font Awesome</a></li><li><a href="http://zhongguose.com/"class="link-3"target="_blank">中国色</a></li><li><a href="https://github-trending.com/"class="link-3"target="_blank">GitHub趋势</a></li><li><a href="https://www.tiobe.com/"class="link-3"target="_blank">编程趋势</a></li><li><a href="https://trends.google.com/"class="link-3"target="_blank">Google趋势</a></li></ul></div></div><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">🔔社区🔔</div><ul class="jj-list-con"><li><a href="https://www.oschina.net/"class="link-3"target="_blank">开源中国</a></li><li><a href="https://hellogithub.com/"class="link-3"target="_blank">Hello GitHub</a></li><li><a href="https://www.icourse163.org/"class="link-3"target="_blank">中国大学慕课</a></li><li><a href="https://open.163.com/"class="link-3"target="_blank">网易公开课</a></li><li><a href="https://www.ituring.com.cn/"class="link-3"target="_blank">图灵社区</a></li><li><a href="https://www.runoob.com/"class="link-3"target="_blank">菜鸟教程</a></li><li><a href="https://distrowatch.com/"class="link-3"target="_blank">Linux发行版</a></li><li><a href="https://www.lanqiao.cn/library/"class="link-3"target="_blank">蓝桥云课</a></li><li><a href="https://www.aminer.cn/"class="link-3"target="_blank">AI科技情报</a></li></ul></div></div><div class="col s12 m6 l4 friend-div"data-aos="zoom-in-up"><div class="card"><div class="jj-list-tit">💡其他💡</div><ul class="jj-list-con"><li><a href="https://ac.scmor.com/"class="link-3"target="_blank">谷歌学术镜像</a></li><li><a href="http://www.pansoso.com/"class="link-3"target="_blank">网盘搜索</a></li><li><a href="https://www.yikm.net/"class="link-3"target="_blank">小霸王</a></li><li><a href="http://www.tbtool.cn/"class="link-3"target="_blank">图吧工具箱</a></li><li><a href="https://carbon.now.sh/"class="link-3"target="_blank">代码图片</a></li><li><a href="https://dddd.cool/#/register?code=ugH0ehti"class="link-3"target="_blank">懂的都懂</a></li><li><a href="https://color.adobe.com/zh/explore/?filter=newest"class="link-3"target="_blank">调色盘</a></li><li><a href="https://hexo.io/zh-cn/"class="link-3"target="_blank">Hexo</a></li><li><a href="https://pages.aliyundrive.com/mobile-page/web/beinvited.html?code=5dc456c"class="link-3"target="_blank">阿里云盘</a></li></ul></div></div></div><script>$('.Select-box ul').hover(function(){$(this).css('height','auto')},function(){$(this).css('height','40px')});$('.Select-box-2 ul').hover(function(){$(this).css('height','auto')},function(){$(this).css('height','46px')});$('.Select-box li').click(function(){var _tihs=$(this).attr('class');var _html=$(this).html();if(_tihs=='baidu_s'){_tihs='https://www.baidu.com/s';_name='wd'}if(_tihs=='google_s'){_tihs='https://www.google.com/search';_name='q'}if(_tihs=='bing_s'){_tihs='https://www.bing.com/search';_name='q'}$('.baidu form').attr('action',_tihs);$('.this_s').html(_html);$('#kw').attr('name',_name);$('.Select-box ul').css('height','40px')});$('.Select-box-2 li').click(function(){var _tihs=$(this).attr('class');var _html=$(this).html();if(_tihs=='baidu_s'){_tihs='https://www.baidu.com/s';_name='wd'}if(_tihs=='google_s'){_tihs='https://www.google.com/search';_name='q'}if(_tihs=='bing_s'){_tihs='https://www.bing.com/search';_name='q'}$('.baidu form').attr('action',_tihs);$('.this_s').html(_html);$('#kw-2').attr('name',_name);$('.Select-box-2 ul').css('height','48px')});</script></div></div><style>*{margin:0;padding:0;font-family:"思源宋体"}ul,li,h1,h2,h3,h4,h5,h6,p,form,dl,dt,dd{margin:0px;padding:0px;font-size:16px;font-weight:normal}img{border-style:none}li{list-style:none;float:left}a{text-decoration:none}.card{background-color:rgba(25,240,229,0);width:96%;margin-left:2%}.baidu{float:left;margin-left:100px}.baidu form{position:relative}.Select-box ul{height:40px;position:absolute;left:-1px;top:0px;z-index:9999;background:#FFF;border:1px solid#ccc;border-top:none;overflow:hidden}.Select-box li{width:60px;line-height:40px;font-size:16px;color:#484848;border:0;cursor:pointer}.Select-box li:hover{background:#0f9d58;color:#FFF}.Select-box.this_s{color:#0f9d58}.Select-box.this_s:hover{background:#FFF;color:#0f9d58}.qingkong{position:absolute;right:120px;top:12px;width:18px;height:18px;background:rgba(0,0,0,0.1);border-radius:18px;line-height:16px;color:#666666;cursor:pointer;text-align:center;font-size:14px;display:none}.qingkong:hover{background:rgba(0,0,0,0.2)}.qingkong:active{background:rgba(0,0,0,0.3)}.baidu-2{width:100%;height:110px;margin:0 auto;background:none;padding-top:50px}.baidu-2 form{width:520px;margin:0 auto}.baidu-2 input{padding:13px 8px;opacity:0.9;font-size:15px}#Select-2{float:left}.Select-box-2{text-align:center;float:left;position:relative}.Select-box-2 ul{height:46px;position:absolute;left:0px;top:1px;z-index:9999;background:rgba(255,255,255,0.9);border:1px solid#ccc;border-top:none;border-radius:10px 0 0 10px;overflow:hidden}.Select-box-2 li{width:60px;line-height:45px;font-size:16px;color:#484848;border:0;cursor:pointer}.Select-box-2 li:hover{background:#0f9d58;color:#FFF}.Select-box-2 .this_s{color:#0f9d58}.Select-box-2 .this_s:hover{background:none;color:#0f9d58}#kw-2{width:335px;outline:0;border:1px solid#ccc;background:rgba(255,255,255,0.2);color:#000000;padding-left:70px;font-weight:bold;border-radius:10px 0 0 10px}#su-2{width:90px;height:47px;font-size:16px;background:#0f9d58;border:none;border-top:#3385ff 1px solid;border-bottom:1px solid#2d78f4;color:#FFF;cursor:pointer;outline:none;border-radius:0 10px 10px 0}#su-2:hover{background:blue;border-bottom:1px solid blue}#su-2:active{background:blue;box-shadow:inset 1px 1px 3px blue;-webkit-box-shadow:inset 1px 1px 3px blue}.jj-list-tit{font-size:16px;line-height:25px;color:#ffffff;width:100%;padding-left:38.5%}.jj-list-con{overflow:hidden;margin:0 auto}.jj-list-con li{width:31.333%;margin:1%}.link-3{display:block;background:rgba(0,0,0,.35);color:#FFF;font-size:13px;text-align:center;line-height:35px;padding:4px 0;border-radius:2px;transition:all 0.2s}.link-3:hover{background:rgba(0,0,0,.45);font-size:15px;font-weight:bold}@media only screen and(max-width:584px){.navi-height{height:1300px}.link-box{margin-top:5%}.large-screen{display:none}}@media only screen and(min-width:584px)and(max-width:993px){.navi-height{height:800px}.link-box{margin-top:5%}.large-screen{display:none}}@media only screen and(min-width:993px){.navi-height{position:absolute;width:100%;height:100%}}.page-footer{display:none}</style><%if(theme.banner.enable){%><script>var bannerUrl="<%- theme.jsDelivr.url %><%- url_for('/medias/banner/') %>"+new Date().getDay()+'.jpg';$('.bg-cover').css('background-image','url('+bannerUrl+')');</script><%}else{%><script>$('.bg-cover').css('background-image','url(<%- theme.jsDelivr.url %><%- url_for('/medias/banner/0.jpg') %>)');</script><%}%>
```
> 注意：这里字体使用的是思源宋体，可以根据自己的需要修改为其它字体。
> 为了减小文章篇幅这里将代码压缩成了一行，代码粘贴后可以通过编辑器的格式化处理或者在线代码美化工具将代码展开，方便修改。

### 添加今日诗词
[今日诗词](https://www.jinrishici.com/) 每次返回一句诗词，根据时间、地点、天气、事件智能推荐。使用前需要将主题配置文件中`subtitle`的值改为`false`。配置方式，在`/themes/matery/layout/_partial/head.ejs`中添加下面的一行代码：
```javascript
<!-- 添加每日诗词 -->
    <script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
```
![](https://s2.loli.net/2021/12/31/n8Vs4GuSJNi7vgb.png)

然后再将`/themes/matery/layout/_partial/bg-cover-content.ejs`中的`<%= config.description %>`修改为：
```javascript
<span id="jinrishici-sentence">正在加载今日诗词....</span>
```
![](https://s2.loli.net/2021/12/31/b84LmMdNwW5goc3.png)

## 备份博客源文件
我们写完博客使用`hexo d`部署到Github仓库，这里上传的是转换后的静态html文件以及所依赖的库文件，而不是我们的源文件。当我们换一台电脑写博客时，直接克隆这个仓库的文件是不行的，因此我们需要把博客源文件上传到GitHub，一来可以方便我们更换电脑后快速部署博客，二来可以备份我们的笔记源文件。

1. 在 github 博客仓库下新建一个分支`hexo`，然后`git clone`到本地，把`.git`文件夹拿出来，放在博客根目录下。

![](https://s2.loli.net/2021/12/30/YmdQK6EvWlTiu4D.png)
![](https://s2.loli.net/2021/12/30/7CE9zZt3ejUAVT2.png)


2. 在博客根目录打开git bash，使用`git checkout hexo`切换到`hexo`分支，然后`git add .`，然后`git commit -m "备份"`，最后`git push origin hexo`提交就行了。

![](https://s2.loli.net/2021/12/30/GlJrHI1S9Mby7fx.png#crop=0&crop=0&crop=1&crop=1&id=h6MwL&originHeight=227&originWidth=801&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)

> 如果`git add .`时提示warning: adding embedded git repository: .deploy_git，是因为你已经部署到Github，将.deploy_git整个文件夹删除，再重新add即可。

当然，如果不想使用分支，也可以直接再新建一个仓库来存放博客源文件。
