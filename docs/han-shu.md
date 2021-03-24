# 函数

### **函数声明**

```javascript
function 函数名(arg0, [agr1]){
    statements
}

return 可以有也可以没有值，可以用来退出函数的后面内容不再执行
```

### 匿名函数

{% hint style="info" %}
用函数表达式创建匿名函数, 即匿名函数作为变量的值, 此时变量名就是函数名称.
{% endhint %}

```javascript
var fun = function(){}

//调用函数
fun();
```

### 递归函数

{% hint style="warning" %}
递归是在函数内部调用自身, 通常结合return加入结束条件, 否则会无限循环.
{% endhint %}

```javascript
//永远点不完的弹窗

function fn(){
    alert('弹窗');
    fn();
}
fn();
```

```javascript
//弹窗三次

var i=0;
function fn(){
    i++;
    alert('弹窗');
    if(i>=3){
        return;
    }
    fn();
}
fn();
```

```javascript
//计算1~n的和

function getSum(n){
    if(n==1){
        return n;
    }
    return n+getSum(n-1);
}
document.write(getSum(5));
```

### foreach

```javascript
arr.forEach(item => {
    if(item instanceof Array) {
        arrMap(item);
    }else{
        newArr.push(item);
    }
});
```

