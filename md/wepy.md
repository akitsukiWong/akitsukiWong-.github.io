title: wepy学习
author: 汪秋月
tags:
  - wepy
categories: []
date: 2018-12-07 14:51:00
---
### 快速入门

##### 全局安装

```
npm install wepy-cli -g
```

##### 生成Demo开发项目

```
wepy init standard myproject
```

##### 安装依赖

```
npm  install
```

##### 实时编译

```
wepy build --watch
```

##### 设置微信开发者工具

- 选项中关闭ES6转ES5
- 选项中关闭上传代码时样式自动补全
- 选项中关闭代码压缩上传
- 选项中打开不检查安全域名（如果已配置好安全域名则建议关闭）

### @符号

- 原 `bindtap="click"` 替换为 `@tap="click"`
- 原 `catchtap="click"` 替换为 ` @tap.stop="click" `
- 原 `capture-bind:tap="click"` 替换为` @tap.capture="click"`
- 原 `capture-catch:tap="click"` 替换为` @tap.capture.stop="click"`

```
bindtap="click" data-index= {{index}}  
```
替换为  
```
@tap="click({{index}})" 
```