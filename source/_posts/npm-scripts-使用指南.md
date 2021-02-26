title: npm scripts 使用
author: 汪秋月
tags: []
categories:
  - 学习
date: 2019-08-08 15:25:00
---
npm 脚本的原理非常简单。每当执行npm run，就会自动新建一个 Shell，在这个 Shell 里面执行指定的脚本命令。因此，只要是 Shell（一般是 Bash）可以运行的命令，就可以写在 npm 脚本里面。

由于 npm 脚本的唯一要求就是可以在 Shell 执行，因此它不一定是 Node 脚本，任何可执行文件都可以写在里面。

npm 脚本的退出码，也遵守 Shell 脚本规则。如果退出码不是0，npm 就认为这个脚本执行失败。

## 通配符

由于 npm 脚本就是 Shell 脚本，因为可以使用 Shell 通配符。

```
"lint": "jshint *.js"
"lint": "jshint **/*.js"
```

上面代码中，*表示任意文件名，**表示任意一层子目录。

如果要将通配符传入原始命令，防止被 Shell 转义，要将星号转义。

```
"test": "tap test/\*.js"
```

## 传参

向 npm 脚本传入参数，要使用--标明。

```
"lint": "jshint **.js"
```

向上面的`npm run lint`命令传入参数，必须写成下面这样。

```
$ npm run lint --  --reporter checkstyle > checkstyle.xml
```

也可以在`package.json`里面再封装一个命令。

```
"lint": "jshint **.js",
"lint:checkstyle": "npm run lint -- --reporter checkstyle > checkstyle.xml"
```

## 执行顺序
如果 `npm` 脚本里面需要执行多个任务，那么需要明确它们的执行顺序。

如果是并行执行（即同时的平行执行），可以使用`&`符号。

```
$ npm run script1.js & npm run script2.js
```
如果是继发执行（即只有前一个任务成功，才执行下一个任务），可以使用`&&`符号。

```
$ npm run script1.js && npm run script2.js
```
这两个符号是 `Bash` 的功能。此外，还可以使用 `node` 的任务管理模块：
[script-runner](https://github.com/paulpflug/script-runner)、[npm-run-all](https://github.com/mysticatea/npm-run-all)、[redrun](http://www.ruanyifeng.com/blog/2016/10/npm_scripts.html)



















