---
layout:     post
title:      "JavaScript编程精解笔记 (4)"
subtitle:   "数据结构：对象和数组"
date:       2017-06-04 00:00:00 
author:     "9aoyang"
header-img: "img/eloquent-javascript.jpg"
catalog: true
tags:
    - 前端
    - Javascript
    - JavaScript编程精解
---
# 第四章 数据结构：对象和数组

我们可以使用对象来把值和其他对象组织起来，通过这种手段来构造更为复杂的结构。

#### 数据集

**数组**：专门用于存储一系列的值。**数组中第一个元素的索引是0，而非1。**

#### 属性

在JavaScript中，几乎所有的值都有属性，但`null`和`undefined`没有。

有两种最为常用的访问属性的方法：使用点（`.`）和方括号`[]`。如果使用点，则点之后的部分必须是一个合法变量名，即直接写变量名称。如果使用方括号，则JavaScript会将方括号中表达式的返回值作为属性名称。

#### 方法

我们通常将包含函数的属性称为某个值的方法。比如说，“toUpperCase是字符串的一个方法”。

```javascript
//数组对象的一些方法
var mack = [];
mack.push("Mack");
mack.push("the", "Knife");
console.log(mack);
// ["Mack", "the", "Knife"]
console.log(mack.join(" "));
// Mack the Knife
console.log((mack.pop));
// Knife;
console.log(mack);
// ["Mack", "the"]
```

#### 对象

对象类型的值可以存储任意类型的属性，我们可以随意增删这些属性。一种创建对象的方法是使用大括号。

```javascript
var day1 = {
    // 大括号中,可以添加一系列属性，并用逗号分隔。每一个属性均以名称开头，紧跟一个冒号，然后是对应属性的表达式。
    squirrel: false,
    events: ['work', 'touched tree', 'pizza', 'running', 'television']
};
console.log(day1.squirrel);
// false
console.log(day1.wolf);
// 读取一个不存在的属性就会产生undefined值
day1.wolf = false;  // 如果属性存在，就会替换原有值，如果属性不存在，则创建一个新的属性。
console.log(day1.wolf);
// false
```

`delete` 一元运算符，其操作数是访问属性的表达式，可以从对象中移除指定属性。
`in` 二元运算符，第一个操作数是一个表示属性名的字符串，第二个操作数是一个对象，它会返回一个布尔值，表示该对象是否包含该属性。

```javascript
var anObject = {left: 1, right: 2};
console.log(anObject.left);
// 1
delete anObject.left;
console.log(anObject.left);
// undefined
console.log(left in anObject);
// false
console.log(right in anObject);
// true
```

数组是一种用于存储数据序列的特殊对象。

#### 可变性

数字、字符串和布尔值都是不可变值，但对于对象来说，我们可以通过修改其属性来改变对象的内容。

```javascript
var object1 = {value: 10};
var object2 = object1;
var object3 = {value: 10};
// 在javascript中，使用 == 运算符来比较两个对象时，只有两个对象引用了同一个值，结果才会返回true
console.log(object1 == object2)
// true
console.log(object1 == object3)
// false
```

#### 对象映射

当我们要保存计算结果时，其中一种方法是使用数组，但这么做有一个问题就是查询时需要循环遍历整个数组。 一种更好的解决方法是用事件类型作为对象的属性名称。这样我们就可以使用方括号来创建或读取对应的属性，也可以使用`in`运算符来检测其中是否包含我们期望的属性。

#### 一些实用的数组方法

`push`和`pop`：在数组末尾添加或删除元素

`unshift`和`shift`：在数组开头添加或删除元素

`indexOf`和`lastIndexOf`：从数组第一个（最后一个）元素向后（前）搜索。都有一个可选参数，用来指定搜索的起始位置

`slice`：接受一个起始索引和一个结束索引，返回[起始索引，结束索引）

[数组方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)

#### 字符串及其属性

`length`：获取字符串长度

`indexOf`：与数组的不同在于字符串中可以使用多个字符作为搜索条件

`trim`：用于删除字符串中开头和结尾的空白符号（空格、换行符和制表符等符号）

`charAt`：获取字符串中某个特定的字符

[字符串方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)

#### arguments对象

每当函数被调用时，就会在函数体的运行环境当中添加一个特殊的变量`arguments`。该变量指向一个包含了所有入参的对象。在JavaScript中，我们可以传递多于（或少于）函数参数列表定义个数的参数。

- `arguments`有一个`length`属性，表示实际传递给函数的参数个数。每个参数对应一个属性，被命名为0、1、2，依次类推。

- `arguments`看起来很像一个数组。但该对象不包含任何数组方法。

#### Math对象

`Math`对象中包含了许多与数字相关的工具函数。简单地把一组相关的功能打包成一个对象供用户使用。其对象本身没有什么实际用途，主要目的是提供一个“命名空间”，封装了所有数学运算函数和值，确保这些元素不会变成全局变量。

#### 全局对象

JavaScript全局作用域中有很多全局变量，都可以通过全局对象进行访问。每一个全局变量作为一个属性存储在全局对象当中。在浏览器中，全局对象存储在`window`变量当中。

```javascript
var myVar = 10;
console.log('myVar' in window);
// true
console.log(window.myVar);
// 10
```

#### 本章小结

1. 对象和数组（一种特殊对象）可以将几个值组合起来形成一个新的值。理论上讲，我们可以将一组相关的元素打包成一个对象，并通过这个对象来访问这些元素，以避免管理那些支离破碎的元素。

1. 在JavaScript中，除了`null`和`undefined`以外，绝大多数的值都含有属性。我们可以用`value.propName`或`value[propName]`的方式来访问属性。对象使用名称来定义和存储一定数量的属性。另外，数组中通常会包含不同数量的值，并使用数字（从0开始）作为这些值的属性。

1. 在数组中有一些具名属性，比如`length`和一些方法。方法是作为属性存在的函数，常常作用于其所属的值。

1. 对象可以用来当做映射表，将名称与值关联起来。我们可以使用`in`运算符确定对象中是否包含特定名称的属性。我们同样可以在`for`循环中（for(var name in object)）使用关键字`in`来遍历对象中包含的属性。