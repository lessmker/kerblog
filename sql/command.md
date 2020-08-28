## 1 简介

### 1.1 什么是 SQL？

- SQL 指结构化查询语言
- SQL 使我们有能力访问数据库
- SQL 是一种 ANSI 的标准计算机语言

### 1.2 SQL 能做什么？

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

**注：sql对大小写不敏感**

## 2 基础语法：

可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。

### 2.1 SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。

#### 2.1.1 select:从数据库表中获取数据

语法：

```sql
select * from 表名称
或
select 列名称 FROM 表名称
```

列名称可以用逗号(,)隔开

##### SELECT DISTINCT

在表中，可能会包含重复值。这并不成问题，不过，有时您也许希望仅仅列出不同（distinct）的值。

关键词 DISTINCT 用于返回唯一不同的值。

语法：

```
select distinct 列名 from 表名称
```

#### 2.1.2 update:更新数据库表中的数据

```sql
UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值
```

#### 2.1.3 delete:从数据库中删除数据

```sql
DELETE FROM 表名称 WHERE 列名称 = 值
```

#### 2.1.4 insert into:向数据库表中插入数据

```sql
INSERT INTO 表名称 VALUES (值1, 值2,....)
INSERT INTO 表名称 (列1, 列2,...) VALUES (值1, 值2,....)
```

### 2.2 SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。

#### 2.2.1 CREATE DATABASE- 创建新数据库

```
CREATE DATABASE 数据库名称
```

#### 2.2.2 ALTER DATABASE - 修改数据库

#### 2.2.3 CREATE TABLE - 创建新表

```sql
CREATE TABLE 表名称(
列名称1 数据类型,
列名称2 数据类型,
列名称3 数据类型,
....)
```

| 数据类型                                                | 描述                                                         |
| :------------------------------------------------------ | :----------------------------------------------------------- |
| integer(size)、int(size)、smallint(size)、tinyint(size) | 仅容纳整数。在括号内规定数字的最大位数。                     |
| decimal(size,d)、numeric(size,d)                        | 容纳带有小数的数字。"size" 规定数字的最大位数。"d" 规定小数点右侧的最大位数。 |
| char(size)                                              | 容纳固定长度的字符串（可容纳字母、数字以及特殊字符）。在括号中规定字符串的长度。 |
| varchar(size)                                           | 容纳可变长度的字符串（可容纳字母、数字以及特殊的字符）。在括号中规定字符串的最大长度。 |
| date(yyyymmdd)                                          | 容纳日期。                                                   |

#### 2.2.4 ALTER TABLE - 变更（改变）数据库表

#### 2.2.5 DROP TABLE - 删除表

#### 2.2.6 CREATE INDEX - 创建索引（搜索键）

#### 2.2.7 DROP INDEX - 删除索引



### 2.3条件子句

#### 2.3.1 where 选择

语法：

```sql
select 列名称 from 表名称 where 列名称 运算符 值
```

操作符

| 操作符  | 描述                                               |
| ------- | -------------------------------------------------- |
| =       | 等于                                               |
| <>      | 不等于(在某些版本的 SQL 中，操作符 <> 可以写为 !=) |
| >       | 大于                                               |
| <       | 小于                                               |
| >=      | 大于等于                                           |
| <=      | 小于等于                                           |
| between | 在某个范围内                                       |
| like    | 搜索某种模式                                       |

#### 2.3.2 and 和 or 运算符

AND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来。

如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。

如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。

#### 2.3.3 order by 对结果进行排序

- ASC 升序(默认为升序)
- DESC 降序

```sql
SELECT 列名称,列名称 FROM 表名 ORDER BY 列名称 DESC, 列名称 ASC
```

## 3 高级

### 3.1 TOP用于规定要返回的记录的数目

```sql
sqlserver :
SELECT TOP number|percent 列名称(s) FROM 表名称
MySQL 和 Oracle 中的 SQL SELECT TOP 是等价的
mysql：
SELECT 列名称(s) FROM 表名称 LIMIT number
Oracle：
SELECT 列名称(s) FROM 表名称 WHERE ROWNUM <= number
```

### 3.2 like 用于在 WHERE 子句中搜索列中的指定模式

```sql
SELECT 列名称(s) FROM 表名 WHERE 列名称 LIKE '%值%'
```

### 3.3 通配符

| 通配符                     | 描述                       |
| :------------------------- | :------------------------- |
| %                          | 替代一个或多个字符         |
| _                          | 仅替代一个字符             |
| [charlist]                 | 字符列中的任何单一字符     |
| [^charlist]或者[!charlist] | 不在字符列中的任何单一字符 |

### 3.4 IN 操作符允许我们在 WHERE 子句中规定多个值

```sql
SELECT 列名称(s) FROM 表名称 WHERE 列名称 IN (value1,value2,...)
```

### 3.5 BETWEEN 操作符在 WHERE 子句中使用，作用是选取介于两个值之间的数据范围。

```sql
SELECT 列名称(s) FROM 表名称 WHERE 列名称 BETWEEN value1 AND value2
```

范围之外用：**NOT BETWEEN...AND**

### 3.6 Alias 可以为列名称和表名称指定别名

```sql
表的SQL Alias语法：
SELECT 列名称(s) FROM 表名称 AS 表别名
列的SQL Alias语法：
SELECT 列名称 AS 列别名 FROM 表名称
```

### 3.7 join 用于根据两个或多个表中的列之间的关系，从这些表中查询数据

```
JOIN(INNER JOIN): 如果表中有至少一个匹配，则返回行(内连接)
LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行(左连接)
RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行(右连接)
FULL JOIN: 只要其中一个表中存在匹配，就返回行(全连接)
```

#### 2.7.1 INNER JOIN 在表中存在至少一个匹配时，INNER JOIN 关键字返回行

```sql
SELECT 列名称(s) FROM 表名称1 INNER JOIN 表名称2 ON 表名称1.列名称=表名称2.列名称
```

> 注：INNER JOIN 与 JOIN 是相同的

#### 2.7.2 LEFT JOIN 会从左表 (table_name1) 那里返回所有的行，即使在右表 (table_name2) 中没有匹配的行

```sql
SELECT 列名称(s) FROM 表名称1 LEFT JOIN 表名称2 ON 表名称1.列名称=表名称2.列名称
```

> 注：在某些数据库中， LEFT JOIN 称为 LEFT OUTER JOIN

#### 2.7.3 RIGHT JOIN 会右表 (table_name2) 那里返回所有的行，即使在左表 (table_name1) 中没有匹配的行

```sql
SELECT 列名称(s) FROM 表名称1 RIGHT JOIN 表名称2 ON 表名称1.列名称=表名称2.列名称
```

> 注：在某些数据库中， RIGHT JOIN 称为 RIGHT OUTER JOIN

#### 2.7.4 FULL JOIN 只要其中某个表存在匹配，FULL JOIN 关键字就会返回行

```sql
SELECT 列名称(s) FROM 表名称1 FULL JOIN 表名称2 ON 表名称1.列名称=表名称2.列名称
```

> 注：在某些数据库中， FULL JOIN 称为 FULL OUTER JOIN

### 2.8 UNION 操作符用于合并两个或多个 SELECT 语句的结果集。

> UNION 内部的 SELECT 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。同时，每条 SELECT 语句中的列的顺序必须相同

#### SQL UNION 语法

```sql
SELECT 列名称(s) FROM 表名称1
UNION
SELECT 列名称(s) FROM 表名称2
```

**注释：**默认地，UNION 操作符选取不同的值。如果允许重复的值，请使用 UNION ALL。

#### SQL UNION ALL 语法

```sql
SELECT column_name(s) FROM table_name1
UNION ALL
SELECT column_name(s) FROM table_name2
```

另外，UNION 结果集中的列名总是等于 UNION 中第一个 SELECT 语句中的列名。

### 2.9 SQL SELECT INTO 语句可用于创建表的备份复件

SELECT INTO 语句从一个表中选取数据，然后把数据插入另一个表中。

SELECT INTO 语句常用于创建表的备份复件或者用于对记录进行存档。

#### SQL SELECT INTO 语法

您可以把所有的列插入新表：

```sql
SELECT *
INTO 新表名称 [IN 外部数据库名称] 
FROM 旧表名称
```

或者只把希望的列插入新表：

```sql
SELECT 列名称(s)
INTO 新表名称 [IN 外部数据库名称] 
FROM 旧表名称
```

### 2.10 SQL 约束 (Constraints)

#### 2.10.1 NOT NULL 约束强制列不接受 NULL 值

NOT NULL 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录

#### 2.10.2 UNIQUE 约束唯一标识数据库表中的每条记录

UNIQUE 和 PRIMARY KEY 约束均为列或列集合提供了唯一性的保证。

PRIMARY KEY 拥有自动定义的 UNIQUE 约束。

请注意，每个表可以有多个 UNIQUE 约束，但是每个表只能有一个 PRIMARY KEY 约束。

命名UNIQUE约束

```
...(
CONSTRAINT uc_PersonID UNIQUE (Id_P,LastName)
)...
```

当表已被创建时，如需在 "Id_P" 列创建 UNIQUE 约束，请使用下列 SQL：

```sql
ALTER TABLE 表名称 ADD UNIQUE (列名称)
```

如需命名 UNIQUE 约束，并定义多个列的 UNIQUE 约束，请使用下面的 SQL 语法：

```sql
ALTER TABLE 表名称 CONSTRAINT 约束名 UNIQUE (列名称1,列名称2)
```

如需撤销 UNIQUE 约束，请使用下面的 SQL：

```sql
mysql:
ALTER TABLE 表名称 INDEX 约束名
SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 DROP CONSTRAINT 约束名
```



#### 2.10.3 PRIMARY KEY 约束唯一标识数据库表中的每条记录

主键必须包含唯一的值。

主键列不能包含 NULL 值。

每个表都应该有一个主键，并且每个表只能有一个主键。

```sql
MySQL:
...(...,PRIMARY KEY (Id_P))...

SQL Server / Oracle / MS Access:
...(列名称 列类型 NOT NULL PRIMARY KEY,...)...
```

多个列定义约束：

```sql
...(...,CONSTRAINT 约束名 PRIMARY KEY (列名称1,列名称2))...
```

如果在表已存在的情况下为 "Id_P" 列创建 PRIMARY KEY 约束，请使用下面的 SQL：

```sql
ALTER TABLE 表名称 ADD PRIMARY KEY (列名称)
```

如果需要命名 PRIMARY KEY 约束，以及为多个列定义 PRIMARY KEY 约束，请使用下面的 SQL 语法：

```sql
ALTER TABLE 表名称 ADD CONSTRAINT 约束名 PRIMARY KEY (列名称1,列名称2)
```

> **注释：**如果您使用 ALTER TABLE 语句添加主键，必须把主键列声明为不包含 NULL 值（在表首次创建时）。

撤销 PRIMARY KEY 约束，请使用下面的 SQL：

```sql
MySQL:
ALTER TABLE 表名称 DROP PRIMARY KEY

SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 DROP CONSTRAINT 约束名称
```

#### 2.10.4 FOREIGN KEY 一个表中的 FOREIGN KEY 指向另一个表中的 PRIMARY KEY

MySQL:

```sql
...(
...FOREIGN KEY (列名称) REFERENCES 其他表名称(列名称)
)...
```

SQL Server / Oracle / MS Access:

```sql
...(
...列名称 列类型 FOREIGN KEY REFERENCES 其他表名称(列名称)
)...
```

如果需要命名 FOREIGN KEY 约束，以及为多个列定义 FOREIGN KEY 约束，请使用下面的 SQL 语法：

```sql
...(
...CONSTRAINT 约束名称 FOREIGN KEY (列名称)
REFERENCES 其他表名称(列名称)
)...
```

如果在 "Orders" 表已存在的情况下为 "Id_P" 列创建 FOREIGN KEY 约束，请使用下面的 SQL：

```sql
ALTER TABLE 表名称 ADD FOREIGN KEY (列名称) REFERENCES 其他表名称(列名称)
```

如果需要命名 FOREIGN KEY 约束，以及为多个列定义 FOREIGN KEY 约束，请使用下面的 SQL 语法：

```sql
ALTER TABLE 表名称 ADD CONSTRAINT 约束名称 FOREIGN KEY (列名称) REFERENCES 其他表名称(列名称)
```

撤销 FOREIGN KEY 约束，请使用下面的 SQL：

```sql
mysql：
ALTER TABLE 表名称 DROP FOREIGN KEY 约束名称
SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 DROP CONSTRAINT 约束名称
```

#### 2.10.5 CHECK

> CHECK 约束用于限制列中的值的范围。
>
> 如果对单个列定义 CHECK 约束，那么该列只允许特定的值。
>
> 如果对一个表定义 CHECK 约束，那么此约束会在特定的列中对值进行限制。

```sql
My SQL:
...(...,CHECK (列名称 > 0 ))...
SQL Server / Oracle / MS Access:
...(列名称 列类型 NOT NULL CHECK (Id_P>0)...)...
```

如果需要命名 CHECK 约束，以及为多个列定义 CHECK 约束，请使用下面的 SQL 语法：

```sql
...(...,CONSTRAINT 约束名称 CHECK (列名称1>0 AND 列名称2='值'))...
```

如果在表已存在的情况下为 "Id_P" 列创建 CHECK 约束，请使用下面的 SQL：

```sql
ALTER TABLE 表名称 ADD CHECK (列名称>0)
```

如果需要命名 CHECK 约束，以及为多个列定义 CHECK 约束，请使用下面的 SQL 语法：

```sql
ALTER TABLE 表名称 ADD CONSTRAINT 约束名称 CHECK (列名称1>0 AND 列名称2='值')
```

撤销 CHECK 约束，请使用下面的 SQL：

```
SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 DROP CONSTRAINT 约束名称
MySQL:
ALTER TABLE 表名称 DROP CHECK 约束名称
```

#### 2.10.6 DEFAULT

DEFAULT 约束用于向列中插入默认值

如果没有规定其他的值，那么会将默认值添加到所有的新记录。

```sql
...(...列名称 列数据类型 DEFAULT '默认值')...
```

通过使用类似 GETDATE() 这样的函数，DEFAULT 约束也可以用于插入系统值：

```sql
...(...,列名称 date DEFAULT GETDATE())...
```

如果在表已存在的情况下为 "City" 列创建 DEFAULT 约束，请使用下面的 SQL：

```sql
MySQL:
ALTER TABLE 表名称 ALTER 列名称 SET DEFAULT '默认值'

SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 ALTER COLUMN 列名称 SET DEFAULT '默认值'
```

撤销 DEFAULT 约束，请使用下面的 SQL：

```sql
MySQL:
ALTER TABLE 表名称 ALTER 列名称 DROP DEFAULT

SQL Server / Oracle / MS Access:
ALTER TABLE 表名称 ALTER COLUMN 列名称 DROP DEFAULT
```

### 2.11 CREATE INDEX 语句

> **CREATE INDEX 语句用于在表中创建索引。**
>
> 在不读取整个表的情况下，索引使数据库应用程序可以更快地查找数据。

```sql
CREATE INDEX 索引名称 ON 表名称 (需要索引的列名称)
```

在表上创建一个唯一的索引。唯一的索引意味着两个行不能拥有相同的索引值。

```sql
CREATE UNIQUE INDEX 索引名称 ON 表名称 (需要索引的列名称)
```

您希望以*降序*索引某个列中的值，您可以在列名称之后添加保留字 *DESC*：

```sql
CREATE INDEX 索引名称 ON 表名称 (需要索引的列名称 DESC) 
```

您希望索引不止一个列，您可以在括号中列出这些列的名称，用逗号隔开：

```sql
CREATE INDEX 索引名称 ON 表名称 (需要索引的列名称1, 需要索引的列名称2)
```

### 2.12 DROP 语句，可以轻松地删除索引、表和数据库

DROP INDEX 命令删除表格中的索引

```
用于 Microsoft SQLJet (以及 Microsoft Access) 的语法:
DROP INDEX 索引名称  ON 表名称

用于 MS SQL Server 的语法:
DROP INDEX 表名称.索引名称

用于 IBM DB2 和 Oracle 语法:
DROP INDEX 索引名称

用于 MySQL 的语法:
ALTER TABLE 表名称 DROP INDEX 索引名称
```

DROP TABLE 语句用于删除表（表的结构、属性以及索引也会被删除）

```sql
DROP TABLE 表名称
```

DROP DATABASE 语句用于删除数据库

```sql
DROP DATABASE 数据库名称
```

如果我们仅仅需要除去表内的数据，但并不删除表本身,用 TRUNCATE TABLE 命令（仅仅删除表格中的数据）

```
TRUNCATE TABLE 表名称
```

### 2.13 ALTER TABLE 语句用于在已有的表中添加、修改或删除列

如需在表中添加列，请使用下列语法:

```sql
ALTER TABLE 表名称 ADD 列名称 列数据类型
```

要删除表中的列，请使用下列语法：

```sql
ALTER TABLE 表名称  DROP COLUMN 列名称
```

**注释：**某些数据库系统不允许这种在数据库表中删除列的方式 (DROP COLUMN column_name)。

要改变表中列的数据类型，请使用下列语法：

```sql
ALTER TABLE 表名称 ALTER COLUMN 列名称 列数据类型
```

### 2.14 Auto-increment 会在新记录插入表中时生成一个唯一的数字

> 我们通常希望在每次插入新记录时，自动地创建主键字段的值。
>
> 我们可以在表中创建一个 auto-increment 字段。

#### 用于 MySQL 的语法

```
...(
P_Id int NOT NULL AUTO_INCREMENT,
...
PRIMARY KEY (P_Id)
)...
```

MySQL 使用 AUTO_INCREMENT 关键字来执行 auto-increment 任务。

默认地，AUTO_INCREMENT 的开始值是 1，每条新记录递增 1。

要让 AUTO_INCREMENT 序列以其他的值起始，请使用下列 SQL 语法：

```
ALTER TABLE 表名称 AUTO_INCREMENT=100
```

#### 用于 SQL Server 的语法

下列 SQL 语句把 "Persons" 表中的 "P_Id" 列定义为 auto-increment 主键：

```
...(
P_Id int PRIMARY KEY IDENTITY,
...)...
```

MS SQL 使用 IDENTITY 关键字来执行 auto-increment 任务。

默认地，IDENTITY 的开始值是 1，每条新记录递增 1。

要规定 "P_Id" 列以 20 起始且递增 10，请把 identity 改为` IDENTITY(20,10)`

要在 "Persons" 表中插入新记录，我们不必为 "P_Id" 列规定值（会自动添加一个唯一的值）

#### 用于 Access 的语法

下列 SQL 语句把 "Persons" 表中的 "P_Id" 列定义为 auto-increment 主键：

```
...(
P_Id int PRIMARY KEY AUTOINCREMENT,
...)...
```

MS Access 使用 AUTOINCREMENT 关键字来执行 auto-increment 任务。

默认地，AUTOINCREMENT 的开始值是 1，每条新记录递增 1。

要规定 "P_Id" 列以 20 起始且递增 10，请把 autoincrement 改为` AUTOINCREMENT(20,10)`

要在 "Persons" 表中插入新记录，我们不必为 "P_Id" 列规定值（会自动添加一个唯一的值）

#### 用于 Oracle 的语法

在 Oracle 中，代码稍微复杂一点。

您必须通过 sequence 对创建 auto-increment 字段（该对象生成数字序列）。

请使用下面的 CREATE SEQUENCE 语法：

```sql
CREATE SEQUENCE 列名称 MINVALUE 1 START WITH 1 INCREMENT BY 1 CACHE 10
```

上面的代码创建名为 seq_person 的序列对象，它以 1 起始且以 1 递增。该对象缓存 10 个值以提高性能。CACHE 选项规定了为了提高访问速度要存储多少个序列值。

要在 "Persons" 表中插入新记录，我们必须使用 nextval 函数（该函数从 seq_person 序列中取回下一个值）

### 2.15 VIEW（视图）

#### 什么是视图？

在 SQL 中，视图是基于 SQL 语句的结果集的可视化的表。

视图包含行和列，就像一个真实的表。视图中的字段就是来自一个或多个数据库中的真实的表中的字段。我们可以向视图添加 SQL 函数、WHERE 以及 JOIN 语句，我们也可以提交数据，就像这些来自于某个单一的表。

**注释：**数据库的设计和结构不会受到视图中的函数、where 或 join 语句的影响。

#### SQL CREATE VIEW 语法

```sql
CREATE VIEW 视图名称 AS SELECT 列名称(s) FROM 表名称 WHERE condition
```

**注释：**视图总是显示最近的数据。每当用户查询视图时，数据库引擎通过使用 SQL 语句来重建数据。

#### SQL 更新视图

您可以使用下面的语法来更新视图：

```sql
SQL CREATE OR REPLACE VIEW Syntax CREATE OR REPLACE VIEW 视图名称 AS SELECT 列名称(s) FROM 表名称 WHERE condition
```

#### DROP VIEW 命令来删除视图。

```sql
SQL DROP VIEW Syntax DROP VIEW 视图名称
```

### 2.16 NULL 值

> 如果表中的某个列是可选的，那么我们可以在不向该列添加值的情况下插入新记录或更新已有的记录。这意味着该字段将以 NULL 值保存。
>
> NULL 值的处理方式与其他值不同。
>
> NULL 用作未知的或不适用的值的占位符。
>
> **注释：**无法比较 NULL 和 0；它们是不等价的

#### is null 列中带有 NULL 值的记录

```sql
SELECT 列名称(s) FROM 表名称 列名称 IS NULL
```

#### IS NOT NULL 列中不带有 NULL 值的记录

```sql
SELECT 列名称(s) FROM 表名称 列名称 IS NOT NULL
```

### 2.17 数据类型

#### Microsoft Access 数据类型

| 数据类型      | 描述                                                         | 存储     |
| :------------ | :----------------------------------------------------------- | :------- |
| Text          | 用于文本或文本与数字的组合。最多 255 个字符。                |          |
| Memo          | Memo 用于更大数量的文本。最多存储 65,536 个字符。注释：无法对 memo 字段进行排序。不过它们是可搜索的。 |          |
| Byte          | 允许 0 到 255 的数字。                                       | 1 字节   |
| Integer       | 允许介于 -32,768 到 32,767 之间的数字。                      | 2 字节   |
| Long          | 允许介于 -2,147,483,648 与 2,147,483,647 之间的全部数字      | 4 字节   |
| Single        | 单精度浮点。处理大多数小数。                                 | 4 字节   |
| Double        | 双精度浮点。处理大多数小数。                                 | 8 字节   |
| Currency      | 用于货币。支持 15 位的元，外加 4 位小数。提示：您可以选择使用哪个国家的货币。 | 8 字节   |
| AutoNumber    | AutoNumber 字段自动为每条记录分配数字，通常从 1 开始。       | 4 字节   |
| Date/Time     | 用于日期和时间                                               | 8 字节   |
| Yes/No        | 逻辑字段，可以显示为 Yes/No、True/False 或 On/Off。在代码中，使用常量 True 和 False （等价于 1 和 0）注释：Yes/No 字段中不允许 Null 值 | 1 比特   |
| Ole Object    | 可以存储图片、音频、视频或其他 BLOBs (Binary Large OBjects)  | 最多 1GB |
| Hyperlink     | 包含指向其他文件的链接，包括网页。                           |          |
| Lookup Wizard | 允许你创建一个可从下列列表中进行选择的选项列表。             | 4 字节   |

#### MySQL 数据类型

在 MySQL 中，有三种主要的类型：文本、数字和日期/时间类型。

##### Text 类型：

| 数据类型         | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| CHAR(size)       | 保存固定长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的长度。最多 255 个字符。 |
| VARCHAR(size)    | 保存可变长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的最大长度。最多 255 个字符。注释：如果值的长度大于 255，则被转换为 TEXT 类型。 |
| TINYTEXT         | 存放最大长度为 255 个字符的字符串。                          |
| TEXT             | 存放最大长度为 65,535 个字符的字符串。                       |
| BLOB             | 用于 BLOBs (Binary Large OBjects)。存放最多 65,535 字节的数据。 |
| MEDIUMTEXT       | 存放最大长度为 16,777,215 个字符的字符串。                   |
| MEDIUMBLOB       | 用于 BLOBs (Binary Large OBjects)。存放最多 16,777,215 字节的数据。 |
| LONGTEXT         | 存放最大长度为 4,294,967,295 个字符的字符串。                |
| LONGBLOB         | 用于 BLOBs (Binary Large OBjects)。存放最多 4,294,967,295 字节的数据。 |
| ENUM(x,y,z,etc.) | 允许你输入可能值的列表。可以在 ENUM 列表中列出最大 65535 个值。如果列表中不存在插入的值，则插入空值。注释：这些值是按照你输入的顺序存储的。可以按照此格式输入可能的值：ENUM('X','Y','Z') |
| SET              | 与 ENUM 类似，SET 最多只能包含 64 个列表项，不过 SET 可存储一个以上的值。 |

##### Number 类型：

| 数据类型        | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| TINYINT(size)   | -128 到 127 常规。0 到 255 无符号*。在括号中规定最大位数。   |
| SMALLINT(size)  | -32768 到 32767 常规。0 到 65535 无符号*。在括号中规定最大位数。 |
| MEDIUMINT(size) | -8388608 到 8388607 普通。0 to 16777215 无符号*。在括号中规定最大位数。 |
| INT(size)       | -2147483648 到 2147483647 常规。0 到 4294967295 无符号*。在括号中规定最大位数。 |
| BIGINT(size)    | -9223372036854775808 到 9223372036854775807 常规。0 到 18446744073709551615 无符号*。在括号中规定最大位数。 |
| FLOAT(size,d)   | 带有浮动小数点的小数字。在括号中规定最大位数。在 d 参数中规定小数点右侧的最大位数。 |
| DOUBLE(size,d)  | 带有浮动小数点的大数字。在括号中规定最大位数。在 d 参数中规定小数点右侧的最大位数。 |
| DECIMAL(size,d) | 作为字符串存储的 DOUBLE 类型，允许固定的小数点。             |

\* 这些整数类型拥有额外的选项 UNSIGNED。通常，整数可以是负数或正数。如果添加 UNSIGNED 属性，那么范围将从 0 开始，而不是某个负数。

##### Date 类型：

| 数据类型    | 描述                                                         |
| :---------- | :----------------------------------------------------------- |
| DATE()      | 日期。格式：YYYY-MM-DD注释：支持的范围是从 '1000-01-01' 到 '9999-12-31' |
| DATETIME()  | *日期和时间的组合。格式：YYYY-MM-DD HH:MM:SS注释：支持的范围是从 '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59' |
| TIMESTAMP() | *时间戳。TIMESTAMP 值使用 Unix 纪元('1970-01-01 00:00:00' UTC) 至今的描述来存储。格式：YYYY-MM-DD HH:MM:SS注释：支持的范围是从 '1970-01-01 00:00:01' UTC 到 '2038-01-09 03:14:07' UTC |
| TIME()      | 时间。格式：HH:MM:SS 注释：支持的范围是从 '-838:59:59' 到 '838:59:59' |
| YEAR()      | 2 位或 4 位格式的年。注释：4 位格式所允许的值：1901 到 2155。2 位格式所允许的值：70 到 69，表示从 1970 到 2069。 |

\* 即便 DATETIME 和 TIMESTAMP 返回相同的格式，它们的工作方式很不同。在 INSERT 或 UPDATE 查询中，TIMESTAMP 自动把自身设置为当前的日期和时间。TIMESTAMP 也接受不同的格式，比如 YYYYMMDDHHMMSS、YYMMDDHHMMSS、YYYYMMDD 或 YYMMDD。

#### SQL Server 数据类型

##### Character 字符串：

| 数据类型     | 描述                                          | 存储 |
| :----------- | :-------------------------------------------- | :--- |
| char(n)      | 固定长度的字符串。最多 8,000 个字符。         | n    |
| varchar(n)   | 可变长度的字符串。最多 8,000 个字符。         |      |
| varchar(max) | 可变长度的字符串。最多 1,073,741,824 个字符。 |      |
| text         | 可变长度的字符串。最多 2GB 字符数据。         |      |

##### Unicode 字符串：

| 数据类型      | 描述                                               | 存储 |
| :------------ | :------------------------------------------------- | :--- |
| nchar(n)      | 固定长度的 Unicode 数据。最多 4,000 个字符。       |      |
| nvarchar(n)   | 可变长度的 Unicode 数据。最多 4,000 个字符。       |      |
| nvarchar(max) | 可变长度的 Unicode 数据。最多 536,870,912 个字符。 |      |
| ntext         | 可变长度的 Unicode 数据。最多 2GB 字符数据。       |      |

##### Binary 类型：

| 数据类型       | 描述                                    | 存储 |
| :------------- | :-------------------------------------- | :--- |
| bit            | 允许 0、1 或 NULL                       |      |
| binary(n)      | 固定长度的二进制数据。最多 8,000 字节。 |      |
| varbinary(n)   | 可变长度的二进制数据。最多 8,000 字节。 |      |
| varbinary(max) | 可变长度的二进制数据。最多 2GB 字节。   |      |
| image          | 可变长度的二进制数据。最多 2GB。        |      |

##### Number 类型：

| 数据类型     | 描述                                                         | 存储        |
| :----------- | :----------------------------------------------------------- | :---------- |
| tinyint      | 允许从 0 到 255 的所有数字。                                 | 1 字节      |
| smallint     | 允许从 -32,768 到 32,767 的所有数字。                        | 2 字节      |
| int          | 允许从 -2,147,483,648 到 2,147,483,647 的所有数字。          | 4 字节      |
| bigint       | 允许介于 -9,223,372,036,854,775,808 和 9,223,372,036,854,775,807 之间的所有数字。 | 8 字节      |
| decimal(p,s) | 固定精度和比例的数字。允许从 -10^38 +1 到 10^38 -1 之间的数字。p 参数指示可以存储的最大位数（小数点左侧和右侧）。p 必须是 1 到 38 之间的值。默认是 18。s 参数指示小数点右侧存储的最大位数。s 必须是 0 到 p 之间的值。默认是 0。 | 5-17 字节   |
| numeric(p,s) | 固定精度和比例的数字。允许从 -10^38 +1 到 10^38 -1 之间的数字。p 参数指示可以存储的最大位数（小数点左侧和右侧）。p 必须是 1 到 38 之间的值。默认是 18。s 参数指示小数点右侧存储的最大位数。s 必须是 0 到 p 之间的值。默认是 0。 | 5-17 字节   |
| smallmoney   | 介于 -214,748.3648 和 214,748.3647 之间的货币数据。          | 4 字节      |
| money        | 介于 -922,337,203,685,477.5808 和 922,337,203,685,477.5807 之间的货币数据。 | 8 字节      |
| float(n)     | 从 -1.79E + 308 到 1.79E + 308 的浮动精度数字数据。 参数 n 指示该字段保存 4 字节还是 8 字节。float(24) 保存 4 字节，而 float(53) 保存 8 字节。n 的默认值是 53。 | 4 或 8 字节 |
| real         | 从 -3.40E + 38 到 3.40E + 38 的浮动精度数字数据。            | 4 字节      |

##### Date 类型：

| 数据类型       | 描述                                                         | 存储       |
| :------------- | :----------------------------------------------------------- | :--------- |
| datetime       | 从 1753 年 1 月 1 日 到 9999 年 12 月 31 日，精度为 3.33 毫秒。 | 8 bytes    |
| datetime2      | 从 1753 年 1 月 1 日 到 9999 年 12 月 31 日，精度为 100 纳秒。 | 6-8 bytes  |
| smalldatetime  | 从 1900 年 1 月 1 日 到 2079 年 6 月 6 日，精度为 1 分钟。   | 4 bytes    |
| date           | 仅存储日期。从 0001 年 1 月 1 日 到 9999 年 12 月 31 日。    | 3 bytes    |
| time           | 仅存储时间。精度为 100 纳秒。                                | 3-5 bytes  |
| datetimeoffset | 与 datetime2 相同，外加时区偏移。                            | 8-10 bytes |
| timestamp      | 存储唯一的数字，每当创建或修改某行时，该数字会更新。timestamp 基于内部时钟，不对应真实时间。每个表只能有一个 timestamp 变量。 |            |

##### 其他数据类型：

| 数据类型         | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| sql_variant      | 存储最多 8,000 字节不同数据类型的数据，除了 text、ntext 以及 timestamp。 |
| uniqueidentifier | 存储全局标识符 (GUID)。                                      |
| xml              | 存储 XML 格式化数据。最多 2GB。                              |
| cursor           | 存储对用于数据库操作的指针的引用。                           |
| table            | 存储结果集，供稍后处理。                                     |

### 2.18 服务器 - RDBMS

现代的 SQL 服务器构建在 RDBMS 之上。

#### DBMS - 数据库管理系统（Database Management System）

数据库管理系统是一种可以访问数据库中数据的计算机程序。

DBMS 使我们有能力在数据库中提取、修改或者存贮信息。

不同的 DBMS 提供不同的函数供查询、提交以及修改数据。

#### RDBMS - 关系数据库管理系统（Relational Database Management System）

关系数据库管理系统 (RDBMS) 也是一种数据库管理系统，其数据库是根据数据间的关系来组织和访问数据的。

20 世纪 70 年代初，IBM 公司发明了 RDBMS。

RDBMS 是 SQL 的基础，也是所有现代数据库系统诸如 Oracle、SQL Server、IBM DB2、Sybase、MySQL 以及 Microsoft Access 的基础。

## 3 SQL函数

```
SELECT function(列) FROM 表
```

函数的基本类型是：

- Aggregate 函数
- Scalar 函数

#### 合计函数（Aggregate functions）

Aggregate 函数的操作面向一系列的值，并返回一个单一的值。

**注释：**如果在 SELECT 语句的项目列表中的众多其它表达式中使用 SELECT 语句，则这个 SELECT 必须使用 GROUP BY 语句！

#### "Persons" table (在大部分的例子中使用过)

| Name           | Age  |
| :------------- | :--- |
| Adams, John    | 38   |
| Bush, George   | 33   |
| Carter, Thomas | 28   |

#### MS Access 中的合计函数

| 函数           | 描述                             |
| :------------- | :------------------------------- |
| AVG(column)    | 返回某列的平均值                 |
| COUNT(column)  | 返回某列的行数（不包括 NULL 值） |
| COUNT(*)       | 返回被选行数                     |
| FIRST(column)  | 返回在指定的域中第一个记录的值   |
| LAST(column)   | 返回在指定的域中最后一个记录的值 |
| MAX(column)    | 返回某列的最高值                 |
| MIN(column)    | 返回某列的最低值                 |
| STDEV(column)  |                                  |
| STDEVP(column) |                                  |
| SUM(column)    | 返回某列的总和                   |
| VAR(column)    |                                  |
| VARP(column)   |                                  |

### 在 SQL Server 中的合计函数

| 函数                   | 描述                                                     |
| :--------------------- | :------------------------------------------------------- |
| AVG(column)            | 返回某列的平均值                                         |
| BINARY_CHECKSUM        |                                                          |
| CHECKSUM               |                                                          |
| CHECKSUM_AGG           |                                                          |
| COUNT(column)          | 返回某列的行数（不包括NULL值）                           |
| COUNT(*)               | 返回被选行数                                             |
| COUNT(DISTINCT column) | 返回相异结果的数目                                       |
| FIRST(column)          | 返回在指定的域中第一个记录的值（SQLServer2000 不支持）   |
| LAST(column)           | 返回在指定的域中最后一个记录的值（SQLServer2000 不支持） |
| MAX(column)            | 返回某列的最高值                                         |
| MIN(column)            | 返回某列的最低值                                         |
| STDEV(column)          |                                                          |
| STDEVP(column)         |                                                          |
| SUM(column)]           | 返回某列的总和                                           |
| VAR(column)            |                                                          |
| VARP(column)           |                                                          |

## Scalar 函数

Scalar 函数的操作面向某个单一的值，并返回基于输入值的一个单一的值。

### MS Access 中的 Scalar 函数

| 函数                    | 描述                                   |
| :---------------------- | :------------------------------------- |
| UCASE(c)                | 将某个域转换为大写                     |
| LCASE(c)                | 将某个域转换为小写                     |
| MID(c,start[,end])      | 从某个文本域提取字符                   |
| LEN(c)                  | 返回某个文本域的长度                   |
| INSTR(c,char)           | 返回在某个文本域中指定字符的数值位置   |
| LEFT(c,number_of_char)  | 返回某个被请求的文本域的左侧部分       |
| RIGHT(c,number_of_char) | 返回某个被请求的文本域的右侧部分       |
| ROUND(c,decimals)       | 对某个数值域进行指定小数位数的四舍五入 |
| MOD(x,y)                | 返回除法操作的余数                     |
| NOW()                   | 返回当前的系统日期                     |
| FORMAT(c,format)        | 改变某个域的显示方式                   |
| DATEDIFF(d,date1,date2) | 用于执行日期计算                       |

### 3.1 Date 函数

#### MySQL Date 函数

下面的表格列出了 MySQL 中最重要的内建日期函数：

| 函数          | 描述                                |
| :------------ | :---------------------------------- |
| NOW()         | 返回当前的日期和时间                |
| CURDATE()     | 返回当前的日期                      |
| CURTIME()     | 返回当前的时间                      |
| DATE()        | 提取日期或日期/时间表达式的日期部分 |
| EXTRACT()     | 返回日期/时间按的单独部分           |
| DATE_ADD()    | 给日期添加指定的时间间隔            |
| DATE_SUB()    | 从日期减去指定的时间间隔            |
| DATEDIFF()    | 返回两个日期之间的天数              |
| DATE_FORMAT() | 用不同的格式显示日期/时间           |

#### SQL Server Date 函数

下面的表格列出了 SQL Server 中最重要的内建日期函数：

| 函数       | 描述                             |
| :--------- | :------------------------------- |
| GETDATE()  | 返回当前日期和时间               |
| DATEPART() | 返回日期/时间的单独部分          |
| DATEADD()  | 在日期中添加或减去指定的时间间隔 |
| DATEDIFF() | 返回两个日期之间的时间           |
| CONVERT()  | 用不同的格式显示日期/时间        |

#### SQL Date 数据类型

MySQL 使用下列数据类型在数据库中存储日期或日期/时间值：

- DATE - 格式 YYYY-MM-DD
- DATETIME - 格式: YYYY-MM-DD HH:MM:SS
- TIMESTAMP - 格式: YYYY-MM-DD HH:MM:SS
- YEAR - 格式 YYYY 或 YY

SQL Server 使用下列数据类型在数据库中存储日期或日期/时间值：

- DATE - 格式 YYYY-MM-DD
- DATETIME - 格式: YYYY-MM-DD HH:MM:SS
- SMALLDATETIME - 格式: YYYY-MM-DD HH:MM:SS
- TIMESTAMP - 格式: 唯一的数字

#### SQL 日期处理

如果不涉及时间部分，那么我们可以轻松地比较两个日期！

假设我们有下面这个 "Orders" 表：

| OrderId | ProductName  | OrderDate  |
| :------ | :----------- | :--------- |
| 1       | computer     | 2008-12-26 |
| 2       | printer      | 2008-12-26 |
| 3       | electrograph | 2008-11-12 |
| 4       | telephone    | 2008-10-19 |

现在，我们希望从上表中选取 OrderDate 为 "2008-12-26" 的记录。

我们使用如下 SELECT 语句：

```
SELECT * FROM 表名称 WHERE 列名称='2008-12-26'
```

结果集：

| OrderId | ProductName  | OrderDate  |
| :------ | :----------- | :--------- |
| 1       | computer     | 2008-12-26 |
| 3       | electrograph | 2008-12-26 |

现在假设 "Orders" 类似这样（请注意 "OrderDate" 列中的时间部分）：

| OrderId | ProductName  | OrderDate           |
| :------ | :----------- | :------------------ |
| 1       | computer     | 2008-12-26 16:23:55 |
| 2       | printer      | 2008-12-26 10:45:26 |
| 3       | electrograph | 2008-11-12 14:12:08 |
| 4       | telephone    | 2008-10-19 12:56:10 |

如果我们使用上面的 SELECT 语句：

```
SELECT * FROM 表名称 WHERE 列名称='2008-12-26'
```

那么我们得不到结果。这是由于该查询不含有时间部分的日期。

**提示：**如果您希望使查询简单且更易维护，那么请不要在日期中使用时间部分！

### 3.2 NULL 函数

#### SQL Server / MS Access

```
SELECT ProductName,UnitPrice*(UnitsInStock+ISNULL(列名称,0))
FROM Products
```

#### Oracle

Oracle 没有 ISNULL() 函数。不过，我们可以使用 NVL() 函数达到相同的结果：

```
SELECT ProductName,UnitPrice*(UnitsInStock+NVL(列名称,0))
FROM Products
```

#### MySQL

MySQL 也拥有类似 ISNULL() 的函数。不过它的工作方式与微软的 ISNULL() 函数有点不同。

在 MySQL 中，我们可以使用 IFNULL() 函数，就像这样：

```
SELECT ProductName,UnitPrice*(UnitsInStock+IFNULL(列名称,0))
FROM Products
```

或者我们可以使用 COALESCE() 函数，就像这样：

```
SELECT ProductName,UnitPrice*(UnitsInStock+COALESCE(列名称,0))
FROM Products
```

### 3.3 AVG 函数 

AVG 函数返回数值列的平均值。NULL 值不包括在计算中。

```sql
SELECT AVG(列名称) FROM 表名称
```

### 3.4 COUNT() 函数

**COUNT() 函数返回匹配指定条件的行数。**

```
SELECT COUNT(列名称) FROM 表名称

SELECT COUNT(*) FROM 表名称

COUNT(DISTINCT column_name) 函数返回指定列的不同值的数目：
SELECT COUNT(DISTINCT 列名称) FROM 表名称
注释：COUNT(DISTINCT) 适用于 ORACLE 和 Microsoft SQL Server，但是无法用于 Microsoft Access。
```

### 3.5 FIRST() 函数

FIRST() 函数返回指定的字段中第一个记录的值。

**提示：**可使用 ORDER BY 语句对记录进行排序。

```
SELECT FIRST(列名称) FROM 表名称
```

### 3.6 LAST() 函数

LAST() 函数返回指定的字段中最后一个记录的值。

**提示：**可使用 ORDER BY 语句对记录进行排序。

```
SELECT LAST(列名称) FROM 表名称
```

### 3.7 MAX() 函数

MAX 函数返回一列中的最大值。NULL 值不包括在计算中。

```
SELECT MAX(列名称) FROM 表名称
```

### 3.8 MIN() 函数

MIN 函数返回一列中的最小值。NULL 值不包括在计算中

```
SELECT MIN(列名称) FROM 表名称
```

### 3.9 SUM() 函数

SUM 函数返回数值列的总数（总额）。

```
SELECT SUM(列名称) FROM 表名称
```

### 3.9 GROUP BY 语句

GROUP BY 语句用于结合合计函数，根据一个或多个列对结果集进行分组。

```sql
SELECT 列名称, aggregate_function(列名称) FROM 表名称 WHERE 列名称 operator value
GROUP BY 列名称
```

### 3.10 HAVING 子句

在 SQL 中增加 HAVING 子句原因是，WHERE 关键字无法与合计函数一起使用。

```sql
SELECT 列名称, aggregate_function(列名称) FROM 表名称 WHERE 列名称 operator value
GROUP BY 列名称 HAVING aggregate_function(列名称) operator value
```

### 3.11 UCASE() 函数

UCASE 函数把字段的值转换为大写。

```
SELECT UCASE(列名称) FROM 表名称
```

### 3.12 LCASE() 函数

LCASE 函数把字段的值转换为小写。

```
SELECT LCASE(列名称) FROM 表名称
```

### 3.13 MID() 函数

MID 函数用于从文本字段中提取字符。

```
SELECT MID(列名称,start[,length]) FROM 表名称
```

### 3.14 LEN() 函数

LEN 函数返回文本字段中值的长度。

```
SELECT LEN(列名称) FROM 表名称
```

### 3.15 ROUND() 函数

ROUND 函数用于把数值字段舍入为指定的小数位数。

```
SELECT ROUND(列名称,decimals) FROM 表名称
```

### 3.16 NOW() 函数

NOW 函数返回当前的日期和时间。

**提示：**如果您在使用 Sql Server 数据库，请使用 getdate() 函数来获得当前的日期时间。

```
SELECT NOW() FROM 表名称
```

### 3.17 FORMAT() 函数

FORMAT 函数用于对字段的显示进行格式化。

```
SELECT FORMAT(列名称,format) FROM 表名称
```

## 4 SQL 快速参考

## SQL 语句

| 语句                                                    | 语法                                                         |
| :------------------------------------------------------ | :----------------------------------------------------------- |
| AND / OR                                                | SELECT 列名称(s) FROM 表名称 WHERE condition AND\|OR condition |
| ALTER TABLE (add column)                                | ALTER TABLE 表名称 ADD 列名称 列类型                         |
| ALTER TABLE (drop column)                               | ALTER TABLE 表名称 DROP COLUMN 列名称                        |
| AS (alias for column)                                   | SELECT 列名称 AS 列别名 FROM 表名称                          |
| AS (alias for table)                                    | SELECT 列名称 FROM table_name AS table_alias                 |
| BETWEEN                                                 | SELECT 列名称(s) FROM 表名称 WHERE 列名称 BETWEEN value1 AND value2 |
| CREATE DATABASE                                         | CREATE DATABASE 数据库名称                                   |
| CREATE INDEX                                            | CREATE INDEX 主键名称 ON 表名称(列名称)                      |
| CREATE TABLE                                            | CREATE TABLE 表名称( 列名称1 列数据类型, 列名称2 列数据类型, ....... ) |
| CREATE UNIQUE INDEX                                     | CREATE UNIQUE INDEX 主键名称 ON 表名称(列名称)               |
| CREATE VIEW                                             | CREATE VIEW 视图名称 AS SELECT 列名称(s) FROM 表名称 WHERE condition |
| DELETE FROM                                             | DELETE FROM 表名称(**Note:** Deletes the entire table!!) *or* DELETE FROM 表名称 WHERE condition |
| DROP DATABASE                                           | DROP DATABASE 数据库名称                                     |
| DROP INDEX                                              | DROP INDEX 表名称.主键名称                                   |
| DROP TABLE                                              | DROP TABLE 表名称                                            |
| GROUP BY                                                | SELECT 列名称1,SUM(列名称2) FROM 表名称 GROUP BY 列名称1     |
| HAVING                                                  | SELECT 列名称1,SUM(列名称2) FROM 表名称  GROUP BY 列名称1 HAVING SUM(列名称2) condition value |
| IN                                                      | SELECT 列名称(s) FROM 表名称 WHERE 列名称 IN (value1,value2,..) |
| INSERT INTO                                             | INSERT INTO 表名称 VALUES (value1, value2,....)*or*INSERT INTO table_name (列名称1, 列名称2,...) VALUES (value1, value2,....) |
| LIKE                                                    | SELECT 列名称(s) FROM 表名称 WHERE 列名称 LIKE pattern       |
| ORDER BY                                                | SELECT column_name(s) FROM table_name ORDER BY 列名称 [ASC\|DESC] |
| SELECT                                                  | SELECT 列名称(s) FROM 表名称                                 |
| SELECT *                                                | SELECT * FROM 表名称                                         |
| SELECT DISTINCT                                         | SELECT DISTINCT 列名称(s) FROM 表名称                        |
| SELECT INTO (used to create backup copies of tables)    | SELECT * INTO 新表名称 FROM 旧表名称 or* SELECT 列名称(s) INTO 新表名称 FROM 旧表名称 |
| TRUNCATE TABLE (deletes only the data inside the table) | TRUNCATE TABLE 表名称                                        |
| UPDATE                                                  | UPDATE 表名称SET 列名称=new_value [, 列名称=new_value] WHERE 列名称=some_value |
| WHERE                                                   | SELECT 列名称(s) FROM 表名称 WHERE condition                 |