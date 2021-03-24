# 规范

### 语法规范

1. `script`必须为双标签
2. 代码有默认执行顺序, 文档流顺序, 从上至下, 从左到右
3. 实际项目中, script标签会放在最后`</body>`之前
4. 每一句代码需要以分号`;`结尾

### 代码位置

#### 行内代码

{% hint style="warning" %}
行内代码书写时结构与行为耦合, 不方便维护, 实际项目不推荐使用!
{% endhint %}

```markup
<span onclick="...">标签</span>
<a href="javascript:;">标签</a>
```

#### 内部代码

```markup
<script type="text/javascript">
  ...    
</script>
```

#### 外部代码

```markup
<script type="text/javascript" src="..."></script>
```

### **调试语句**

#### 弹窗警告

```javascript
alert("hello, world!");
```

#### 弹出输入框

{% hint style="info" %}
prompt有输入时返回输入内容，无输入时返回null
{% endhint %}

```javascript
var age = prompt("请输入年龄");
```

#### 向浏览器页面输出内容

```javascript
document.write("hello, world!");
```

#### 向控制台输出

```javascript
console.log("hello, world!");
```

### 注释

单行注释

```javascript
// 注释内容
```

多行注释

```javascript
/*
注释内容
*/
```

