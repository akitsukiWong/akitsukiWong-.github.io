---
title: javascript高级程序设计学习笔记
date: 2017-12-01 01:45:22
tags: js
categories: 前端学习
---


# 第一章 HTML中使用JavaScript

## script元素

**script中有六个属性**

- `async`
- `charset `
- `defer`
- `language`
- `src`
- `type`

### 标签的位置

传统做法放在`<head>`中，js会被先加载页面会有延迟

所以把JavaScript引入放在`<body>`元素中页面元素的后面

这样先加载页面内容，用户会因为空白页面时间缩短而感到页面打开速度加快







### 延迟脚本

HTML 4.01为`<script>`标签定义了`defer`属性。

相当于告诉浏览器立即下载延迟执行。

```
<script type="text/javascript" defer="defer" src="example.js"></script>
```
### 异步脚本
`async`

```
<script type='text/javascript' async src='example.js'></script>
```
### 在XHTML中的用法

XTML（可拓展超文本标记语言），是将HTML作为XML的应用而重新定于的一个标准
规则比HTML严格






# 第二章  基本概念
## 语法

ECMAScript大量借鉴C及其他类C语言（Java等）

### 区分大小写

ECMAScript中一切（变量、函数名和操作符）都区分大小写。

### 标识符

标识符，指变量、函数、属性都名字，或者函数的参数。

- 第一个字符必须是字母、下划线（_）或者一个美元符号（$）；
- 其他字符可以是字母、下划线、美元符号或数字。





### 注释

C风格注释

```
// 单行注释

/*
* 这是一个多行
*（块级）注释
*/
```

### 严格模式

ECMAScript 5 引入严格模式

启用严格模式可在顶部添加`use strict`;

```
function(){
    "use strict";
    //函数体
}
```

### 语句

分号结尾；代码块{ } 里面

## 关键字和保留字

## 变量

ECMAScript的变量是松散类型的，可以保存任何类型的数据。

定义变量使用 `var` 操作符

函数中`var`的是局部变量，省略`var`是全局变量

定义多个变量（用逗号隔开）

```
  var message = "hi" ,
        found = false ,
        age = 29 ;
```





## 数据类型

ES中有五种简单的数据类型

1- `Undefined`   ----- 未定义

2- `Null`  ------------- 

3- `Boolean`  -------- 布尔值

4- `Number` --------- 数值

5- `String` ------------ 

还有一种复杂数据类型 `Object`







### typeof 操作符

```
var message = "some string" ;
alert(typeof message) ;         //"string"
```

**typeof** 返回值

- undefined  ------ 为定义
- boolean --------- 布尔值
- string ------------ 字符串
- number ---------- 数值
- object ------------ 对象 或者 null
- function ---------- 函数


### undefined 类型

`var` 声明变量但为对其加以初始化的值就是undefined

### Null类型

### Boolean 类型

true和false

### Number类型

 整数和浮点数（带小数点的数值，小数点后至少有一位数字）






#### 浮点数值

极大极小的数字用e表示法（科学计数法）

```
var floatNum = 3.125e7        //31250000
var floatNum = 3e-17             //0.00000000000000003
```

浮点数值最高精度为17位小数，其计算精度远远不如整数，例如 0.1 + 0.2 结果不是 0.3 而是 0.300000000000004。



#### 数值范围
- Infinity （负无穷）
- Infinity （正无穷）




#### NaN

非数值 （not a number）

任何涉及NaN的操作都会返回NaN

NaN和任何值都不相等，包括NaN


```
alert（NaN == NaN）        //false
```

isNaN（）函数，查询是否为数值


```
alert(isNaN(NaN));        //true
alert(isNaN(10));            //false(10是一个数值)
alert(isNaN("blue"))        //true
```


#### 数值转换

- number()

-- 如果是布尔值，返回0和1

-- 如果是数字，简单的传入和返回

-- 如果是null，返回0

-- 如果是undefined，返回NaN

-- 如果是字符串.........

-- 如果是对象，调用valueOf( ) 方法，如果转换的对象是NaN，调用toString（）方法

- parseInt()

- parseFloat()

### string 类型

单引号和双引号字符串形式完全相同

#### 字符字面量

string数据类型包含一些特殊的字符字面量，也叫转义序列，用于表示非打印字符

**\n**       换行

**\t**        制表

**\b**        退格

等...

#### 字符串的特点

ES中字符串是不可变的，字符串一旦创建，它们的值就不能改变。要改变某个变量保存的字符串，首先要销毁原来的字符串，然后再用另一个包含新值的字符串填充改变量。

#### 转换为字符串

toString（）

### Object 类型

对象其实就是一组数据和功能的集合。
对象可以通过`new`操作符来创建

```
var o = new Object( ) ;  （括号可以省略，但不推荐）
```

## 操作符

###  一元操作符

只能操作一个值但操作符叫做一元操作符。

#### 递增和递减操作符

++age；等于age = age +1;

--age; 等于age = age - 1；

【前置型】会影响语句的结果，求值之前执行

【后置型】不会影响语句结果，求值之后执行





例子

```
var num1 = 2 ;
var num2 = 20 ;
var num3 = --num + num2 ;        //21
var num4 = num1 + num2 ;        //21
```

```
var num1 = 2 ;
var num2 = 20 ;
var num3 = num-- + num2 ;        //22
var num4 = num1 + num2 ;        //21

```

#### 一元加和减操作符

一元加操作符以一个加号（+）表示，放在数值前面，对数值不会产生任何影响。

```
var num = 25 ;
num = +num ;        //25
```

一元减操作符主要表示负数。

### 位操作符

转化位二进制

```
var num = -18 ;
alert(num.toString(2)) ;             //"-10010"

```



#### 按位非（NOT）

按位非由一个波浪号【～】表示，执行按位非的结果就是返回数值的反码（二进制逐位取反）


#### 按位与（AND）

按位与由一个和字符号【&】表示，都是1返回1，有0就返回0


#### 按位或（OR）

按位或由一个竖线符号【|】表示，有1返回1，都是0才返回0


#### 左移

【<<】，会将数值的所有位向左移动制定的位数。


```
var oldValue = 2 ;                //二进制10
var newValue = oldValue << 5;        //二进制100000，即64
```

#### 右移

【>>】,会将数值向右移动，但保留符号位


```
var oldValue = 64 ;                //二进制1000000
var newValue = oldValue >> 5;        //二进制10，即2

```



#### 无符号右移
【>>>】，会将数值的所有32位都向右移动。

对于正数于【>>】一样，对于负数无符号右移后结果会变得非常大，因为无符号右移会移动所有的二进制码。


```
var oldValue = -64 ;                //二进制1000000
var newValue = oldValue >>> 5;        //十进制134217726

```

### 3.5.3 布尔操作符

布尔操作符一共三个

- 非（NOT）【  ！】
- 与（AND）  【 && 】
- 或（OR） 【 || 】

### 乘性操作符

- 乘法    【 * 】
- 除法    【 / 】
- 求模  （余数）  【 % 】


```
var result = 26 % 5 ;        //等于 1
```

### 加性操作符

- 加法    【 + 】
- 减法    【 - 】

### 关系操作符

- 小于  【 < 】
- 大于 【  > 】
- 小于等于 【 <= 】
- 大于等于 【 >= 】

### 相等操作符

相等和不相等（先转换再比较）

全等和不全等（仅比较不转换）

#### 相等和不相等

- 相等 【 == 】
- 不相等 【 != 】

#### 全等和不全等

- 全等 【 === 】
- 不全等 【 !== 】

### 条件操作符

```
variable = boolean_expression ? true_value : false_value
```

基于对boolean_expression求值对结果，决定给变量variable赋什么值。如果为true，赋true_value值，如果为false，赋false_value值


```
var max = (num1 > num2) ? num1 : num2 ;
```


max将保存最大对值，表达式意思是：如果num1大于num2，给max赋num1值，反之赋值num2













### 赋值操作符


简单赋值操作符由符号【 = 】表示，作用：把右侧对值赋给左侧对变量



### 逗号操作符



可以在一条语句中执行多个操作


```
var num1 = 1, num2 = 2, num3 = 3;   
```

逗号操作符还可以用作赋值，会返回表达式对最后一项。

```
var num = ( 5, 1, 4, 8, 0);        //num的值为0，因为0是表达式的最后一项
```


















## 语句


### if语句


```
if ( condition【条件】 ) {
    statement1【语句1】；
 } else {
    statement【语句2】； 
}
```


```
if( condition1【条件1】 ){
    statement1【语句1】；
} else if ( condition2【条件2】 ){ 
    statemen2【语句2】；
} else {
    statement3【语句3】；
}
```


### do-while 语句


```
do{
    statement【语句】
} while {
    expression【条件】
}
```


### while 语句


```
while( expression【条件】 ){
    statement【语句】
}
```


### for语句



`for`语句也是一种前端测试循环语句，它具有在执行循环之前初始化变量和定义循环后要执行的代码的能力。


```
for(initialization【初始化】; expression【条件】; post-loop-expression【循环表达式】){
    statement【语句】;
}
```

当三个表达式全部省略就会创建一个无限循环

```
for( ; ; ){                    //无限循环
    doSomething();
}
```

### 3.6.5 `for-in`语句

`for-in`语句是一种精准当迭代语句，可以用来枚举对象当属性。

```
for( property【属性】 in expression){ 
statement【语句】
}
```

### 3.6.6 `label`语句

```
label【标签】: statement
```
```
start: for (var i = 0; i < count; i++){
    alert(i);
}
```

### 3.6.7 `break`和`continue`语句
`break`和`continue`用于在循环中精确的控制代码的执行
【break】立即退出循环，强制继续执行循环后面的语句
【continue】立即退出循环，退出循环后会从循环的顶部继续执行
break和continue都可以和label语句联合使用，从而返回代码中特定的位置。



### 3.6.8 `with`语句
```
with(expreession【条件】){
    statement【语句】
}
```
`with`语句主要目的是为了简化多次编写同一个对象的工作
```
var qs = location.search.substring(1);
var hostName = location.hostname;
var url = location.href;
```
以上代码都包含了location对象，用with语句
```
with(location){
    var qs = search.substring(1);
    var hostName = hostname;
    var url = href;
}
```
不建议使用过with语句

### 3.6.9 `switch` 语句
```
switch(expression){
    case value: statement
        break;
    case value: statement
        break;
    case value: statement
        break;
    case value: statement
        break;
    default: statement
}
```

相当于if-else语句简化写法
```
if(i == 25){
    alert("25");
} else if(i == 35){
    alert("35")
} else if(i == 45){
    alert("45")
}else {
    alert("other")
}
```
等价于`switch`语句
```
switch( i ){
    case 25:
        alert("25");
        break;
    case 35:
        alert("35");
        break;
    case 45:
        alert("45");
        break;
    default:
        alert("other");
} 
```



## 3.7 函数
```
function functionName(arg0, arg1, ...,argN){
    statements
}
```

**位于语句之后都任何代码都永远不会执行**

### 3.7.1 理解参数
命名的参数只提供便利，但不是必须的

### 3.7.2 没有重载

# 第三章 变量、作用域和内存问题

## 4.1 基本类型和引用类型的值
【基本类型】简单的数据段
【引用类型】可能有多个值构成的对象

### 4.1.1 动态的属性

### 4.1.2 复制变量值

### 4.1.3 传递参数
当在函数内部重写obj时，这个变量引用的就是一个局部对象，这个局部对象会在函数执行完毕后立即销毁。
```
function setName(obj){
    obj.name = "Nicholas";
    obj = new Object();
    obj.name = "Greg";
}
var person = new Object();
set.Name(person);
alert(person.name);        //"Nicholas"
```

### 4.1.4 检测类型
## `instanceof`操作符
```
result = variable instanceof constructor
```
例子
```
alert(person instanceof Object);        //变量person是Object吗？
alert(colors instanceof Array);        //变量colors是Array吗？
alert(pattern instanceof RegExp);        //变量pattern是RegExp吗？
```

## 4.2 执行环境及作用域

### 延长作用域链

### 4.2.2 没有块级作用域

#### 声明变量
使用`var`声明的变量会自动添加到最接近到环境中
如果初始化变量没有使用`var` 声明，该变量会自动被添加到全局环境。

#### 查询标识符
 
## 4.3 垃圾收集
js具有垃圾自动收集功能

### 4.3.1 标记清除

### 4.3.2 引用计数

### 4.3.3 性能问题

### 4.3.4 管理内存

# 第五章 引用类型

## 5.1 `Object`类型
创建`Object`实例有两种方式
- 使用new操作符后跟Object构造函数
```
var person = new Object();
person.name = "Nicholas";
person.age = "29";
```
Object可以省略，用大括号代替
```
var person = {};
person.name = "Nicholas";
person.age = "29";

```

- 使用对象字面量表示法，是对象定义的一种简写形式，目的在于简化创建包含大量属性的对象的过程。
```
var person = {
    name = "Nicholas" ,
    age = 29
};
```

访问对象属性可以用点表示法，也可以用方括号
```
alert(person.name);         //Nicholas
alert(person["name"]);         //Nicholas
```
方括号语法的主要优点是可以通过变量来访问属性
```
var propertyName = "name";
alert(person[propertyName]);        //Nicholas
```

## 5.2 `array`类型
创建数组有两种方法
```
var colors = new Array();
```
创建length值为20的数组
```
var colors = new Array( 20 );
```
也可以向Array构造函数传递数组中应该包含的项
```
var colors = new Array( "red","blue","green" );
```
可以省略new操作符
```
var colors = Array();
```
可以使用字面量表示法，数组用方括号表示，逗号隔开
```
var colors = ["red","blue","green"]; 
var names = []        //创建一个空数组
```
利用length属性可以方便的在数组末尾添加新项
```
var colors =  ["red","blue","green"]; 
colors[colors.length] = "black";        //在位置3添加一种颜色
colors[colors.length] = "brown"        //在位置4添加一种颜色
```

### 5.2.1 检测数组
```
if(value instanceof Array){
        //do something
}
```
ES5新增的Array.isArray()方法，用于确定某个值到底是不是数组，而不管它是在哪个全局环境下创建的。
```
if(Array.isArray(value)){
        //do something
}
```

### 5.2.2 转换方法

`join`方法可以使用不同的分隔符来构建这个字符串
`join`方法只接受一个参数，用作分隔符的字符串
```
var colors = ["red","blue","green"];
alert(colors.join(","));        //red,blue,green
alert(colors.join("||"));        //red||blue||green
```

### 5.2.3 栈方法
栈是一种【LOFO】后进先出的数据结构
栈中 插入叫做推入，移除叫做弹出

`push()` 接收任意数量的参数逐个添加到数组末尾（从末尾加）
`pop()` 从数组末尾移除最后一项（删最后一个）

### 5.2.4 队列方法
队列是【FIFO】先进先出

`shift()` 移除数组中的第一个项（删第一个）
`unshift()` 在数组前端添加任意个项（从前面加）

### 5.2.5 重排列方法
`reverse()` 翻转数组项的顺序
`sort()` 升序排列（首字母排序，不是按大小）

**比较函数**
### 升序
```
function compare(value1, value2) { if (value1 < value2) { return -1; } else if (value1 > value2) { return 1; } else { return 0; } } var values = [0, 1, 5, 10, 15]; values.sort(compare); alert(values); //0,1,5,10,15

```
### 降序
```
function compare(value1, value2) { if (value1 < value2) { return 1; } else if (value1 > value2) { return -1; } else { return 0; } } var values = [0, 1, 5, 10, 15]; values.sort(compare); alert(values); //15,10,5,1,0

```

### 5.2.6 操作方法

`concat()` 末尾添加数组

`splice()` 数组中部插入项
## 删除
`splice（要删除的第一项的位置， 要删除的项数）`
`splice( 0, 2 )` 删除数组中前两项

## 插入
`splice( 起始位置， 0（要删除的项数）， 要插入的项)`
`splice( 2, 0, "red", "green" )`  从当前数组的位置2 开始插入字符串“red” 和“green”

## 替换
` splice( 起始位置， 要删除的项数， 要插入的任意数量的项)`
` splice( 2, 1, "red", "green" )` 会删除当前数组位置 2 的项， 然后再从位置 2 开始插入字符串 “red” 和“green”
例子

```
var colors = ["red", "green", "blue"]; var removed = colors.splice(0,1); //remove the first item alert(colors); //green,blue alert(removed); //red - one item array removed = colors.splice(1, 0, "yellow", "orange"); //insert two items at position 1 alert(colors); //green,yellow,orange,blue alert(removed); //empty array removed = colors.splice(1, 1, "red", "purple"); //insert two values, remove one alert(colors); //green,red,purple,orange,blue alert(removed); //yellow - one item array
```

### 5.2.7 位置方法
`indexOf()` 从数组的开头（位置0）开始向后查找， 没找到的情况下会返回-1
`lastIndexOf` 从数组的末尾开始向前查找， 没找到的情况下会返回-1
例子
 
```
        var numbers = [1,2,3,4,5,4,3,2,1];
     
        alert(numbers.indexOf(4));        //3
        alert(numbers.lastIndexOf(4));    //5
      
        alert(numbers.indexOf(4, 4));     //5
        alert(numbers.lastIndexOf(4, 4)); //3       

        var person = { name: "Nicholas" };
        var people = [{ name: "Nicholas" }];
        var morePeople = [person];
      
        alert(people.indexOf(person));     //-1
        alert(morePeople.indexOf(person)); //0
```

### 5.2.8 迭代方法
` every()` 对数组中的每一项运行给定函数， 如果该函数对每一项都返回true， 则返回true。
` filter()` 对数组中的每一项运行给定函数， 返回该函数会返回 true 的项组成的数组。
` forEach()` 对数组中的每一项运行给定的函数。 这个方法没有返回值。 
` map()` 对数组中的每一项运行给定的函数， 返回每次函数调用的结果组成的数组。
` some()` 对数组中的每一项运行给定的函数， 如果该函数对任一项返回true， 则返回true。
 **以上方法都不会修改数组中的包含的值， 传入这些方法会接受三个参数（数组项的值， 该项在数组中的位置， 数组对象本身）**

**every()   some()  例子**
以上代码调用的every() 和 some() ， 传入的函数只要给定项大于 2 就会返回true， 对于every()，它返回的是false， 因为只有部分数组项符合条件，对于some() 就返回true， 因为至少有一项是大于 2 的。

```
        var numbers = [1,2,3,4,5,4,3,2,1];
        
        var everyResult = numbers.every(function(item, index, array){
            return (item > 2);
        });
        
        alert(everyResult);       //false
        
        var someResult = numbers.some(function(item, index, array){
            return (item > 2);
        });
        
        alert(someResult);       //true

```
 

### filter() 例子
通过filter（）方法创建并返回一个所有数值都大于 2 的数组

```
        var numbers = [1,2,3,4,5,4,3,2,1];
        
        var filterResult = numbers.filter(function(item, index, array){
            return (item > 2);
        });
        
        alert(filterResult);   //[3,4,5,4,3]

```


### map() 例子
给数组中每一项都乘以 2 
```
        var numbers = [1,2,3,4,5,4,3,2,1];
        
        var mapResult = numbers.map(function(item, index, array){
            return item * 2;
        });
        
        alert(mapResult);   //[2,4,6,8,10,8,6,4,2]

```
### forEach() 例子
```
var numbers = [1,2,3,4,5,4,3,2,1];
numbers.forEach(function(item, index, array){
    //执行某些操作
})
```

### 5.2.9 归并方法
` reduce()` 从数组第一项开始逐个遍历到最后
` reduceRight()` 从数组最后一项开始，向前遍历到第一项
**四个参数（前一个值， 当前值， 项的索引， 数组对象）**
### reduce() 例子
**求数组所有值之和**
```
var values = [1,2,3,4,5];
        var sum = values.reduce(function(prev, cur, index, array){
            return prev + cur;
        });
        alert(sum);


```
### reduceRight() 例子
**求数组所有值之和**

```
var values = [1,2,3,4,5];
        var sum = values.reduceRight(function(prev, cur, index, array){
            return prev + cur;
        });
        alert(sum);
 
```

## 5.3 `Data` 类型
`Data.parse()`-接收一个表示日期的字符串参数，然后根据这个字符串返回相应日期的毫秒数
`Data.UTC()`-同样返回日期的毫秒数，但参数分别是年份、基于0但月份（一月是0，二月是1...）、月中的哪一天（1-31）、小时数（0-23）、分钟、秒、毫秒数。只有前两个参数，年和月是必须的

```
//GMT时间2000年1月1日午夜零时
var y2k = new Data(Data.UTC(2000,0));

//GMT时间2005年5月5日下午5:55:55
var allFive = new Data(Data.UTC(2005,4,5,17,55,55));
```
ES5中添加来Data.now()方法

### 5.3.1 继承的方法











