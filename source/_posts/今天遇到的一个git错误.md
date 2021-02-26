title: 遇到了一个git错误，记录一下
author: 汪秋月
date: 2020-03-20 14:15:11
tags:
---
今天在工作中遇到了这个错误，在git中无论做什么操作都会报

`
Another git process seems to be running in this repository, e.g.
an editor opened by 'git commit'. Please make sure all processes
are terminated then try again. If it still fails, a git process
may have crashed in this repository earlier:
remove the file manually to continue.`


百度一下，大概意思是git崩溃了

解决方法：

删除项目根目录.git文件夹里的 index.lock文件

完美解决