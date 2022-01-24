# day7

##MySQL

MySQL 是一种关系型数据库管理系统

而数据库（Database）则是按照数据结构来组织、存储和管理数据的仓库。

每个数据库都有一个或多个不同的 API（API 是 Application Programming Interface 的首字母缩写，它是一种软件中介，允许两个应用程序相互通信。） 用于创建，访问，管理，搜索和复制所保存的数据。

我们也可以将数据存储在文件中，但是在文件中读写数据速度相对较慢。

所以，现在我们使用关系型数据库管理系统（RDBMS）来存储和管理大数据量。所谓的关系型数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。

### RDBMS术语

+ **数据库:** 数据库是一些关联表的集合。
+ **数据表:** 表是数据的矩阵。在一个数据库中的表看起来像一个简单的电子表格。
+ **列:** 一列(数据元素) 包含了相同类型的数据, 例如邮政编码的数据。
+ **行：**一行（=元组，或记录）是一组相关的数据，例如一条用户订阅的数据。
+ **冗余**：存储两倍数据，冗余降低了性能，但提高了数据的安全性。
+ **主键**：主键是唯一的。一个数据表中只能包含一个主键。你可以使用主键来查询数据。
+ **外键：**外键用于关联两个表。
+ **复合键**：复合键（组合键）将多个列作为一个索引键，一般用于复合索引。
+ **索引：**使用索引可快速访问数据库表中的特定信息。索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录。
+ **参照完整性:** 参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性。

MySQL 为关系型数据库(Relational Database Management System), 这种所谓的"关系型"可以理解为"表格"的概念, **一个关系型数据库由一个或数个表格组成**, 如图所示的一个表格:

![img](https://www.runoob.com/wp-content/uploads/2014/03/0921_1.jpg)

+ 表头(header): 每一列的名称;
+ 列(col): 具有相同数据类型的数据的集合;
+ 行(row): 每一行用来描述某条记录的具体信息;
+ 值(value): 行的具体信息, **每个值必须与该列的数据类型相同;**
+ **键(key)**: 键的值在当前列中具有唯一性。

MySQL 是一种关联数据库管理系统，关联数据库将数据**保存在不同的表中**，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。

---



### 连接

可以使用MySQL二进制方式进入到mysql命令提示符下来连接MySQL数据库。

**实例**

以下是从命令行中连接mysql服务器的简单实例：

```mysql
[root@host]# mysql -u root -p
Enter password:******
```

在登录成功后会出现 mysql> 命令提示窗口，可以在上面执行任何 SQL 语句。

以上命令执行后，登录成功输出结果如下:

```mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2854760 to server version: 5.0.9

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
```

退出 mysql> 命令提示窗口可以使用 exit 命令，如下所示：

```mysql
mysql> exit
Bye
```

---



### 创建数据库

我们可以在登陆 MySQL 服务后，**使用 create 命令创建数据库**，语法如下:

```mysql
CREATE DATABASE 数据库名;
```

**使用 mysqladmin 创建数据库**

当我们使用root用户登录时，因为root用户拥有最高权限，可以使用 **mysql mysqladmin** 命令来创建数据库。

以下命令简单的演示了创建数据库的过程，数据名为 RUNOOB:

```mysql
[root@host]# mysqladmin -u root -p create RUNOOB
Enter password:******
```

---



### 删除数据库

在删除数据库过程中，务必要十分谨慎，因为在执行删除命令后，所有数据将会消失。

当我们使用root用户登录时，可以

**drop 命令删除数据库**

drop 命令格式：

```mysql
drop database <数据库名>;
```

例如删除名为 RUNOOB 的数据库：

```mysql
mysql> drop database RUNOOB;
```

**使用 mysqladmin 删除数据库**

也可以使用 mysql **mysqladmin** 命令在终端来执行删除命令。

以下实例删除数据库 RUNOOB：

```mysql
[root@host]# mysqladmin -u root -p drop RUNOOB
Enter password:******
```

执行以上删除数据库命令后，会出现一个提示框，来确认是否真的删除数据库：

```mysql
Dropping the database is potentially a very bad thing to do.
Any data stored in the database will be destroyed.

Do you really want to drop the 'RUNOOB' database [y/N] y
Database "RUNOOB" dropped
```

---

### 选择数据库

在我们连接到 MySQL 数据库后，可能有多个可以操作的数据库，所以需要选择要操作的数据库。

**从命令提示窗口中选择MySQL数据库**

在 mysql> 提示窗口中可以很简单的选择特定的数据库。你可以使用SQL命令来选择指定的数据库。

**实例**

以下实例选取了数据库 RUNOOB:

```mysql
[root@host]# mysql -u root -p
Enter password:******
mysql> use RUNOOB;
Database changed
mysql>
```

执行以上命令后，我们就已经成功选择了 RUNOOB 数据库，在后续的操作中都会在 RUNOOB 数据库中执行。

---



### 数据表

####创建

创建MySQL数据表需要以下信息：

+ 表名
+ 表字段名
+ 定义每个表字段

**语法**

以下为创建MySQL数据表的SQL通用语法：

```mysql
CREATE TABLE table_name (column_name column_type);
```

**通过命令提示符创建表**

通过 mysql> 命令窗口可以很简单的创建MySQL数据表。我们可以使用 SQL 语句 **CREATE TABLE** 来创建数据表。

**实例**

以下为创建数据表 runoob_tbl 实例:

```mysql
root@host# mysql -u root -p
Enter password:*******
mysql> use RUNOOB;
Database changed
mysql> CREATE TABLE runoob_tbl(
    runoob_id INT NOT NULL AUTO_INCREMENT,
    runoob_title VARCHAR(100) NOT NULL,
    runoob_author VARCHAR(40) NOT NULL,
    submission_date DATE,
    PRIMARY KEY ( runoob_id )
    )ENGINE=InnoDB DEFAULT CHARSET=utf8;
Query OK, 0 rows affected (0.16 sec)
mysql>
```

**注意：**MySQL命令终止符为分号 **;** 。

---

####删除

**语法**

以下为删除MySQL数据表的通用语法：

```mysql
DROP TABLE table_name ;
```

------

**在命令提示窗口中删除数据表**

在mysql>命令提示窗口中删除数据表SQL语句为 **DROP TABLE** ：

**实例**

以下实例删除了数据表runoob_tbl:

```mysql
root@host# mysql -u root -p
Enter password:*******
mysql> use RUNOOB;
Database changed
mysql> DROP TABLE runoob_tbl;
Query OK, 0 rows affected (0.8 sec)
mysql>
```

---

####  插入数据

MySQL 表中使用 **INSERT INTO** SQL语句来插入数据。

可以通过 mysql> 命令提示窗口中向数据表中插入数据

**语法**

以下为向MySQL数据表插入数据通用的 **INSERT INTO** SQL语法：

```mysql
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

如果数据是字符型，必须使用单引号或者双引号，如："value"。

**通过命令提示窗口插入数据**

使用 SQL **INSERT INTO** 语句向 MySQL 数据表 runoob_tbl 插入数据

**实例**

向 runoob_tbl 表插入三条数据:

```mysql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use RUNOOB;
Database changed
mysql> INSERT INTO runoob_tbl 
     (runoob_title, runoob_author, submission_date)
     VALUES
     ("学习 html", "三剑客", NOW());
Query OK, 1 rows affected, 1 warnings (0.01 sec)
mysql> INSERT INTO runoob_tbl
     (runoob_title, runoob_author, submission_date)
     VALUES
     ("学习 css", "三剑客", NOW());
Query OK, 1 rows affected, 1 warnings (0.01 sec)
mysql> INSERT INTO runoob_tbl
     (runoob_title, runoob_author, submission_date)
     VALUES
     ("JAVA javascript", "三剑客", '2016-05-06');
Query OK, 1 rows affected (0.00 sec)
mysql>
```

其中的now（）时一个函数用来返回日期和时间

---

#### **查询数据**

MySQL 数据库使用SQL SELECT语句来查询数据。

**语法**

以下为在MySQL数据库中查询数据通用的 SELECT 语法：

```mysql
SELECT column_name,column_name
FROM table_name
[WHERE Clause]
[LIMIT N][ OFFSET M]
```

+ 查询语句中你可以使用一个或者多个表，表之间使用逗号(,)分割，并使用WHERE语句来设定查询条件。
+ SELECT 命令可以读取一条或者多条记录。
+ 可以使用星号（*）来代替其他字段，SELECT语句会返回表的所有字段数据
+ 可以使用 WHERE 语句来包含任何条件。
+ 可以使用 LIMIT 属性来设定返回的记录数。
+ 可以通过OFFSET指定SELECT语句开始查询的数据偏移量。默认情况下偏移量为0。

**通过命令提示符获取数据**

以下实例我们将通过 SQL SELECT 命令来获取 MySQL 数据表 runoob_tbl 的数据：

**实例**

以下实例将返回数据表 runoob_tbl 的所有记录:

**读取数据表：**

~~~ mysql
select * from runoob_tbl;
~~~

---

#### 修改

修改表名 : ALTER TABLE 旧表名 RENAME AS 新表名

添加字段 : ALTER TABLE 表名 ADD字段名 列属性[属性]

修改字段 :

ALTER TABLE 表名 MODIFY 字段名 列类型[属性]
ALTER TABLE 表名 CHANGE 旧字段名 新字段名 列属性[属性]
删除字段 : ALTER TABLE 表名 DROP 字段名

~~~mysql
-- 修改表名
-- ALTER TABLE 旧表名 RENAME AS 新表名
ALTER TABLE teacher RENAME AS teachers;

-- 增加表的字段
-- ALTER TABLE 表名 ADD 字段名 列属性
ALTER TABLE teachers ADD age INT(11);

-- 修改表的字段(重命名，修改约束)
-- ALTER TABLE 表名 MODIFY 字段名 [列属性];
ALTER TABLE teachers MODIFY age VARCHAR(11);-- 修改约束
-- ALTER TABLE 表名 CHANGE 旧名字 新名字 [列属性];
ALTER TABLE teachers CHANGE age age1 INT(1);-- 字段重命名

-- 删除表的字段
-- ALTER TABLE 表名 DROP 字段名
ALTER TABLE teachers DROP age1;

~~~

---



### 数据类型

数值

|           |                                      |         |
| --------- | ------------------------------------ | ------- |
| 数据类型  | 描述                                 | 大小    |
| tinyint   | 十分小的数据                         | 1个字节 |
| smallint  | 较小的数据                           | 2个字节 |
| mediumint | 中等大小的数据                       | 3个字节 |
| int       | 标准的整数                           | 4个字节 |
| bigint    | 较大的数据                           | 8个字节 |
| float     | 浮点数                               | 4个字节 |
| double    | 浮点数                               | 8个字节 |
| decimal   | 字符串形式的浮点数，一般用于金融计算 |         |

字符串

| 数据类型 | 描述           | 大小    |
| -------- | -------------- | ------- |
| char     | 字符串固定大小 | 0~255   |
| varchar  | 可变字符串     | 0~65535 |
| tinytext | 微型文本       | 2^8-1   |
| text     | 文本串         | 2^16-1  |

时间日期

|           |                                |                       |
| --------- | ------------------------------ | --------------------- |
| 数据类型  | 描述                           | 格式                  |
| date      | 日期格式                       | YYYY-MM-DD            |
| time      | 时间格式                       | HH：mm：ss            |
| datetime  | 最常用的时间格式               | YYYY-MM-DD HH：mm：ss |
| timestamp | 时间戳，1970.1.1到现在的毫秒数 |                       |
| year      | 年份表示                       |                       |

---

### WHERE 子句（用来查询）

在MySQL 表中可以使用 SQL SELECT 语句来读取数据。

但是如果需要有条件地从表中选取数据，可将 WHERE 子句添加到 SELECT 语句中。

**语法**

以下是 SQL SELECT 语句使用 WHERE 子句从数据表中读取数据的通用语法：

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

+ 查询语句中，可以使用一个或者多个表，表之间使用逗号**,** 分割，并使用WHERE语句来设定查询条件。
+ 可以在 WHERE 子句中指定任何条件。
+ 可以使用 AND 或者 OR 指定一个或多个条件。
+ WHERE 子句也可以运用于 SQL 的 DELETE 或者 UPDATE 命令。
+ WHERE 子句类似于程序语言中的 if 条件，根据 MySQL 表中的字段值来读取指定的数据。

| 操作符 | 描述                                                         | 实例                 |
| :----- | :----------------------------------------------------------- | :------------------- |
| =      | 等号，检测两个值是否相等，如果相等返回true                   | (A = B) 返回false。  |
| <>, != | 不等于，检测两个值是否相等，如果不相等返回true               | (A != B) 返回 true。 |
| >      | 大于号，检测左边的值是否大于右边的值, 如果左边的值大于右边的值返回true | (A > B) 返回false。  |
| <      | 小于号，检测左边的值是否小于右边的值, 如果左边的值小于右边的值返回true | (A < B) 返回 true。  |
| >=     | 大于等于号，检测左边的值是否大于或等于右边的值, 如果左边的值大于或等于右边的值返回true | (A >= B) 返回false。 |
| <=     | 小于等于号，检测左边的值是否小于或等于右边的值, 如果左边的值小于或等于右边的值返回true | (A <= B) 返回 true。 |

如果我们想在 MySQL 数据表中读取指定的数据，WHERE 子句是非常有用的。

使用主键来作为 WHERE 子句的条件查询是非常快速的。

如果给定的条件在表中没有任何匹配的记录，那么查询不会返回任何数据。

---

### UPDATE 更新

如果我们需要修改或更新 MySQL 中的数据，我们可以使用 SQL UPDATE 命令来操作。

**语法**

以下是 UPDATE 命令修改 MySQL 数据表数据的通用 SQL 语法：

```mysql
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

+ 可以同时更新一个或多个字段。
+ 可以在 WHERE 子句中指定任何条件。
+ 可以在一个单独表中同时更新数据。

当需要更新数据表中指定行的数据时， WHERE 子句将会变得非常有用。

---

### DELETE 语句

我们可以使用 SQL 的 DELETE FROM 命令来删除 MySQL 数据表中的记录。

**语法**

以下是 SQL DELETE 语句从 MySQL 数据表中删除数据的通用语法：

```mysql
DELETE FROM table_name [WHERE Clause]
```

+ 如果没有指定 WHERE 子句，MySQL 表中的所有记录将被删除。
+ 可以在 WHERE 子句中指定任何条件
+ 可以在单个表中一次性删除记录。

当想删除数据表中指定的记录时 WHERE 子句将会非常有用。

**实例**

以下实例将删除 runoob_tbl 表中 runoob_id 为3 的记录：

~~~mysql
mysql> use RUNOOB;
Database changed
mysql> DELETE FROM runoob_tbl WHERE runoob_id=3;
Query OK, 1 row affected (0.23 sec)
~~~

---

### LIKE 子句

在 MySQL 中我们可以使用 SQL SELECT 命令来读取数据， 同时也可以在 SELECT 语句中使用 WHERE 子句来获取指定的记录。

WHERE 子句中可以使用等号 **=** 来设定获取数据的条件，如 "runoob_author = 'RUNOOB.COM'"。

但是有时候我们需要获取 runoob_author 字段含有 "COM" 字符的所有记录，这时我们就需要在 WHERE 子句中使用 SQL LIKE 子句。

SQL LIKE 子句中使用百分号 **%**字符来表示任意字符

如果没有使用百分号 **%**, LIKE 子句与等号 **=** 的效果是一样的。

**语法**

以下是 SQL SELECT 语句使用 LIKE 子句从数据表中读取数据的通用语法：

```mysql
SELECT field1, field2,...fieldN 
FROM table_name
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

+ 可以在 WHERE 子句中指定任何条件。
+ 可以在 WHERE 子句中使用LIKE子句。
+ 可以使用LIKE子句代替等号 **=**。
+ LIKE 通常与 **%** 一同使用，类似于一个元字符的搜索。
+ 可以使用 AND 或者 OR 指定一个或多个条件。
+ 可以在 DELETE 或 UPDATE 命令中使用 WHERE...LIKE 子句来指定条件。

---

###  UNION 操作符

MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。当有多个 SELECT 语句时会删除语句中重复的数据。

**语法**

MySQL UNION 操作符语法格式：

```mysql
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```

**参数**

+ **expression1, expression2, ... expression_n**: 要检索的列。
+ **tables:** 要检索的数据表。
+ **WHERE conditions:** 可选， 检索条件。
+ **DISTINCT:** 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没有影响。
+ **ALL:** 可选，返回所有结果集，包含重复数据。

---

### 排序

如果我们需要对读取的数据进行排序，我们就可以使用 MySQL 的 **ORDER BY** 子句来设定你想按哪个字段哪种方式来进行排序，再返回搜索结果。

### 语法

以下是 SQL SELECT 语句使用 ORDER BY 子句将查询数据排序后再返回数据：

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
ORDER BY field1 [ASC [DESC][默认 ASC]], [field2...] [ASC [DESC][默认 ASC]]
```

+ 可以使用任何字段来作为排序的条件，从而返回排序后的查询结果。
+ 可以设定多个字段来排序。
+ 可以使用 ASC 或 DESC 关键字来设置查询结果是按升序或降序排列。 默认情况下，它是按升序排列。
+ 可以添加 WHERE...LIKE 子句来设置条件。

---

### 正则表达式

MySQL可以通过 **LIKE ...%** 来进行模糊匹配，同样的MySQL也支持其他正则表达式的匹配， MySQL中使用 REGEXP 操作符来进行正则表达式匹配。

| 模式       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| ^          | 匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性，^ 也匹配 '\n' 或 '\r' 之后的位置。 |
| $          | 匹配输入字符串的结束位置。如果设置了RegExp 对象的 Multiline 属性，$ 也匹配 '\n' 或 '\r' 之前的位置。 |
| .          | 匹配除 "\n" 之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用像 '[.\n]' 的模式。 |
| [...]      | 字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。 |
| [^...]     | 负值字符集合。匹配未包含的任意字符。例如， '[^abc]' 可以匹配 "plain" 中的'p'。 |
| p1\|p2\|p3 | 匹配 p1 或 p2 或 p3。例如，'z\|food' 能匹配 "z" 或 "food"。'(z\|f)ood' 则匹配 "zood" 或 "food"。 |
| *          | 匹配前面的子表达式零次或多次。例如，zo* 能匹配 "z" 以及 "zoo"。* 等价于{0,}。 |
| +          | 匹配前面的子表达式一次或多次。例如，'zo+' 能匹配 "zo" 以及 "zoo"，但不能匹配 "z"。+ 等价于 {1,}。 |
| {n}        | n 是一个非负整数。匹配确定的 n 次。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。 |
| {n,m}      | m 和 n 均为非负整数，其中n <= m。最少匹配 n 次且最多匹配 m 次。 |

**实例**

了解以上的正则需求后，我们就可以根据自己的需求来编写带有正则表达式的SQL语句。

查找name字段中以'st'为开头的所有数据：

```mysql
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^st';
```

查找name字段中以'ok'为结尾的所有数据：

```mysql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'ok$';
```

查找name字段中包含'mar'字符串的所有数据：

```mysql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'mar';
```

查找name字段中以元音字符开头或以'ok'字符串结尾的所有数据：

```mysql
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^[aeiou]|ok$';
```

---

### 索引

索引可以大大提高MySQL的检索速度。

索引分单列索引和组合索引。单列索引，即一个索引只包含单个列，一个表可以有多个单列索引，但这不是组合索引。组合索引，即一个索引包含多个列。

#### 普通索引

**创建索引**

这是最基本的索引，它没有任何限制。它有以下几种创建方式：

```mysql
CREATE INDEX indexName ON table_name (column_name)
```

如果是CHAR，VARCHAR类型，length可以小于字段实际长度；如果是BLOB和TEXT类型，必须指定 length。

**修改表结构(添加索引)**

```mysql
ALTER table tableName ADD INDEX indexName(columnName)
```

**创建表的时候直接指定**

```mysql
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
INDEX [indexName] (username(length))  
 
);  
```

**删除索引的语法**

```mysql
DROP INDEX [indexName] ON mytable; 
```

#### 唯一索引

它与前面的普通索引类似，不同的就是：索引列的值必须唯一，但允许有空值。如果是组合索引，则列值的组合必须唯一。它有以下几种创建方式：

**创建索引**

```mysql
CREATE UNIQUE INDEX indexName ON mytable(username(length)) 
```

**修改表结构**

```mysql
ALTER table mytable ADD UNIQUE [indexName] (username(length))
```

**创建表的时候直接指定**

```mysql
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
UNIQUE [indexName] (username(length))  
 
);  
```

#### 使用ALTER 命令添加和删除索引

有四种方式来添加数据表的索引：

+ ALTER TABLE tbl_name ADD PRIMARY KEY (column_list):

   该语句添加一个主键，这意味着索引值必须是唯一的，且不能为NULL。

+ **ALTER TABLE tbl_name ADD UNIQUE index_name (column_list):** 这条语句创建索引的值必须是唯一的（除了NULL外，NULL可能会出现多次）。

+ **ALTER TABLE tbl_name ADD INDEX index_name (column_list):** 添加普通索引，索引值可出现多次。

+ **ALTER TABLE tbl_name ADD FULLTEXT index_name (column_list):**该语句指定了索引为 FULLTEXT ，用于全文索引。

以下实例为在表中添加索引。

```mysql
mysql> ALTER TABLE testalter_tbl ADD INDEX (c);
```

还可以在 ALTER 命令中使用 DROP 子句来删除索引。尝试以下实例删除索引:

```mysql
mysql> ALTER TABLE testalter_tbl DROP INDEX c;
```

------

#### 使用 ALTER 命令添加和删除主键

主键作用于列上（可以一个列或多个列联合主键），添加主键索引时，需要确保该主键默认不为空（NOT NULL）。实例如下：

```mysql
mysql> ALTER TABLE testalter_tbl MODIFY i INT NOT NULL;
mysql> ALTER TABLE testalter_tbl ADD PRIMARY KEY (i);
```

也可以使用 ALTER 命令删除主键：

```mysql
mysql> ALTER TABLE testalter_tbl DROP PRIMARY KEY;
```

删除主键时只需指定PRIMARY KEY，但在删除索引时，必须知道索引名。

------

#### 显示索引信息

可以使用 SHOW INDEX 命令来列出表中的相关的索引信息。可以通过添加 \G 来格式化输出信息。

尝试以下实例:

```mysql
mysql> SHOW INDEX FROM table_name\G
........
```