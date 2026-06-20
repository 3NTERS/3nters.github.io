---
title: JavaScript入门笔记（十）JSON
date: 2022-09-05 17:33:38
categories: [javaScript,javaScript入门]
tags: js
---
# JSON（JavaScript Object Notaion）

- 一种轻量级的数据包交换格式
- 是独立的语言
- 易于理解

# 语法规则

- 数据为键值对
  ```javascript
  "name":"Frank"
  ```
- 数据由逗号`,`分隔
- 大括号`{}`保存对象
  ```javascript
  {"name":"Frank","url":"3nters.github.io"}
  ```
- 方括号`[]`保存数组
  `sites`是一个数组，包含三个对象，每个对象为站点信息
  ```javascript
  "sites":[
    {"name":"Frank","url":"3nters.github.io"},
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
  ]
  ```
# JSON字符串转换为JavaScript对象
通常从服务器中读取`JSON`数据
图方便就用上面手动写的`JSON`数据用于演示
`text`是`JSON`格式发到页面后的形式
```javascript
var text= '{"sites":['+
    '{"name":"Frank","url":"3nters.github.io"},'+
    '{"name":"Google", "url":"www.google.com"},'+
    '{"name":"Taobao", "url":"www.taobao.com"}]}';
var obj=JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;
//Google www.google.com
```
# 解析数据
`JSON`不能存储`Date()`对象，但是可以转换为字符串，之后再转换为`Date()`对象
```javascript
var text = '{ "name":"Runoob", "initDate":"2013-12-14", "site":"www.runoob.com"}';
var obj = JSON.parse(text);
obj.initDate = new Date(obj.initDate);//重新转换为Date对象
document.getElementById("demo").innerHTML = obj.name + "创建日期: " + obj.initDate;
//Runoob创建日期: Sat Dec 14 2013 08:00:00 GMT+0800 (香港标准时间)
```

# 解析函数
`JSON`不能包含函数，但可以将函数作为字符串保存
```javascript
var text = '{ "name":"Runoob", "alexa":"function () {return 10000;}", "site":"www.runoob.com"}';
var obj = JSON.parse(text);
obj.alexa = eval("(" + obj.alexa + ")");
document.getElementById("demo").innerHTML = obj.name + " Alexa 排名：" + obj.alexa();
//10000
```