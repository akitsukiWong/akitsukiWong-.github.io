title: mac 生成树形目录图
author: 汪秋月
date: 2019-09-19 14:07:26
tags:
---
方法一：mac本身可以使用如下命令来生成树形图：
```
find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
```

方法二：使用tree工具：
```
brew install tree
```

```
tree                         #打印所有目录层级
tree -L 2                    #遍历2层
tree > README.md             #输出结果到 Markdown 文档
```
