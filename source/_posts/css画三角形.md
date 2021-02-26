title: css画三角形
tags:
  - css
categories:
  - 代码片段
date: 2017-05-12 14:13:00
---

面试时候遇到的问题，只要设置两个边框透明就行了,学会了这个，妈妈再也不怕我面试的时候被要求画三角形了

<div style="width: 0;
height: 0;
border-left: 50px solid transparent;
border-right: 50px solid transparent;
border-bottom: 100px solid red;"></div>


**上三角**

```
#triangle-up {
width: 0;
height: 0;
border-left: 50px solid transparent;
border-right: 50px solid transparent;
border-bottom: 100px solid red;
} 
```
<div style="width: 0;
height: 0;
border-left: 50px solid transparent;
border-right: 50px solid transparent;
border-top: 100px solid red;"></div>

**下三角**

```
#triangle-down {
width: 0;
height: 0;
border-left: 50px solid transparent;
border-right: 50px solid transparent;
border-top: 100px solid red;
}
```

<div style="width: 0;
height: 0;
border-top: 50px solid transparent;
border-right: 100px solid red;
border-bottom: 50px solid transparent;"></div>

**左三角**

```
#triangle-left {
width: 0;
height: 0;
border-top: 50px solid transparent;
border-right: 100px solid red;
border-bottom: 50px solid transparent;
}
```

<div style="width: 0;
height: 0;
border-top: 50px solid transparent;
border-left: 100px solid red;
border-bottom: 50px solid transparent;"></div>

**右三角**

```
#triangle-right {
width: 0;
height: 0;
border-top: 50px solid transparent;
border-left: 100px solid red;
border-bottom: 50px solid transparent;
}
```


