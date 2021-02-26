title: webpack之proxyTable设置跨域
author: 汪秋月
date: 2018-09-29 08:44:03
tags:
---
###webpack之proxyTable设置跨域

使用vue-cli搭建的vue项目可以使用在项目内设置代理（proxyTable）的方式来解决跨域问题。

```
proxyTable: {
      '/api': {
        target: 'http://www.ykt.com/',//接口域名
        changeOrigin: true,//是否跨域
        pathRewrite: {
          '^/api': '/index/index'//需要rewrite重写
        }
      }
    }

```

实现效果：

```
localhost:8080/api/getbuildcate   ===>  www.ykt.com/index/index/getbuildcate
```