title: 前端面试题（html）
author: 汪秋月
date: 2019-04-01 10:34:02
tags:
---

#### HTML行内元素、块状元素、行内块状元素的区别

块级元素：块级大多为结构性标记

```
  <address>...</adderss>   
  <center>...</center>  地址文字
  <h1>...</h1>  标题一级
  <h2>...</h2>  标题二级
  <h3>...</h3>  标题三级
  <h4>...</h4>  标题四级
  <h5>...</h5>  标题五级
  <h6>...</h6>  标题六级
  <hr>  水平分割线
  <p>...</p>  段落
  <pre>...</pre>  预格式化
  <blockquote>...</blockquote>  段落缩进   前后5个字符
  <marquee>...</marquee>  滚动文本
  <ul>...</ul>  无序列表
  <ol>...</ol>  有序列表
  <dl>...</dl>  定义列表
  <table>...</table>  表格
  <form>...</form>  表单
  <div>...</div>
```

行内元素：行内大多为描述性标记

```
  <span>...</span>
  <a>...</a>  链接
  <br>  换行
  <b>...</b>  加粗
  <strong>...</strong>  加粗
  <img >  图片
  <sup>...</sup>  上标
  <sub>...</sub>  下标
  <i>...</i>  斜体
  <em>...</em>  斜体
  <del>...</del>  删除线
  <u>...</u>  下划线
  <input>...</input>  文本框
  <textarea>...</textarea>  多行文本
  <select>...</select>  下拉列表
```

互相转换
- display:inline;转换为行内元素
- display:block;转换为块状元素
- display:inline-block;转换为行内块状元素

#### 对浏览器内核的理解？
主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
- 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
- JS引擎则：解析和执行javascript来实现网页的动态效果。
  最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

#### 常见的浏览器内核有哪些？
- Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
- Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
- Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]
- Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]

#### cookies，sessionStorage 和 localStorage 的区别？
- cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
- cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
- sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

  存储大小：
  	cookie数据大小不能超过4k。
  	sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

  有期时间：
  	localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
  	sessionStorage  数据在当前浏览器窗口关闭后自动删除。
  	cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
















