# <Central>SQL</Central>
&emsp;&emsp;全称StructuredQuery Language，结构化查询语言。操作关系型数据库的编程语言，定义了一套操作关系型数据库统一标准。

## 1、SQL通用语法

&emsp;1）SQL语句可以单行或多行书写，以分号结尾

&emsp;2）SQL语句可以使用空格/缩进来增强语句的可读性

&emsp;3）MySQL数据库的SQL语句不区分大小写，关键字建议使用大写

&emsp;4）注释:

&emsp;&emsp;单行注释：-- 注释内容  或 #注释内容（MySQL特有)

&emsp;&emsp;多行注释：/*注释内容*/
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
