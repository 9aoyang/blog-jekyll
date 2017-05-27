---
layout:     post
title:      "如何在ubuntu16.04下安装XMind8？"
subtitle:   ".zip和.deb的一般安装步骤和常见问题"
date:       2017-05-25 12:00:00 
author:     "9aoyang"
header-img: "img/install_xmind8.jpg"
tags:
    - Linux 
    - Ubuntu
    - 软件
---

## .zip
1. 官网下载最新的[XMind8版本](http://www.xmind.net/download/linux/)（以前在官网直接能下到.deb格式的软件包，但是好像从8开始没有了……不然也就不会有这篇文章了）
2. 下载好之后，你会得到一个`.zip`的压缩包，在任意目录新建一个文件夹，提取到文件夹中。
3. 打开文件夹，在根目录下有一个`set.sh`脚本，在终端中运行（打开终端后直接拖拽进去，可以省去切换命令的步骤），不习惯命令行的朋友可以直接：右键➜打开方式➜其他应用➜终端。与你的预期不同，这个脚本仅仅只是安装一些XMind8所需的共享库和字体，
4. 第3步的`set.sh`执行完成后，再次打开文件夹，里面有`XMind_amd64`（64位）和`XMind_i386`（32位），任选一个打开，双击目录下的`XMind`，打开应用程序，你会看见XMind8的图标躺尸在里面，大功告成！

## .deb
虽然官网下不到，但这些开发人员真的是心机很深，不过道高一尺魔高一丈，还是有高人在官网找到了`.deb`格式的软件包：[传送门](http://www.xmind.net/xmind/downloads/xmind-8-beta-linux_amd64.deb)，链接直至我写这篇文章时还是有效的，但不知道是否会一直有效，所以掌握`.zip`安装的方法还是有必要的。


至于Xmind8的一些进阶用法和使用技巧，可以参考我的[另一篇文章]()。