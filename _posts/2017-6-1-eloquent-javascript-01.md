---
layout:     post
title:      "JavaScript编程精解笔记 (1)"
subtitle:   "值、类型和运算符"
date:       2017-06-01 00:00:00 
author:     "9aoyang"
header-img: "img/eloquent-javascript.jpg"
catalog: true
tags:
    - 前端
    - Javascript
    - JavaScript编程精解
---

***
> 在计算机的世界当中，只有数据可以读取、修改以及新建数据，数据可以用来表示任何信息

# 第一章 值、类型和运算符

## 1.1 值

#### 六种基本的值类型：

- 数字（number）
- 字符串（string）
- 布尔值（boolean）
- 对象（object）
- 函数（function）
- 未定义类型（undefined）

## 1.2 数字

- JavaScript使用固定长度为64的位序列来存储数字值
- 如果长度有64位，则可以表示2^64个数字（1800亿亿），但事实上因为符号位的存在，以及表示非整数，实际可存储的数字范围是1900万亿
- 三个特殊值：Infinity，-Infinity，NaN

```javascript
Infinity + Infinity;    // Infinity
Infinity - Infinity;    // NaN
```

## 1.3 字符串

- 单引号和双引号都可以用来标记字符串，但遵从良好的代码习惯一般最外层用单引号
- 字符串中含有特殊字符时要使用转义符`\`

## 1.4 一元运算符

- 并非所有运算符都用符号表示，有些运算符是用单词表示的
- 使用N个值进行运算的运算符称为N元运算符

## 1.5 布尔值

该类型的值只有两种取值：`true`和`false`

#### 比较

```javascript
//大于
3 > 2    // true

//小于
3 < 2    // false

//不等于
'9aoyang' != 'gaoyang'    // false

//不同的非法运算结果也不会相等
NaN == NaN    // false
```

此外还有`>=`（大于等于）、`<=`（小于等于）、`===`（严格相等）、`!==`(严格不等)

#### 逻辑运算符

JavaScript支持三种逻辑运算符：与（`and`）、或（`or`）和非（`not`），可用于推理布尔值。

```javascript
//逻辑与
true && false    // false
true && true    // true

//逻辑或
false || true    // true
false || false    // false

//逻辑非
!true    // false
!false    // true
```

`||`优先级最低，其次是`&&`，接着是比较运算符（>，==等），最后是其他运算符。

#### 三元运算符

```javascript
true ? 1 : 2    // 1
fasle ? 1 : 2    // 2
```

## 1.6 未定义值

`null`和`undefined`，用于表示无意义的值，各自表示自身含义，不包含其他任何信息。

```javascript
null == 0    // false
null == undefined    // true
null === undefined    // false
```

## 1.7 自动类型转换

```javascript
8 * null    // 0    null变成0
'5' - 1    // 4    '5'变成5
'5' + 1    // 51    1变成'1'
'five' * 2    // NaN    无法显式地转成数字
false == 0    // true
```

建议使用三字符比较运算符来防止意外类型转换

**短路特性**：`&&`和`||`逻辑运算符使用一种特殊方式来处理不同类型的值，这两个运算符会将左侧的值转换成布尔类型，以决定如何进行后续操作，但返回左侧值还是右侧值，则取决于运算符和左侧转换结果。

```javascript
null || '9aoyang'    // 9aoyang
'羔羊' || '9aoyang'    // 羔羊
```

**短路计算**：只有必要时才会计算右侧的表达式。

## 1.8 小结

- 介绍了JavaScript的四种类型的值：数字、字符串、布尔值和未定义值。
- 算数二元运算符（`+`、`-`、`*`、`/`和`%`）
- 字符串连接符（`+`）
- 比较运算符（`==`、`!=`、`===`、`!==`、`<`、`>`、`<=`、`>=`）
- 逻辑运算符（`&&` 和 `||`）
- 一些一元运算符（`-` 表示负数、`！`表示逻辑非、`typeof`用于查询值类型）