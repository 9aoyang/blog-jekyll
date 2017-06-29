---
layout:     post
title:      "Github Page && Jekyll 搭建个人博客"
subtitle:   ""
date:       2016-11-30 00:00:00 
author:     "9aoyang"
header-img: "img/"
catalog: true
tags:
    - 博客 
    - Github
---



## 前言
#### GIthub Pages
GIthub Pages是Github提供给托管项目的开发者一个更个性化展示自己项目的方法，使用GitHub Pages服务可以编写同样是托管在Github上的静态网页。

#### Jekyll
- 将纯文本转化为静态网站和博客
- 简单 -- 无需数据库、评论功能，不需要不断的更新版本——只用关心你的博客内容
- 静态 -- 只用 Markdown (或Textile)、Liquid、HTML & CSS 就可以构建可部署的静态网站

只要遵循Jekyll规范编写网站源码，上传到Github上，Github会自动进行编译出最终的网站文件，这个过程就像黑魔法一样！

Tip: 如果本地安装Jekyll编译环境，便可实时预览网站，不必每修改一点都要经过上传刷新才能看到结果，大大方便了我们的调试。因此在下文中我们会逐步来配置本地的一些环境。

#### Github Pages && Jekyll 方案的优、缺点：
- 优点：
  - Github免费托管源文件，自动编译符合Jekyll规范的网站。
  - 引入版本管理，修改网站更加安全方便。
  - 支持 Markdown ，编写具有优美排版的文章。

- 缺点：
 - 需要学习一些基础的Git命令
 - 若要自己全权制作主题的话需要懂一点网页开发
 - 由于生成的是静态网页，若要使用动态功能，如评论功能（下文解决），则要使用第三方服务。

 如果你只是想有一个地方来让你专注于内容的，这就是一个绝佳的方案。



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
$ ssh-keygen -t rsa -C "youremail@example.com"    #一路回车即可，不要瞎搞事。
```
<img src="/img/in-post/bulid-myblog/SSH_Key.png" alt="SSH Key" title="SSH Key">

如果一切顺利的话，会出现上图中的内容。之后可以在用户主目录里找到`.ssh`目录（隐藏目录），里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。

4. 登录[Github](https://github.com/)，点击用户头像，在下拉菜单中选择”Setting“

然后，点“SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容：

<img src="/img/in-post/bulid-myblog/ssh-key.png" alt="add ssh key" title="">

点“Add Key”，你就应该看到已经添加的Key：

<img src="/img/in-post/bulid-myblog/ssh-key1.png" alt="add ssh key" title="">


## 配置Jekyll环境

1. 安装ruby

```
sudo apt install ruby
```

2. 安装jekyll

```
sudo apt install jekyll
```

3. 安装过程中视情况可能会缺少一些其他的安装项，根据提示一一安装即可

## Fork仓库并克隆到本地
由于要从0到1创造一个博客的话，前期的学习成本太高，而且也不符合我们专注于内容的初衷，因此这里推荐直接在现有模板的基础上进行个性化的改进。后期有精力的话可以加入更多自己的元素。

#### 选择一款自己喜欢的模板
- [github主题站](https://github.com/jekyll/jekyll/wiki/sites)
- [jekyll主题站](http://jekyllthemes.org/)

#### Fork到自己的github
1. 找到自己github中的此项目

2. 点击“Settings”，将“Repository name”改为 username.github.io，点击“Rename”

3. 修改成自己的名字.此时就可以通过 http://username.github.io 访问你fork下来的网站了。

4. 克隆到本地
```
git clone git@github.com:username/username.github.io.git
```

就是这么简单。从现在开始，你可以通过创建文章、改变头信息来控制模板和输出、修改 Jekyll 设置来使你的站点变得更有趣～更多内容请参见[Jekyll中文指南](http://jekyllcn.com/docs/home/)


## 绑定域名
既然都有专属于自己的博客了，那么，有一个自己的个性域名难道不是一件很酷的事吗！

关于域名的购买，网上的资料有很多，这里就不再赘述了，默认看到这一步的你已经有了一个准备好的域名。

1. 在本地仓库根目录的master分支上创建文件CNAME(必须大写，否则Github Pages服务器z无法识别和解析)，不带后缀。并将不带协议名的裸域名写进去(9aoyang.cn，而不是http://9aoyang.cn/)

2. 推送到github的远程仓库

3. 打开你的域名供应商提供的管理系统，把要绑定的域名解析到github.io.（注意io末尾的.），在DNS配置中添加3条记录
```
 @         A        192.30.252.153
 @         A        192.30.252.154   
www      CNAME    username.github.io.
```

4. 等待你的DNS配置生效
对DNS的配置不是即时生效的，过10分钟再去访问你的域名看看有没有配置成功：）