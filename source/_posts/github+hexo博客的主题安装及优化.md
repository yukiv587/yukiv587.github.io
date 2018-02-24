---
title: github+hexo博客的主题安装及优化
tags: Hexo
categories : 学习文档
---

在[hexo官网](https://hexo.io/)有很多比较不错的主题推荐，可以在上面选择自己喜欢的主题，然后进行相应的个性化修改，这是我使用的主题indigo，通过github+hexo搭建个人博客。

## 安装Hexo
在自己认为合适的地方创建一个文件夹，这里我以E：/hexo 为例子讲解，首先在E盘目录下创建Hexo文件夹，并在命令行的窗口进入到该目录
{% image hexo-1.jpg %}

在命令行中输入：
``` bash
npm install hexo-cli -g
```

然后你会看到命令行窗口刷了一大堆白字，下面我们来看一看Hexo是不是已经安装好了。 在命令行中输入：
``` bash
hexo -v
```
{% image hexo-2.png %}

## hexo的相关配置

### 初始化Hexo
``` bash
hexo init
```
然后输入：
``` bash
npm install
```
之后npm将会自动安装你需要的组件，只需要等待npm操作即可。

### 首次体验Hexo
``` bash
hexo g
hexo s
```
在浏览器中打开http://localhost:4000/，你将会看到：
{% image hexo-3.jpg %}
  

### 安装主题
选择一款自己喜欢的主题，这将成为你个人博客模版。[这里是主题安装的教程](https://github.com/yscoder/hexo-theme-indigo/wiki/%E5%AE%89%E8%A3%85)，下面是我安装时的经验及个人见解。
安装需确认你的 Hexo 版本在 3.0 以上，以及 Node 版本为 6.x 以上，在 Hexo 根目录，执行以下命令。
``` bash
    git clone git@github.com:yscoder/hexo-theme-indigo.git themes/indigo
```
>这个命令要在博客文件夹的根目录右击鼠标打开Git Bash输入命令，其中themes/indigo就是会在博客文件夹根目录中的themes新建一个indigo文件夹存放clone下来的主题，以后的主题通常都是存放在这个目录下。
通俗来说就是这样git clone +通过主题的github中获取的URL+ +themes/indigo


## 将Hexo与Github page联系起来
设置Git的user name和email（如果是第一次的话）

{% image hexo-4.png %}

上图是在其文件夹里面鼠标右键，点击Git Base Here。这里“feng”可以替换成自己的用户名，邮箱可以替换成自己的邮箱

输入cd ~/.ssh，检查是否由.ssh的文件夹

{% image hexo-5.png %}

输入ls，列出该文件下的内容。下图说明存在

{% image hexo-6.png %}

输入ssh-keygen -t rsa -C “929762930@qq.com”，连续三个回车，生成密钥，最后得到了两个文件：id_rsa和id_rsa.pub（默认存储路径是：C:\Users\Administrator\.ssh）。

{% image hexo-7.png %}

输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent

{% image hexo-8.png %}

再输入ssh-add ~/.ssh/id_rsa，添加生成的SSH key到ssh-agent

{% image hexo-9.png %}

登录[github官网](https://github.com/)账号，点击头像下的settings，添加ssh

{% image hexo-10.png %}

新建一个new ssh key，将id_rsa.pub文件里的内容复制上去

{% image hexo-11.png %}

输入ssh -T git@github.com，测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了

{% image hexo-12.png %}

>问题：假如ssh-key配置失败，那么只要以下步骤就能完全解决

>首先，清除所有的key-pair
ssh-add -D
rm -r ~/.ssh
删除你在github中的public-key

>重新生成ssh密钥对
ssh-keygen -t rsa -C "xxx@xxx.com"

>接下来正常操作
在github上添加公钥public-key:
1、首先在你的终端运行 xclip -sel c ~/.ssh/id_rsa.pub将公钥内容复制到剪切板
2、在github上添加公钥时，直接复制即可
3、保存

>测试：
在终端 ssh -T git@github.com

配置Deployment，在其文件夹中，找到_config.yml文件，修改repo值（在末尾）

{% image hexo-13.png %}

repo值是你在github项目里的ssh（右下角）

{% image hexo-14.png %}

新建一篇博客，在cmd执行命令：hexo new post “博客名”

需要安装一个扩展：
```
npm install hexo-deployer-git --save
```

那么就可以使用命令：hexo d -g，生成以及部署了
部署成功后访问你的地址："http://用户名.github.io "。那么将看到生成的文章