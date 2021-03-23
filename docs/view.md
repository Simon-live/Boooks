# View

### 视图

含义：理解成一张虚拟的表

视图和表的区别：

```text
    使用方式    占用物理空间

视图    完全相同    不占用，仅仅保存的是sql逻辑

表    完全相同    占用
```

视图的好处：

```text
1、sql语句提高重用性，效率高
2、和表实现了分离，提高了安全性
```

#### 视图的创建

```text
语法：
CREATE VIEW  视图名
AS
查询语句;
```

#### 视图的增删改查

```text
1、查看视图的数据 ★

SELECT * FROM my_v4;
SELECT * FROM my_v1 WHERE last_name='Partners';

2、插入视图的数据
INSERT INTO my_v4(last_name,department_id) VALUES('虚竹',90);

3、修改视图的数据

UPDATE my_v4 SET last_name ='梦姑' WHERE last_name='虚竹';


4、删除视图的数据
DELETE FROM my_v4;
```

#### 某些视图不能更新

```text
包含以下关键字的sql语句：分组函数、distinct、group  by、having、union或者union all
常量视图
Select中包含子查询
join
from一个不能更新的视图
where子句的子查询引用了from子句中的表
```

#### 视图逻辑的更新

```text
#方式一：
CREATE OR REPLACE VIEW test_v7
AS
SELECT last_name FROM employees
WHERE employee_id>100;

#方式二:
ALTER VIEW test_v7
AS
SELECT employee_id FROM employees;

SELECT * FROM test_v7;
```

#### 视图的删除

```text
DROP VIEW test_v1,test_v2,test_v3;
```

#### 视图结构的查看

```text
DESC test_v7;
SHOW CREATE VIEW test_v7;
```

