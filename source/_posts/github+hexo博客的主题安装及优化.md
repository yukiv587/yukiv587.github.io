---
title: github+hexo博客的主题安装及优化
tags: Hexo
categories : 学习文档
---

在[hexo官网](https://hexo.io/)有很多比较不错的主题推荐，可以在上面选择自己喜欢的主题，然后进行相应的个性化修改，这是我使用的主题indigo，通过github+hexo搭建个人博客。

## 安装Hexo
在自己认为合适的地方创建一个文件夹，这里我以E：/hexo 为例子讲解，首先在E盘目录下创建Hexo文件夹，并在命令行的窗口进入到该目录

### 安装主题
选择一款自己喜欢的主题，这将成为你个人博客模版。[这里是主题安装的教程](https://github.com/yscoder/hexo-theme-indigo/wiki/%E5%AE%89%E8%A3%85)，下面是我安装时的经验及个人见解。
安装需确认你的 Hexo 版本在 3.0 以上，以及 Node 版本为 6.x 以上，在 Hexo 根目录，执行以下命令。
``` bash
    git clone git@github.com:yscoder/hexo-theme-indigo.git themes/indigo
```
>这个命令要在博客文件夹的根目录右击鼠标打开Git Bash输入命令，其中themes/indigo就是会在博客文件夹根目录中的themes新建一个indigo文件夹存放clone下来的主题，以后的主题通常都是存放在这个目录下。
通俗来说就是这样git clone +通过主题的github中获取的URL+ +themes/indigo

{% image hexo-1.jpg %}

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
