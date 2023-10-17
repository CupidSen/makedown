## SQL通用语法

1. SQL语法可以单行或多行书写，以分号结尾。
2. SQL语句可以使用空格/缩进来增强语句的可读性。
3. MySQL数据库的SQL语句不区分大小写，关键字建议使用大写。
4. 注释：

- 单行注释：--注释内容 或者#注释内容（MySQL特有）
- 多行注释：/* 注释内容 */

## 数据类型

**数值类型**

|     类型     |              大小              |    描述    |
| :----------: | :----------------------------: | :--------: |
|   TINYINT    |             1 byte             |   小整数   |
|   SMALLINT   |            2 bytes             |   大整数   |
|  MEDIUMINT   |            3 bytes             |   大整数   |
| INT或INTEGER |            4 bytes             |   大整数   |
|    BIGINT    |            8 bytes             |  极大整数  |
|    FLOAT     |            4 bytes             | 单精度浮点 |
|    DOUBLE    |            8 bytes             | 双精度浮点 |
|   DECIMAL    | 依赖于M（精度）和D（标准）的值 | 精确浮点数 |

==数值类型分为有符号(SIGNED)与无符号(UNSIGNED)，无符号就是没有负数==

==当数值类型不需要负数的时候，在字段类型后添加UNSIGNED==

**数值类型**

|    类型    |         大小          |            描述             |
| :--------: | :-------------------: | :-------------------------: |
|    CHAR    |      0-255 bytes      |         定长字符串          |
|  VARCHAR   |     0-65535 bytes     |         变长字符串          |
|  TINYBLOB  |      0-255 bytes      | 不超过255个字符的二进制数据 |
|  TINYTEXT  |      0-255 bytes      |        短文本字符串         |
|    BLOB    |    0-65 535 bytes     |  二进制形式的长文本字符串   |
|    TEXT    |    0-65 535 bytes     |        长文本字符串         |
| MEDIUMBLOB |    0-16 777 bytes     | 二进制形式的中长文本字符串  |
| MEDIUMTEXT |    0-16 777 bytes     |       中长文本字符串        |
|  LONGBLOB  | 0-4 294 967 295 bytes | 二进制形式的极长文本字符串  |
|  LONGTEXT  | 0-4 294 967 295 bytes |       极长文本字符串        |

**日期时间类型**

|   类型    |                  大小范围                  |        格式         |        描述        |
| :-------: | :----------------------------------------: | :-----------------: | :----------------: |
|   DATE    |         3 1000-01-01 至 9999-12-31         |     YYYY-MM-DD      |       日期值       |
|   TIME    |          -838:59:59 至 838:59:59           |      HH:MM:SS       | 时间值或持续时间值 |
|   YEAR    |                1901 至 2155                |        YYYY         |       年份值       |
| DATETIME  | 1000-01-01 00:00:00 至 9999-12-31 23:59:59 | YYYY-MM-DD HH:MM:SS |  混合日期和时间值  |
| TIMESTAMP | 1970-01-01 00:00:01 至 2038-01-19 03:14:07 | YYYY-MM-DD HH:MM:SS |       时间戳       |

## DDL

1. DDL-数据库操作

- SHOW DATABASES； 查看当前存在的数据库
- CREATE DATABASE [IF NOT EXISTS] 数据库名[DEFAULT CHARSET]；创建数据库 
- USE 数据库名；切换使用某一个数据库
- SELECT DATABASE()；查看当前使用的是那个数据库
- DROP DATABASE [IF EXISTS] 数据库名；删除某个数据库

2. DDL-表操作

- SHOW TABLES：查看当前数据库所有的表

- CREATE TABLE 表名 (字段 字段类型，字段 字段类型); ：创建表

  > CREATE TABLE 表名(
  >
  > ​			字段1 字段1类型[COMMENT 字段1注释]，
  >
  > ​			字段2 字段2类型[COMMENT 字段2注释]，
  >
  > ​			字段3 字段3类型[COMMENT 字段3注释]
  >
  > )[COMMENT 表注释]；

- DESC 表名：查看表中的字段

- SHOW CREATE TABLE 表名：查看这张表的建表语句

- ALTER TABLE 表名 ADD 字段名 字段类型：在表中添加字段

- ALTER TABLE 表名 MODIFY 字段名  新字段类型：修改字段类型

- ALTER TABLE 表名 CHANGE 旧字段名 新字段名 字段类型：修改字段名和字段类型

- ALTER TABLE 表名 DROP 字段名：删除字段

- ALTER TABLE 表名 RENAME TO 新表名：修改表名

- DROP TABLE[IF EXISTS] 表名：删除表

- TRUNCATE TABLE 表名：删除表并重新创建该表

## INSERT（添加）

INSERT INTO 表名（字段1，字段2，...）VALUES (值1，值2，...);

INSERT INTO 表名VALUES (值1，值2，...);

INSERT INTO 表名（字段1，字段2，...）VALUES (值1，值2，...),(值1，值2，...);

INSERT INTO 表名 VALUES (值1，值2，...),(值1，值2，...);

==注意== 

- 插入数据时，指定的字段顺序需要与值的顺序是一一对应的
- 字符串和日期型数据因该包含在引号中
- 插入的数据大小，应该在字段的规定范围内

## UPDATE （修改）

UPDATE 表名 SET 字段名1 = 值一，字段名2 = 值2，.....[WHERE 条件]；

==修改语句的条件可以有，也可以没有，如果没有则会修改整张表的数据==

## DELETE FROM (删除)

DELETE FROM 表名 [WHERE 条件]

==注意==

- DELETE语句的条件可以有也可以没有，如果没有就是删除整张表的数据
- DELETE语句不能删除某一个字段，如果想删除某一个字段可以把那个字段的值修改为空