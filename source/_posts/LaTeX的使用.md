---
title: LaTeX的使用
date: 2021-12-13 14:33:20
update: 
img: 
top: true
cover: true
coverImg: /medias/coverImg/coverImg1.jpg
toc: true
mathjax: true
summary: 
tags: 
- Latex
- overleaf
- 论文写作
categories: 软件与工具
---

# LaTeX基础

## TEX是什么
TEX 是高德纳 (Donald E. Knuth) 为排版文字和数学公式而开发的程序。

- TEX 系统提供了 300 + 600 多条基本的排版命令 
- TEX 是目前公认的数学公式排版最好的排版语言
- TEX 是免费的 
- TEX 的名字来自大写的希腊字母 (τ, ϵ, χ)，意思是“科技”和“艺术” 

## LaTeX是什么
LaTeX 是一个写作工具，可以用于创建具有专业排版的文档。它基于所见即所得的思想，即写作者只需要关注文档的内容，而计算机负责将其格式化。用户不再需要像 Word 中那样，在页面上用空格来控制格式，而是只需要输入纯文本，让 LaTeX 处理剩下的一切。
>  LaTeX 是一种使用 TEX 程序作为排版引擎的格式，可以粗略地将它理解成是对 TEX 的一层封装。 

## LaTeX的用处
LaTeX 被广泛应用于科学文档、书籍以及许多其他出版物。它不仅可以创建精美的排版文档，而且还使得用户可以很快速地处理复杂的排版问题，比如输入数学公式、创建目录、管理引用、创建书目、保持布局一致等等。由于可用的开源软件包数量众多，因此 LaTeX 有无限的可能性。这些软件包赋予了用户更多的能力，例如添加脚注，绘制原理图，创建表格等。

&nbsp;
人们使用 LaTeX 的最重要原因之一就是它分离了文档的内容与样式。这意味着你只需要编写文档的内容，我们就可以轻松更改其外观。同样，你也可以创建一个文档模板，用它来统一许多不同文档的外观，这样学术期刊可以创建投稿模板。这些模板具有预制的布局，只需要往里面添加内容即可。实际上，LaTeX 有数百种模板，覆盖从简历到幻灯片的所有内容。

## LaTeX的优点
- LaTeX 特点
   - 专注于内容撰写，很少操心文档的版面设计
   - 自动编号：章节、图表、公式定理、参考文献 ·······
   - 自动生成目录、索引
   - 公式、定理、参考文献、插图、页码等可以交叉引用
   - 可以通过各种宏包扩展其功能, 实现各种特殊要求
- LaTeX VS. Word
   - Word 简单易用，所见即所得，普通办公文档建议用 Word
   - LaTeX 输出美观，质量高，科技排版 (特别是数学) 推荐使用 LaTeX
   - LaTeX 能实现 Word 的所有功能，定制性高，但易用性不如 Word


## 写LaTeX的工具
### TEX的发行版
- Windows 系统：TeXLive (推荐)，MiKTeX，CTEX 套装 (不推荐)
- Unix/Linux 系统：TeXLive
- Mac OS 系统：TeXLive，MacTeX

### 下载和安装
- TeXLive : [http://tug.org/texlive/](http://tug.org/texlive/) (大而全，全部宏包)
- 编辑器: WinEdt, TeXworks, TeXmaker, TeXStudio, vim, emacs, ...
- 安装演示: 以 [TeXLive 2017](http://math.ecnu.edu.cn/~jypan/Teaching/Latex/Install/install_texlive_gb2312.html) 为例

### 在线平台[Overleaf](https://cn.overleaf.com/)
本文章接下来对LaTeX的使用介绍主要以该平台为例。

---

# LaTeX排版
## LaTeX文稿的排版过程
1. **编写源文件**：tex 源文件为纯文本文件，以 `.tex` 为扩展名
	- 可以使用任何文本编辑器编写, 如: WinEdt, EditPlus, Vi, Emacs, 推荐 WinEdt，专门针对 tex 开发, 提供许多便捷功能, 有助于提高排版效率

2. **编译**：用 `pdflatex` (英文文档) 或 `xelatex` (中文文档) 编译，生成相应的 pdf 文件

![来源：华东师范大学潘建瑜老师的课件](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212181900.png)


## 第一个LaTeX文件
创建一个新的 LaTeX 项目。你可以在自己的电脑上创建 `.tex` 文件，也可以在 Overleaf 中启动新项目。让我们从最简单的示例开始：
```latex
\documentclass{article} %指定文档类型
% 序言区
%
\begin{document}
% 正文
First document. This is a simple example, with no extra parameters or packages included.
\end{document}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212183155.png)

可以看到，LaTeX 已经对文本进行了格式化（如首行缩进）。下面我们仔细看一下上面这段代码每个部分的功能。

- 代码的第一行声明了文档的类型，称为**类 (class)**。类控制文档的整体外观，不同类型的文档需要选择不同的类，比如，简历与论文需要不同的类。在这个例子中，类是 `article`，是最简单和最常见的 LaTeX 类。其他类型的文档可能需要使用不同的类，例如 `book` 或 `report`。

- 在`\begin {document}` 和 `\end {document}`这两个标记之间写入文档内容。这部分就是文档的**主体 (body)**，你可以在此处开始编写和更改文本。要在 PDF 中查看更改的结果，必须首先编译文档。

> 在 Overleaf 中只需单击 重新编译（Recompile）。还可以单击重新编译按钮旁边的小箭头，并将 “自动编译” 设置为 “开”，这样编辑文件时项目将会自动重新编译。
> LATEX 源文件: 正文 + 命令 + 注解
> 排版命令 (简称 命令): 反斜杠开头的字符串
> 注解符: 百分号 %，注释的内容不会被显示出来
> 文档类型: \documentclass{...} (论文, 书籍, 幻灯片, 海报)
> 环境: `\begin{...}` 开头, `\end{...}` 结尾


## LaTex命令
```latex
\command
\command[option]{arguments}
```

- 方括号中的是可选的 (称为选项)，花括号中的参数是必需的。

```latex
例: 一些常用命令
\documentcalss, \title, \author, \date, \usepackage
\begin{环境名}, \end{环境名} 组成一个环境
```

- 定义新命令

```latex
\newcommand{新命令}{命令内容}
\renewcommand{已有命令}{命令内容}

例：
\newcommand{\eps}{\varepsilon} % $\eps$ = ε
```


## 分组和环境
- 分组
   - 有些命令只对其参数起作用，如`\textbf{abc}`
   - 有些命令对后面所有的内容都起作用，这些命令通常也称为声明，如`\bfseries`
   - 可以利用大括号 (即分组) 来限制声明的作用范围

```latex
This is \textbf{bold face} style.    % bold face 粗体显示
This is \bfseries bold face style.   % bold face style. 粗体显示
This is {\bfseries bold face} style. % bold face 粗体显示
```

- 环境：某些具有特定格式的内容需要放在相应的环境中, 如表格，数学公式等
	- document 是 LaTeX 的一个最基本的环境，一篇文档有且只能有一个 document 环境

```latex
\begin{环境名}
.
.
.
\end{环境名}
```

## 文档的序言区
在基本框架中，文本是在 `\begin {document}` 命令之后输入的。在这个命令之前 `.tex` 文件中的所有内容都称为 **序言 (preamble)**。
```latex
\documentclass[12pt, letterpaper]{article}
\usepackage[utf8]{inputenc}
```

-  位于源文件的最前面, 用于指定文档的整体结构和布局, 必须且只能选一种
   - 常用文档类: article, book, beamer, ctexart, ctexbook, ctexbeamer. 常用选项:
      - 10pt(缺省值)，11pt，12pt，指定基本字体的大小
      - letterpaper(缺省值)，a4paper，a5paper，...  指定纸张的大小
      - 单双面选项：oneside，twoside，openright，openany
      - 数学公式：leqno (公式编号在左边)，fleqn (靠左显示行间公式)
- 导言区用于放置**全局控制命令**，如：调用宏包，设置页面大小，...
- 放在导言区的命令对整个文档都起作用

> 更多有关 [页面大小和边距](https://www.overleaf.com/learn/Page_size_and_margins) 的信息，可以参阅这篇文章。

`\usepackage[utf8]{inputenc}`这行命令指定了文档的编码，可以省略或更改为其他编码，但建议使用 utf-8。除非特别需要其他编码，否则请将此行添加到序言中。

## 添加标题、作者和日期
要将标题、作者和日期添加到文档中，就必须**在序言中**（不是文章的主体中）添加下面三行。它们是：
- `\title{标题}`
- `\author{姓名}`
   - `\thanks{简介}`在 author 命令的大括号里添加这条命令，可以添加上标和脚注。如果你需要在文章中感谢一个机构，这个功能将非常有用。
- `\date{February 2021}`你可以手动输入日期，或使用 \today 命令，以便在编译文档时自动更新日期。

&nbsp;
现在可以使用 `\maketitle` 命令在文档上打印这些信息。这条命令应该写在文档 主体 (body) 中你想要打印标题的位置。示例：

```latex
\documentclass[12pt, letterpaper, twoside]{article}
\usepackage[utf8]{inputenc}

\title{LaTeX Tutorial}
\author{Cheng Budong \thanks{School of computer Science and Engineering}}
\date{December 2021}

\begin{document}
\maketitle
We have now added a title, author and date to our first \LaTeX{} document!
\end{document}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212194706.png)

## 换行，分段，分页
- 换行：自然换行 (若需强制换行，可使用 `\\` 或 `\linebreak`)
   - 一般情况下, 不建议使用强制换行
- 分段：一个空行或 `\par`
   - 建议使用空行进行分段，简洁直观
- 分页：自然分页，若需 强制分页, 可用 `\newpage`，`\clearpage` 或 `\pagebreak`
   - 一般情况下，不建议使用强制分页
- 行间距：行间距伸展因子 `\baselinestretch` 或伸展命令 `\linespread`
```latex
\renewcommand{\baselinestretch}{1.2}
\linespread{1.2}
```

- 段落间距和段落缩进：用自动设定的即可，英文每节的第一段首行不会自动缩进

> 可以在这篇有关 [段落和换行](https://www.overleaf.com/learn/Paragraphs_and_new_lines) 的文章中找到更多信息。


## 加粗、斜体和下划线
- 加粗：在 LaTeX 中，加粗字体使用 `\textbf{}` 命令。
- 斜体：在 LaTeX 中，斜体使用 `\textit{}` 命令。
- 下划线：在 LaTeX 中，下划线使用 `\underline{}` 命令。

示例：
```latex
Some of the \textbf{greatest}
were made by \textbf{\textit{accident}}.
discoveries in \underline{science}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212200351.png)


## 引入宏包
宏包可用于更改 LaTeX 文档的默认外观，或实现更多功能。

- 宏包调用方法 (只能出现在导言区)  `\usepackage[选项]{宏包名}`
- 如果宏包不带选项, 则可以多个一起调用, 如: 

```latex
\usepackage{amsmath,amssymb,amsfonts}
\usepackage[pagebackref]{hyperref}
\usepackage[numbers,sort&compress]{natbib}
```


## 添加图片
LaTeX本身不能管理图像，因此需要使用一个 包 (package)。在这个例子中，要实现在文档中添加图片，需要使用 graphicx 包。graphicx 包提供了新的命令`\includegraphics{}`和`\graphicspath{}`。

- 支持的图片格式：pdf，jpg，png (pdfLaTeX 和 xeLaTeX 编译)
   - eps 格式的图片，epstopdf 宏包, 自动将 eps 转换为 pdf
- 图形文件名中可以含路径
- 常用选项有
   - width, height：指定图形的宽度和高度 (若只指定宽度或高度, 则按比例缩放)
   - scale：缩放因子，如 scale=0.5

添加图片的示例：
```latex
% 在序言区导入包
\usepackage{graphicx}
\graphicspath{{images/}} % 告诉LaTeX，这些图片保存在当前目录下名为images的文件夹中。

% 在需要插入图片的地方写
\includegraphics[scale=0.5]{overleaf.png} % 将图像实际包含在文档中的命令，scale缩放因子
```

> 注意：在 Overleaf 中，你需要首先上传图片。有关更多详细信息，请参见有关[生成高分辨率和低分辨率图像](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes#Generating_high-res_and_low-res_images)的内容。

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212204315.png)


### 标题、标签和引用
可以像下面这样，在 figure 环境中对图片添加标题、标签和引用。

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.5\textwidth]{overleaf}
    \caption{overleaf icon}
    \label{fig:icon}
\end{figure}
As you can see in the figure \ref{fig:icon}.
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212210237.png)

在这个示例中，有三个重要的命令：

- \caption{overleaf icon}：此命令为图形设置标题。你可以将这条命令放置在图的上方或下方。
- \label{fig:icon}：如果你需要在文档中引用图像，请使用这条命令为图像设置标签。标签可以为图像编上号，并与下一个命令结合，对图片进行引用。
- \ref{fig:icon}：这条命令在编译后将显示替换为被引用图片对应的编号。

> 将图像放置在 LaTeX 文档中时，应始终将它们放置在 figure 环境或类似环境中，以便 LaTeX 适配图像和文字。
> 图片排版技巧：[图片的插入及排版方法](https://blog.csdn.net/qq_31347869/article/details/103832190)，

---

## 创建列表
在 LaTeX 中创建列表非常简单。可以使用不同的环境来创建不同形式的列表。环境是我们文档中具有不同呈现形式的各个部分。它们以`\begin{...}` 命令开始，以`\end{...}`命令结束。

&nbsp;
列表主要有两种类型，**有序列表**和**无序列表**。分别使用不同的环境。

### 无序列表
无序列表是由 itemize 环境生成的。每个条目之前必须有 \item，如下所示。默认情况下，各个条目用黑点表示。条目中的文本可以是任何长度。

```latex
\begin{itemize}
\item[标签] 条目内容
· · · · · ·
\end{itemize}
```

- 缺省的标签与层数有关，分别为：`·，-，∗`
- 也可通过选项标签来指定标签
- 不要标签：\item 

无序列表示例：

```latex
\begin{itemize}
  \item The individual entries are indicated with a black dot, a so-called bullet.
  \item The text in the entries may be of any length.
\end{itemize}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212210954.png)

### 有序列表
有序列表在 enumerate 环境中创建，针对条目的语法与无序列表一致。与无序列表一样，每个条目前必须添加 \item，它将自动生成标记该项目的数字，由从 1 开始。

```latex
\begin{enumerate}
\item[标签] 条目内容
· · · · · ·
\end{enumerate}
```

- 缺省标签为自动编号的符号，与层数有关，分别为:
   - 第一层：阿拉伯数字后跟圆点: 1. 2.
   - 第二层：圆括号包围的小写拉丁字母: (a) (b)
   - 第三层：小写罗马数字后跟圆点: i. ii.
   - 第四层：大写拉丁字母后跟圆点: A. B.
- 高级列表功能：list 环境，enumitem 宏包


有序列表示例：

```latex
\begin{enumerate}
  \item This is the first entry in our list
  \item The list numbers increase with each entry we add
\end{enumerate}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212211202.png)

---

## 添加数学表达式
LaTeX 中有两种模式用于数学表达式：**行内 (inline)模式**和**行间 (display)** 模式。行内模式编写的公式是文本中的一部分，行间模式编写的公式不在段落中，而是放在单独的行上。

### 行内
要在行内模式下添加数学表达式，可以使用以下定界符之一，它们作用相同。选择哪个完全取决于个人喜好，推荐第一种。

```latex
$ ... $
\(... \)
\begin{math} ... \end{math}
```

行内模式示例：

```latex
In physics, the mass-energy equivalence is stated
by the equation $E=mc^2$, discovered in 1905 by Albert Einstein.
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212213703.png)

### 行间
要在行间模式下显示数学公式，可以使用以下定界符之一。

```latex
\[ ... \] % displaymath 环境的简化形式
$$ ··· $$ % 与上面等价, 但可用\eqno 或 \leqno 手工编号
\begin{displaymath} ... \end{displaymath} % 不带编号的单行公式数学环境
\begin{equation} ... \end{equation} % 带 自动编号 的单行公式数学环境
```

行间模式示例：

```latex
The mass-energy equivalence is described by the famous equation
\[E=mc^2 \]
discovered in 1905 by Albert Einstein. In natural units ($c = 1$), 
the formula expresses the identity
\begin{equation}
E=m
\end{equation}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212215015.png)

> 重要说明：equation* 环境是由外部软件包提供的，请参阅 [amsmath文章](https://www.overleaf.com/learn/Aligning_equations)。
> [不鼓励](https://texfaq.org/FAQ-dolldoll) 使用 \$\$ \$\$，因为它会产生不一致的间距，而且可能不适用于某些数学软件包。
> 相关资料：[Latex所有常用数学符号整理](https://blog.csdn.net/qq_17783559/article/details/88181836)，[在线LaTeX公式编辑器](https://www.latexlive.com/)

---

## 基本框架
### 摘要
在科学文献中，通常会在摘要部分里面简述论文的主要内容。在 LaTeX 中有针对摘要部分设计的环境。摘要环境会将文本以特殊格式放在文档顶部。

```latex
\begin{document}

\begin{abstract}
This is a simple paragraph at the beginning of the document.
A brief introduction about the main subject.
\end{abstract}
\end{document}
```

### 章节命令
用来组织文档的命令因文档类型而异，最简单的组织形式是分节，它对所有文档格式均可用。

```latex
\chapter{First Chapter}

\section{Introduction}
This is the first section.

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Etiam lobortisfacilisis sem. 
Nullam nec mi et neque pharetra sollicitudin. Praesent imperdietmi nec ante.
Donec ullamcorper, felis non sodales...

\section{Second Section}
Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Etiam lobortis facilisissem. 
Nullam nec mi et neque pharetra sollicitudin. Praesent imperdiet mi necante...

\subsection{First Subsection}
Praesent imperdietmi nec ante. Donec ullamcorper, felis non sodales...

\section*{Unnumbered Section}
Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Etiam lobortis facilisissem
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212222432.png)

命令 `\section{}` 标记一个新分节的开始，在大括号内设置标题。分节编号是自动的，也可以通过在命令中加一个`*`来禁用编号，像这样：`\section*{}`。也可以有 \subsection{}，甚至 \subsubsection{}。下面列出了基本的标题深度级别：

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212222849.png)

> 请注意，\part 和 \chapter 仅在 report 和 book 类中可用。
> 有关文档结构的更完整讨论，请参阅 [这篇文章](https://www.overleaf.com/learn/Sections_and_chapters)。

### 参考文献
1. **thebibliography形式**
这种形式不需要额外的文件，参考文献信息直接在 thebibliography 环境内填写。

```latex
\begin{thebibliography}{编号样本}
\bibitem[编号]{标签} 文献条目
\bibitem[编号]{标签} 文献条目
.
.
.
\end{thebibliography}
```

- “编号”：通常省略，系统自动按顺序编号，如 [1]，[2]，...
- “编号样本”：指定用多大地方显示 “编号”，一般为数字，位数等于最大编号的位数
-  标签 ：文献的 id，可以由字母，数字和除逗号外的符号组成
   - 每个文献的标签必须唯一 (互不相同)
   - 文献的引用：\cite{标签}，\cite{标签1，标签2}
- 文献条目：论文 (作者，标题，期刊，卷期，年代，页码)，书籍 (作者，书名，出版社，年代)
- 参考文献的高级定制: natbib 宏包 (详细用法参见宏包手册)


示例：

```latex
\begin{thebibliography}{00}
\bibitem{b2} L. Bariah, D. Shehada and E. Salaha, ``Recent Advancesin VANET Security:
A Survey," Vehicular Technology Conference. 2016.

\bibitem{b3} S. A. A. Shah, E. Ahmed, F. Xia, A. Karim, M. Shiraz and R. M. Noor, 
``Adaptive beaconing approaches for vehicular ad hoc networks: A survey", 
IEEE Systems Journal, vol. 12, no. 2, pp. 1263-1277, 2018.
\end{thebibliography}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212224152.png)


2. **Bibtex格式**

这种方式是把参考文献写在`.bib`文件中，然后和`.tex`放在同一文件夹下，`.tex`直接引用`.bib`中的参考文献。这种方法比较简单，不需要你根据期刊的格式每个都改动，只需要你找到相关的文件，按照Bibtex格式放到`.bib`文件中，在`tex`文件中会按照指定的参考文献格式现实。

```latex
% 从google学术或者百度学术上找到参考文采用，然后引用->导出Bibtex格式，粘贴到.bib文件中
@article{greenwade93,
    author  = "George D. Greenwade",
    title   = "The {C}omprehensive {T}ex {A}rchive {N}etwork ({CTAN})",
    year    = "1993",
    journal = "TUGBoat",
    volume  = "14",
    number  = "3",
    pages   = "342--351"
}
```

```latex
\bibliographystyle{ieeetr} %设置参考文献类型
\bibliography{sample} %声明参考文献文件名称
```
![Bibtex格式示例](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212230200.png)

> 参考资料：[LaTeX 参考文献及格式调整](https://zymin.cn/arcticle/latex-reference-with-bib.html)

---

## 创建表格
### 一个简单的表格

```latex
\begin{center}
\begin{tabular}{ c c c }
 cell1 & cell2 & cell3 \\
 cell4 & cell5 & cell6 \\
 cell7 & cell8 & cell9
\end{tabular}
\end{center}
```

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212231756.png)

- `tabular` 环境是创建表的默认 LaTeX 方法。必须为此环境指定一个参数，这个例子里是 `{c c c}`。这告诉 LaTeX，表格将有三列，每列中的文本居中。你还可以使用 `r` 将文本向右对齐，使用 `l` 进行左对齐。
- 符号 `&` 是分隔符，每行中的分隔符始终少于列数。要转到表格的下一行，需要使用换行命令 `\\`。
- 将整个表包装在 `center` 环境中，以让它出现在页面的中心。


### 添加边框
`tabular` 环境很灵活，可以在每列之间放置分隔线。

```latex
\begin{center}
\begin{tabular}{ |c|c|c| }
 \hline
 cell1 & cell2 & cell3 \\
 cell4 & cell5 & cell6 \\
 cell7 & cell8 & cell9 \\
 \hline
\end{tabular}
\end{center}
```

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212231902.png)

使用水平线命令 `\hline` 和垂直线参数 `|` 来添加边框。

- `{|c|c|c|}`：这声明表中将会有由垂直线分隔的三列。`|` 符号指定这些列应由垂直线分隔。
- `\hline`：这条命令将插入一条水平线。这个示例中，我们在表格的顶部和底部加入了水平线。\hline 的使用次数没有限制。


> 可以借助 [TablesGenerator.com](https://www.tablesgenerator.com/) 这样的在线工具导出表格的 LaTeX 代码。_“文件”>“粘贴表数据”_ 选项从电子表格软件粘贴数据。

### 标题、标签和引用
可以使用与图片几乎相同的方式来为表格添加标题、标签和引用。唯一的区别是，使用`table`环境代替了`figure`环境。

```latex
Table \ref{table:data} is an example of referenced \LaTeX{} elements.

\begin{table}[h!]
\centering
\begin{tabular}{||c c c c||}
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex]
 \hline\hline
 1 & 6 & 87837 & 787 \\
 2 & 7 & 78 & 5415 \\
 3 & 545 & 778 & 7507 \\
 4 & 545 & 18744 & 7560 \\
 5 & 88 & 788 & 6344 \\ [1ex]
 \hline
\end{tabular}
\caption{Table to test captions and labels}
\label{table:data}
\end{table}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212232247.png)

---

## 添加算法伪代码
在LaTeX中写伪代码也是需要导入外部宏包，常用的宏包有`algorithms`、`algorithmicx` 和 `algorithm2e`。

&nbsp;
`algorithms`和`algorithmicx`一般一起使用， 简易但可定制性不高。`algorithm2e`相对复杂些，但是操作性更高，可定制性更强，所以这里主要详细介绍`algorithm2e`的使用。

### algorithms和algorithmicx示例

```latex
\begin{algorithm}
  \renewcommand{\algorithmicrequire}{\textbf{Input:}}
	\renewcommand{\algorithmicensure}{\textbf{Output:}}
	\caption{Calculate $y = x^n$} 
	\label{alg3} 
	\begin{algorithmic}
		\REQUIRE $n \geq 0 \vee x \neq 0$ 
		\ENSURE $y = x^n$ 
		\STATE $y \gets 1$ 
		\IF{$n < 0$} 
		\STATE $X \gets 1 / x$ 
		\STATE $N \gets -n$ 
		\ELSE 
		\STATE $X \gets x$ 
		\STATE $N \gets n$ 
		\ENDIF 
		\WHILE{$N \neq 0$} 
		\IF{$N$ is even} 
		\STATE $X \gets X \times X$ 
		\STATE $N \gets N / 2$ 
		\ELSE[$N$ is odd] \STATE $y \gets y \times X$ 
		\STATE $N \gets N - 1$ 
		\ENDIF 
		\ENDWHILE 
	\end{algorithmic} 
\end{algorithm}
```

> 注意：
> 要在序言区引入宏包：\usepackage{algorithm, algorithmic}
> \renewcommand{\algorithmicrequire}{\textbf{Input:}} 将官方的require关键字换成常用的input
> \renewcommand{\algorithmicensure}{\textbf{Output:}} 将官方的ensure关键字换成常用的output

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211213105605.png)

### algorithm2e

1. **第一个示例**


```latex
\documentclass{article}
\usepackage[linesnumbered,ruled]{algorithm2e} % 导入宏包

\begin{document}

\begin{algorithm} % 伪代码开始
	\caption{identify Row Context}  
  \KwIn{$r_i$, $Backgrd(T_i)$=${T_1,T_2,\ldots ,T_n}$ and similarity threshold $\theta_r$}  
  \KwOut{$con(r_i)$}  
  $con(r_i)= \Phi$\;  
  \For{$j=1;j \le n;j \ne i$}  
  {  
    float $maxSim=0$ \;  
    $r^{maxSim}=null$ \;  
    \While{not end of $T_j$}  
    {  
      compute Jaro($r_i,r_m$)($r_m\in T_j$) \;  
      \If{$(Jaro(r_i,r_m) \ge \theta_r)\wedge (Jaro(r_i,r_m)\ge r^{maxSim})$}  
      {  
        replace $r^{maxSim}$ with $r_m$ \;  
      }  
    }  
    $con(r_i)=con(r_i)\cup {r^{maxSim}}$ \;  
  }  
  return $con(r_i)$ \;
\end{algorithm}   % 伪代码结束

\end{document} 
```

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211213112018.png)

> **注意：**每一行的结尾必须以 `\;` 结束, 只有那些以宏命令开始的不应该以 `\;` 结束, 例如在此示例中的 `\caption`、`\KwIn` 、`\KwOut`属于宏命令, 不需要以 `\;` 结尾. 


2. **常用环境**
- algorithm：这是最常用的环境
- algorithm*：与前者一样, 但它用于两列文本中, 使算法跨两列


3. **基本关键字**

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211213142106.png)


4. **算法布局**

在引入宏包时，在option选项中加入了 linesnumbered 和 ruled，所以在算法伪代码中会有行编号和上下尺（即三线表样式）。当然，外部的封装环境不止 ruled 一种选项, 也可以选择完全封闭的选项亦或者完全没有外部边框的选项。

- boxed：将算法封装在框中
- boxruled：用方框将算法环绕，将标题放在上方，并在标题后添加一行
- ruled：在顶部和底部都有一条线的算法。请注意，标题不再位于算法下方，而是在算法开始时设置
- algoruled：如上所述，但在尺后留有多余的空格
- tworuled：tworuled 的行为就 ruled 的一样，但标题后面没有加一行
- plain：默认值，无功能


5. **第二个示例**


```latex
\documentclass{article}
\usepackage[linesnumbered,ruled]{algorithm2e}
\begin{document}
\begin{algorithm}
  \renewcommand{\algorithmcfname}{Pseudo code} % 这句如果写在引言区，将对全部算法生效
  \SetKwData{Left}{left}\SetKwData{This}{this}\SetKwData{Up}{up}
  \SetKwFunction{Union}{Union}\SetKwFunction{FindCompress}{FindCompress}
  \SetKwInOut{Input}{input}\SetKwInOut{Output}{output}
  \Input{A bitmap $Im$ of size $w\times l$}
  \Output{A partition of the bitmap}
  \BlankLine
  \emph{special treatment of the first line}\;
  \For{$i\leftarrow 2$ \KwTo $l$}{
    \emph{special treatment of the first element of line $i$}\;
    \For{$j\leftarrow 2$ \KwTo $w$}{\label{forins}
      \Left$\leftarrow$ \FindCompress{$Im[i,j-1]$}\;
      \Up$\leftarrow$ \FindCompress{$Im[i-1,]$}\;
      \This$\leftarrow$ \FindCompress{$Im[i,j]$}\;
      \If(\tcp*[h]{O(\Left,\This)==1}){\Left compatible with \This}{\label{lt}
        \lIf{\Left $<$ \This}{\Union{\Left,\This}}
        \lElse{\Union{\This,\Left}}
      }
    }
    \lForEach{element $e$ of the line $i$}{\FindCompress{p}}
  }
  \caption{disjoint decomposition}
  \label{algo_disjdecomp}
\end{algorithm}
\end{document}
```

![编译后的效果](https://gitee.com/chengbudong/noteimg/raw/master/image/20211213141730.png)

---

# Overleaf写LaTeX
## Overleaf网站：[链接](https://cn.overleaf.com/project)
Overleaf是一个使用LaTeX进行多人协同编辑的平台，可以免费注册和使用，不用下载LaTeX软件，是最为著名的LaTeX在线协作系统。主要特色是有LaTeX插件，编辑功能十分完善，有实时预览（即编即看，无需手动编译）的功能。科研工作者可以在各大期刊的网站上下载到其Overleaf模板，进行论文写作。

![Overleaf项目首页](https://gitee.com/chengbudong/noteimg/raw/master/image/overleaf%E9%A6%96%E9%A1%B5.png)

## 创建项目
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212153121.png)


- **空白项目**：一个最基本的.tex文档，适用于从零开始定制个人性化的板式。

![空白项目](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212154608.png)


- **样例项目**：一个通用的模板，包含了一篇论文的基本结构、基础样式，作者可以在此模板上填充自己的内容，适用于快速开始一篇论文的撰写。

![带模板项目](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212154413.png)


- **上传项目**：通过其它地方下载的模板创建项目，适用于使用所投期刊提供的模板撰写论文。


- **从模板库导入**：通过Overleaf平台的模板库中寻找模板，里面有各式各样的模板。

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212160030.png)

## 编辑页面介绍

![页面介绍](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212233704.png)

## 上传图片

![](https://gitee.com/chengbudong/noteimg/raw/master/image/overleaf_uploadFig.png)

## 下载完成的文档

![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211212233900.png)

# 学习资料

- LaTeX工作室在知识库：[链接](https://www.latexstudio.net/texdoc/#/)
- 华东师范大学潘建瑜老师讲义：[链接](http://math.ecnu.edu.cn/~jypan/Teaching/Latex/)
- 简短的 LaTeX2e 介绍：[链接](https://mirrors.tuna.tsinghua.edu.cn/CTAN/info/lshort/chinese/lshort-zh-cn.pdf)
- algorithm2e 宏包官方文档：[链接](http://tug.ctan.org/macros/latex/contrib/algorithm2e/doc/algorithm2e.pdf)
