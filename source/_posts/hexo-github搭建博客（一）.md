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

> 前言：经过连续几天的熬夜折腾，终于搭建完成了自己的博客。是看了阮一峰的个人博客后，也想建立一个自己的博客。起初只想到在各种博客网站直接注册使用，但是这种网站大部分已经关闭，很不稳定。最后决定在github建立仓库来记录博客。没想在网上搜索一下便出现hexo+github的建立方法。我觉得这才是我真正想要的博客模式。教程网上很多但良莠不齐，有些与现在的版本存在差异。于是，写下一份教程，既作为记录，以后重新配置起来方便，也作为技术分享，跟大家交流。欢迎大家在评论区提交意见。

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

安装 Node.js 的最佳方式是使用 nvm。

cURL:

` curl https://raw.github.com/creationix/nvm/v0.33.11/install.sh | sh`

Wget:

` wget -qO- https://raw.github.com/creationix/nvm/v0.33.11/install.sh | sh`

安装完成后，重启终端并执行下列命令即可安装 Node.js。

` nvm install stable`

>
> ### Windows用户
> 对与windows用户来说建议使用[安装程序](https://nodejs.org/en/)进行安装。安装时，请勾选**Add to PATH**选项。
> Windows可以使用**Git Bash**,安装完git之后在开始菜单中搜索git或在任意目录下右键选择`Git Bash Here`，可在该环境下直接使用上述命令安装Node.js。

## 安装Hexo

npm的默认软件源速度非常慢，通常将其改成淘宝镜像
在**Git Bash**中输入以下命令进行配置：
`npm config set registry https://registry.npm.taobao.org`
然后执行
`$ npm install -g hexo-cli`
等待安装结束。