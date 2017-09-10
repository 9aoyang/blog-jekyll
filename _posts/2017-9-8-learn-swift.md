---
layout:     post
title:      "Swift入门（一）"
subtitle:   "变量和类型"
date:       2017-09-01 00:00:00 
author:     "9aoyang"
header-img: "img/iphone7.jpg"
catalog: true
tags:
    - iOS
    - Swift
---
# 变量和类型

## 数据类型

![Built-in data types](http://upload-images.jianshu.io/upload_images/4260383-e26a936d8081ee33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 变量

```swift
var petsAge = 12 
var myMiddleInitial: Character = "A"
var numberOfWheels: Int = 4
var centimetersOfRainfall: Float = 5.5
var pi: Double = 3.14159265359
var letterOfTheDay: Character = "z"
var myFavoriteAnimal: String  = "nudibranch"
var rainingOutside: Bool  = true
```

#### float和double
float可以提高性能，double可以获得更高的精度。

#### 变量重新赋值
swift是强类型语言，不能改变已有类型变量的值为其他类型

## 常量

常量无法重新赋值，应在值预计不会变化时使用

```swift
let encouragement = "You can do it!"
encouragement = "C'mon, you got this!"

let birthYear = 2008
birthYear = 2010
```

> compiler: ERROR: Cannot assign a value: 'encouragement' is a 'constant'
compiler: ERROR: Cannot assign a value: 'birthYear' is a 'constant'

变量可以重新赋值，应在值预计会变化时使用
不确定时，最好声明变量为常量，这样可以避免代码中的值出现不希望发生的变动

```swift
// Example 1
let encouragement = "You can do it!"
var customizedEncouragement = "You can do it, Stephanie!"
customizedEncouragement = "You can do it, Ryder!"

// Example 2
let birthYear = 2008
var currentYear = 2016
var age = currentYear - birthYear
currentYear = 2017
age = currentYear - birthYear
```

## 命名规则

- 不能含有空格、数学符号、箭头和特殊符号
- 必须以字母、下划线开头

允许的命名

```swift
NumberOfYears
_numberOfYears
_numberOfYearsSince1800
valueOf$
```

不允许的命名

```swift
$myVariable
1dollarIsWorth
```

## 命名惯例

#### 驼峰命名法

```swift
totalCumulativeScore
secondsSinceLastUpdate
minutesTillLaunch
```

## 字面值

> A literal is a value that is written exactly as it's meant to be interpreted. In contrast, a variable is a name that can represent different values during the execution of the program. And a constant is a name that represents the same value throughout a program. But a literal is not a name — it is the value itself.

这段话解释了字面值和常量及变量之间的区别。简单点说，字面值就代表了值本身。