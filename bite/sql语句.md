#  SQL 语句指南

## 一、基本概念

**SQL（Structured Query Language**）是用于管理**关系型数据库**的**标准语言**。主要包括以下几个部分：

1. 数据定义语言（**DDL**）：用于创建、修改和删除数据库对象，如表、视图、索引等。
2. 数据操作语言（**DML**）：用于对数据库中的数据进行插入、更新、删除和查询操作。
3. 数据控制语言（**DCL**）：用于控制用户对数据库的访问权限。

## **二、基本语法**

##  1、 DDL

### 数据定义语言

1.1 **显示**数据库

```sql
show database;
```

1.2 **创建**数据库

```sql
create database db2;
create database if not exists db2;
```

1.3 **删除**数据库

```sql
drop database db2;
drop database if exists db2;
```

> 查看当前所使用（进入）的数据库
>
> ```sql
> select database();
> ```

1.4 使用数据库

1.4.1 **创建**表

```sql
create table User(
	id int,
    username varchar(32),
    password varchar(32)
)
```

1.4.2  **查看**表的结构

```sql
DESC stu
```

1.4.3  **查看**当前数据库下的所有表

```sql
use database db1;
show tables;
```

1.4.4 基础的增删改查

1.4.4.1 **删除**表

```sql
drop table User;
drop table if exists User;
```

1.4.4.2 **添加**列

```sql
alter table User add address varchar(32)
```

1.4.4.3  **添加**表名

```sql
alter table User rename to AutoUser;
```

1.4.4.4 **修改**数据类型

```sql
alter table User modify address char(32);
DESC User;
```

1.4.4.5  **修改**列名和数据类型

```sql
alter table User change addresss location varchar(64);
```

1.4.5 查询所有数据

```sql
select * from User;
select * from stu;
```

---

## 2、DML

### 数据操作语言



插入数据**（INSERT）**

` INSERT INTO table_name (column1, column2,...) VALUES (value1, value2,...);`

删除数据**（DELETE）**

` DELETE FROM table_name WHERE condition;`

更新数据**（UPDATE）**

` UPDATE table_name SET column1 = value1, column2 = value2,... WHERE condition;`

查询数据**（SELECT）**

` SELECT column1, column2,... FROM table_name;`



2.1 给指定的列添加数据

2.1.1 修改中文列的编码格式（修改列名和数据类型）

```sql
alter table stu change name name varchar(255) character set utf8;
insert into stu(id,name)  values(1,"张三")
```

2.1.2  给所有列添加数据

```sql
alter table stu change sex sex varchar(255) character set utf8;
insert into stu(id,name,sex,birthday,score,email,tel,status)values(2,'lisa','女','1999-11-11',98.00,'1@qq.com',1123,1);
```

2.1.3 给所有的列添加数据，列名的列表可以省略

```sql
insert into stu values(3,'jay','男','1998-10-17',93.00,'2@qq.com',1433,1);
```

2.1.4  批量添加

```sql
insert into stu values
(4,'huawei','男','1998-10-17',93.00,'2@qq.com',1433,1),
(5,'荣耀','男','1998-10-17',93.00,'2@qq.com',1433,1),
(6,'苹果','男','1998-10-17',93.00,'2@qq.com',1433,1);
```

2.2 修改数据
2.2.1 将张三的性别改为男

```
update stu SET sex ='男' WHERE name = '张三'
```

2.2.2 将张三的生日改成2000-02-28，成绩改成99.00

```sql
update stu SET birthday = '2000-02-28',score = '99.00' WHERE name ='张三'
```

**2.2.3 如果update语句没有where条件，则表中的数据全部都被修改**

2.3 删除数据

2.3.1 删除小米记录

```sql
delete from stu WHERE name ='小米';
```



## 3、DQL

### 数据控制语言，重中之重

### 3.1 基础查询

查询数据（SELECT）

`SELECT column1, column2,... FROM table_name;`



3.1.1 查询所有列的数据，列名的列表可以使用* 代替

```sql
select *from stu1;
select  name,age,sex,address,math,english,hire_date FROM stu1;
```

3.1.2 查询name age 两列

```sql
select name,age FROM stu1;
```

3.1.3 查询单列

```SQL
select english from stu1;
```

3.1.4 查询列表 且 去除重复记录  以保证查询到的列中的数据 都是独一无二distinct

```sql
select distinct english from stu1；
```

3.1.5 查询时起别名 as

```sql
select name AS 姓名，math AS 数学,english AS 英语 FROM stu1;
```



### 3.2 条件查询

3.2.1 查询年龄大于23岁的学员信息

```sql
SELECT * FROM stu1	WHERE age > 23;
```

其他条件都是照葫芦画瓢，略



### 3.3 模糊查询

#### 3.3.1 使用LIKE进行模糊搜索

` SELECT column1, column2,... FROM table_name WHERE column_name LIKE pattern;`

* 与正常的查询语法结构类似，都是 select column from table where condtion;

* 只不过这里的condition加上了特殊的LIKE字符， where后的condition一般形式为：

` column_name LIKE pattern`

> column_name：表中依赖列进行模糊查询的那列的列名
>
> LIKE: 模糊查询所需的特定关键词
>
> pattern :   `%` 代表零个或多个字符，`_` 代表单个字符。

示例：

- 查询 “students” 表中姓名以 “T” 开头的学生。
  `SELECT * FROM students WHERE name LIKE 'T%';`
- 查询姓名中包含 “o” 的学生。
  `SELECT * FROM students WHERE name LIKE '%o%';`

#### 3.3.2 使用正则表达式进行更复杂的模糊搜索

- 不同数据库对正则表达式的支持略有不同。以 MySQL 为例，可以使用 REGEXP 关键字。
- 语法：`SELECT column1, column2,... FROM table_name WHERE column_name REGEXP pattern;`
- 示例：查询 “students” 表中姓名以大写字母开头的学生。
  `SELECT * FROM students WHERE name REGEXP '^[A-Z]';`



## 3.4 排序查询

` SELECT column1, column2,... FROM table_name ORDER BY column_name [ASC|DESC];`

- ASC 表示升序，DESC 表示降序。默认是升序。

- 示例：查询 “students” 表中的所有学生，并按照年龄升序排列。
  `SELECT * FROM students ORDER BY age ASC;`



## 3.5 分组查询

` SELECT column1, column2,... FROM table_name GROUP BY column_name;`

- 通常与聚合函数（如 SUM、AVG、COUNT、MAX、MIN）一起使用。

- 示例：查询 “students” 表中每个年龄的学生人数。
  `SELECT age, COUNT(*) FROM students GROUP BY age;`



#### 3.5.1 聚合函数

3.5.1.1 统计班级有多少个学生

```sql
SELECT COUNT(id) FROM stu1;
SELECT COUNT(*) FROM stu1;
```

3.5.1.2 查询数学成绩最高分

```sql
SELECT MAX(math) FROM stu1;
```

3.5.1.3 查询数学成绩最低分

```sql
SELECT MIN(math) FROM stu1;
```

3.5.1.4 查询数学成绩总分

```sql
SELECT SUM(math) FROM stu1;
```

3.5.1.5 查询数学成绩平均分

```sql
SELECT AVG(math) FROM stu1;
```

#### 3.5.2 分组函数

3.5.2.1 查询男同学和女同学的各自平均分‘

```sql
SELECT sex,AVG(math) FROM stu1 GROUP BY sex;
```

3.5.2.2 查询男同学和女同学的各自平均分,以及各自人数

```sql
SELECT sex,AVG(math),COUNT(*) FROM stu1 GROUP BY sex;
```

3.5.2.3 查询男同学和女同学的各自平均分,以及各自人数,要求分数低于80的不参与分组

```sql
SELECT sex,AVG(math),COUNT(*) FROM stu1 WHERE math > 80 GROUP BY sex;
```

3.5.2.4 查询男同学和女同学的各自平均分,以及各自人数,要求分数低于80的不参与分组,分组之后人数大于2

```sql
SELECT sex,AVG(math),COUNT(*) FROM stu1 WHERE math > 80 GROUP BY sex HAVING COUNT(*) > 2;
```



## 3.6 分页查询

1. 使用 `LIMIT` 和 `OFFSET`
   - `LIMIT` 用于限制返回的行数，`OFFSET` 用于指定从哪一行开始返回数据。
   - 语法：`SELECT column1, column2,... FROM table_name LIMIT offset, row_count;`
   - 例如，要查询第 11 到 20 条记录：

```sql
SELECT * FROM mytable LIMIT 10, 10;
```

2. 使用子查询：
   - 可以通过子查询来实现更复杂的分页逻辑。
   - 例如，查询按某个字段排序后的第 11 到 20 条记录：

```sql
SELECT * FROM (SELECT *, ROW_NUMBER() OVER (ORDER BY id) AS rn FROM mytable) AS subquery WHERE
```



## 3.7 约束

### 3.7.1 主键约束 **Primary Key**

**作用**：

- 唯一标识表中的每一行数据。
- 确保表中某一列或多列的值具有唯一性且非空。

**语法**：

- 在创建表时指定主键：

```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
   ...
);
```

- 在已有的表上添加主键：

```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
```

**示例**：

- 创建一个名为 “students” 的表，其中 “id” 列为主键：

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
```

### 3.7.2 唯一约束 Unique

**作用**：

- 确保表中某一列的值具有唯一性，但可以为空。

**语法**：

- 在创建表时指定唯一约束：

```sql
CREATE TABLE table_name (
    column1 datatype UNIQUE,
    column2 datatype,
   ...
);
```

- 在已有的表上添加唯一约束：

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name);
```

**示例**：

- 创建一个名为 “users” 的表，其中 “email” 列具有唯一约束：

```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100) UNIQUE
);
```

### 3.7.3 外键约束 Foreign Key

**作用**：

- 建立两个表之间的关联，确保表中的某一列的值必须存在于另一个表的特定列中。

**语法**：

- 在创建表时指定外键约束：

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
   ...
    FOREIGN KEY (column_name) REFERENCES referenced_table(referenced_column)
);
```

- 在已有的表上添加外键约束：

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES referenced_table(referenced_column);
```

**示例**：

- 创建两个表 “orders” 和 “customers”，并在 “orders” 表中添加外键约束，关联到 “customers” 表的 “id” 列：

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```

### 3.7.4 检查约束 Check

**作用：**

- 限制表中某一列的值必须满足特定的条件。

**语法：**

- 在创建表时指定检查约束：

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
   ...
    CHECK (condition)
);
```

- 在已有的表上添加检查约束：

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name CHECK (condition);
```

**示例：**

- 创建一个名为 “employees” 的表，其中 “age” 列的取值范围在 18 到 65 之间：

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    CHECK (age >= 18 AND age <= 65)
);
```

### 3.7.5 非空约束 Not Null

**作用：**

- 确保表中某一列的值不能为空。

**语法：**

- 在创建表时指定非空约束：

```sql
CREATE TABLE table_name (
    column1 datatype NOT NULL,
    column2 datatype,
   ...
);
```

**示例：**

- 创建一个名为 “students” 的表，其中 “name” 列不能为空：

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT
);
```