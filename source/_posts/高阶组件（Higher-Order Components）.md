title: 理解高阶组件
author: 汪秋月
date: 2019-11-18 10:12:22
tags:
---
## 前言
- - - - 
> 有时候人们很喜欢造一些名字很吓人的名词，让人一听这个名词就觉得自己不可能学会，从而让人望而却步。但是其实这些名词背后所代表的东西其实很简单<br>
> 不能说高阶组件就是这么一个东西。但是它是一个概念上很简单，但却非常常用、实用的东西，被大量 React.js 相关的第三方库频繁地使用。<br>
> 在前端的业务开发当中，你不掌握高阶组件其实也可以完成项目的开发，但是如果你能够灵活地使用高阶组件，可以让你代码更加优雅，复用性、灵活性更强。它是一个加分项，而且加的分还不少。
> <p align=right >-----    React.js 小书</p>

想要理解 **高阶组件** ，我们得先来回顾一下 **高阶函数** 的定义


## 高阶函数(Higher-Order Function)
- - - - 

在介绍高阶函数的定义之前，先简单的举几个例子

js中内置的很多方法其实都是高阶函数，如 `setTimeout()` 、`setInterval()`、`some()`、`every()`、`filter()`、`map()`、`forEach()`等

比如 setTimeout

用法：
```
setTimeout(() => { 
    alert("Hello"); 
}, 3000);
```
观察 `setTimeout` 中接受的参数

其中第一个参数是一个函数，是你想要在到期时间(delay毫秒)之后执行的函数。第二个参数是延迟的毫秒数。


像这样把函数作为参数的函数，其实就是一种高阶函数。


这样我们再来看高阶函数的定义就很容易被理解了

### 高阶函数的定义

- 函数可以作为参数被传递
- 函数可以作为返回值输出




## 高阶组件（Higher-Order Components）
- - - - 
 先放个[官网文档](https://zh-hans.reactjs.org/docs/higher-order-components.html#gatsby-focus-wrapper)
 
 总结下：
 
- 高阶组件其实并不是一个组件而是一个函数

- 高阶组件就是接受一个组件作为参数并返回一个新组件的函数

联系高阶函数，高阶组件就很容易被理解了，它其实就是一个组件为参数的函数



### 高阶组件举例

举个例子，我们在写代码中经常用到的高阶组件

`react-router` 中的 `withRouter` 就是一个高阶组件

看看官网用法

```
import React from "react";
import PropTypes from "prop-types";
import { withRouter } from "react-router";

// A simple component that shows the pathname of the current location
class ShowTheLocation extends React.Component {
  static propTypes = {
    match: PropTypes.object.isRequired,
    location: PropTypes.object.isRequired,
    history: PropTypes.object.isRequired
  };

  render() {
    const { match, location, history } = this.props;

    return <div>You are now at {location.pathname}</div>;
  }
}

// Create a new component that is "connected" (to borrow redux
// terminology) to the router.
const ShowTheLocationWithRouter = withRouter(ShowTheLocation);
```

`withRouter()` 函数的参数是一个组件，这样的函数就叫做高阶组件

## 高阶函数的使用
 - - - - 
1. 直接包裹 higherOrderComponent(WrappedComponent)

2. 使用装饰器 @higherOrderComponent


### 为什么需要高阶组件

- 多个组件都需要某个相同的功能，使用高阶组件可以减少重复实现



## 编写高阶组件
 - - - - 
1. 实现一个普通组件

2. 将普通组件用函数包裹

