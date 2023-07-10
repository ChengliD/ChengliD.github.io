# SQL
&emsp;&emsp;全称StructuredQuery Language，结构化查询语言。操作关系型数据库的编程语言，定义了一套操作关系型数据库统一标准。

## 1、SQL通用语法

&emsp;1）SQL语句可以单行或多行书写，以分号结尾

&emsp;2）SQL语句可以使用空格/缩进来增强语句的可读性

&emsp;3）MySQL数据库的SQL语句不区分大小写，关键字建议使用大写

&emsp;4）注释:

&emsp;&emsp;单行注释：-- 注释内容  或 #注释内容（MySQL特有)

&emsp;&emsp;多行注释：/*

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;注释内容

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*/
## 2、SQL分类

&emsp;SQL语句，根据其功能，主要分为四类：

| 分类  | 全称                        | 说明                                                   |
|-----| ------------------------- | ----------------------------------------------------- |
| DDL | Data Definition Language   | 数据定义语言，用来定义数据库对象（数据库，表，字段）   |
| DML | Data Manipulation Language | 数据操作语言，用来对数据库表中的数据进行增删改         |
| DQL | Data Query Language        | 数据查询语言，用来查询数据库中表的记录                 |
| DCL | Data Control Language      | 数据控制语言，用来创建数据库用户、控制数据库的访问权限 |

## 3、DDL

### &emsp;3.1、数据库操作

#### &emsp;&emsp;1）查询所有数据库

```sql
show databases;
```

#### &emsp;&emsp;2）创建数据库

```sql
create database [if not exists] 数据库名 [default charset 字符集] [collate 排序规则];
```
&emsp;&emsp;&emsp;说明：字符集一般使用utf8mb4，本文所有的[...]中均为可选参数

#### &emsp;&emsp;3）删除数据库

```sql
drop database[if exists] 数据库名;
```

#### &emsp;&emsp;4）使用数据库

```sql
use 数据库名;
```

#### &emsp;&emsp;5）查询当前数据库

```sql
select database();
```

### &emsp;3.2、表操作

#### &emsp;&emsp;3.2.1、查询创建

##### &emsp;&emsp;&emsp;1）查询当前数据库所有表

```sql
show tables;
```

##### &emsp;&emsp;&emsp;2）创建表结构

```sql
CREATE TABLE 表名(
	字段1 字段1类型 [COMMENT 字段1注释],
	字段2 字段2类型 [COMMENT 字段2注释],
	字段3 字段3类型 [COMMENT 字段3注释],
	......
	字段n 字段n类型 [COMMENT 字段n注释]
) [COMMENT表注释];
```

##### &emsp;&emsp;&emsp;3）查看指定表结构

```sql
desc 表名
```

##### &emsp;&emsp;&emsp;4）查询指定表的建表语句

```sql
show create table 表名
```

#### &emsp;&emsp;3.2.2、数据类型

##### &emsp;&emsp;&emsp;1）数值类型

| 类型        | 大小  | 有符号（SIGNED）范围                                | 无符号（UNSIGNED）范围                                | 描述               |
| ----------- | ----- | --------------------------------------------------- | ----------------------------------------------------- | ------------------ |
| TINYINT     | 1byte | (-128，127)                                         | (0，255)                                              | 小整数值           |
| SMALLINT    | 2byte | (-32768，32767)                                     | (0，65535)                                            | 大整数值           |
| MEDIUMINT   | 3byte | (-8388608，8388607)                                 | (0，16777215)                                         | 大整数值           |
| INT/INTEGER | 4byte | (-2147483648，2147483647)                           | (0，4294967295)                                       | 大整数值           |
| BIGINT      | 8byte | (-2^63，2^63-1)                                     | (0，2^64-1)                                           | 极大整数值         |
| FLOAT       | 1byte | (-3.402823466E+38，3.402823466351E+38)              | 0和(1.175494351E38，3.402823466E+38)                  | 单精度浮点数值     |
| DOUBLE      | 1byte | (-1.7976931348623157E+308，1.7976931348623157E+308) | 0和(2.2250738585072014E-308，1.7976931348623157E+308) | 双精度浮点数值     |
| DECIMAL     |       | 依赖于M(精度)和D(标度)的值                          | 依赖于M(精度)和D(标度)的值                            | 小数值(精确定点数) |

##### &emsp;&emsp;&emsp;2）字符串类型

| 类型        | 大小                  | 描述                         |
| ----------- | --------------------- | ---------------------------- |
| CHAR        | 0-255 bytes           | 定长字符串(需要指定长度)     |
| VARCHAR     | 0-65535 bytes         | 变长字符串(需要指定长度)     |
| TINYBLOB    | 0-255 bytes           | 不超过255个字符的二进制数据  |
| TINYTEXT    | 0-255 bytes           | 短文本字符串                 |
| BLOB        | 0-65 535 bytes        | 二进制形式的长文本数据       |
| TEXT        | 0-65 535 bytes        | 长文本数据                   |
| MEDIUMTBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据 |
| MEDIUMTEXT  | 0-16 777 215 bytes    | 中等长度文本数据             |
| LONGBLOB    | 0-4 294 967 295 bytes | 二进制形式的极大文本数据     |
| LONGTEXT    | 0-4 294 967 295 bytes | 极大文本数据                 |

##### &emsp;&emsp;&emsp;3）日期时间

| 类型      | 大小 | 范围                                     | 格式               | 描述                     |
| --------- | ---- | ---------------------------------------- | ------------------ | ------------------------ |
| DATE      | 3    | 1000-01-01至9999-12-31                   | YYYY-MM-DD         | 日期值                   |
| TIME      | 3    | -838:59:59至838:59:59                    | HH:MM:SS           | 时间值或持续时间         |
| YEAR      | 1    | 1901至2155                               | YYYY               | 年份值                   |
| DATETIME  | 8    | 1000-01-01 00:00:00至9999-12-31 23:59:59 | YYYY-MM-DDHH:MM:SS | 混合日期和时间           |
| TIMESTAMP | 4    | 1970-01-01 00:00:01至2038-01-19 03:14:07 | YYYY-MM-DDHH:MM:SS | 混合日期和时间值，时间戳 |

#### &emsp;&emsp;3.2.3、修改

##### &emsp;&emsp;&emsp;1）添加字段

```sql
alter table 表名 add 字段名 类型 [COMMENT 注释][约束];
```

##### &emsp;&emsp;&emsp;2）修改数据类型

```sql
alter table 表名 modify 字段名 新数据类型;
```

##### &emsp;&emsp;&emsp;3）修改字段名和字段类型

```sql
alter table 表名 change 旧字段名 新字段名 类型 [COMMENT 注释][约束];
```

##### &emsp;&emsp;&emsp;4）删除字段

```sql
alter table 表名 drop 字段名;
```

##### &emsp;&emsp;&emsp;5）修改表名

```sql
alter table 表名 rename to 新表名;
```

#### &emsp;&emsp;3.2.4、删除

##### &emsp;&emsp;&emsp;1）删除表

```sql
drop table[if exists] 表名;
```

##### &emsp;&emsp;&emsp;2）删除指定表，并重新创建

```sql
truncate table 表名;
```
&emsp;&emsp;&emsp;用该语句删除重建后，索引仍然是保留的

## 4、DML
&emsp;&emsp;DML英文全称是Data Manipulation Language(数据操作语言)，用来对数据库中表的数据记录进
行增、删、改操作。

### &emsp;4.1、添加数据

#### &emsp;&emsp;1）给指定字段添加数据

```sql
instrt into 表名(字段1,字段2,...) values (值1,值2,...);
```

#### &emsp;&emsp;2）给全部字段添加数据

```sql
instrt into 表名 values (值1,值2,...);
```

#### &emsp;&emsp;3）批量添加数据

```sql
instrt into 表名(字段1,字段2,...) values (值1,值2,...),(值1,值2,...),(值1,值2,...);
instrt into 表名 values (值1,值2,...),(值1,值2,...),(值1,值2,...);
```

&emsp;&emsp;注意：

&emsp;&emsp;&emsp;• 插入数据时，指定的字段顺序需要与值的顺序是一一对应的

&emsp;&emsp;&emsp;• 字符串和日期型数据应该包含在引号中

&emsp;&emsp;&emsp;• 插入的数据大小，应该在字段的规定范围内

### &emsp;4.2、修改数据

```sql
update 表名 set 字段名1 = 值1, 字段名2 = 值2,... where	
```

&emsp;&emsp;注意：修改语句的条件可以有，也可以没有，如果没有条件，则会修改整张表的所有数据。

### &emsp;4.3、删除数据

```sql
delete from 表名 [where 条件]
```



## 5、DQL

DQL英文全称是Data Query Language(数据查询语言)，数据查询语言，用来查询数据库中表的记
录。

### &emsp;5.1、基本查询

#### &emsp;&emsp;1）查询多个字段

```sql
select 字段1,字段2,字段3,... from 表名;
select * from 表名
```

#### &emsp;&emsp;2）字段设置别名

```sql
select 字段1[as 别名1],字段2 [AS 别名2]...from 表名;
select 字段1[别名1],字段2[别名2 ]...from 表名;
```

#### &emsp;&emsp;3）去除重复记录

```sql
select distinct 字段列表 from 表名;
```

### &emsp;5.2、条件查询

#### &emsp;&emsp;1）语法

```sql
select 字段列表 from 表名 where 条件列表
```

#### &emsp;&emsp;2）条件

&emsp;&emsp;常见的比较运算符如下：

| 比较运算符          | 功能                                     |
| ------------------- | ---------------------------------------- |
| >                   | 大于                                     |
| >=                  | 大于等于                                 |
| <                   | 小于                                     |
| <=                  | 小于等于                                 |
| =                   | 等于                                     |
| <> 或 !=            | 不等于                                   |
| between ... and ... | 在某个范围之内(含最小、最大值)           |
| in(...)             | 在in之后的列表中的值，多选一             |
| like(占位符)        | 模糊匹配(_匹配单个字符, %匹配任意个字符) |
| is null             | 是NULL                                   |

&emsp;&emsp;常见的逻辑运算符如下：

| 逻辑运算符 | 功能                        |
| ---------- | --------------------------- |
| and 或 &&  | 并且 (多个条件同时成立)     |
| or 或 \|\| | 或者 (多个条件任意一个成立) |
| not 或 ！  | 非 , 不是                   |

### &emsp;5.3、聚合函数

#### &emsp;&emsp; 1）介绍

&emsp;&emsp;&emsp;&emsp;将一列数据作为一个整体，进行纵向计算。

#### &emsp;&emsp;2）常见的聚合函数

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sum   | 求和     |

#### &emsp;&emsp; 3）语法

```sql
select 聚合函数(字段列表) from 表名
```

&emsp;&emsp;&emsp;注意：null值是不参与所有聚合函数运算的

### &emsp;5.4、分组查询

#### &emsp;&emsp;1）语法

```sql
select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件]
```

#### &emsp;&emsp;2）where和having的区别

&emsp;&emsp;1、执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组
之后对结果进行过滤。

&emsp;&emsp;2、判断条件不同：where不能对聚合函数进行判断，而having可以。

&emsp;&emsp;注意事项：

&emsp;&emsp;&emsp;• 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义。

&emsp;&emsp;&emsp;• 执行顺序: where > 聚合函数 > having 。

&emsp;&emsp;&emsp;• 支持多字段分组, 具体语法为 : group by columnA,columnB

### &emsp;5.5、排序查询

#### &emsp;&emsp;1）语法

```sql
select 字段列表 from 表名 order by 字段1 排序方式1 , 字段2 排序方式2;
```

#### &emsp;&emsp;2）排序方式

ASC：升序

DESC：降序

注意事项：

• 如果是升序, 可以不指定排序方式ASC ;

• 如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序 ;

### &emsp;5.6、分页查询

#### &emsp;&emsp;1）语法

```sql
select 字段列表 from 表名 limit 起始索引,查询记录数;
```

&emsp;&emsp;注意事项:

&emsp;&emsp;&emsp;• 起始索引从0开始，起始索引 = （查询页码 - 1）* 每页显示记录数。

&emsp;&emsp;&emsp;• 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。

&emsp;&emsp;&emsp;• 如果查询的是第一页数据，起始索引可以省略，直接简写为 limit 10。

### &emsp;5.7、执行顺序

![](https://chenglid.github.io/imgs/mysql/sql1.png)

## 6、DCL

DCL英文全称是Data Control Language(数据控制语言)，用来管理数据库用户、控制数据库的访
问权限。

### 6.1、管理用户

1）查询用户

```sql
select * from mysql.user;
```

Host代表当前用户访问的主机, 如果为localhost, 仅代表只能够在当前本机访问，是不可以
远程访问的。 User代表的是访问该数据库的用户名。在MySQL中需要通过Host和User来唯一标识一
个用户。

2）创建用户

```sql
create user '用户名'@'主机名' identified by '密码';
```

3）修改用户密码

```sql
alter user '用户名'@'主机名' identified with mysql_native_password by '新密码';
```

4）删除用户

```sql
drop uesr '用户名'@'主机名';
```

注意事项:

• 在MySQL中需要通过用户名@主机名的方式，来唯一标识一个用户。

• 主机名可以使用 % 通配。

• 这类SQL开发人员操作的比较少，主要是DBA（ Database Administrator 数据库

管理员）使用。

### 6.2、权限控制

| 权限                | 说明               |
| ------------------- | ------------------ |
| all，all provileges | 所有权限           |
| select              | 查询数据           |
| insert              | 插入数据           |
| update              | 修改数据           |
| delete              | 删除数据           |
| alter               | 修改表             |
| drop                | 删除数据库/表/视图 |
| create              | 创建数据库/表      |

#### 1）查询权限

```sql
show grants for '用户名'@'主机名';
```

#### 2）授予权限

```sql
show 权限列表 on 数据库名.表名 to '用户名'@'主机名';
```

#### 3）撤销权限

```sql
revoke 权限列表 on 数据库名.表名 from '用户名'@'主机名';
```

注意事项：
• 多个权限之间，使用逗号分隔
• 授权时， 数据库名和表名可以使用 * 进行通配，代表所有。
