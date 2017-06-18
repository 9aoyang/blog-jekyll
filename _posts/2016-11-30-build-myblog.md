---
layout:     post
title:      "Github Page + Jekyll 搭建个人博客"
subtitle:   "托管在Github服务器上的博客"
date:       2017-11-30 00:00:00 
author:     "9aoyang"
header-img: "img/"
catalog: true
tags:
    - 博客 
    - Github
---

## 配置github环境
1. 安装git
打开终端，尝试输入git，看看系统有没有装git：

```
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```
像上面的命令，Linux会友好地告诉你Git没有安装，还会告诉你如何安装Git。再次输入上面提示你的命令语句即可安装
```
sudo apt-get install git
```

git安装之后，还需要最后一步设置，在命令行输入：

```
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。

2. git命令别名配置（快捷键）

这一步主要是为了平时更方便的使用git命令，不过我现在主要用`vscode`内置的[git插件](https://marketplace.visualstudio.com/items?itemName=KnisterPeter.vscode-github)来管理版本库，但偶尔还是会在终端使用git，就顺便设置了，你可以直接复制粘贴使用，也可以更改`alias.`后面的组合来自定义你喜欢的快捷键。
```
#查看状态
git config --global alias.st status

#切换分支
git config --global alias.co checkout

#提交修改
git config --global alias.ci commit

#查看分支
git config --global alias.br branch

#撤销修改
git config --global alias.unstage 'reset HEAD'

#查看最近一次提交
git config --global alias.last 'log -1'

#查看历史提交（增强版）
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

3. 创建SSH Key
```
$ ssh-keygen -t rsa -C "youremail@example.com"
```

把这个过程当成一个黑盒，一路回车即可，不要瞎搞事。

当出现上图所示时说明已经成功创建了。

4. 登录Github

## 配置Jekyll环境

1. 安装ruby

```
sudo apt install ruby
```

2. 安装jekyll

```
sudo apt install jekyll
```

## 快速获取一个简单模板

```
~ $ jekyll new myblog
~ $ cd myblog
~/myblog $ jekyll serve
# => Now browse to http://localhost:4000
```
如果你希望把 jekyll 安装到当前目录，你可以运行 `jekyll new` . 来代替。如果当前目录非空，你还需要增添 `--force` 参数，所以命令应为 `jekyll new . --force`。

就是这么简单。从现在开始，你可以通过创建文章、改变头信息来控制模板和输出、修改 Jekyll 设置来使你的站点变得更有趣～更多内容请参见[Jekyll中文指南](http://jekyllcn.com/docs/home/)


##