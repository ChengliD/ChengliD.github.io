# 约束

## 1、概述

&emsp;概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。

&emsp;目的：保证数据库中数据的正确、有效性和完整性。

&emsp;分类:

| 约束     | 描述                                                     | 关键字      |
| -------- | -------------------------------------------------------- | ----------- |
| 非空约束 | 限制该字段的数据不能为null                               | not null    |
| 唯一约束 | 保证该字段的所有数据都是唯一、不重复的                   | unique      |
| 主键约束 | 主键是一行数据的唯一标识，要求非空且唯一                 | primary key |
| 默认约束 | 保存数据时，如果未指定该字段的值，则采用默认值           | default     |
| 检查约束 | 保证字段值满足某一个条件                                 | check       |
| 外键约束 | 用来让两张表的数据之间建立连接，保证数据的一致性和完整性 | foreign key |

&emsp;注意：约束是作用于表中字段上的，可以在创建表/修改表的时候添加约束

## 2、约束演示案例

&emsp;完成以下的建表需求：

| 字段名 | 字段含义   | 字段类型    | 约束条件                  | 约束关键字                  |
| ------ | ---------- | ----------- | ------------------------- | --------------------------- |
| id     | ID唯一标识 | int         | 主键，并且自动增长        | primary key，auto_increment |
| name   | 姓名       | varchar(10) | 不为空，并且唯一          | not null，unique            |
| age    | 年龄       | int         | 大于0，并且小于等于120    | check                       |
| status | 状态       | char(1)     | 如果没有指定该值，默认为1 | default                     |
| gender | 性别       | char(1)     | 无                        |                             |

&emsp;对应的建表语句为：

```sql
create table tb_user(
	id int primary key auto_increment comment 'ID唯一标识',
    name varchar(10) not null unique comment '姓名',
    age int check(age>0 and age<=120) comment '年龄',
    status char(1) default '1' comment '状态',
    gender char(1) comment '性别'
) comment '用户表'
```

## 3、外键约束

外键：用来让两张表的数据之间建立连接，从而保证数据的一致性和完整性。

### &emsp;3.1、语法

#### &emsp;&emsp;1）添加外键

&emsp;&emsp;&emsp;建表时语句：

```sql
CREATE TABLE 表名(
	字段名 数据类型,
	...,
	...,    
	字段名 数据类型,
	[CONSTRAINT] [外键名称] FOREIGN KEY (外键字段名) REFERENCES 主表 (主表列名)
);
```

&emsp;&emsp;&emsp;建表后语句：

```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名) REFERENCES 主表 (主表列名) ;
```

#### &emsp;&emsp;2）删除外键

```sql
alter table 表名 drop foreign key 外键名称
```

### &emsp;3.2、删除/更新行为

&emsp;&emsp;添加了外键之后，再删除父表数据时产生的约束行为，我们就称为删除/更新行为。具体的删除/更新行为有以下几种:

| 行为        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| no action   | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。 (与 RESTRICT 一致) 默认行为 |
| restrict    | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。 (与 NO ACTION 一致) 默认行为 |
| cascade     | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有，则也删除/更新外键在子表中的记录。 |
| set null    | 当在父表中删除对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为null（这就要求该外键允许取null）。 |
| set default | 父表有变更时，子表将外键列设置成一个默认的值 (Innodb不支持)  |

&emsp;&emsp;具体语法为：

```sql
alter table 表名 add constraint 外键名称 foreign key (外键字段) references 主表名(主表字段名) on update 行为 on delete 行为
```

