---
title: hexo+github搭建博客（二）
copyright: true
date: 2018-12-02 13:34:49
tags: 
- hexo
- blog
- github
categories: 
- 折腾
---

{% note %}
 现在搭建博客需要的软件已经安装完毕，然后就要介绍建立博客的具体步骤了。
 {% endnote %}

<!--more-->

# 搭建网站

## 在本地搭建

在本地磁盘上找到一个地方存放博客本地文件。（例如H盘）

打开H盘目录，右键选择**Git Bash Here。执行以下命令

```bash
hexo init <folder>
cd <folder>
npm install
```

> 这里的 `<folder>`改为自己喜欢的名字。这个就是你博客的本地文件夹的名字。

完成之后，你的文件夹的目录如下：

![s](https://i.loli.net/2018/12/02/5c039142b95b9.png)

使用以下命令：

```bash
hexo g
hexo s
```

输入命令后终端输出为：

```Shell
ubw@DESKTOP-12HM3DA MINGW64 /h/blog
$ hexo g
INFO  Start processing
INFO  Files loaded in 133 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: 2018/12/02/hello-world/index.html
INFO  Generated: archives/2018/index.html
INFO  Generated: archives/2018/12/index.html
INFO  5 files generated in 206 ms

ubw@DESKTOP-12HM3DA MINGW64 /h/blog
$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```

在浏览器网址输入`http://localhost:4000`

首次体验Hexo
![canvas](https://i.loli.net/2018/12/02/5c039a17a5cbf.png)

{% note warning %}

现在原则上博客已经可以使用了。你可以通过`Hexo s` 开启本地服务器，在浏览器输入网址`http://localhost:4000`进行访问和阅读。但别人不能在网上访问你的博客，因为你还没有把本地静态文件部署到网上。
{% endnote %}

## 基本操作

### 新建

```bash
hexo new <title>          #title处填写文件名。
```

新建一篇标题为`title`的文章。文章自动生成在`source\\_posts`文件夹中。文件名为`title.md`。使用markdown编辑器进行编辑即可。

### 生成静态文件

```bash
hexo g   #hexo generate的简写
```

### 启动服务器

```bash
hexo s  #hexo server的简写
```

开启后默认端口是4000.默认访问网址是`http://localhost:4000/`
如果您想要更改端口，或是在执行时遇到了 EADDRINUSE 错误，可以在执行时使用 -p 选项指定其他端口，如下：

```bash
hexo s -p 5000  #修改端口为5000
```

### 部署网站

```bash
hexo d  #hexo deploy的简写
```

{% note %}

### 完成后部署

您可执行下列的其中一个命令，让 Hexo 在生成完毕后自动部署网站，两个命令的作用是相同的。

hexo g -d
hexo d -g

{% endnote %}

## 部署到github

### 注册github

{% note success %}

注册步骤很简单，这里不再叙述。在王顶Github之旅中有详细介绍。

{% endnote %}

[GitHub](https://github.com)官网

![火狐截图_2018-12-02T09-28-08.986Z](https://i.loli.net/2018/12/02/5c03a5d42b6ab.png)

### 建立博客仓库

与建立普通仓库不同的是仓库名要设置为`用户名.github.io`的格式。
> 比如我的Github用户名为`erhuoyan`，那么我创建的repository的名字应该是 `erhuoyan.github.io`

### SSH授权

> ssh授权是为了简化我们的工作，使用ssh协议部署和提交文件到github就不需要每次都重复输入密码了。

如下命令来生成 ssh key:

```bash
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"
```

按照提示完成三次回车，即可生成 ssh key。通过查看 `~/.ssh/id_rsa.pub`文件内容，获取到你的 public key

```bash
cat ~/.ssh/id_rsa.pub
# ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6eNtGpNGwstc....
```

复制生成后的 ssh key，添加到github上

操作步骤可参考[远程仓库](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000)

### 配置

安装插件

```bash
npm install hexo-deployer-git --save
```

配置 Hexo根目录的 _config.yml，xxx为你的用户名。

```yaml
deploy:
  type: git
  repo: git@github.com:xxx/xxx.github.io.git
  branch: master
```

### 推送Hexo到github

使用命令

```bash
hexo d
```

接下来访问`xxx.github.io`即可看到你的博客了