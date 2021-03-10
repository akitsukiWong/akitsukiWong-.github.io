title: canvas
author: 汪秋月
tags:
  - canvas
categories: []
date: 2021-02-05 09:53:00
---
**参考：[canvas API中文文档](https://www.canvasapi.cn)**

# canvas

## 什么是 canvas

- canvas 是一个HTML5标签
- canvas 的作用是绘制图形
- canvas 本身并没有绘图能力，通常是通过js绘制
- canvas 提供了多种绘制路径、矩形、圆形、字符以及添加图像等方法可以供开发者调用，可以完成工作中遇到的绝大部分开发问题

## canvas 的主要作用

- 特效、动图
- 制作图形编辑器等工具
- 用于可视化领域
- 可内嵌多种媒体内容和特效内容
- 游戏，适合图像密集，其中的许多对象会被频繁重绘的游戏

## canvas 和 svg 的简单对比

- canvas 是HTML5标签，svg 是XML标签
- canvas 是基于像素的图形，也就是[位图](https://baike.baidu.com/item/%E4%BD%8D%E5%9B%BE)，svg 是[矢量图](https://baike.baidu.com/item/%E7%9F%A2%E9%87%8F%E5%9B%BE)，所以canvas依赖分辨率，放大会失真，产生锯齿，svg不会，所以svg更适合做高保真的视觉呈现
- canvas 不支持事件处理器，svg 支持，因为svg绘制出来的每一个图形的元素都是独立的DOM节点，能够方便的绑定事件或用来修改，canvas是一整张画布
- canvas 能够以 `.png` 或 `.jpg` 格式保存结果图像
- canvas 适合游戏，svg不适合做游戏



## 简单使用

```
<canvas id="myCanvas" width="200" height="100">您的浏览器不支持canvas，请升级或选择其他浏览器</canvas>
```
与其他标签一样，我们可以使用`<canvas></canvas>`的方式来向页面中嵌入一个画布内容。

标签里的内容只在不支持 `canvas` 的浏览器上才会显示

- width: 宽度，默认值300
- height: 高度，默认值150

[demo](/demo/canvas/index.html)

**canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成**

```
<canvas id="myCanvas" width="200" height="100">您的浏览器不支持canvas，请升级或选择其他浏览器</canvas>

<script type="text/javascript">
    var canvas = document.getElementById("myCanvas");	//根据 id 获取 canvas 元素
    var cxt = canvas.getContext("2d");	//getContext() 方法返回一个用于在画布上绘图的环境，指定为 2d 的视图环境
    cxt.fillStyle = "#FF0000";  //填充颜色
    cxt.fillRect(0, 0, 100, 50);    //规定了形状，位置，尺寸
</script>
```
[demo](/demo/canvas/index2.html)

总结一下

1. 布置画布：添加`<canvas>`标签
2. 获取画布：通过js获得`canvas`对象
3. 获得画笔：使用`canvas`对象的`getContext("2d")`方法，获得2D环境

## 坐标

![upload successful](/images/pasted-0.png)

# 常见形状

## 线

- [beginPath](https://www.canvasapi.cn/CanvasRenderingContext2D/beginPath)：开始画一段路径
- [strokeStyle](https://www.canvasapi.cn/CanvasRenderingContext2D/strokeStyle)：设置线条颜色
- [moveTo(x, y)](https://www.canvasapi.cn/CanvasRenderingContext2D/moveTo)： 起始点
- [lineTo(x, y)](https://www.canvasapi.cn/CanvasRenderingContext2D/lineTo)：终点
- [stroke()](https://www.canvasapi.cn/CanvasRenderingContext2D/stroke)：连接
- [lineWidth](https://www.canvasapi.cn/CanvasRenderingContext2D/lineWidth)：控制线条宽度
- [lineCap](https://www.canvasapi.cn/CanvasRenderingContext2D/lineCap): 控制线段两端展示

<iframe width="100%" height="300" src="//jsrun.net/bPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


## 矩形
- [rect](https://www.canvasapi.cn/CanvasRenderingContext2D/rect)：绘制矩形
- [strokeRect](https://www.canvasapi.cn/CanvasRenderingContext2D/strokeRect)：绘制矩形描边

<iframe width="100%" height="300" src="//jsrun.net/WPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 被填充的矩形
- [fillRect](https://www.canvasapi.cn/CanvasRenderingContext2D/fillRect#&introduction)：矩形填充


<iframe width="100%" height="300" src="//jsrun.net/fPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 圆

-[arc](https://www.canvasapi.cn/CanvasRenderingContext2D/arc)：绘制圆弧

<iframe width="100%" height="300" src="//jsrun.net/qPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


## 被填充的圆形
- [fill](fill)：路径填充

<iframe width="100%" height="300" src="//jsrun.net/FmaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 椭圆
- [ellipse](https://www.canvasapi.cn/CanvasRenderingContext2D/ellipse#&introduction)

## 贝塞尔曲线
- [quadraticCurveTo](https://www.canvasapi.cn/CanvasRenderingContext2D/quadraticCurveTo)：二次贝塞尔曲线
- [bezierCurveTo](https://www.canvasapi.cn/CanvasRenderingContext2D/bezierCurveTo)：三次贝塞尔曲线

[贝塞尔生成器](http://wx.karlew.com/canvas/bezier/)

# 文字
- [font](https://www.canvasapi.cn/CanvasRenderingContext2D/font#&introduction)
- [textAlign](https://www.canvasapi.cn/CanvasRenderingContext2D/textAlign)
- [textBaseline](https://www.canvasapi.cn/CanvasRenderingContext2D/textBaseline)
- [fillText](https://www.canvasapi.cn/CanvasRenderingContext2D/fillText)
- [strokeRect](https://www.canvasapi.cn/CanvasRenderingContext2D/strokeText#&introduction)
- [measureText](https://www.canvasapi.cn/CanvasRenderingContext2D/measureText)


## 根据文字生成随机头像
<iframe width="100%" height="300" src="//jsrun.net/JuaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

# canvas动画

## 原理
快速刷新的静态画面

利用定时器`setTimeout`或者`requestAnimationFrame`

绘制 - 清空 - 绘制 - 清空 - 绘制 ...

- [clearRect](https://www.canvasapi.cn/CanvasRenderingContext2D/clearRect)：清空画布

### [setTimeout](https://developer.mozilla.org/zh-CN/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)
通过设定间隔时间来不断改变图像位置，达到动画效果。但是容易出现卡顿、抖动的现象；

卡顿原因：
- settimeout任务被放入异步队列，只有当主线程任务执行完后才会执行队列中的任务，因此实际执行时间总是比设定时间要晚；
- settimeout的固定时间间隔不一定与屏幕刷新时间相同，会引起丢帧。


### [requestAnimationFrame](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestAnimationFrame)

优点：
- 是由浏览器专门为动画提供的API，在运行时浏览器会自动优化方法的调用，并且如果页面不是激活状态下的话，动画会自动暂停，有效节省了CPU开销。
- 重绘或回流的时间间隔紧紧跟随浏览器的刷新频率。
- 隐藏或不可见的元素不会进行重绘或回流，这意味着更少的CPU、GPU和内存使用量。




## 画一条直线
<iframe width="100%" height="300" src="//jsrun.net/HAaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


## 画一条正弦曲线

[复习正弦曲线知识](https://baike.baidu.com/item/%E6%AD%A3%E5%BC%A6%E6%9B%B2%E7%BA%BF)

<iframe width="100%" height="300" src="//jsrun.net/vPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>