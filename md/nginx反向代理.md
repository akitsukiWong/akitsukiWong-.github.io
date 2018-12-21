title: nginx反向代理
author: 汪秋月
date: 2018-09-29 08:45:22
tags:
---
###nginx反向代理

1.下载nginx

http://nginx.org/en/download.html         下载稳定版本，以nginx/Windows-1.12.2为例，直接下载 nginx-1.12.2.zip

2.启动nginx

有很多种方法启动nginx

(1)直接双击nginx.exe，双击后一个黑色的弹窗一闪而过

(2)打开cmd命令窗口，切换到nginx解压目录下，输入命令 nginx.exe 或者 start nginx ，回车即可

3.检查nginx是否启动成功

直接在浏览器地址栏输入网址 http://localhost:80，回车，出现以下页面说明启动成功


#### 反向代理

1.定义

跨域是指a页面想获取b页面资源，如果a、b页面的协议、域名、端口、子域名不同，所进行的访问行动都是跨域的，而浏览器为了安全问题一般都限制了跨域访问，也就是不允许跨域请求资源。注意：跨域限制访问，其实是浏览器的限制。理解这一点很重要！！！

2.跨域访问示例

假设有两个网站，A网站部署在：http://localhost:81 即本地ip端口81上；B网站部署在：http://localhost:82 即本地ip端口82上。

关于nginx的配置可以查看另一篇博文：http://www.cnblogs.com/renjing/p/6126284.html。找到nginx的配置文件“nginx.conf”，修改一下信息

```
server {
        listen       80; #监听80端口，可以改成其他端口
        server_name  localhost; # 当前服务的域名

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            proxy_pass http://localhost:81;
            proxy_redirect default;
        }

		location /apis { #添加访问目录为/apis的代理配置
			rewrite  ^/apis/(.*)$ /$1 break;
			proxy_pass   http://localhost:82;
       }
#以下配置省略

```

配置解释：

1.由配置信息可知，我们让nginx监听localhost的80端口，网站A与网站B的访问都是经过localhost的80端口进行访问。

2.我们特殊配置了一个“/apis”目录的访问，并且对url执行了重写，最后使以“/apis”开头的地址都转到“http://localhost:82”进行处理。

3.rewrite  ^/apis/(.*)$ /$1 break; 

代表重写拦截进来的请求，并且只能对域名后边以“/apis”开头的起作用，例如www.a.com/apis/msg?x=1重写。只对/apis重写。

　　rewrite后面的参数是一个简单的正则 ^/apis/(.*)$ ,$1代表正则中的第一个(),$2代表第二个()的值,以此类推。

　　break代表匹配一个之后停止匹配。

访问地址修改


既然配置了nginx，那么所有的访问都要走nginx，而不是走网站原本的地址（A网站localhost:81,B网站localhost:82）。所以要修改A网站中的ajax访问地址，把访问地址由

“http://localhost:82/api/values”改成》》》“/apis/api/values”。
