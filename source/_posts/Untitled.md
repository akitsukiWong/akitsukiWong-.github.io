title: 高阶组件 与 render props
author: 汪秋月
date: 2020-09-04 15:25:14
tags:
---
==参考资料==
- [高阶组件](https://zh-hans.reactjs.org/docs/higher-order-components.html#gatsby-focus-wrapper)
- [Render Props](https://zh-hans.reactjs.org/docs/render-props.html)
- [React.js 小书](https://www.bookstack.cn/read/react-naive-book/about.md)

# 前言
- - - - 

在编码中如果要重复实现相同功能，如何处理？

在react中有两种方法 **高阶组件** 和 **render props**


# 高阶组件（Higher-Order Components，HOC）

先来介绍一下高阶组件

> 有时候人们很喜欢造一些名字很吓人的名词，让人一听这个名词就觉得自己不可能学会，从而让人望而却步。但是其实这些名词背后所代表的东西其实很简单<br>
> 不能说高阶组件就是这么一个东西。但是它是一个概念上很简单，但却非常常用、实用的东西，被大量 React.js 相关的第三方库频繁地使用。<br>
> 在前端的业务开发当中，你不掌握高阶组件其实也可以完成项目的开发，但是如果你能够灵活地使用高阶组件，可以让你代码更加优雅，复用性、灵活性更强。它是一个加分项，而且加的分还不少。
> <p align=right >-----    React.js 小书</p>

**高阶组件** 其实不是什么高深莫测的东西，它类似于 **高阶函数**，就是一个纯函数，它会接受一个组件作为参数，然后返回一个新的组件。

那我们先来回顾一下 **高阶函数** 的定义

## 高阶函数(Higher-Order Function)

在介绍 **高阶函数** 的定义之前，先简单的举几个例子

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


像这样把函数作为参数的函数，其实就是一种 **高阶函数**。


这样我们再来看高阶函数的定义就很容易被理解了

### 高阶函数的定义

- 函数可以作为参数被传递
- 函数可以作为返回值输出




## 高阶组件（Higher-Order Components）
联系高阶函数，高阶组件就很容易被理解了，它其实就是一个组件为参数的函数

 先放个 [官网文档](https://zh-hans.reactjs.org/docs/higher-order-components.html#gatsby-focus-wrapper)
 
 总结下：
 
- 高阶组件其实并不是一个组件而是一个函数

- 高阶组件就是接受一个组件作为参数并返回一个新组件的函数





### 高阶组件举例

举个例子，我们在写代码中经常用到的高阶组件

`react-router` 中的 `withRouter` 就是一个高阶组件

看看`withRouter`官网用法

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
**注意最后一行**

`withRouter()` 是个函数，函数的参数是一个组件，这样的函数就叫做高阶组件

### 高阶函数的使用

1. 直接包裹 higherOrderComponent(WrappedComponent)

2. 使用装饰器 @higherOrderComponent


### 为什么需要高阶组件

- 多个组件都需要某个相同的功能，使用高阶组件可以减少重复实现



### 如何编写高阶组件

1. 实现一个普通组件

2. 将普通组件用函数包裹


# render props

以上我们对 高阶组件（HOC）有了基本的理解，那 render props 是什么呢？

其实 render props 的作用和高阶组件类似

唬人的效果也跟高阶组件类似，看起来很复杂，其实也很简单，如果不知道render props是啥，那就先从props入手。

## props
 
props大家应该都很清楚，props是react组件的属性，子组件通过 props 来传递数据。

举个例子：

```
function Hello(props) {
    return <h1>你好，{props.name}!</h1>;
}
 
const sayHello = <Hello name="小明"/>;
 
ReactDOM.render(
    sayHello,
    document.getElementById('example')
);
```
在子组件Hello中，通过 props.name 就可以取到name属性传来的值

这就是组件上进行普通数据的传递

但其实 props 也是可以传递组件的，这种在组件上传递组件的方式，就叫做render props

## render props

还是先放 [官网文档](https://zh-hans.reactjs.org/docs/render-props.html)

从官网示例来分析一下 render props

简单解释一下，就是组件中通过一个render的属性传递了一个组件

当然这个例子中属性叫做 render 只是凑巧了，这个属性名是可以随便起的

虽然叫做render props但是不一定得叫render的  

比如也可以叫 "children props"，像这样：

```
<Mouse children={mouse => (
  <p>The mouse position is {mouse.x}, {mouse.y}</p>
)}/>
```
完全没问题

甚至不一定得放在属性中，可以直接置到元素的内部，变成真正的 "children props"，像这样：

```
<Mouse>
  {mouse => (
    <p>The mouse position is {mouse.x}, {mouse.y}</p>
  )}
</Mouse>
```

回到例子，像这样的`<Mouse>`组件，组件的props中有一个 render（名字可以自己起）的方法，可以决定什么时候应该渲染`<Cat>`组件 ，并不是把 `<Cat>`组件硬写到 `<Mouse>` 组件里，的方式就是 `render props`

在Cat组件中，数据通过Mouse组件的state传过来，这样在Cat内部


高阶组件 https://codesandbox.io/s/hoc-fkv9b?file=/src/App.js

renderProps https://codesandbox.io/s/renderprop-ke8k1