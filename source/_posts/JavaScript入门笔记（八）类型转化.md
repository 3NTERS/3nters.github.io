---
title: JavaScript入门笔记（八）类型转换
date: 2022-08-23 10:44:46
categories: [javaScript,javaScript入门]
tags: js
---
# 转字符串
全局方法`String()`
>这里的`值`可以是任何类型

```javascript
String(值);
```
方法`toString()`
```javascript
值.toString();
```

## 数字
>这里`值`只能是数字

```javascript
String(数字);
值.toString();
```
## 布尔值
>`true`同理

```javascript
string(false);
false.toString();
```

## 日期
> 函数`Date()`自动返回字符串

```javascript
Date();
String(Date());
obj=new Date();
obj.toString();
```
# 转数字
全局方法`Number()`可以将字符串转化为数字，其他字符转成`NaN`(非数字)

## 布尔值
```javascript
Number(false);//return 0
Number(true);//return 1
```
  
## 日期

`getTime()`直接获取数字形式时间
获取的是从 1970 年 1 月 1 日午夜到指定日期之间的毫秒数
>所以每次刷新获取的值都不同

{% tabs 样例 %}

<!-- tab 代码  -->
```javascript
d=new Date();
document.write(Number(d)+"<br> ");
document.write(d.getTime());
```
<!-- endtab -->

<!-- tab 预览  -->
<script>
d=new Date();
document.write(Number(d)+"<br> ");
document.write(d.getTime());
</script>
<!-- endtab -->

{% endtabs %}

# 自动转换类型

>当js尝试操作一个“错误”的数据类型时，会自动转换为“正确”的数据类型

- 数字`+null`
- 字符串`+null`
- 字符串`+`数字
- 字符串`-`数字
  
```javascript
5 + null    // 返回 5         null 转换为 0
"5" + null  // 返回"5null"   null 转换为 "null"
"5" + 1     // 返回 "51"      1 转换为 "1" 
"5" - 1     // 返回 4         "5" 转换为 5
```
## 转换为字符串
当尝试输出对象或变量时js会自动调用变量的`toString()`方法
```javascript
myVar = {name:"Fjohn"}  // toString 转换为 "[object Object]"
myVar = [1,2,3,4]       // toString 转换为 "1,2,3,4"
myVar = new Date()      // toString 转换为 "Fri Jul 18 2014 09:08:55 GMT+0200"
```
数字和布尔值也经常相互转换：
```javascript
myVar = 123             // toString 转换为 "123"
myVar = true            // toString 转换为 "true"
myVar = false           // toString 转换为 "false"

```

