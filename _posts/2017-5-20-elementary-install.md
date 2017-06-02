---
layout:     post
title:      "体验号称最漂亮的Linux系统：elementary OS"
subtitle:   " elementary OS快速配置指南 "
date:       2017-05-20 05:20:20 
author:     "9aoyang"
header-img: "img/eos_desktop.png"
tags:
    - Linux 
    - Ubuntu
---

最近心血来潮，正值项目结项，Win10也用到审美疲劳，就想要转到Linux系统，经过一番Google，elementary OS引起了我的兴趣。来看看维基百科上对elementary OS的介绍：

>elementary OS是一个基于Ubuntu的Linux发行版。它使用一个自己开发的基于GNOME的名为Pantheon的桌面环境。 这个桌面环境出众的原因是它深度集成了其他elementary OS应用程序，如Plank（一个基于Docky的Dock）、Midori（默认的网页浏览器）或Scratch（一个简单的文本编辑器）。该发行版使用基于Mutter的Gala作为其窗口管理器。

>这个发行版是从为Ubuntu设计的一套主题和应用程序发展而来的。由于是基于Ubuntu的，因此与Ubuntu的仓库和包完全兼容。它使用Ubuntu自己的软件中心来处理软件的安装和卸载。其类似于Mac OS X的界面致力于使新用户不需要费太大力气就可以根据直觉使用。

**安装步骤**：
1. 下载[elementary OS镜像](https://elementary.io/zh_CN/) 

2. 制作[USB引导](https://rufus.akeo.ie/)

3. 安装系统（这一步如果不会的话请自行使用搜索引擎进行学习～），进入引导选择安装后会进入elementary OS系统的界面，语言选择中文，之后根据安装提示一路确认即可（新手建议，老鸟或者要装双系统的请注意自行配置安装）。如果在安装时出现分区挂载失败的情况，根据具体情况通过终端对相应的分区进行格式化即可。
 
4. 如果你跟我一样，是一个Linux菜鸟或者完全不了解Linux系统，没关系，我在贴吧发现了一位大神（再次给dalao送上膝盖）写好的elementary OS 0.4快速配置工具，你唯一要做的就是找一个网络环境良好的地方，打开终端terminal（在屏幕左上角的应用程序中），然后复制执行：
```
wget http://linux-1251056822.costj.myqcloud.com/elementary_config 
&& bash elementary_config
```
<img src="/img/in-post/elementary-install/configurationtool.png" alt="elementary-install tool" title="elementary0.4快速配置工具">

　这里面包括系统软硬件环境配置，网易云音乐，搜狗输入法，常用的办公软件，系统主题，甚至还有翻墙工具等Linux系统下的热门软件，可以根据需求自行选择安装。有了这些，基本就能完成你之前在Win系统下90%的工作了。解决了这些后顾之忧，再慢慢去深入学习Linux，岂不是一举两得？
