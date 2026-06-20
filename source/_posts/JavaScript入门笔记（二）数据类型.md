---
title: javaScript入门笔记（二）数据类型
date: 2022-08-19 17:12:26
categories: [javaScript,javaScript入门]
tags: js
---
# 数据类型
基本数据类型：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol
引用数据类型（对象类型）：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）
> NaN是number
> null是object
# 动态数据类型
意味着相同变量可用作不同的类型
```javascript
var x;//Undefined(未定义)
var x=5;//Number(数值)
var x= "John";//String(字符串)
```
可使用```typeof```操作符查看数据类型
```javascript
typeof "John"                // 返回 string
typeof 3.14                  // 返回 number
typeof false                 // 返回 boolean
typeof [1,2,3,4]             // 返回 object
typeof {name:'John', age:34} // 返回 object
```

# 字符串

是存储字符的变量，可以是引号(```"" / ''```)中的任意文本
```javascript
var carname="Volvo XC60";
var carname='Volvo XC60';
```

# 数字
> 它能表示最大值（Number.MAX_VALUE）为 ±1.7976931348623157e+308，最小值（Number.MIN_VALUE）为 ±5e-324

只有一种数字类型(浮点型)，可带小数点也可不带
```javascript
var x1=12.00;
var x2=12;
```
可以通过科学计数法来书写极大或极小值
{% tabs 样例 %}

<!-- tab 代码  -->
```javascript
var x1=123e5;
var x2=123-e5;
document.write(x1+"<br>"+x2);
```
<!-- endtab -->
<!-- tab 预览  -->
<script>
var x1=123e5;
var x2=123e-5;
document.write(x1 + "<br>"+ x2)
</script>
<!-- endtab -->
{% endtabs %}

## 精度

整数（不使用小数点和指数计数法）最多为15位
> 大于15位则均为10e17
{% tabs 样例 %}

<!-- tab 代码  -->
```html
<script>
var x=999999999999999;//15个9
var y=9999999999999999;//16个9
document.write(x+"<br>"+y);
</script>
```
<!-- endtab -->

<!-- tab 预览  -->
<script>
var x=999999999999999;//15个9
var y=9999999999999999;//16个9
document.write(x+"<br>"+y);
</script>
<!-- endtab -->

{% endtabs %}

## 八进制和十六进制

- 前缀为```0```则解释为八进制数
- 前缀为```0x```则解释为十六进制

> 没事别在数字前加```0```
```javascript
var y=0377;//八进制
var z=0xff;//十六进制
```
使用```toString()```方法输出16进制、8进制、2进制
{% tabs 样例 %}

<!-- tab 代码  -->
```html
<script>
var myNumber=128;
document.write("十六："+myNumber.toString(16)+"<br>");//十六进制
document.write("八："+myNumber.toString(8)+"<br>");//八进制
document.write("二："+myNumber.toString(2)+"<br>");//二进制
</script>
```
<!-- endtab -->

<!-- tab 预览  -->
<script>
var myNumber=128;
document.write("十六："+myNumber.toString(16)+"<br>");//十六进制
document.write("八："+myNumber.toString(8)+"<br>");//八进制
document.write("二："+myNumber.toString(2)+"<br>");//二进制
</script>
<!-- endtab -->

{% endtabs %}

## 无穷大（Infinity）

- 计算值超出上限时结果为一个特殊的无穷大（Infinity）值
- 计算值超过负数范围时结果为一个负无穷大值（-Infinity）值

>基于无穷大的加减乘除运算还是无穷大（正负符号也保留）

{% tabs 样例 %}

<!-- tab 代码  -->
```html
<script>
var x=2; 
while(x!=Infinity){
    x=x*x;//一直平方到无穷大
}
document.write(x+"<br>")
//除以0也能获得无穷大
var y=2/0;
var z=-2/0;
document.write(y+"<br>"+z)
</script>
```

<!-- endtab -->

<!-- tab 预览  -->
<script>
var x=2; 
while(x!=Infinity){
    x=x*x;//一直平方到无穷大
}
document.write(x+"<br>")
//除以0也能获得无穷大
var y=2/0;
var z=-2/0;
document.write(y+"<br>"+z)
</script>
<!-- endtab -->

{% endtabs %}

## NaN非数字

- NaN代表非数字值的特殊值，用于指示某个值不是数字
- Number对象设置为Nan来指示其不是数字值
- ```isNaN()```全局函数用于判断一个值是否为NaN
  
```javascript
var x=1000/"Apple";
isNaN(x);//return true
var y=100 /"1000";
isNaN(y);//return false
var z=1000/0;
isNaN(z);//return false;无穷大是数字
```
## 数字对象

数字对象初始化，```var y = new Number(123)```
```javascript
var y = new Number(123);
typeof(y);//return Object
```
### 属性
<table class="reference">
 <thead>
  <tr>
   <th>属性</th>
   <th>描述</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Number.MAX_VALUE</td>
   <td>最大值</td>
  </tr>
  <tr>
   <td>Number.MIN_VALUE</td>
   <td>最小值</td>
  </tr>
  <tr>
   <td>Number.NaN</td>
   <td>非数字</td>
  </tr>
  <tr>
   <td>Number.NEGATIVE_INFINITY</td>
   <td>负无穷，在溢出时返回</td>
  </tr>
  <tr>
   <td>Number.POSITIVE_INFINITY</td>
   <td>正无穷，在溢出时返回</td>
  </tr>
  <tr>
   <td>Number.EPSILON</td>
   <td>
    <p>表示 1 和比最接近 1 且大于 1 的最小 Number 之间的差别</p>
   </td>
  </tr>
  <tr>
   <td>Number.MIN_SAFE_INTEGER</td>
   <td>最小安全整数。</td>
  </tr>
  <tr>
   <td>Number.MAX_SAFE_INTEGER</td>
   <td>最大安全整数。</td>
  </tr>
 </tbody>
</table>

### 方法
<table class="reference">
 <thead>
  <tr>
   <th>方法</th>
   <th>描述</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Number.parseFloat()</td>
   <td>将字符串转换成浮点数，和全局方法 parseFloat()</a> 作用一致。</td>
  </tr>
  <tr>
   <td>Number.parseInt()</td>
   <td>
    <p>将字符串转换成整型数字，和全局方法 parseInt()</a> 作用一致。</p>
   </td>
  </tr>
  <tr>
   <td>Number.isFinite()</td>
   <td>判断传递的参数是否为有限数字。</td>
  </tr>
  <tr>
   <td>Number.isInteger()</td>
   <td>判断传递的参数是否为整数。</td>
  </tr>
  <tr>
   <td>Number.isNaN()</td>
   <td>判断传递的参数是否为&nbsp;isNaN()。</td>
  </tr>
  <tr>
   <td>Number.isSafeInteger()</td>
   <td>判断传递的参数是否为安全整数。</td>
  </tr>
  <tr>
   <td>toExponential()</td>
   <td>返回一个数字的指数形式的字符串，如：1.23e+2</td>
  </tr>
  <tr>
   <td>toFixed()</td>
   <td>返回指定小数位数的表示形式。
   ```javascript
   var a=123;
   b=a.toFixed(2);// b="123.00"
   ```
   
   </td>
  </tr>
  <tr>
   <td>toPrecision()</td>
   <td>返回一个指定精度的数字。如下例子中，a=123 中，3会由于精度限制消失:
   ```javascript
   var a=123;
   b=a.toPrecision(2); // b="1.2e+2"
   ```
   </td>
  </tr>
 </tbody>
</table>

# 布尔

只能有两个值:```true```和```false```

# Undefined和Null

- Undefined表示这个变量不含有值
- Null赋给变量来清空变量
  ```javascript
  cars =null;
  ```

# 数组
三种创建方法
```javascript
//1
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
//2 
var cars=new Array("Saab","Volvo","BMW")
//3 类似于c数组创建
var cars=["Saab","Volvo","BMW"];
```

# 对象
```javascript
var person={firstName:"John",lastName:"Doe",id:5566};
var person={
    firstName:"John",
    lastName:"Doe",
    id:5566
};
```
寻址方式(两种)
```javascript
name=person.lastName;
name=person["lastName"];
```


# 声明变量类型
关键字```new```来声明其类型
```javascript
var carname= new String;
var x      = new Number;
var y      = new Boolean;
var cars   = new Array;
var person = new Object;
```