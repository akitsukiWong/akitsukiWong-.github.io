title: SQL语句学习
author: 汪秋月
tags:
  - SQL
categories: []
date: 2018-10-25 14:55:00
---
# SQL语句学习

上周试着用Express去搭后台 , 搭好了一个基础的框架 , 后端还是挺有意思的 

我如果需要更丰富的功能就需要学习更多的SQL语句 , 所以这周的计划是学习SQL语句

学习的主要途径是看W3C的文档

[链接](http://www.w3school.com.cn/sql/index.asp)

## SQL 简介

SQL 是用于访问和处理数据库的标准的计算机语言。


### 什么是 SQL？

- SQL 指结构化查询语言
- SQL 使我们有能力访问数据库
- SQL 是一种 ANSI (美国国家标准化组织) 的标准计算机语言


### SQL 能做什么？

- SQL 面向数据库执行查询
- SQL 可从数据库取回数据
- SQL 可在数据库中插入新的记录
- SQL 可更新数据库中的数据
- SQL 可从数据库删除记录
- SQL 可创建新数据库
- SQL 可在数据库中创建新表
- SQL 可在数据库中创建存储过程
- SQL 可在数据库中创建视图
- SQL 可以设置表、存储过程和视图的权限

## SQL 语法

### 数据库表

一个数据库通常包含一个或多个表。每个表由一个名字标识（例如“客户”或者“订单”）。表包含带有数据的记录（行）。

下面的例子是一个名为 "Persons" 的表：

|Id|LastName|FirstName|Address|City|
|:-|:-|:-|:-|
|1|Adams|John|Oxford Street|London|
|2|Bush|George|Fifth Avenue|New York|
|3|Carter|Thomas|Changan Street|Beijing|

上面的表包含三条记录（每一条对应一个人）和五个列（Id、姓、名、地址和城市）。

### SQL 语句

您需要在数据库上执行的大部分工作都由 SQL 语句完成。

下面的语句从表中选取 LastName 列的数据：

```
SELECT LastName FROM Persons
```

结果集类似这样：

|LastName|
|:-|
|Adams|
|Bush|
|Carter|

在本教程中，我们将为您讲解各种不同的 SQL 语句。

**重要事项 : 一定要记住，SQL 对大小写不敏感！**

### SQL DML 和 DDL

可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。

SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。

查询和更新指令构成了 SQL 的 DML 部分：

- SELECT - 从数据库表中获取数据
- UPDATE - 更新数据库表中的数据
- DELETE - 从数据库表中删除数据
- INSERT INTO - 向数据库表中插入数据

SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。

SQL 中最重要的 DDL 语句:

- CREATE DATABASE - 创建新数据库
- ALTER DATABASE - 修改数据库
- CREATE TABLE - 创建新表
- ALTER TABLE - 变更（改变）数据库表
- DROP TABLE - 删除表
- CREATE INDEX - 创建索引（搜索键）
- DROP INDEX - 删除索引

## SQL SELECT 语句

### SQL SELECT 语句

SELECT 语句用于从表中选取数据。

结果被存储在一个结果表中（称为结果集）。

### SQL SELECT 语法

```
SELECT 列名称 FROM 表名称
```

以及：

```
SELECT * FROM 表名称
```

**注释：** 
SQL 语句对大小写不敏感。SELECT 等效于 select。

### SQL SELECT 实例

如需获取名为 "LastName" 和 "FirstName" 的列的内容（从名为 "Persons" 的数据库表），请使用类似这样的 SELECT 语句：

```
SELECT LastName,FirstName FROM Persons
```

"Persons" 表:

|Id|LastName|FirstName|Address|City|
|:-|:-|:-|:-|:-|
|1 |Adams |	John|Oxford Street|London|
|2 |Bush|George|Fifth Avenue|New York|
|3 |Carter|Thomas|Changan Street|Beijing|

结果：

|LastName|FirstName|
|:-|:-|
|Adams|John|
|Bush|George|
|Carter|Thomas|

### SQL SELECT * 实例

现在我们希望从 "Persons" 表中选取所有的列。

请使用符号 * 取代列的名称，就像这样：

```
SELECT * FROM Persons
```

**提示：**星号（*）是选取所有列的快捷方式。

结果：

|Id|LastName|FirstName|Address|City|
|-|
|1|Adams|John|Oxford Street|London|
|2|Bush|George|Fifth Avenue|New York|
|3|Carter|Thomas|Changan Street|Beijing|

## SQL SELECT DISTINCT 语句

### SQL SELECT DISTINCT 语句

在表中，可能会包含重复值。这并不成问题，不过，有时您也许希望仅仅列出不同（distinct）的值。

关键词 DISTINCT 用于返回唯一不同的值。

语法：

```
SELECT DISTINCT 列名称 FROM 表名称
```

### 使用 DISTINCT 关键词

如果要从 "Company" 列中选取所有的值，我们需要使用 SELECT 语句：

```
SELECT Company FROM Orders
```

"Orders"表：

|Company|OrderNumber|
|-|
|IBM|3532|
|W3School|2356|
|Apple|4698|
|W3School|6953|

结果：

|Company|
|-|
|IBM|
|W3School|
|Apple|
|W3School|

请注意，在结果集中，W3School 被列出了两次。

如需从 Company" 列中仅选取唯一不同的值，我们需要使用 SELECT DISTINCT 语句：

```
SELECT DISTINCT Company FROM Orders 
```

现在，在结果集中，"W3School" 仅被列出了一次。

## SQL WHERE 子句

### WHERE 子句用于规定选择的标准。

### WHERE 子句

如需有条件地从表中选取数据，可将 WHERE 子句添加到 SELECT 语句。

语法

```
SELECT 列名称 FROM 表名称 WHERE 列 运算符 值
```

下面的运算符可在 WHERE 子句中使用：

|操作符 	|描述|
|-|
|= |	等于|
|<> |	不等于|
|> 	|大于|
|< |小于|
|>=|大于等于|
|<=|小于等于|
|BETWEEN|在某个范围内|
|LIKE|搜索某种模式|

**注释：在某些版本的 SQL 中，操作符 <> 可以写为 !=。**

### 使用 WHERE 子句

如果只希望选取居住在城市 "Beijing" 中的人，我们需要向 SELECT 语句添加 WHERE 子句：

```
SELECT * FROM Persons WHERE City='Beijing'
```

"Persons" 表

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
    <th>Year</th>
  </tr>
  <tr>
    <td>Adams</td>
    <td>John</td>
    <td>Oxford Street</td>
    <td>London</td>
    <td>1970</td>
  </tr>
  <tr>
    <td>Bush</td>
    <td>George</td>
    <td>Fifth Avenue</td>
    <td>New York </td>
    <td>1975</td>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
    <td>1980</td>
  </tr>
  <tr>
    <td>Gates</td>
    <td>Bill</td>
    <td>Xuanwumen 10</td>
    <td>Beijing</td>
    <td>1985</td>
  </tr>
</tbody></table>

结果：

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
    <th>Year</th>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
    <td>1980</td>
  </tr>
  <tr>
    <td>Gates</td>
    <td>Bill</td>
    <td>Xuanwumen 10</td>
    <td>Beijing</td>
    <td>1985</td>
  </tr>
</tbody></table>

引号的使用

请注意，我们在例子中的条件值周围使用的是单引号。

SQL 使用单引号来环绕文本值（大部分数据库系统也接受双引号）。如果是数值，请不要使用引号。

文本值：

```
这是正确的：
SELECT * FROM Persons WHERE FirstName='Bush'

这是错误的：
SELECT * FROM Persons WHERE FirstName=Bush
```

数值：

```
这是正确的：
SELECT * FROM Persons WHERE Year>1965

这是错误的：
SELECT * FROM Persons WHERE Year>'1965'
```

## SQL AND & OR 运算符

### AND 和 OR 运算符用于基于一个以上的条件对记录进行过滤。

### AND 和 OR 运算符

AND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来。

如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。

如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。

原始的表 (用在例子中的)：

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Adams</td>
    <td>John</td>
    <td>Oxford Street</td>
    <td>London</td>
  </tr>
  <tr>
    <td>Bush</td>
    <td>George</td>
    <td>Fifth Avenue</td>
    <td>New York </td>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
  </tr>
  <tr>
    <td>Carter</td>
    <td>William</td>
    <td>Xuanwumen 10</td>
    <td>Beijing</td>
  </tr>
</tbody></table>

### AND 运算符实例

使用 AND 来显示所有姓为 "Carter" 并且名为 "Thomas" 的人：

```
SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
  </tr>
</tbody></table>

### OR 运算符实例

使用 OR 来显示所有姓为 "Carter" 或者名为 "Thomas" 的人：

```
SELECT * FROM Persons WHERE firstname='Thomas' OR lastname='Carter'
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
  </tr>
  <tr>
    <td>Carter</td>
    <td>William</td>
    <td>Xuanwumen 10</td>
    <td>Beijing</td>
  </tr>
</tbody></table>

### 结合 AND 和 OR 运算符

我们也可以把 AND 和 OR 结合起来（使用圆括号来组成复杂的表达式）:

```
SELECT * FROM Persons WHERE (FirstName='Thomas' OR FirstName='William')
AND LastName='Carter'
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>LastName</th>
    <th>FirstName</th>
    <th>Address</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Carter</td>
    <td>Thomas</td>
    <td>Changan Street</td>
    <td>Beijing</td>
  </tr>
  <tr>
    <td>Carter</td>
    <td>William</td>
    <td>Xuanwumen 10</td>
    <td>Beijing</td>
  </tr>
</tbody></table>

## SQL ORDER BY 子句

### ORDER BY 语句用于对结果集进行排序。

### ORDER BY 语句

ORDER BY 语句用于根据指定的列对结果集进行排序。

ORDER BY 语句默认按照升序对记录进行排序。

如果您希望按照降序对记录进行排序，可以使用 DESC 关键字。

原始的表 (用在例子中的)：

Orders 表:

<table class="dataintable">
  <tbody><tr>
    <th>Company</th>
    <th>OrderNumber</th>
  </tr>
  <tr>
    <td>IBM</td>
    <td>3532</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>2356</td>
  </tr>
  <tr>
    <td>Apple</td>
    <td>4698</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>6953</td>
  </tr>
</tbody></table>

实例 1

以字母顺序显示公司名称：

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>Company</th>
    <th>OrderNumber</th>
  </tr>
  <tr>
    <td>Apple</td>
    <td>4698</td>
  </tr>
  <tr>
    <td>IBM</td>
    <td>3532</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>6953</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>2356</td>
  </tr>
</tbody></table>

实例 2

以字母顺序显示公司名称（Company），并以数字顺序显示顺序号（OrderNumber）：

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company, OrderNumber
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>Company</th>
    <th>OrderNumber</th>
  </tr>
  <tr>
    <td>Apple</td>
    <td>4698</td>
  </tr>
  <tr>
    <td>IBM</td>
    <td>3532</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>2356</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>6953</td>
  </tr>
</tbody></table>

实例 3

以逆字母顺序显示公司名称：

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>Company</th>
    <th>OrderNumber</th>
  </tr>
  <tr>
    <td>W3School</td>
    <td>6953</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>2356</td>
  </tr>
  <tr>
    <td>IBM</td>
    <td>3532</td>
  </tr>
  <tr>
    <td>Apple</td>
    <td>4698</td>
  </tr>
</tbody></table>

实例 4

以逆字母顺序显示公司名称，并以数字顺序显示顺序号：

```
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC, OrderNumber ASC
```

结果：

<table class="dataintable">
  <tbody><tr>
    <th>Company</th>
    <th>OrderNumber</th>
  </tr>
  <tr>
    <td>W3School</td>
    <td>2356</td>
  </tr>
  <tr>
    <td>W3School</td>
    <td>6953</td>
  </tr>
  <tr>
    <td>IBM</td>
    <td>3532</td>
  </tr>
  <tr>
    <td>Apple</td>
    <td>4698</td>
  </tr>
</tbody></table>

注意：在以上的结果中有两个相等的公司名称 (W3School)。只有这一次，在第一列中有相同的值时，第二列是以升序排列的。如果第一列中有些值为 nulls 时，情况也是这样的。

## SQL INSERT INTO 语句

INSERT INTO 语句用于向表格中插入新的行。

```
INSERT INTO 表名称 VALUES (值1, 值2,....)
```

我们也可以指定所要插入数据的列：

```
INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)
```







