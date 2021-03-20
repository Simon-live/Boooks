# Stored Procedure

### 存储过程

含义：一组经过预先编译的sql语句的集合 好处：

```text
1、提高了sql语句的重用性，减少了开发程序员的压力
2、提高了效率
3、减少了传输次数
```

分类：

```text
1、无返回无参
2、仅仅带in类型，无返回有参
3、仅仅带out类型，有返回无参
4、既带in又带out，有返回有参
5、带inout，有返回有参
注意：in、out、inout都可以在一个存储过程中带多个
```

#### 创建存储过程

语法：

```text
create procedure 存储过程名(in|out|inout 参数名  参数类型,...)
begin
    存储过程体

end
```

类似于方法：

```text
修饰符 返回类型 方法名(参数类型 参数名,...){

    方法体;
}
```

注意

```text
1、需要设置新的结束标记
delimiter 新的结束标记
示例：
delimiter $

CREATE PROCEDURE 存储过程名(IN|OUT|INOUT 参数名  参数类型,...)
BEGIN
    sql语句1;
    sql语句2;

END $

2、存储过程体中可以有多条sql语句，如果仅仅一条sql语句，则可以省略begin end

3、参数前面的符号的意思
in:该参数只能作为输入 （该参数不能做返回值）
out：该参数只能作为输出（该参数只能做返回值）
inout：既能做输入又能做输出
```

## 调用存储过程

```text
call 存储过程名(实参列表)
```

### 函数

#### 创建函数

学过的函数：LENGTH、SUBSTR、CONCAT等 语法：

```text
CREATE FUNCTION 函数名(参数名 参数类型,...) RETURNS 返回类型
BEGIN
    函数体

END
```

#### 调用函数

```text
SELECT 函数名（实参列表）
```

#### 函数和存储过程的区别

```text
        关键字        调用语法    返回值            应用场景
函数        FUNCTION    SELECT 函数()    只能是一个        一般用于查询结果为一个值并返回时，当有返回值而且仅仅一个
存储过程    PROCEDURE    CALL 存储过程()    可以有0个或多个        一般用于更新
```

