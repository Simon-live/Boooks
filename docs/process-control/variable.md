# Variable

#### 系统变量

一、全局变量

作用域：针对于所有会话（连接）有效，但不能跨重启

```text
查看所有全局变量
SHOW GLOBAL VARIABLES;
查看满足条件的部分系统变量
SHOW GLOBAL VARIABLES LIKE '%char%';
查看指定的系统变量的值
SELECT @@global.autocommit;
为某个系统变量赋值
SET @@global.autocommit=0;
SET GLOBAL autocommit=0;
```

二、会话变量

作用域：针对于当前会话（连接）有效

```text
查看所有会话变量
SHOW SESSION VARIABLES;
查看满足条件的部分会话变量
SHOW SESSION VARIABLES LIKE '%char%';
查看指定的会话变量的值
SELECT @@autocommit;
SELECT @@session.tx_isolation;
为某个会话变量赋值
SET @@session.tx_isolation='read-uncommitted';
SET SESSION tx_isolation='read-committed';
```

#### 自定义变量

一、用户变量

声明并初始化：

```text
SET @变量名=值;
SET @变量名:=值;
SELECT @变量名:=值;
```

赋值：

```text
方式一：一般用于赋简单的值
SET 变量名=值;
SET 变量名:=值;
SELECT 变量名:=值;


方式二：一般用于赋表 中的字段值
SELECT 字段名或表达式 INTO 变量
FROM 表;
```

使用：

```text
select @变量名;
```

二、局部变量

声明：

```text
declare 变量名 类型 【default 值】;
```

赋值：

```text
方式一：一般用于赋简单的值
SET 变量名=值;
SET 变量名:=值;
SELECT 变量名:=值;


方式二：一般用于赋表 中的字段值
SELECT 字段名或表达式 INTO 变量
FROM 表;
```

使用：

```text
select 变量名
```

二者的区别：

```text
        作用域            定义位置        语法
```

用户变量 当前会话 会话的任何地方 加@符号，不用指定类型 局部变量 定义它的BEGIN END中 BEGIN END的第一句话 一般不用加@,需要指定类型

