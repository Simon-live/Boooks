# Data Define Languge

### DDL语句

#### 库和表的管理

库的管理：

```text
一、创建库
create database 库名
二、删除库
drop database 库名
```

表的管理：

```text
#1.创建表

CREATE TABLE IF NOT EXISTS stuinfo(
    stuId INT,
    stuName VARCHAR(20),
    gender CHAR,
    bornDate DATETIME


);

DESC studentinfo;
#2.修改表 alter
语法：ALTER TABLE 表名 ADD|MODIFY|DROP|CHANGE COLUMN 字段名 【字段类型】;

#①修改字段名
ALTER TABLE studentinfo CHANGE  COLUMN sex gender CHAR;

#②修改表名
ALTER TABLE stuinfo RENAME [TO]  studentinfo;
#③修改字段类型和列级约束
ALTER TABLE studentinfo MODIFY COLUMN borndate DATE ;

#④添加字段

ALTER TABLE studentinfo ADD COLUMN email VARCHAR(20) first;
#⑤删除字段
ALTER TABLE studentinfo DROP COLUMN email;


#3.删除表

DROP TABLE [IF EXISTS] studentinfo;
```

#### 常见类型

```text
整型：

小数：
    浮点型
    定点型
字符型：
日期型：
Blob类型：
```

#### 常见约束

```text
NOT NULL
DEFAULT
UNIQUE
CHECK
PRIMARY KEY
FOREIGN KEY
```

