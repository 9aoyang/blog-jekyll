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