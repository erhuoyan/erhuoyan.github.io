---
title: hexo+github搭建博客（一）
copyright: true
date: 2018-12-01 11:44:37
tags: 
- hexo
- blog
- github
categories: 
- 折腾
---

{% note %}
前言：经过连续几天的熬夜折腾，终于搭建完成了自己的博客。是看了阮一峰的个人博客后，也想建立一个自己的博客。起初只想到在各种博客网站直接注册使用，但是这种网站大部分已经关闭，很不稳定。最后决定在github建立仓库来记录博客。没想在网上搜索一下便出现hexo+github的建立方法。我觉得这才是我真正想要的博客模式。教程网上很多但良莠不齐，有些与现在的版本存在差异。于是，写下一份教程，既作为记录，以后重新配置起来方便，也作为技术分享，跟大家交流。欢迎大家在评论区提交意见。
{% endnote %}

<!--more-->

# 安装

安装 Hexo必须先在电脑中安装下列应用程序：
- [Node.js](https://nodejs.org/en/)
- [Git](http://xk2.ahu.cn/CheckCode.aspx)  

## 安装Git

Windows|Ubuntu
:-----:|:----:
下载后直接安装|`sudo add-apt-repository ppa:git-core/ppa;`
下载地址：[git](https://git-scm.com/download/win)|`sudo apt update;sudo apt install git`

## 安装Node.js

安装 Node.js 的最佳方式是使用 nvm。大家需要在**Git Bash**中输入以下命令：

cURL:

` curl https://raw.github.com/creationix/nvm/v0.33.11/install.sh | sh`

Wget:

` wget -qO- https://raw.github.com/creationix/nvm/v0.33.11/install.sh | sh`

安装完成后，重启终端并执行下列命令即可安装 Node.js。

` nvm install stable`

{% note warning %}

### Windows用户
对与windows用户来说建议使用[安装程序](https://nodejs.org/en/)进行安装。安装时，请勾选**Add to PATH**选项。
Windows可以使用**Git Bash**,安装完git之后在开始菜单中搜索git或在任意目录下右键选择`Git Bash Here`，可在该环境下直接使用上述命令安装Node.js。

{% endnote %}

## 安装Hexo

npm的默认软件源速度非常慢，通常将其改成淘宝镜像
在**Git Bash**中输入以下命令进行配置：

`npm config set registry https://registry.npm.taobao.org`

然后执行

`$ npm install -g hexo-cli`

等待安装结束。

# 建议

hexo的安装过程可能对没有使用过Linux或Mac系统的伙伴来说有点不习惯，毕竟大家在windows系统上安装软件的时候都是图形交互，鼠标点击就可以了。但是这里，还是建议大家学习一些其他东西，方便之后博客的创作、部署、配置等操作。

## 1. bash命令

我们安装了Git之后，对于用过Linux的用户来说会感到非常熟悉，没错Git Bash其实使用的就是Linux系统的bash命令。想要深入学习Linux的朋友可以在网上寻找教程，或者在网易云课堂找一些视频。当然也可以找我咨询一些建议，交流经验。

## 2. vim编辑器

vim被誉为编辑器之神。学习Linux的过程中不可能跳过这一步。在之后我们需要对博客进行配置的时候经常用到vim的搜索功能。大家需要知道vim如何进行编辑、保存、搜索。

## 3. github

其实只需要**Hexo**和**git bash**我们便可以把博客部署到本地。但如果想要部署到网上让别人也能访问，就需要用到Github了，大家需要先注册一个[github](https://github.com/)，在之后我会教大家如何将本地博客部署到github，如果购买了域名，也可以将域名与github绑定。github的主要功能并不是解决博客部署问题，它是一个开源社区，强烈推荐大家学习一下。

## 4. Markdown语法

在windows上大家都是用word进行写作，但是word保存之后是二进制文件，只能用word软件打开，并不适合作为网页文本编辑器。Hexo采用markdown语法编辑博文，大家需要学习一下markdown的无法规范，以便能将自己的博文排版做的漂亮。Markdown编辑器推荐：[Typora](https://www.typora.io/)。

# 附：

{% note %}

最后附上一些我觉得很好教程和博客网站。  

{% endnote %}

- [【王顶】GitHub 开源之旅视频课程](https://github.com/wangding/courses/tree/master/github)
- [廖雪峰的官方网站](https://www.liaoxuefeng.com/)
- [阮一峰的个人网站](http://www.ruanyifeng.com/home.html)
- [Hexo文档](https://hexo.io/zh-cn/docs/)

{% note %}

说明：

- 王顶的Github开源之旅课程分多季，每一季需要支付几块钱，在网易云课堂也能找到。建议大家看>完前两季。分别是**启程**和**Markdown**。
- 廖雪峰的官网上有Git教程，也有**python**和**JavaScript**的教程。
- 阮一峰的个人网站阮一峰的博客，有兴趣的朋友可以读一下他的《未来世界的幸存者》。可以在他的博客中免费阅读。
- Hexo文档是Hexo的官方文档。我主要参考这篇文档的同时借鉴了网上其他人的经验和自己的想法。建议大家参考其中的基本操作部分，学习一下如何进行写作。

{% endnote %}