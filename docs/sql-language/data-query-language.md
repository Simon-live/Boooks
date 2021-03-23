# Data Query Language

## 进阶1：基础查询

1. 通过select查询完的结果 ，是一个虚拟的表格，不是真实存在
2. 要查询的东西 可以是常量值、可以是表达式、可以是字段、可以是函数

```sql
SELECT 要查询的东西
[FROM 表名];
```

## 进阶2：条件查询

{% hint style="info" %}
根据条件过滤原始表的数据，查询到想要的数据
{% endhint %}

```sql
select 
    要查询的字段|表达式|常量值|函数
from 
    表
where 
    条件 ;

三、模糊查询
示例：last_name like 'a%'
```

### 条件语句查询

```sql
where 
    salary>10000;
```

#### 条件查询语句的运算符

大于 `>` , 小于 `<` , 大于等于 `>=` , 小于等于 `<=` , 等于 `=` , 不等于`<>` \(不推荐使用 `!=` \)

### 逻辑语句查询

```sql
where 
    salary>10000 && salary<20000;
```

#### 逻辑查询语句的运算符

| 运算符 | 描述 |
| :--- | :--- |
| and `&&` | 两个条件如果同时成立，结果为true，否则为false |
| or `||` | 两个条件只要有一个成立，结果为true，否则为false |
| not `!` | 如果条件成立，则not后为false，否则为true |

### 模糊查询

```sql
where 
    last_name like 'a%';
```

## 进阶3：排序查询

```text
语法：
select
    要查询的东西
from
    表
where 
    条件

order by 排序的字段|表达式|函数|别名 【asc|desc】
```

## 进阶4：常见函数

### 一、单行函数

```text
1、字符函数
    concat拼接
    substr截取子串
    upper转换成大写
    lower转换成小写
    trim去前后指定的空格和字符
    ltrim去左边空格
    rtrim去右边空格
    replace替换
    lpad左填充
    rpad右填充
    instr返回子串第一次出现的索引
    length 获取字节个数

2、数学函数
    round 四舍五入
    rand 随机数
    floor向下取整
    ceil向上取整
    mod取余
    truncate截断
3、日期函数
    now当前系统日期+时间
    curdate当前系统日期
    curtime当前系统时间
    str_to_date 将字符转换成日期
    date_format将日期转换成字符
4、流程控制函数
    if 处理双分支
    case语句 处理多分支
        情况1：处理等值判断
        情况2：处理条件判断

5、其他函数
    version版本
    database当前库
    user当前连接用户
```

### 二、分组函数

```text
    sum 求和
    max 最大值
    min 最小值
    avg 平均值
    count 计数

    特点：
    1、以上五个分组函数都忽略null值，除了count(*)
    2、sum和avg一般用于处理数值型
        max、min、count可以处理任何数据类型
    3、都可以搭配distinct使用，用于统计去重后的结果
    4、count的参数可以支持：
        字段、*、常量值，一般放1

       建议使用 count(*)
```

## 进阶5：分组查询

```text
语法：
select 查询的字段，分组函数
from 表
group by 分组的字段


特点：
1、可以按单个字段分组
2、和分组函数一同查询的字段最好是分组后的字段
3、分组筛选
        针对的表    位置            关键字
分组前筛选：    原始表        group by的前面        where
分组后筛选：    分组后的结果集    group by的后面        having

4、可以按多个字段分组，字段之间用逗号隔开
5、可以支持排序
6、having后可以支持别名
```

## 进阶6：多表连接查询

```text
笛卡尔乘积：如果连接条件省略或无效则会出现
解决办法：添加上连接条件
```

### 一、传统模式下的连接 ：等值连接——非等值连接

```text
1.等值连接的结果 = 多个表的交集
2.n表连接，至少需要n-1个连接条件
3.多个表不分主次，没有顺序要求
4.一般为表起别名，提高阅读性和性能
```

### 二、sql99语法：通过join关键字实现连接

```text
含义：1999年推出的sql语法
支持：
等值连接、非等值连接 （内连接）
外连接
交叉连接

语法：

select 字段，...
from 表1
【inner|left outer|right outer|cross】join 表2 on  连接条件
【inner|left outer|right outer|cross】join 表3 on  连接条件
【where 筛选条件】
【group by 分组字段】
【having 分组后的筛选条件】
【order by 排序的字段或表达式】

好处：语句上，连接条件和筛选条件实现了分离，简洁明了！
```

三、自连接

案例：查询员工名和直接上级的名称

sql99

```text
SELECT e.last_name,m.last_name
FROM employees e
JOIN employees m ON e.`manager_id`=m.`employee_id`;
```

sql92

```text
SELECT e.last_name,m.last_name
FROM employees e,employees m 
WHERE e.`manager_id`=m.`employee_id`;
```

## 进阶7：子查询

含义：

```text
一条查询语句中又嵌套了另一条完整的select语句，其中被嵌套的select语句，称为子查询或内查询
在外面的查询语句，称为主查询或外查询
```

特点：

```text
1、子查询都放在小括号内
2、子查询可以放在from后面、select后面、where后面、having后面，但一般放在条件的右侧
3、子查询优先于主查询执行，主查询使用了子查询的执行结果
4、子查询根据查询结果的行数不同分为以下两类：
① 单行子查询
    结果集只有一行
    一般搭配单行操作符使用：> < = <> >= <= 
    非法使用子查询的情况：
    a、子查询的结果为一组值
    b、子查询的结果为空

② 多行子查询
    结果集有多行
    一般搭配多行操作符使用：any、all、in、not in
    in： 属于子查询结果中的任意一个就行
    any和all往往可以用其他查询代替
```

## 进阶8：分页查询

应用场景：

```text
实际的web项目中需要根据用户的需求提交对应的分页查询的sql语句
```

语法：

```text
select 字段|表达式,...
from 表
【where 条件】
【group by 分组字段】
【having 条件】
【order by 排序的字段】
limit 【起始的条目索引，】条目数;
```

特点：

```text
1.起始条目索引从0开始

2.limit子句放在查询语句的最后

3.公式：select * from  表 limit （page-1）*sizePerPage,sizePerPage
假如:
每页显示条目数sizePerPage
要显示的页数 page
```

## 进阶9：联合查询

引入： union 联合、合并

语法：

```text
select 字段|常量|表达式|函数 【from 表】 【where 条件】 union 【all】
select 字段|常量|表达式|函数 【from 表】 【where 条件】 union 【all】
select 字段|常量|表达式|函数 【from 表】 【where 条件】 union  【all】
.....
select 字段|常量|表达式|函数 【from 表】 【where 条件】
```

特点：

```text
1、多条查询语句的查询的列数必须是一致的
2、多条查询语句的查询的列的类型几乎相同
3、union代表去重，union all代表不去重
```

