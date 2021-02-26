title: canvas
author: 汪秋月
tags:
  - canvas
categories: []
date: 2021-02-05 09:53:00
---
# 什么是canvas？

- HTML5 元素
- 是一个矩形区域画布，可以控制其每一像素，用于在网页上绘制图形
- canvas 本身并没有绘图能力，通常是通过js绘制
- canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法

# canvas 的历史和优势
...

# 简单示例

```
<canvas width="200" height="100"></canvas>
```

- width: 宽度
- height: 高度

[demo](/demo/canvas/index.html)

**canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成**

```
<canvas id="myCanvas" width="200" height="100"></canvas>

<script type="text/javascript">
    var canvas = document.getElementById("myCanvas");	//根据 id 找到 canvas 元素
    var cxt = canvas.getContext("2d");	//getContext() 方法返回一个用于在画布上绘图的环境
    cxt.fillStyle = "#FF0000";  //填充颜色
    cxt.fillRect(0, 0, 100, 50);    //规定了形状，位置，尺寸
</script>
```
[demo](/demo/canvas/index2.html)


# 基本形状

## 线

<iframe width="100%" height="300" src="//jsrun.net/bPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 圆

<iframe width="100%" height="300" src="//jsrun.net/qPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 矩形

<iframe width="100%" height="300" src="//jsrun.net/WPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 被填充的矩形

<iframe width="100%" height="300" src="//jsrun.net/fPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


## 画一条正弦曲线

<iframe width="100%" height="300" src="//jsrun.net/vPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## 飘动的小红旗

<iframe width="100%" height="300" src="//jsrun.net/XPaKp/embedded/all/light" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

