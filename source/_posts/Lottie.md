title: Lottie
author: 汪秋月
date: 2019-10-22 09:08:40
tags:
---
## Lottie 是什么


Lottie 是 Airbnb 开源的一个动画渲染库，可应用于 Android, iOS, Web, React Native 等平台。

Lottie 支持渲染播放 AE 动画，通过Bodymovin解析AE动画，并导出可在移动端和web端渲染动画的json文件。换言之，设计师用AE把动画效果做出来，再用Bodymovin导出相应地json文件给到前端，前端使用Lottie库就可以实现动画效果。


## 为什么使用 Lottie

设计使用AE设计出炫酷动画，开发实现十分困难，极其复杂。毕竟开发工程师要通过代码把动效实现出来，数值什么的都是开发通过设计给了效果图去猜测，实现出来了也都存在还原度的问题。

使用 Lottie 不仅可以 100% 还原动效，而且无需动效标注。直接通过 AE 输出动效文件给开发。开发人员直接调用，然后完美还原。

## Lottie支持的AE属性


![upload successful](/images/pasted-12.png)


## 效果预览

[https://lottiefiles.com/](https://lottiefiles.com)


## 前端使用 Lottie

### 静态url

```
https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.5.9/lottie.min.js
```

### NPM

```
npm install lottie-web
```

### 使用

```
lottie.loadAnimation({
    container: element,
    renderer: 'svg',
    loop: true,
    autoplay: true,
    path: 'data.json' 
});
```