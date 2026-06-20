---
title: javaScript入门笔记（一）基本语法
date: 2022-08-18 00:22:27
categories: [javaScript,javaScript入门]
tags: js
anchor: true
---
> 三马车之javaScript，控制页面的行为

# 输出

简单输出
```javaScript
// 内容写入弹出窗口
alert('HelloWorld!');
// 内容写入hml文档
document.write('HelloWorld!');
// 内容写入浏览器控制台
console.log('HelloWorld!')
```

通过```id```选择性输出
```javascript
// 选取id=demo的元素并innerHTML来获取或插入元素内容
document.getElementById("demo").innerHTML = "段落已修改";
//  获取id=demo元素的值
document.getElementById("demo").value;
```

通过```button```行为调用```函数```输出
```javaScript
//通过按钮来执行输出函数(显示时间)
<button onclick="myFunction()">点我</button>
<script>
    function myFunction(){
        document.write(Date());
    }
</script>
```
# 注释
>类似于c的注释

单行注释
```javascript
// 这是一行注释
```
多行注释
```javascript
/*
这是多行注释1
这是多行注释2
*/
```
行末使用注释
```javascript
var Ez=666;//声明Ez并赋值666
```

# 字面量
一般固定值被称为字面量
## 数字字面量
  小数 整数 科学计数(e)
```javascript
3.14 ;1001 ;123e5 ;
```
## 字符字面量
 可使用单引号或双引号
```javaScript
"Frank Cassidy"

'Frank Cassidy'
```
## 表达式字面量
 用于计算
```javaScript
5 + 6;
5 * 10;
```
## 数组字面量
定义数组
```javaScript
[40, 100, 1, 5, 25, 10]
```
## 对象字面量
定义对象，里面类似于c++的成员
```javaScript
{firstName:"John", lastName:"Doe", age:50,eyeColor:"black"}
```
## 函数字面量
可以返回为值或直接空
```javascript
function myFunciton(a,b){
    return ;
}
```
# 变量
通常用关键字```var```定义变量，使用```=```给变量赋值
```javascript
var x, length;
x = 5;
lenght = 6;
```
## 一条语句多个变量

```javascript
//一行声明
var lastname="Doe", age=30, job="carpenter";
//跨行声明
var lastname="Doe",
age=30,
job="carpenter";
```

禁止🚫多个变量同时赋同一个值
```javascript
var x,y,z=1;
```
x,y为undefined，z为1

# 操作符

算术运算符&赋值运算符
```+ - * / =```

# 数据类型
字面量的类型：数据类型。有六种
- String(字符串)
-  Number(数值) 
-  Boolean(布尔值)
-  Null (空值)
-  Undefined(未定义)
-   Object(对象)

> 基本数据类型：String(字符串)、Number(数值)、Boolean(布尔值)、 Null (空值)、Undefined(未定义)
> 引用数据类型：Object(对象)

一般的变量命名后未赋值，此时为```Undefiend```未定义

```javascript
document.write(16+"Volve")
// 输出16Volve
```

# 字母大小写&字符集

> js对字母大小写严格区分
> js使用Unicode字符集

函数 getElementById 与 getElementbyID 是不同的。
同样，变量 myVariable 与 MyVariable 也是不同的。

# 代码&代码块形式

浏览器按照代码编写顺序依次执行每条语句
向网页输出两个段落
```javascript
document.getElementById("demo").innerHTML = "Hello Dolly";
document.getElementById("myDiv").innerHTML = "最近如何？";
```
代码块以左花括号开始，以右花括号结束。一并地执行语句序列
```javascript
function myFunction(){
    ocument.getElementById("demo").innerHTML = "Hello Dolly";
    document.getElementById("myDiv").innerHTML = "最近如何？";
    return ;
}
```
# 标识符

- js中自主命名的都是标识符
- 例如变量名、函数名、属性名
- 命名规则
    1.含有字母、数字、_、$
    2.不能数字开头
    3.不能是关键字和保留字
    4.驼峰命名法
    - 首字母小写，每个单词开头大写，其余小写
        例如：helloWorld
- 以下列出关键字
    {% hideToggle 点击以打开 %}
  <table class="reference">
<tbody><tr>
	<th>语句</th>
	<th>描述</th>
</tr>
<tr>
<td>break</td>
<td>用于跳出循环。</td>
</tr>
<tr>
<td>catch</td>
<td>语句块，在 try 语句块执行出错时执行 catch 语句块。</td>
</tr>
<tr>
<td>continue</td>
<td>跳过循环中的一个迭代。</td>
</tr>
<tr>
<td>do ... while</td>
<td>执行一个语句块，在条件语句为 true 时继续执行该语句块。</td>
</tr>
<tr>
<td>for</td>
<td>在条件语句为 true 时，可以将代码块执行指定的次数。 </td>
</tr>
<tr>
<td>for ... in </td>
<td>用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作）。</td>
</tr>
<tr>
<td>function</td>
<td>定义一个函数</td>
</tr>
<tr>
<td>if ... else</td>
<td>用于基于不同的条件来执行不同的动作。</td>
</tr>
<tr>
<td>return</td>
<td>退出函数</td>
</tr>
<tr>
<td>switch</td>
<td>用于基于不同的条件来执行不同的动作。</td>
</tr>
<tr>
<td>throw</td>
<td>抛出（生成）错误 。 </td>
</tr>
<tr>
<td>try</td>
<td>实现错误处理，与 catch 一同使用。 </td>
</tr>
<tr>
<td>var</td>
<td>声明一个变量。</td>
</tr>
<tr>
<td>while</td>
<td>当条件语句为 true 时，执行语句块。 </td>
</tr>
</tbody></table>

    {% endhideToggle %}

# 多行写一句&一行写多句
使用反斜杠对代码进行换行
```javascript
document.write("Hello\
!World");
```
用```;```隔开
```javascript
document.write("HelloWorld!");doucment.write("Ty");
```
# 选择与循环

## If
```javascript
if (condition1){
    当条件1为true时执行代码
}
else if(condition2) {
    当条件2为true时执行代码
}
else {
    当条件1和条件2都不为true时执行代码

}
```
## switch
```javascript
switch(n){
    case 1:
        执行代码块1
        break;
    case 2:
        执行代码块2
        break;
    default:
        与case 1和case 2 不同时执行的代码
}
```
## For 
```javascript
for(语句1;语句2;语句3){
    被执行的代码块
}

```
## For/In循环

遍历对象的属性
{% tabs 样例 %}

<!-- tab 代码  -->
```javascript

	var x;//x为person的属性名
	var txt="";
	var person={fname:"Bill",lname:"Gates",age:56}; 
	for (x in person){
		txt=txt + person[x];
	}
	document.write(txt);

```
<!-- endtab -->

<!-- tab 预览  -->
<p id="demo"></p>
<script>
	var x;
	var txt="";
	var person={fname:"Bill",lname:"Gates",age:56}; 
	for (x in person){
		txt=txt + person[x];
	}
	document.getElementById("demo").innerHTML=txt;
</script>
<!-- endtab -->

{% endtabs %}

## while&do/while循环

与c语言的类似
```javascript
while (condition){
    code1;
}

do{
    code1;
}
while(condition);
```
## Break
用于跳出循环，继续执行循环后的的代码

{%tabs 样例 %} 

<!-- tab 代码 -->
```javascript
var i=0,x="";
for(i=0;i<10;i++){
    if(i==3){
        break;
    }
    x=x+"The number is "+ i +" <br>";
}
    document.write(x);
```
<!-- endtab -->
<!-- tab 预览 -->
<script>
var i=0,x="";
for(i=0;i<10;i++){
    if(i==3){
        break;
    }
    x=x+"The number is "+ i +" <br>";
}
document.write(x);
</script>
<!-- endtab -->
{%endtabs%}

## Continue

用于中断循环本次迭代，继续循环下一个迭代
{% tabs 样例 %}

<!-- tab 代码  -->
```javascript
var i=0,x="";
for(i=0;i<10;i++){
    if(i==3){
        i++;
        continue;
    }
    x=x+"The number is "+ i +" <br>";
}
document.write(x);
```
<!-- endtab -->

<!-- tab 预览  -->
<script>
var i=0,x="";
for(i=0;i<10;i++){
    if(i==3){
        i++;
        continue;
    }
    x=x+"The number is "+ i +" <br>";
}
document.write(x);
</script>

<!-- endtab -->

{% endtabs %}

## js标记

如需标记js语句，请在语句之前加上冒号
{% tabs 样例 %}

<!-- tab 代码  -->

```javascript
cars=["BMW","Volvo","Saab","Ford"];
list:{
	document.write(cars[0] + "<br>"); 
	document.write(cars[1] + "<br>"); 
	document.write(cars[2] + "<br>"); 
	break list;
	document.write(cars[3] + "<br>"); 
	document.write(cars[4] + "<br>"); 
	document.write(cars[5] + "<br>"); 
}
```

<!-- endtab -->

<!-- tab 预览  -->

<script>
cars=["BMW","Volvo","Saab","Ford"];
list:{
	document.write(cars[0] + "<br>"); 
	document.write(cars[1] + "<br>"); 
	document.write(cars[2] + "<br>"); 
	break list;
	document.write(cars[3] + "<br>"); 
	document.write(cars[4] + "<br>"); 
	document.write(cars[5] + "<br>"); 
}
</script>

<!-- endtab -->

{% endtabs %}
