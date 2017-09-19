---
layout:     post
title:      "JavaScript编程精解笔记 (5)"
subtitle:   "高阶函数"
date:       2017-06-05 00:00:00 
author:     "9aoyang"
header-img: "img/eloquent-javascript.jpg"
catalog: true
tags:
    - 前端
    - Javascript
    - JavaScript编程精解
---
# 第五章 高阶函数

#### 5.1 抽象

抽象可以隐藏底层的实现细节，从更高（或更加抽象）的层次看待我们要解决的问题。

我们需要具备在恰当时候将代码抽象出来，形成一个新的函数或概念的能力。

#### 5.2 数组遍历抽象

常见的`for`循环语句：

```javascript
var array = [1, 2, 3];
for (var i = 0; i < array.length; i++) {
    var current = array[i];
    console.log(current);
}
```

这样的编写方法不仅不够优雅，而且也会程序缺陷留下了可乘之机。我们有可能不小心复用了变量`i`，错误地拼写了`length`，或者混淆了
变量`i`和`current`等。

如果将这段代码抽象成一段函数，该怎么做呢？

```javascript
function logEach(array) {
    for (var i = 0; i < array.length; i++) {
        console.log(array[i]);
    }
}
```

如果我们想执行打印元素以外的操作该怎么办呢？我们可以使用函数来定义我们想做的事，而函数也是值，因此我们可以将期望执行的操作封装成函数，然后传递进来。

```javascript
function forEach(array, action) {
    for (var i = 0 ; i <array.length; i++)
        action(array[i]);
}

forEach(['gaoyang', '9aoyang', '羔羊']， console.log)；
// gaoyang
// 9aoyang
// 羔羊
```

通常来说，我们不会给`forEach`传递一个预定义的函数，而是直接新建一个函数值。

```javascript
var numbers = [1, 2, 3, 4, 5], sum = 0;
forEach(numbers, function(number) {
    sum += number;
});
console.log(sum);
```

实际上，我们不需要自己编写`forEach`函数，该函数其实是数组的一个标准方法。因为数组提供的方法是对自身进行操作，因此`forEach`函数实际上只接受一个参数，即每个元素的处理函数。

#### 5.3 高阶函数

如果一个函数操作其他函数，即将其他函数作为参数或将函数作为返回值，那么我们可以将其称为高阶函数。

我们可以使用高阶函数对一系列操作和值进行抽象。高阶函数有多种表现形式。

你可以使用高阶函数来新建另一些函数

```javascript
function greaterThan(n) {
    return function(m) { return m > n; }
}
var greaterThan10 = greaterThan(10);
console.log(greaterThan10(11))
```

你也可以使用高阶函数来修改其他的函数

```javascript
function noisy(f) {
    return function(arg) {
        console.log('calling with', arg);
        var val = f(arg);
        console.log('calling with', '- got', val);
        return val;
    };
}
noisy(Boolean)(0);
// call with 0
// call with 0 - got false
```

你甚至可以使用高阶函数来实现新的控制流

```javascript
function unless(test, then) {
    if (!test) then();
}
function repeat(times, body) {
    for (var i = 0; i < times; i++) body(i);
}

repeat(3, function(n) {
    unless(n % 2, function() {
        console.log(n, 'is even');
    });
});
```

高阶函数的用法正是利用了我们在第3章中所讨论的词法作用域规则。在前面的示例当中，变量n是属于外部函数的参数，但由于内部函数可以访问外部的作用域，因此内部的函数也可以使用变量n。内部函数的函数体可以访问其外部环境的变量，这与循环及条件语句中的{}语句块有异曲同工之妙。其中内部函数与语句块
之间的主要区别在于，在内部函数中声明的变量不会因为外部函数执行结束而丢失，这个特性十分有用。

#### 5.4 参数传递
