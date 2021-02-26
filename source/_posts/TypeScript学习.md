title: TypeScript学习
author: 汪秋月
tags:
  - TS
categories:
  - 学习
date: 2019-06-27 13:46:00
---


# TypeScript 基础知识

## 什么是 TypeScript

> JavaScript的超集，又叫类型化的JavaScript，最终编译成JavaScript。微软出品。

官网：<https://www.tslang.cn>

## 特点

* 始于JavaScript，归于JavaScript
  * 可以编译出纯净、 简洁的JavaScript代码，并且可以运行在任何浏览器上、Node.js环境中和任何支持ECMAScript 3（或更高版本）的JavaScript引擎中。
* 强大的工具构建 大型应用程序
  * 类型允许JavaScript开发者在开发JavaScript应用程序时使用高效的开发工具和常用操作比如静态检查和代码重构。
  * 类型是可选的，类型推断让一些类型的注释使你的代码的静态验证有很大的不同。类型让你定义软件组件之间的接口和洞察现有JavaScript库的行为。
* 先进的 JavaScript
  * 提供最新的和不断发展的JavaScript特性，包括那些来自2015年的ECMAScript和未来的提案中的特性，比如异步功能和Decorators，以帮助建立健壮的组件。

## 意义

JavaScript是弱类型的语言，是它的优点同时也是弱点。优点是比较随意，写的代码可能会少点；弱点是代码出错检查起来比较困难，当一个变量可能被赋予多个类型的值的时候，对每个类型进行处理需要相对应的判断处理。

* 在写代码的时候，对于未定义值得变量，编译器无法推断出具体的类型，在调用相应的函数或者属性的时候，无法借助于编辑器的智能提示，如下代码编辑器就无法提示

```
var a;

function f(a, b) { }

```

* 当去调用一个对象的属性或者方法的时候，编译器无法知道它是否存在，只有等到运行的时候才能确定，如下所示

```
var a = { }

function f() {
  // 编译器无法知道say是否存在，万一你在其他的某个地方给加上了呢？
  a.say()
}
```

当然，上面只是列举了部分，都是无类型化引起的，为了解决这些痛点，TypeScript应运而生，给变量加上类型标识，限制了灵活性，但是极大的改善了更多的不确定性。

> 时刻要注意的是，类型一旦确定，就只能接受指定类型的值，赋予其他类型的值，就会出错。当然编辑器会提醒你的~

下面简单的看看TypeScript，更多的东西当然是借助于官方文档。

## TypeScript示例

类型标识的基本格式

```
变量名:类型

```

只要在原来的JavaScript变量定义或声明的地方标识一下类型就可以转换成TypeScript代码了，当然这样粗略的转换后的代码一般是有问题的，可能需要额外的修补才能完美转换

当变量有初值的时候，若类型和初值类型一致，可以省略类型标识

### 首先介绍一下类型

#### 基本类型

也就是基本的JavaScript类型

* number
* string
* boolean
* null
* undefined
* 更多的内置类型，如Object, Number, String, RegExp等
* any 随意类型，相当于是没有类型


#### 枚举

只能为固定的值

```
enum Color {
  Red,
  Green, 
  Blue
}
let c: Color = Color.Green;

```

#### 类型数组

基本格式类型[]，这样可以标识出这个数组里面装的是指定类型的数据

还可以通过Array<类型>来标识

另外每个位置指定类型也行[类型1, 类型2]

#### 接口

```
interface Interface1 {
  a: number
  b: string
}

```

只需要把属性或者方法列出来就好了

接口可以继承已有接口，相同的属性声明可以放在父接口里面

```
interface Interface2 extends Interface1 {
  c: boolean
}

```

#### 类

```
class Class1 {
  a: number = 1
  b: string = 'hello'
}

```

类似于接口，不过声明的属性得有相应的初值才行，值得注意的是

* 当指定属性可能为undefined的时候，在变量后面添加?
* 当指定属性是通过其他方式赋予的初值，在变量后面添加!
* 可以在构造函数中声明带访问修饰符的属性，这样可以省略显示的属性声明，如下，与上面代码等价


```
class Class1 {
  a: number = 1
  constructor(public b: string = 'hello') { }
}

```

#### 联合类型

`类型1 | 类型2`
使用`|`联合多种类型，表示可能变量可能的类型

#### 函数

比较通用的是使用Function来标识函数类型，当需要指定具体的参数和返回类型的时候，可以使用箭头函数，前面为参数声明，后面为返回类型，如

```
var f: (a: number, b: string) => string

```

上面指定了f为一个函数，接收一个数字类型a和一个字符串类型b，返回一个string类型

> 要注意区分函数的定义与实现，定义只要定义好输入值以及返回值行了

#### 类型别名

`type 类型别名 = 类型`
给类型起一个别名，如type `Phone = string`，就可以给电话号码字符串起一个好听点的名字

#### 字面量类型

直接把类型换成

```
{
  a: number
  b: string
}

```
就如定义接口一样的写法

#### 根据对象推断类型

可以根据一个对象推断类型，如下

```
var obj = {
  a: 1,
  b: 'hello'
}
type T = typeof obj

```

以上T就为obj相对应的类型，类似于以下这种形式

```
{
  a: number
  b: string
}

```

#### 泛型

通俗的讲就是比较广泛的类型，通常出现在接口，类，以及函数中，当数据类型是不确定的，或者说是根据调用来确定的。

TypeScript官网的描述

> 软件工程中，我们不仅要创建一致的定义良好的API，同时也要考虑可重用性。 组件不仅能够支持当前的数据类型，同时也能支持未来的数据类型，这在创建大型系统时为你提供了十分灵活的功能。

可能对于没有接触过强类型语言的人来说，开始会有点懵逼。可以把泛型理解成一个类型占位符，当调用的时候根据需要指定你想要的类型。这样可以达到为了完成某些除类型不一样但实现的功能类似的代码。站在更高角度的抽象，增加了灵活性。

下面我用几个简单的例子加以说明，力图能表达清楚。

就拿官网的例子，一个identity函数，返回传给它的值

若不用泛型实现，那么假如我可能传两种类型(只是可能，不意味着哪天高兴了需要更多的类型)，number和string

```
function identity(arg: number): number {
  return arg;
}

function identity2(arg: string): string {
  return arg;
}

```

从上面看，当需要更多的时候，是不是需要一个一个的定义，挺麻烦的，而且功能还差不多

当然你可以用下面的代码

```
function identity(arg: any): any {
  return arg
}

```

虽然能实现相应的功能，但是不要忘了，我们需要类型，有了类型才能借助于编译器帮我们检查以及利用编辑器的智能提示

下面看看利用泛型如何实现

```
function identity<T>(arg: T): T {
  return arg
}

```

上面跟再上的代码差不多，但是功能更加强大，可以接受任意类型，并且返回指定类型，下面让我们看看如何用

* 数字 identity<number>(123)，编译器就可以知道返回值为数字了
* 字符串 identity<string>('hello')
* 布尔值 identity<boolean>(true)
* 更多其他类型…
以上对于编译器来说返回值是什么就一目了然了

> 注意T是可以换成别的任何一个标识符的，只是一个占位符而已

另外看看接口中如何定义和使用(类中类似)

```
interface Interface1<T> {
  aa: T
  bb: number
}
var t: Interface1<string> = {
  aa: 'hello',
  bb: 123
}

```

当需要什么类型的时候，指定好就行了

```
当有多个类型不确定的时候，在<>里面指定任意数量的类型，使用,进行分隔

function identity<T1, T2>(t1: T1, t2: T2): string {
 return 'xxxxxxxxxxxxxxx'
}
调用的时候，按照定义顺序传递相应的类型
identity<number, string>(1, 'hello')

```

#### 总结

上面简要的介绍了下TypeScript的基础知识，需要更全面的了解，还是应该去官网。

平时的开发过程中，注意给变量标识好类型，尽量少用any，由于TypeScript是JavaScript的超集，所以’js’代码也是可以编译通过的，但会给你一系列的报错和警告。




# vue2.5 + TypeScript 构建项目

- 安装vue-cli
- 安装ts依赖
- 配置 webpack
- 添加 tsconfig.json
- 添加 tslint.json
- 让 ts 识别 .vue
- 改造 .vue文件

## vue-cli拉取1.5模板

```
npm install -g @vue/cli-init
# `vue init` 的运行效果将会跟 `vue-cli@2.x` 相同
vue init webpack my-project
```

## 引入 TypeScript

安装必要插件

```
安装vue的官方插件
npm i vue-class-component vue-property-decorator --save

// ts-loader typescript 必须安装，其他的相信你以后也会装上的
npm i ts-loader typescript tslint tslint-loader tslint-config-standard --save-dev
```

插件作用：

- vue-class-component：强化 Vue 组件，使用 TypeScript/装饰器 增强 Vue 组件
- vue-property-decorator：在 vue-class-component 上增强更多的结合 Vue 特性的装饰器
- ts-loader：TypeScript 为 Webpack 提供了 ts-loader，其实就是为了让webpack识别 .ts .tsx文件
- tslint-loader跟tslint：我想你也会在.ts .tsx文件 约束代码格式（作用等同于eslint）
- tslint-config-standard：tslint 配置 standard风格的约束

## 1.3 配置 webpack

首先找到`./build/webpack.base.conf.js`

- 找到`entry.app` 将`main.js` 改成 `main.ts`, 顺便把项目文件中的`main.js`也改成`main.ts`, 里面内容保持不变

`
entry: {
  app: './src/main.ts'
}
`

- 找到`resolve.extensions` 里面加上`.ts` 后缀 （是为了之后引入`.ts`的时候不写后缀）

```
 resolve: {
    extensions: ['.js', '.vue', '.json', '.ts'],
    alias: {
      '@': resolve('src')
    }
  }
```

- 找到`module.rules` 添加`webpack`对`.ts`的解析


```
module: {
  rules: [
    {
      test: /\.(js|vue)$/,
      loader: 'eslint-loader',
      enforce: 'pre',
      include: [resolve('src'), resolve('test')],
      options: {
        formatter: require('eslint-friendly-formatter')
      }
    },
// 从这里复制下面的代码就可以了
    {
      test: /\.ts$/,
      exclude: /node_modules/,
      enforce: 'pre',
      loader: 'tslint-loader'
    },
    {
      test: /\.tsx?$/,
      loader: 'ts-loader',
      exclude: /node_modules/,
      options: {
        appendTsSuffixTo: [/\.vue$/],
      }
    },
// 复制以上的
  }
}
```

解释：

- `ts-loader` 会检索当前目录下的 `tsconfig.json` 文件，根据里面定义的规则来解析`.ts`文件（就跟`.babelrc`的作用一样）

- `tslint-loader` 作用等同于 `eslint-loader`

## 添加 tsconfig.json

根路径下创建`tsconfig.json`文件

参考配置：

```
{
  // 编译选项
  "compilerOptions": {
    // 输出目录
    "outDir": "./output",
    // 是否包含可以用于 debug 的 sourceMap
    "sourceMap": true,
    // 以严格模式解析
    "strict": true,
    // 采用的模块系统
    "module": "esnext",
    // 如何处理模块
    "moduleResolution": "node",
    // 编译输出目标 ES 版本
    "target": "es5",
    // 允许从没有设置默认导出的模块中默认导入
    "allowSyntheticDefaultImports": true,
    // 将每个文件作为单独的模块
    "isolatedModules": false,
    // 启用装饰器
    "experimentalDecorators": true,
    // 启用设计类型元数据（用于反射）
    "emitDecoratorMetadata": true,
    // 在表达式和声明上有隐含的any类型时报错
    "noImplicitAny": false,
    // 不是函数的所有返回路径都有返回值时报错。
    "noImplicitReturns": true,
    // 从 tslib 导入外部帮助库: 比如__extends，__rest等
    "importHelpers": true,
    // 编译过程中打印文件名
    "listFiles": true,
    // 移除注释
    "removeComments": true,
    "suppressImplicitAnyIndexErrors": true,
    // 允许编译javascript文件
    "allowJs": true,
    // 解析非相对模块名的基准目录
    "baseUrl": "./",
    // 指定特殊模块的路径
    "paths": {
      "jquery": [
        "node_modules/jquery/dist/jquery"
      ]
    },
    // 编译过程中需要引入的库文件的列表
    "lib": [
      "dom",
      "es2015",
      "es2015.promise"
    ]
  }
}
```

我的配置：

```
{
  "include": [
    "src/**/*"
  ],
  "exclude": [
    "node_modules"
  ],
  "compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "experimentalDecorators": true,
    "allowJs": true,
    "module": "esnext",
    "target": "es5",
    "moduleResolution": "node",
    "isolatedModules": true,
    "lib": [
      "dom",
      "es5",
      "es2015.promise"
    ],
    "sourceMap": true,
    "pretty": true
  }
}

```

## 1.5 添加 tslint.json

根路径下创建`tslint.json`文件,引入 `ts `的 `tandard `规范

```
{
  "extends": "tslint-config-standard",
  "globals": {
    "require": true
  }
}
```


## 让 ts 识别 .vue

由于 `TypeScript` 默认并不支持 `*.vue `后缀的文件，所以在 `vue` 项目中引入的时候需要创建一个` vue-shim.d.ts `文件，放在项目项目对应使用目录下，例如` src/vue-shim.d.ts`

```
declare module "*.vue" {
  import Vue from "vue";
  export default Vue;
}
```

意思是告诉` TypeScript` `*.vue `后缀的文件可以交给` vue `模块来处理。

而在代码中导入 `*.vue `文件的时候，需要写上 `.vue` 后缀。原因还是因为`TypeScript` 默认只识别 `*.ts `文件，不识别` *.vue` 文件：


```
import Component from 'components/component.vue'
```


## 改造 `.vue` 文件

修改`App.vue`文件

1. 在`script `标签上加上 `lang="ts"`, 意思是让`webpack`将这段代码识别为`typescript `而非`javascript`
2. 修改`vue`组件的构造方式( 跟`react`组件写法有点类似, 详见官方 )， 如下图
3. 用`vue-property-decorator`语法改造之前代码

修改成：

```
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'

@Component({})
export default class App extends Vue {
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
```

相同的方式修改HelloWorld.vue

## 最后

npm run dev

