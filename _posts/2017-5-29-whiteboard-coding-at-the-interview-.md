---
layout:     post
title:      "当面试官让你手写代码时，请使用PREP"
subtitle:   "一个能给面试官留下绝佳印象的解决方案"
date:       2017-05-29 16:00:00 
author:     "9aoyang"
header-img: "img/whiteboard-coding.jpg"
tags:
    - 面试 
    - 算法
    - 编程
---

> PREP is a mnemonic I created to help you remember the steps involved in solving whiteboard coding problems. It stands for **P**arameters, **R**eturn, **E**xample, **P**seudocode

<p style="text-align: right">——Andy Tiffany</p>

<img src="/img/in-post/whiteboard-coding/PREP-diagram.png" alt="PREP diagram" title="PREP图解">

这个助记符是新的，但是其技术是经过实战检验的。本质是一个对初学者比较友好版本的[测试驱动开发](https://zh.wikipedia.org/wiki/%E6%B5%8B%E8%AF%95%E9%A9%B1%E5%8A%A8%E5%BC%80%E5%8F%91)，很适合编程挑战者。

我们一起通过一个例子来学习PREP。例子中我将使用JavaScript语言，但是这项技术适用于任何编程语言。

**面试官要求你写一个函数，输入一个句子并返回其中最长的单词。你怎么做？**

---
## “P” is for Parameters

大部分问题都会涉及编写函数。在这一步中你需要确定你的函数需要输入一些什么参数。并给它们取一个有意义的名字。

在这里，问题描述中“输入”，“获取”等关键字会给你指导，你也可以和面试官确认。在本例中“输入一个句子”这一描述说明了这个函数应该输入一个字符串参数。

所以你已经确定了参数的类型。但是参数名称呢？听起来也许很简单，但是好的命名是一项至关重要的编程技巧，这需要练习。

你可以命名为“sentenceString”，但是命名为“sentence”相比更简洁，并仍然清晰地表明我们处理的是字符串。

这只是第一步，你还需要为函数取一个有意义的名称。在本例中“longestWord”既准确又具有描述性。好了现在你已经决定了这一点，你可以像这样写下一个函数：

```
function longestWord(sentence){ 

}
```

---

## “R” is for Return

这个函数返回什么？一个数字？一个boolean值？还是一个字符串？

请牢记：函数的返回不等同于它在print或者log语句中显示的内容（如果有print或者log输出的话）。

同样的，你可以查看问题的描述来确认返回内容。“返回最长的单词”告诉你需要返回一个单词，单词也就是字符串。现在我们可以创建一个变量来代表返回值并放置到你的函数中。尽管你还不能返回一个正确的结果，但是你已经设置了一个正确的返回类型。你已经创建了一个占位符，这使得我们更容易进行下一步。

```
function longestWord(sentence){ 

    var word = "placeholder"; 

    return word; 

}
```

---
## “E” is for Example

即使是专家级的开发者，静止的代码也没有运行起来的代码好理解。你需要尽快的让你的代码跑起来并保持“活力“。你可以通过一个测试用例来给你的函数注入活力。


你知道如果给你的函数输入”I saw a hippopotamus,“这个句子，只要正确运行它应该返回字符串”hippopotamus“。但是现在，你只需要看一下上一步设置的占位符来确认代码已经设置正确并能够跑起来。

```
function longestWord(sentence){ 

    var word = "placeholder"; 

    return word; 

} 

console.log(longestWord("I saw a hippopotamus"));
```
---
## The last “P” is for Pseudocode

现在是不是已经蠢蠢欲动准备编码了，但是现在开始编码会很容易陷入一些细节从而分散你解决整体问题的注意力。首先你需要设计一个策略，而伪代码就是针对这种情形的策略。



伪代码是一系列用口头语言写成的精确语句，描述了你需要做什么。

```
function longestWord(sentence){

    // 用一个变量来保存目前为止最长的单词

    var word = "placeholder";



    //将句子转换成一组单词，以便我们能够遍历每一个单词。



    // 遍历每一个单词。    



    //如果当前单词的比目前为止最长的单词还长，更新保存最长单词的变量



    // 在检查完所有的单词后，返回保持最长单词的变量

    return word;

}



//只要代码运行正常，log应该输出“hippopotamus”。现在它应该输出“placeholder”

console.log(longestWord("I saw a hippopotamus"));
```

## You’ve finished PREP. Now you can code!

```
function longestWord(sentence){

    // 用一个变量来保存目前为止最长的单词.

    var longestWordSoFar = "";



    // 将句子转换成一组单词，以便我们能够遍历每一个单词

    var wordArray = sentence.split(" ");

    var currentWord;



    // 遍历每一个单词

    for (var i = 0; i < wordArray.length; i++){

    currentWord = wordArray[i];

    // 如果当前单词的比目前为止最长的单词还长，更新保存最长单词的变量

    if (currentWord.length > longestWordSoFar.length){

        longestWordSoFar = currentWord;

    }

    }



    // 在检查完所有的单词后，返回保持最长单词的变量

    return longestWordSoFar;

}



// 只要代码运行正常，log应该输出“hippopotamus”

console.log(longestWord("I saw a hippopotamus"));
```

现在你已经完成了最困难的部分。你可以长舒一口气，至少已经有一个可以运行的解决方案。这时，还有两个问题需要思考：

- 是否存在一些边界条件会使代码崩溃？例如，你有考虑句末有句号的情形吗？你需要为这些边界条件写更多的测试用例，在必要的情况下修改代码。

- 你能够把代码整理得更整洁、或者更高效吗？在贸然解决问题之前你应该与面试官讨论让他知道你的想法。

好了，就这么多。整个过程第一次看起来有点过于呆板，但是请相信我，这将成为第二自然--就像学习驾驶一样。即使已经编程超过12年，在解决问题是我仍然会遵循这样的顺序。我可能会使用一些正式的测试框架，而不是像本例中这样使用log输出，但是其本质是一样的。

现在你也来试一试？这里有几个入门级的问题你可以用来练习，总体由易到难的顺序：

1. 加入你有一个字符串数组[ “adios”, “bye”, “ciao” ]。你的任务是写一个total_characters函数，接收这个数组作为参数返回数组中所有字符的总和。

2. 写一个函数，抛硬币n次，计算出现“人头”的次数。

3. 我们会给你一个包含两个数的数组，返回这两个数的和以及这两个数之间的所有数。注意最小的数不一定总是在第一个。尝试使用自己先使用PREP来完成框架，并且随时都可以到这里确认并完成最后的解决方案。摘自[Free Code Camp](https://www.freecodecamp.com/challenges/sum-all-numbers-in-a-range)

本文译自有着12年编程经验的First Step Coding创始人Andy Tiffany的经验分享。

<a href="https://medium.freecodecamp.com/before-you-code-remember-to-prep-for-your-coding-interview-2ccfb58147db" title="When it comes to whiteboard coding interviews, remember to PREP">阅读原文</a>




