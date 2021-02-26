title: 重新学习Java​Script
author: 汪秋月
tags: []
categories: []
date: 2018-05-28 09:52:00
---
# 概览

JavaScript 是一种面向对象的动态语言

## 类型

- `NUmber` （数字）
- `String`	（字符串）
- `Boolean`	（布尔）
- `Function`（函数）
- `Object`（对象）
- `Symbol`（ES2015新增）

`undefined` (未定义) `null`(空) `Array`（数组）`Date`(日期) `RegExp` （正则表达式）

都是特殊的对象

所以准确来说，JavaScript 中的类型应该包括这些：

- `Number`（数字）
- `String`（字符串）
- `Boolean`（布尔）
- `Symbol`（符号）（ES2015 新增）
- `Object`（对象）
 - `Function`（函数）
 - `Array`（数组）
 - `Date`（日期）
 - `RegExp`（正则表达式）
- `null`（空）
- `undefined`（未定义）

# 数字

根据语言规范，JavaScript 采用“遵循 IEEE 754 标准的双精度 64 位格式”

JavaScript 不区分整数值和浮点数值，所有数字在 JavaScript 中均用浮点数值表示，所以在进行数字运算的时候要特别注意，例：

```
0.1 + 0.2 = 0.30000000000000004
```

** 内置对象 `Math` **

```
Math.sin(3.5);
var d = Math.PI * (r + r)
```

**内置函数 `parseInt()` **

将字符串转换为整型，第二个参数表示字符串所表示数字的基（进制）

```
parseInt("123", 10); // 123
parseInt("010", 10); //10
```

如果调用时没有提供第二个参数（字符串所表示数字的基），2013 年以前的 JavaScript 实现会返回一个意外的结果：

```
parseInt("010");  //  8
parseInt("0x10"); // 16
```

这是因为字符串以数字 0 开头，parseInt()函数会把这样的字符串视作八进制数字；同理，0x开头的字符串则视为十六进制数字。

如果想把一个二进制数字字符串转换成整数值，只要把第二个参数设置为 2 就可以了：

```
parseInt("11", 2); // 3
```

**内置函数 `parseFloat()` **

解析浮点数字符串,只应用于解析十进制数字


单元运算符 + 也可以把数字字符串转换成数值


```
+ "42";   // 42
+ "010";  // 10
+ "0x10"; // 16
```

如果给定的字符串不存在数值形式，函数会返回一个特殊的值 NaN（Not a Number 的缩写）：

```
parseInt("hello", 10); // NaN
```

如果把 NaN 作为参数进行任何数学运算，结果也会是 NaN

```
NaN + 5; //NaN
```
可以使用内置函数 `isNaN()` 来判断一个变量是否为 NaN：

```
isNaN(NaN); // true
```
JavaScript 还有两个特殊值：`Infinity`（正无穷）和 `-Infinity`（负无穷）：

```
1 / 0; //  Infinity
-1 / 0; // -Infinity
```
可以使用内置函数 `isFinite()` 来判断一个变量是否是一个有穷数， 如果类型为`Infinity`, `-Infinity` 或 `NaN`则返回`false`：

```
isFinite(1/0); // false
isFinite(Infinity); // false
isFinite(-Infinity); // false
isFinite(NaN); // false

isFinite(0); // true
isFinite(2e64); // true

isFinite("0"); // true
// 如果是纯数值类型的检测，则返回 false：
Number.isFinite("0"); // false
```

# 字符串

JavaScript 中的字符串是一串Unicode 字符序列。这对于那些需要和多语种网页打交道的开发者来说是个好消息。更准确地说，它们是一串UTF-16编码单元的序列，每一个编码单元由一个 16 位二进制数表示。每一个Unicode字符由一个或两个编码单元来表示。

如果想表示一个单独的字符，只需使用长度为 1 的字符串。

通过访问字符串的 length（编码单元的个数）属性，可以得到它的长度。

```
"hello".length; // 5
```

这是我们第一次碰到 JavaScript 对象。我们有没有提过你可以像  object  一样使用字符串？是的，字符串也有 methods（方法）能让你操作字符串和获取字符串的信息。

```
"hello".charAt(0); // "h"
"hello, world".replace("world", "mars"); // "hello, mars"
"hello".toUpperCase(); // "HELLO"
```

# 其他类型

与其他类型不同，JavaScript 中的 null 表示一个空值（non-value），必须使用 null 关键字才能访问，undefined 是一个“undefined（未定义）”类型的对象，表示一个未初始化的值，也就是还没有被分配的值。我们之后再具体讨论变量，但有一点可以先简单说明一下，JavaScript 允许声明变量但不对其赋值，一个未被赋值的变量就是 undefined 类型。还有一点需要说明的是，undefined 实际上是一个不允许修改的常量。

JavaScript 包含布尔类型，这个类型的变量有两个可能的值，分别是 true 和 false（两者都是关键字）。根据具体需要，JavaScript 按照如下规则将变量转换成布尔类型：

1. false、0、空字符串（""）、NaN、null 和 undefined 被转换为 false
2. 所有其他值被转换为 true

也可以使用 Boolean() 函数进行显式转换：

```
Boolean(""); // false
Boolean(234); // true
```