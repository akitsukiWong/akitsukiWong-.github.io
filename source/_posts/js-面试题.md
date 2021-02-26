title: 前端面试题（js）
author: 汪秋月
date: 2019-04-01 10:35:14
tags:
---


#### js的基本数据类型

  Undefined、 Null、 Boolean、 Number、 String、 
  ECMAScript 2015 新增:Symbol(创建后独一无二且不可变的数据类型 )

#### js有哪些内置对象

 Object 是 JavaScript 中所有对象的父对象

 数据封装类对象： Object、 Array、 Boolean、 Number 和 String
 其他对象： Function、 Arguments、 Math、 Date、 RegExp、 Error

#### 原型与原型链

**__proto__是每个对象都有的一个属性， 而prototype是函数才会有的属性!!!**

```
Object.__proto__ === Function.prototype;
Function.prototype.__proto__ === Object.prototype;
Object.prototype.__proto__ === null;
```

- 题目 1

```
var A = function() {};
A.prototype.n = 1;
var b = new A();
A.prototype = {
    n: 2,
    m: 3
}
var c = new A();

console.log(b.n);
console.log(b.m);

console.log(c.n);
console.log(c.m);
```

请写出上面编程的输出结果是什么？ 

- 题目 2

```
var F = function() {};

Object.prototype.a = function() {
    console.log('a');
};

Function.prototype.b = function() {
    console.log('b');
}

var f = new F();

f.a();
f.b();

F.a();
F.b();
```

请写出上面编程的输出结果是什么？ 

- 题目 3

```
function Person(name) {
    this.name = name
}
let p = new Person('Tom');
```

问题1： 1. p.__proto__等于什么？ 
问题2： Person.__proto__等于什么？ 

- 题目 4

```
var foo = {},
    F = function() {};
Object.prototype.a = 'value a';
Function.prototype.b = 'value b';

console.log(foo.a);
console.log(foo.b);

console.log(F.a);
console.log(F.b);
```

请写出上面编程的输出结果是什么？ 

> - 题目 1 答案： 
> b.n -> 1
> b.m -> undefined; 
> c.n -> 2; 
> c.m -> 3; 
> - 题目 2 答案： 
> f.a() -> a
> f.b() -> f.b is not a function
> F.a() -> a
> F.b() -> b
> - 题目 3 答案
> 答案1： Person.prototype
> 答案2： Function.prototype
> - 题目 4 答案
> foo.a => value a
> foo.b => undefined
> F.a => value a
> F.b => value b

### 什么是深拷贝？ 什么是浅拷贝？ 

简单来说， 有两个对象 A 和 B， B = A， 当你修改 A 时， B 的值也跟着发生了变化， 这时候就叫浅拷贝。 如果不发生变化， 就叫深拷贝。 

### new的实现原理是什么？

- 创建一个空对象，构造函数中的this指向这个空对象
- 这个新对象被执行 [[原型]] 连接
- 执行构造函数方法，属性和方法被添加到this引用的对象中
- 如果构造函数中没有返回其它对象，那么返回this，即创建的这个的新对象，否则，返回构造函数中返回的对象。




