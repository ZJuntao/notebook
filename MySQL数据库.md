# MySQL数据库

## 创建数据库

### create命令创建数据库

create DATABASE 数据库名;



### mysqladmin创建数据库

mysqladmin -u root -p create 数据库名

Enter password：



## 删除数据库

### drop命令

drop database <数据库名>;



### mysqladmin  删除数据库

mysqladmin -u root -p drop 数据库名

Enter password：



## 选择数据库

- use RUNOOB;



## 数据类型

### MySQL支持类型

数值、日期/时间和字符串（字符）类型



### 数值类型

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| ------------ | ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| TINYINT      | 1 byte                                   | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3  bytes                                 | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4  bytes                                 | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8  bytes                                 | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4  bytes                                 | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8  bytes                                 | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |



## 数据表创建

```mysql
create table test1(
    id int unsigned auto_increment, 
    title varchar(100) not null,
	author varchar(40) not null
	date date
	primary key(id))
	ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

- innodb是存储引擎。nnoDB 是 MySQL 上第一个bai提供外键约du束的数据存储引擎，zhi除了提供事务处理外，InnoDB 还支持行锁dao，提供和 Oracle 一样的一致性的不加锁读取，能增加并发读的用户数量并提高性能，不会增加锁的数量。InnoDB 的设计目标是处理大容量数据时最大化性能，它的 CPU 利用率是其他所有基于磁盘的关系数据库引擎中最有效率的

- AUTO_INCREMENT定义列为自增的属性，一般用于主键，数值会自动加1



## 数据表删除

```mysql
drop table test1
```



## 插入数据

```mysql
insert into test1
(title, author, date)
values
("学习mysql", "菜鸟教程", now());
```



## 查询数据

```mysql
select * from test1 where id=1;
select title, author from test1 where id=1;
select * from test1 limit 2;	//limit n 表示查询n条数据
```



## 更新数据

```mysql
update test1 set title="学习PHP",author="尾田" where id=2;
```



## 删除数据

```mysql
delete from test1 where id=2;
```



## LIKE子句

- 模糊查询

```mysql
select * from test1 where title like "学习%" and author="菜鸟教程";
```

- %相当于正则表达式 中的*



## UNION操作符

### 描述

MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

### 语法

```mysql
select title from test1 where id=1
union [all | distinct]
select title from test2 where id=2;
```

**distinct:** 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。

**all:** 可选，返回所有结果集，包含重复数据。

注：可在不同的数据表之间选择。



## 排序

### 语法

以下是 SQL SELECT 语句使用 ORDER BY 子句将查询数据排序后再返回数据：

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
ORDER BY field1 [ASC [DESC][默认 ASC]], [field2...] [ASC [DESC][默认 ASC]]
```

- 你可以使用任何字段来作为排序的条件，从而返回排序后的查询结果。
- 你可以设定多个字段来排序。
- 你可以使用 ASC 或 DESC 关键字来设置查询结果是按升序或降序排列。 默认情况下，它是按升序排列。
- 你可以添加 WHERE...LIKE 子句来设置条件。



## GROUP BY 语句

GROUP BY 语句根据一个或多个列对结果集进行分组。

在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。

### GROUP BY 语法

```mysql
SELECT column_name, function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```

count：计数函数