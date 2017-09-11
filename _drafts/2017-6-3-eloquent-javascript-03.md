---
layout:     post
title:      "JavaScript编程精解笔记（3）"
subtitle:   "函数"
date:       2017-06-03 00:00:00 
author:     "9aoyang"
header-img: "img/eloquent-javascript.jpg"
catalog: true
tags:
    - 前端
    - Javascript
    - JavaScript编程精解
---
# 第三章 函数

- 函数是JavaScript中不可或缺的组成部分
- 函数是构造大型程序的工具，可以用于减少重复性工作、为子程序命名并隔离各个子程序的运行。

#### 3.1 定义函数

创建函数的表达式以关键字`function`开头。

```javascript
var fun = function (parameter1, parameter2, ...) {//参数可以为空，也可以为一或多个
    // 函数体，哪怕只有一条语句，也要包含在大括号中，语句会在调用函数时执行
    ...
    // return语句决定了函数的返回值，后面不跟表达式时返回undefined
    return;
}
```

#### 3.2 参数和作用域

- 函数的参数初始值由函数调用者提供。

- 函数内部创建的变量和参数都属于函数的局部变量，这种隔离机制确保了函数间不会相互干扰。

#### 3.3 嵌套作用域

- 可以在函数中创建其他函数，并产生不同程度的局部作用域。

- 任何局部作用域都可以访问到包含它的局部作用域

- 函数内部变量的可见性取决于函数在代码当中的位置，在包含了一个函数定义的代码块中，这个函数可以访问到代码块中的所有变量，即函数上层的代码块中的变量和函数内部的变量。这种控制变量的方法称为**词法作用域**。

- `let`关键字作用与`var`相同，只不过变量作用域是块作用域而非函数局部作用域。

#### 3.4 函数值

**函数和函数名的区别**：**函数**是一种叫做function引用类型的实例，因此函数是一个对象。对象是保存在内存中的，**函数名**则是指向这个对象的指针。

JavaScript中**函数是一等公民**，可以作为参数传入别的函数，也可以作为一个函数的返回值，也可以被重新赋值。

#### 3.5 符号声明

函数声明还有一种更为简洁的方式：

```javascript
function fun(parameter) {
    //todo
}
```

- 函数声明不遵循一般的从上到下的流控制规则。

```javascript
console.log('are you ok ?', ans());

function ans() {
    return 'yeah, i\'m ok';
}
```

- 为了确保函数在不同环境下运行的行为一致，应在最外层的函数或程序作用域中进行函数声明。

#### 3.6 调用栈

由于函数需要在执行结束后跳转回调用该函数的代码位置，因此计算机必须记住函数调用的上下文。我们将计算机存储这个上下文的区域称之为`调用栈`。

- 当函数调用时，当前的上下文信息就会被存储在栈顶

- 当函数返回时，系统会删除存储在栈顶的上下文信息，并使用该信息继续执行程序。

```javascript
// 若计算机空间无限大，循环调用会一直执行下去，但事实上是该程序会耗尽内存空间，导致“栈空间溢出”。
function chicken() {
    return egg();
}
function egg() {
    return chicken();
}
console.log(chicken() + ' came first.');
```

#### 3.7 可选参数

JavaScript对传送函数的参数数量几乎不做任何限制。如果你传递了过多参数，多余的参数就会被忽略，而如果你传递的参数过少，遗漏的参数将会被赋值成undefined。

缺点：你可能恰好向函数传递了错误数量的参数，但没有人会告诉你这个错误。

优点： 我们可以利用这种行为来让函数接收可选参数。

#### 3.8 闭包

如果函数已经执行结束，那么这些由函数创建的局部变量会如何处理呢？

```javascript
function wrapValue(n) {
    var localVariable = n;
    return function { return localVariable; };
}
var wrap1 = wrapValue(1);
var wrap2 = wrapValue(2);
console.log(wrap1());
// 1
console.log(wrap2());
// 2
```

这段代码很好地印证了局部变量会在每次函数调用时重新创建，不同的函数调用是不会对其他函数内的局部变量产生影响的。

这种引用特定的局部变量实例的功能称为**闭包**。一个包装了一些局部变量的函数是一个闭包。利用闭包的特性，我们不再需要担心变量的生命周期问题，很多高级应用都依靠它来实现。

```javascript
function multiplier(factor) {
    return function(number) {
        return number * factor;
    }
}

var twice = multiplier(2);
console.log(twice(5));
//10
```

可以把关键字`function`当做一种“冻结”代码并将其打包成函数值的模型。所以当看到“return function(...) {...}”这样的代码时，可以将其理解为一个句柄，其中句柄指向一段包装好的计算代码。

#### 3.9 递归

函数完全可以自己调用自己，只要避免栈溢出的问题即可。我们把函数调用自身的行为称为**递归**。

```javascript
function power(base, exponent) {
    if (exponent == 0)
      return 1;
    else
      return base * power(base, exponent-1);
}

console.log(power(2, 3));
// 8
```

需要注意的是，在标准的JavaScript实现当中，递归写法的函数执行效率比循环写法的函数慢了大约10倍。如何权衡性能与优雅是一个值得考虑的问题，但有一条基本原则：**除非程序执行速度确实太慢，否则先不要关注效率问题。**

对于某些问题来说，递归相较于循环更能解决问题。这类问题通常需要执行和处理多个分支，而每个分支又会引出更多的执行分支。

#### 3.10 添加新函数