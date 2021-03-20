# Data Manipulate Language



#### 插入

语法： insert into 表名\(字段名，...\) values\(值1，...\);

特点：

```text
1、字段类型和值类型一致或兼容，而且一一对应
2、可以为空的字段，可以不用插入值，或用null填充
3、不可以为空的字段，必须插入值
4、字段个数和值的个数必须一致
5、字段可以省略，但默认所有字段，并且顺序和表中的存储顺序一致
```

#### 修改

修改单表语法：

```text
update 表名 set 字段=新值,字段=新值
【where 条件】
```

修改多表语法：

```text
update 表1 别名1,表2 别名2
set 字段=新值，字段=新值
where 连接条件
and 筛选条件
```

#### 删除

方式1：delete语句

单表的删除： ★ delete from 表名 【where 筛选条件】

多表的删除： delete 别名1，别名2 from 表1 别名1，表2 别名2 where 连接条件 and 筛选条件;

方式2：truncate语句

```text
truncate table 表名
```

两种方式的区别【面试题】

```text
#1.truncate不能加where条件，而delete可以加where条件

#2.truncate的效率高一丢丢

#3.truncate 删除带自增长的列的表后，如果再插入数据，数据从1开始
#delete 删除带自增长列的表后，如果再插入数据，数据从上一次的断点处开始

#4.truncate删除不能回滚，delete删除可以回滚
```

