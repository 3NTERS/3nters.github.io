---
title: javaScript入门笔记（四）函数
date: 2022-08-21 15:59:00
categories: [javaScript,javaScript入门]
tags: js
---
# 函数语法

>关键字`function`必须小写
```javascript
function functionName(){
    //执行代码
}
```
## 带参函数

```javascript
function functionName(var1,var2){
    //执行代码
}
```
## 带返回值的函数

```javascript
function myFunction(){
    var x=5;
    return x; 
}
```
- 可以返回表达式
  
```javascript
function myFunction(a,b){
    return a*b; 
}
```
- 可以用于退出函数
  
```javascript
function myFunction(a,b){
    if(a>b){
        return ;
    } 
    return 1;
}
```
# 局部变量与全局变量

## 局部变量

- 函数内部声明的变量（使用 var）是局部变量，所以只能在函数内部访问它
- 不同函数可以使用名称相同的局部变量
- 生存周期为声明开始到函数运行后被删除

## 全局变量

- 函数外部声明的变量是全局变量，网页上的所有脚本和函数都能访问它
- 生存周期为声明开始到页面关闭后被删除
  
> 把值赋给未声明变量将自动作为全局变量的一个可配置属性（即使是在函数内声明）

```javascript
var var1 = 1; // 不可配置全局属性
var2 = 2; // 没有使用 var 声明，可配置全局属性

console.log(this.var1); // 1
console.log(window.var1); // 1
console.log(window.var2); // 2

delete var1; // false 无法删除
console.log(var1); //1

delete var2; 
console.log(delete var2); // true
console.log(var2); // 已经删除 报错变量未定义

```





