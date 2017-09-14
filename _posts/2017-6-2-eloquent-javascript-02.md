---
layout:     post
title:      "JavaScript编程精解笔记 (2)"
subtitle:   "程序结构"
date:       2017-06-02 00:00:00 
author:     "9aoyang"
header-img: "img/eloquent-javascript.jpg"
catalog: true
tags:
    - 前端
    - Javascript
    - JavaScript编程精解
---
# 第二章 程序结构

#### 2.1 表达式和语句

**表达式**：产生值的操作的代码片段。

**语句**：表达式 + 分号 = 一条语句，在掌握何时省略语句结尾的分号以前，应遵循以分号为结尾的规则。

```javascript
// 这样的表达式不对外界产生任何影响
// 一条语句只有对外部产生影响才有意义
1;
!false;
```

#### 2.2 变量

可以使用任意不是**关键字**的单词作为变量名，变量名可以包含数字（不能以数字开头）、字母、下划线，除了$和_字符以外，不能包含其他任何标点符号。

可以将变量想象为许多的触须，而不是一个箱子。

1. 变量并不包含值，而是会引用这些值

1. 两个不同的变量可以引用同一个值

1. 程序只能访问仍被引用的值

1. 当需要保存一些状态的时候，可以生出一条新触须或者伸出一条触须，将其指向某个值

1. 空变量的值就是没有指向的触须，结果为undefined

```javascript
// 一条语句可以定义多个变量
var a = 1, b = 2;
console.log(a + b);
// 3
```

#### 2.3 关键字和保留字

**关键字**：具有特殊含义的单词

**保留字**：官方不允许将其作为变量名的单词

部分关键字和保留字列表：

```javascript
break case catch continue debugger default delete
do else false finally for function if implements
in instanceof interface let new null package private
protected public return static switch throw true
try typeof var void while yield this
```

#### 2.4 环境

给定时间内的变量和变量值的集合

#### 2.5 函数

函数：包装在变量中的一段程序

执行函数的操作称为**调用**或者**应用**

传递给函数的值称为**参数**

#### 2.6 `console.log`函数

console.log不是一个简单的变量，其实是一个表达式，从console变量中获取了其内部含有的log属性。

#### 2.7 返回值

我们把函数生成值的操作称之为**返回值**。在JavaScript中，任何生成值的表达式都可以嵌套在另一个作用域更大的表达式当中。

```javascript
console.log(Math.min(2, 4) + 100);
// 102
```

#### 2.8 `prompt` 和 `confirm` 函数

除`alert`之外，浏览器环境中还包含了其他几个用于弹出窗口的函数

```javascript
// confirm来询问用户是非性问题,返回true或false
confirm('Are you ok ?');

// prompt询问开放式问题，第一个参数是问题，第二个参数是缺省文本信息
// 用户输入信息以字符串的形式返回
prompt('Are you ok ?', '...');
```

现代Web编程中很少使用这两个函数，主要原因是无法对弹出窗口的风格进行控制。

#### 2.9 控制流

顺序执行流：如果程序中包含了不止一条语句，那么这些语句一定是按照自上而下的顺序执行的。

```javascript
var a = 1;
console.log(a);
// 1
```

#### 2.10 条件执行

条件执行流：通过布尔值判断，选择不同的路径执行语句。

```javascript
var a = 1;
if (!isNaN(a)) {
    console.log(a);
} else {
    colsole.log('Not a number');
}
```

#### 2.11 `while` 和 `do` 循环

循环控制流：重复执行某些代码的方法。

```javascript
// while循环
while (...) {
    //todo
}

// do循环
do {
    //todo
} while (...)
```

#### 2.12 代码缩进

缩进代码的作用：凸显出代码结构.

谁都不想阅读[面条式代码](https://zh.wikipedia.org/wiki/%E9%9D%A2%E6%9D%A1%E5%BC%8F%E4%BB%A3%E7%A0%81)不是吗?

#### 2.13 `for`循环

与`while`的不同在于，`for`将所有与循环状态相关的语句放在了一起。
```javascript
// for循环
for (...) {
    //todo
}
```

#### 2.14 跳出循环

1. 循环条件为`false`

1. `break`语句

1. `continue`语句,与`break`类似，可以跳出当前循环体，并进入下一轮循环迭代。

```javascript
for (var current = 20; ; current++) {
    if(current % 7 == 0) {
        break;
    }
}
console.log(current);
// 21

```

#### 2.15更新变量的简便方法

- `++`
- `--`
- `+=`
- `-=`
- `*=`
- `/=`

#### 2.16 `switch`分支

`switch`语句的设计初衷就是为了解决多条件分支的问题，令人尴尬的是，在JavaScript中，`if`编写的条件分支反而看起来更好。

```javascript
//switch语法
switch (...) {
    case 'condition1':
      //todo
      break;
    case 'condition2':
      //todo
    ...
    default:
      //todo
      break;
}
```

一旦开始执行某个`case`标签下的语句，就会一直执行下去，直到遇到`break`为止。

#### 2.17 大写

变量名中不能含有空格，但使用多个单词有助于清晰表达变量用途。随之也出现了很多书写方式：

```javascript
var fuzzylittleturtle;    // 不好的命名
var fuzzy_little_turtle;  // 比较好的命名
var FuzzyLittleTurtle;    // 不好的命名
var fuzzyLittleTurtle;    // 好的命名，驼峰命名法，一般都遵循这种风格
```

极少数情况下，变量名首字母也会大写，比如`Number`函数。这种方式表示该函数是`构造函数`。

#### 2.18 注释

什么时候需要注释：

1. 哪怕代码结构很清晰，阅读者（包括作者）很难只通过纯粹的代码来读懂程序包含的全部信息。

1. 代码中包含的信息晦涩难懂，阅读者无法理解其中含义

1. 将想法记录在程序中，或对开发尚未完成的部分做标记

```
// 单行注释
/*
多行注释
*/
```

#### 2.19 本章小结

1. 程序由语句构成，每条语句又有可能包含了更多的语句。语句中往往包含表达式，表达式又可以由更小的表达式组成。

1. 程序中语句从上到下执行，可以使用条件语句（if、else 和 switch）或循环语句（while、do 和 for）来改变程序控制流

1. 变量可以用来保存任何数据，并用一个变量名对其引用。环境是一组定义好的变量集合。JavaScript运行环境中总会包含一系列有用的标准变量。

1. 函数是一种特殊的值，用于封装一段程序。可以通过`funcrtionName（parameter1, parameter2`这种写法来调用函数。函数调用可以是一个表达式，也可以是一个值。