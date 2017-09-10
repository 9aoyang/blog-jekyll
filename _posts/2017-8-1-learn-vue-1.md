---
layout:     post
title:      "Vue学习笔记"
subtitle:   "振翼篇（一）"
date:       2017-08-01 00:00:00 
author:     "9aoyang"
header-img: "img/vue.png"
catalog: true
tags:
    - 前端
    - vue
---

## 介绍
***
> Vue.js（读音 /vjuː/，类似于 **view**） 是一套构建用户界面的**渐进式框架**。与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。Vue 的核心库只关注视图层，它不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)和 [Vue 生态系统支持的库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用程序提供驱动。

Vue是一个[MVVM](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)的框架,特点是**易用**、**灵活**、**高效**

#### 易用
Vue.js 的核心是一个允许采用简洁的模板语法来声明式的将数据渲染进 DOM：

![声明式渲染](http://upload-images.jianshu.io/upload_images/4260383-74e4059af7ee82f6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 灵活

![](http://upload-images.jianshu.io/upload_images/4260383-a0e034ac19f0eb21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1. 声明式渲染
 不论是开发单页面还是多页面的应用程序，首先要做的就是声明式的渲染来渲染页面上的每个字段

2. 组件系统
提取一些公共的头部和尾部

3. 客户端路由
单页面应用程序往往需要路由
引进vue-router、~~vue-resource~~(已经不被官方推荐，推荐使用axios作为ajax请求库)

4. 大规模状态管理
项目业务足够复杂，大量使用组件，而且难以去管理组件的状态，这时候就可以引进Vuex，Vuex就是一个专为Vue.js 应用程序开发的状态管理模式

5. 构建工具
整个项目完成之后，我们可能还需要构建工具来bulid我们的项目，整体提升项目效率，形成一个完整的系统

项目从简单到复杂，缺什么补什么，这就是一个**渐进式的过程**。

#### 高效

- 16kb min+gzip的运行大小
更小的体积，却能提供远超其他模板引擎的性能

- 超快虚拟DOM
多次操作，一次写入

- 最省心的优化
js能做的，就不会在vue中再次实现，更多的是提升vue的效率


## 基础指令介绍
***

#### 指令使用
- v-model
用于表单
- v-text
用于文本渲染，和双大括号的功能一致，但是后者在Vue未初始化之前会可能会呈现在页面上，所以在渲染页面的过程中更多的去使用v-text.
- v-show
用于DOM的显示隐藏（display:none/block/...）
- v-if
用于DOM的显示隐藏（DOM如果不显示，则整个DOM都没有）
- v-bind
用于属性绑定
- v-for
用于表格，li标签的循环
- v-on
用于事件绑定

#### 过滤器filter
对接口返回的字段进行业务转换

#### 组件Component
把一个网页拆分成多个组件，每一个独立的组件可以进行复用