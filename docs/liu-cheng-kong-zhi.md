# 流程控制

## 流程控制

| 控制方式 | 语句 |
| :--- | :--- |
| 顺序流程 | 从上到下从左到右 |
| 分支控制 | if/switch |
| 循环控制 | for/while |

### if语句

通常用于判断数据是范围或逻辑.

```javascript
if( 表达式1 ){

   执行语句1

}else if( 表达式2 ){

   执行语句2

}else{

   执行语句3

}
```

### switch语句

通常用于判断数据是某个固定数值.

```javascript
switch ( 表达式 ) {
    case 1:
        执行语句1;
        break;
    case 2:
        执行语句2;
        break;

        ...

    default:
        无匹配执行语句;
        break;
}
```

### for循环

先执行循环体,再执行步长

```javascript
for( 定义并赋值循环变量：var i= []; 进入循环条件; 步长){

    循环体;

}
```

针对数组的循环,别名不需要定义,跟下标一样从0开始,到下标最大值

```javascript
for( 下标别名 in 数组 ){

    循环体;

}
```

### do-while循环

```javascript
do{

    循环体;

}while( 条件 )
```

### while循环

```javascript
while( 满足条件进行循环 ) {

    循环体;   

}
```

### break和continue

`break`是终止整个循环

`continue`是终止本次循环直接进入下一次循环

