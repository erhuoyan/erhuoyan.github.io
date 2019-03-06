---
title: hexo备份与恢复
copyright: true
tags:
  - hexo
  - 备份
categories:
  - 折腾
abbrlink: c062
date: 2019-03-06 19:35:00
---

{% note %}
今天早上不小心把博客本地文件弄坏了，这已经不是第一次了。还好从一开始我就做好了备份工作，这里将备份和恢复过程写下来，恢复博客时作为手册使用，如果更换了电脑，这种方法依然可以使用。
{% endnote %}
<!--more-->

## 备份

由于我的博客本来就是部署到github上的，有一个专用的仓库来存放博客的静态文件，所以最好的办法就是把hexo的源文件也推送到这个仓库。

{% note danger %}
不要把源文件直接推送到github仓库，这样，源文件与网页静态文件堆放在一起，不仅不美观，可能也会影响博客的运行。所以我们需要新建一个分支。
{% endnote %}

1. 新建hexo分支并设为默认

    ```bash
    # 新建hexo分支
    git checkout -b hexo
    # 将hexo设为默认
    git branch --set-upstream-to=origin/hexo
    ```

2. 将以下内容添加至`.gitignore`文件中

    ```
    .DS_Store
    Thumbs.db
    db.json
    *.log
    node_modules/
    public/
    .deploy*/
    ```

3. 将 themes/next/（我用的是 NexT 主题）中的 .git/ 删除，否则无法将主题文件夹 push

4. 执行 `git add`、`git commit -m "hexo"`、`git push origin hexo` 来提交 hexo 网站源文件

5. 执行 hexo g -d 生成静态网页部署至 Github 上

经过这些步骤后远程仓库中就会有了master和hexo两个分支分别用来存放静态和源文件。以后再对博客进行修改后只需重复4,5两步即可（对顺序没有要求）。

## 恢复

### 本电脑恢复

1. 使用 git clone 将仓库拷贝至本地

2. 切换到hexo分支

    ```bash
    # 查看所有分支
    git branch -a
    * master
    remotes/origin/HEAD -> origin/master
    remotes/origin/master
    remotes/origin/hexo

    # 切换hexo分支
    git checkout hexo

    # 更新本地仓库
    git pull
    ```

3. 在文件夹内执行以下命令 `npm install hexo-cli -g`、`npm install`、`npm install hexo-deployer-git`

### 在另一台电脑恢复

不同电脑主要区别在于有没有安装Node.js，git和npm。在另一台电脑上提前安装这三种工具后，就可以依次执行上面的1~3步即可。

{% note %}
经过今天的测试，npm的在国内速度很慢，使用`npm install`可能会报错。执行`npm install -g cnpm --registry=https://registry.npm.taobao.org`后，使用`cnpm`代替`npm`即可。
{% endnote %}

## hexo 的源文件

hexo的源文件并非全部需要拷贝：

- _config.yml站点的配置文件，需要拷贝；
- themes/主题文件夹，需要拷贝；
- source 博客文章的 .md 文件，需要拷贝；
- scaffolds/ 文章的模板，需要拷贝；
- package.json 安装包的名称，需要拷贝；
- .gitignore 限定在 push 时哪些文件可以忽略，需要拷贝；
- .git/ 主题和站点都有，标志这是一个 git 项目，不需要拷贝；
- node_modules/ 是安装包的目录，在执行 npm install 的时候会重新生成，不需要拷贝；
- public 是 hexo g 生成的静态网页，不需要拷贝；
- .deploy_git 同上，hexo g 也会生成，不需要拷贝；
- db.json文件，不需要拷贝。

其实不需要拷贝的文件正是添加到`.gitignore` 中的内容。