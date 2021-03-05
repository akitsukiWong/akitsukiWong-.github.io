title: webpack4+babel7构建React应用
author: 汪秋月
date: 2020-03-12 16:54:33
tags:
---
# 初始化项目
创建一个新项目文件夹，进入并执行以下命令创建 `package.json` 文件
```
npm init
```

如果不想init时一步步配置项目，可以使用以下命令，所有配置项默认选择y
```
npm init -y
```

# 安装 webpack
```
npm i webpack webpack-cli webpack-dev-server -D
```

## 创建 webpack.config.js

```
module.exports = {
    entry: '',               // 入口文件
    output: {},              // 出口文件
    module: {},              // 处理对应模块
    plugins: [],             // 对应的插件
    devServer: {},           // 开发服务器配置
    mode: 'development'      // 模式配置
}
```

## 修改 webpack.config.js

```
const path = require('path');

module.exports = {
    entry: './src/index.js',    // 入口文件
    output: {
        filename: 'bundle.js',      // 打包后的文件名称
        path: path.resolve('dist')  // 打包后的目录，必须是绝对路径
    }
}
```

## 修改 package.json

```
{
	...
	"scripts": {
    	"start": "webpack-dev-server --mode development",
    	"build": "webpack --mode production"
  	}
    ...
}
```
npm run build 尝试打包

npm start 启动尝试


# 安装Babel

```
npm i @babel/core babel-loader @babel/preset-env @babel/preset-react -D
```
- babel-loader：使用 Babel 转换 JavaScript依赖关系的 Webpack 加载器
- @babel/core：即 babel-core，将 ES6 代码转换为 ES5
- @babel/preset-env：即 babel-preset-env，根据您要支持的浏览器，决定使用哪些 transformations / plugins 和 polyfills，例如为旧浏览器提供现代浏览器的新特性
- @babel/preset-react：即 babel-preset-react，针对所有 React 插件的 Babel 预设，例如将 JSX 转换为函数


## 创建.babelrc文件
```
{
    "presets": [
        "@babel/preset-env",
        "@babel/preset-react"
    ]
}
```

## webpack.config.js 中配置 loader

```
module.exports = {
	...
  	module: {
    	rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader"
                }
            }
        ]
 	}
  	...
};
```
# 安装 html-webpack-plugin 

```
npm i html-webpack-plugin -D
```

## webpack.config.js 中配置 html-webpack-plugin

```
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
	...
  	plugins: [                 
        new HtmlWebpackPlugin({
            // 用哪个html作为模板
            // 在src目录下创建一个index.html页面当做模板来用
            template: './src/index.html',
            filename: './index.html',
            hash: true,         // 会在打包好的bundle.js后面加上hash串
        }),

    ]
  	...
};
```


# 在 src 目录下创建 index.html 和 index.js

index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="root"></div>
</body>
</html>
```

index.js
```
import React from 'react';
import ReactDOM from 'react-dom';

const Index = () => {
  return <div>Hello React!</div>;
};

ReactDOM.render(<Index />, document.getElementById('root'));

```
npm run build 尝试打包

npm start 启动尝试


# 其它


## 打包前清除文件夹
```
npm i clean-webpack-plugin -D
```

### webpack.config.js 配置 clean-webpack-plugin


```
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
	...
  	plugins: [                 
        // 打包前清除dist文件夹
        new CleanWebpackPlugin()
    ]
  	...
};
```

** 注意引入 `CleanWebpackPlugin` 时要加花括号，一开始没加报错了 **
    