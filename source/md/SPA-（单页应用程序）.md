title: SPA （单页应用程序）
author: 汪秋月
date: 2018-09-29 08:42:59
tags:
---
#SPA （单页应用程序）

先简单复制粘贴一下什么是SPA

### 百度百科

单页Web应用（single page web application，SPA），就是只有一张Web页面的应用，是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。

#### 应用介绍

单页Web应用（single page web application，SPA），就是只有一张Web页面的应用。单页应用程序 (SPA) 是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。浏览器一开始会加载必需的HTML、CSS和JavaScript，所有的操作都在这张页面上完成，都由JavaScript来控制。因此，对单页应用来说模块化的开发和设计显得相当重要。

#### 特点

速度：更好的用户体验，让用户在web app感受native app的速度和流畅，

- MVVM：经典MVVM开发模式，前后端各负其责。
- ajax：重前端，业务逻辑全部在本地操作，数据都需要通过AJAX同步、提交。
- 路由：在URL中采用#号来作为当前视图的地址,改变#号后的参数，页面并不会重载。

## 笔记

初次学习vue-cli做的SPA
[代码在这](https://github.com/akitsukiWong/vueCliStudy) 

记个笔记

### 一. 流程

#### 1. 全局安装 vue-cli

```
npm install -g vue-cli
```

#### 2. 初始化

```
vue init webpack 项目名称
```

#### 3. 安装模块

```
npm install
```

#### 4. 启动服务器

```
npm run dev
```

#### 5. 打包

```
npm run build
```


























