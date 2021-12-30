---
title: wsl2(Ubuntu) + Miniconda3 + PyCharm配置
date: 2021-12-15 20:41:18
update: 
img: 
top: false
cover: false
toc: true
mathjax: true
summary: 
tags: 
- Linux
- wsl2
- PyCharm
categories: 
- 软件与工具
---

## WSL2安装
WSL的安装之前已写过，按照这边文章操作即可。[win10下wsl2+golang+goland配置](https://www.yuque.com/chengbudong/coding/nwkmk3)
## 安装Miniconda3
Miniconda是一个免费的conda最小安装程序。它是Anaconda的一个小型版本，只包括conda、Python、它们所依赖的包，以及pip、zlib等少量其他有用的包。
### 下载安装
```bash
# 下载
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
# 安装
bash Miniconda3-latest-Linux-x86_64.sh 
```

根据提示一步一步地安装。安装完成后，输入
```bash
source ~/.bashrc  #重新激活环境变量
conda -V          #检查conda是否安装成功
```

### 添加镜像
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
```

### 创建python环境
创建自己需要的虚拟环境，也就是自己的工作区。基本命令需指定**环境名称**和**Python 版本**：
```bash
# 基本格式
conda create -n [env_name] [python=version]
# 例子
conda create -n python_3.6 python=3.6
```

安装完毕后，进入 conda 环境：
```bash
# 进入
conda active python_3.6
# 退出
conda deactivate
```

## pycharm配置
使用 Pycharm 内置终端打开 WSL 运行 Python 代码
```bash
bask	# 在pycharm终端里输入
conda activate [env_name]	# 激活环境
python xxx.py # 运行.py文件
```
![](https://gitee.com/chengbudong/noteimg/raw/master/image/20211215204103.png)

### 附：Conda 的基本使用
- 环境管理

conda 常用操作可使用命令`conda -h`和`conda config -h`查看，这里列出几个常用命令：
```bash
# 创建
conda create -n [env_name]
# 删除
conda env remove -n [env_name]
# 参照配置文件更新
conda env update --file [file.yml]
# 环境列表
conda env list
# conda 信息
conda info
# 添加频道
conda config --add channels [channel]
# 删除频道
conda config --remove channels [channel]
```

- 包管理

```bash
# 安装
conda install [package_name]
# 删除
conda uninstall [package_name]
# 更新
conda update [package_name]
# 更新所有包
conda update --all
# 搜索
conda search [package_name]
# 已安装列表
conda list
```

- 配置文件：conda 会生成配置文件`.condarc`。其位置如下：
- Windows：`C:\Users\username\.condarc`
- MacOS 和 Linux：`~/.condarc`

其文件结构如下：
```bash
# 频道
channels:
  - conda-forge
  - defaults
# 将 pip 作为 Python 的依赖
add_pip_as_python_dependency: true
# 安装按照频道的顺序
channel_priority: false
# 生成错误报告
report_errors: false
# ssl 验证
ssl_verify: false
# 显示频道具体链接
show_channel_urls: true
# 错误回滚
rollback_enabled: true
# 重试
remote_max_retries: 3
```

- 镜像：为了加快速度，国内往往需要使用镜像，修改`channels`如下

```bash
channels:
 # 中科大镜像
  - https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
 # 清华镜像
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - defaults
```
