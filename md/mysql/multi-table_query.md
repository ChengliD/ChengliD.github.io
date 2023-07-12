# 多表查询

## 1、多表关系

&emsp;&emsp;项目开发中，在进行数据库表结构设计时，会根据业务需求及业务模块之间的关系，分析并设计表结构，由于业务之间相互关联，所以各个表结构之间也存在着各种联系，基本上分为三种。

### &emsp;1.1、一对多

&emsp;&emsp;&emsp;案例: 部门与员工的关系

&emsp;&emsp;&emsp;关系: 一个部门对应多个员工，一个员工对应一个部门

&emsp;&emsp;&emsp;实现: 在多的一方建立外键，指向一的一方的主键

![](https://chenglid.github.io/imgs/mysql/multi-table_query_1.png)

### &emsp;1.2、多对多

&emsp;&emsp;&emsp;案例: 学生 与 课程的关系

&emsp;&emsp;&emsp;关系: 一个学生可以选修多门课程，一门课程也可以供多个学生选择

&emsp;&emsp;&emsp;实现: 建立第三张中间表，中间表至少包含两个外键，分别关联两方主键

![](https://chenglid.github.io/imgs/mysql/multi-table_query_2.png)

### &emsp;1.3、多对一

&emsp;&emsp;&emsp;案例: 用户 与 用户详情的关系

&emsp;&emsp;&emsp;关系: 一对一关系，多用于单表拆分，将一张表的基础字段放在一张表中，其他详情字段放在另一张表中，以提升操作效率

&emsp;&emsp;&emsp;实现: 在任意一方加入外键，关联另外一方的主键，并且设置外键为唯一的(UNIQUE)

![](https://chenglid.github.io/imgs/mysql/multi-table_query_3.png)



## 2、内连接

&emsp;&emsp;内连接查询的是两张表交集部分的数据，其语法分为两种：隐式内连接和显式内连接。

### &emsp;2.1、隐式内连接

```sql
select 字段列表 from 表1 , 表2 where 条件
```

### &emsp;2.2、显式内连接

```sql
select 字段列表 from 表1 [inner] join 表2 on 连接条件
```

## 3、外连接

### &emsp;3.1、左外连接

```sql
select 字段列表 from 表1 left [outer] join 表2 on 条件
```

&emsp;&emsp;左外连接相当于查询表1（左表）的所有数据，当然也包括表1和表2交集部分的数据

### &emsp;3.2、右外连接

```sql
select 字段列表 from 表1 right [outer] join 表2 on 条件
```

&emsp;&emsp;右外连接相当于查询表1（右表）的所有数据，当然也包括表1和表2交集部分的数据

&emsp;&emsp;注意：在使用左外连接时，查询的时左表的所有数据，这里将其拆分开，一是与右表没有交集的部分，这一部分的数据单独查出来，二是与右表有交集的部分，如果左表与右表是一对多的关系，那么这些多的数据会被全部查出来

## 4、自连接

### &emsp;4.1、自连接查询

```sql
select 字段列表 from 表A 别名A  inner/left/right  join 表A 别名B on 条件
```

&emsp;&emsp;自连接查询，可以是内连接查询，也可以是外连接查询，在查询时，必须要给表起别名。

### &emsp;4.2、联合查询

&emsp;&emsp;对于union查询，就是把多次查询的结果合并起来，形成一个新的查询结果集。

```sql
select 字段列表 from 表A ...
union [all]
select 字段列表 from 表B ...;
```

&emsp;&emsp;对于联合查询的多张表的列数必须保持一致，字段类型也需要保持一致。

&emsp;&emsp;union all 会将全部的数据直接合并在一起，union 会对合并之后的数据去重。

## 5、子查询

### &emsp;5.1、概述

#### &emsp;&emsp;1）概念

&emsp;&emsp;&emsp;SQL语句中嵌套select语句，称为嵌套查询，又称子查询。

```sql
select * form t1 where column1 = (select column1 from t2);
```

&emsp;&emsp;&emsp;子查询外部的语句可以是insert/update/delete/select 的任何一个

#### &emsp;&emsp;2）分类

&emsp;&emsp;&emsp;根据子查询的结果不同，分为：

&emsp;&emsp;&emsp;&emsp;A. 标量子查询（子查询结果为单个值）

&emsp;&emsp;&emsp;&emsp;B. 列子查询（子查询结果为一列）

&emsp;&emsp;&emsp;&emsp;C. 行子查询（子查询的结果为一行）

&emsp;&emsp;&emsp;&emsp;D. 表子查询（子查询结果为多行多列）



&emsp;&emsp;&emsp;根据子查询位置，分为：

&emsp;&emsp;&emsp;&emsp;A. where之后

&emsp;&emsp;&emsp;&emsp;B. from之后

&emsp;&emsp;&emsp;&emsp;C. select之后

### &emsp;5.2、标量子查询

&emsp;&emsp;&emsp;子查询返回的结果是单个值（数字、字符串、日期等），最简单的形式，这种子查询称为标量子查询。

&emsp;&emsp;&emsp;常用的操作符：= 、 <> 、  > 、  >= 、  < 、  <=

### &emsp;5.3、列子查询

&emsp;&emsp;&emsp;子查询返回的结果是一列（可以是多行），这种子查询称为列子查询。

&emsp;&emsp;&emsp;常用的操作符：IN 、NOT IN 、 ANY 、SOME 、 ALL

| 操作符 | 描述                                   |
| ------ | -------------------------------------- |
| in     | 在指定的集合范围之内，多选一           |
| not in | 不在指定的集合范围之内                 |
| any    | 子查询返回列表中，有任意一个满足即可   |
| some   | 与any等同，使用some的地方都可以使用any |
| all    | 子查询返回列表的所有值都必须满足       |

### &emsp;5.4、行子查询

&emsp;&emsp;&emsp;子查询返回的结果是一行（可以是多列），这种子查询称为行子查询

&emsp;&emsp;&emsp;常用的操作符：=、 <>、 in、 not in

&emsp;&emsp;&emsp;在操作符前，如果是多个字段的比对，用括号加逗号分隔表示多个字段

### &emsp;5.5、表子查询

&emsp;&emsp;&emsp;子查询返回的结果是多行多列，这种子查询称为表子查询

&emsp;&emsp;&emsp;常用的操作符：in