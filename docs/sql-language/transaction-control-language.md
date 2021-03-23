# Transaction Control Language

#### 含义

```text
通过一组逻辑操作单元（一组DML——sql语句），将数据从一种状态切换到另外一种状态
```

#### 特点

```text
（ACID）
原子性：要么都执行，要么都回滚
一致性：保证数据的状态操作前和操作后保持一致
隔离性：多个事务同时操作相同数据库的同一个数据时，一个事务的执行不受另外一个事务的干扰
持久性：一个事务一旦提交，则数据将持久化到本地，除非其他事务对其进行修改
```

相关步骤：

```text
1、开启事务
2、编写事务的一组逻辑操作单元（多条sql语句）
3、提交事务或回滚事务
```

#### 事务的分类：

隐式事务，没有明显的开启和结束事务的标志

```text
比如
insert、update、delete语句本身就是一个事务
```

显式事务，具有明显的开启和结束事务的标志

```text
    1、开启事务
    取消自动提交事务的功能

    2、编写事务的一组逻辑操作单元（多条sql语句）
    insert
    update
    delete

    3、提交事务或回滚事务
```

#### 使用到的关键字

```text
set autocommit=0;
start transaction;
commit;
rollback;

savepoint  断点
commit to 断点
rollback to 断点
```

#### 事务的隔离级别:

事务并发问题如何发生？

```text
当多个事务同时操作同一个数据库的相同数据时
```

事务的并发问题有哪些？

```text
脏读：一个事务读取到了另外一个事务未提交的数据
不可重复读：同一个事务中，多次读取到的数据不一致
幻读：一个事务读取数据时，另外一个事务进行更新，导致第一个事务读取到了没有更新的数据
```

如何避免事务的并发问题？

```text
通过设置事务的隔离级别
1、READ UNCOMMITTED
2、READ COMMITTED 可以避免脏读
3、REPEATABLE READ 可以避免脏读、不可重复读和一部分幻读
4、SERIALIZABLE可以避免脏读、不可重复读和幻读
```

设置隔离级别：

```text
set session|global  transaction isolation level 隔离级别名;
```

查看隔离级别：

```text
select @@tx_isolation;
```

