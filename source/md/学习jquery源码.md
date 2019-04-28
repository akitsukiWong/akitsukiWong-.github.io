title: 学习jquery源码
author: 汪秋月
tags: []
categories: []
date: 2018-09-07 09:21:00
---
## 学习jQuery源码笔记

### 1. 立即执行函数

**IIFE** (立即调用的函数表达,Immediately-Invoked Function Expression，简称IIFE)


```
(function() {
    /*code*/
})()
```
或者
```
(function() {
    /*code*/
}())
```

##### IIFE的作用

- 不必为函数命名，避免了污染全局变量
我们这里直接对匿名函数使用这种“立即执行的函数表达式”，并且在函数的在括号内定义之后立刻调用执行，这样避免为函数命名，减少命名的冲突

- IIFE内部形成了一个单独的作用域，可以封装一些外部无法读取的私有变量。
在的JavaScript语法中我们知道作用域分为全局作用域和函数作用域(当然在后面的ES6中引入了块级作用域)，依据函数作用域这一特点，在匿名函数中我们可以封装一些自己内部模块使用的私有变量。

> 例子
> ```
(function () {
   var a=10;
})();
alert(a);
```
> 会报错 ` a is not defined `
