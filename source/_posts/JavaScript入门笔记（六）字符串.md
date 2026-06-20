---
title: javaScript入门笔记（六）字符串
date: 2022-08-21 19:29:52
categories: [javaScript,javaScript入门]
tags: js
---
# javaScript字符串
- 可以使用`''`或`""`
    ```javascript
    var carname1="Volvo XC60";//Volvo XC60
    var carname2='Volvo XC60';//Volvo XC60
    ```
- 可以使用索引（从`0`开始）访问字符串中任何字符
- 可以在字符串中使用转义字符`\`
    ```javascript
    var answer1='It\'s alright';//It's alright
    var answer2="He is called \"Johnny\"";//He is called "Johnny"
    var answer3='He is called "Johnny"';//He is called "Johnny"
    ```
# 计算字符串长度

`length`是属性，不是方法所以不用加`()`
```javascript
var txt="asdasdas";
var ln=txt.length;
```
# 查找字符串

>都是从`0`位置开始算，实际位置需要`+1`
- 使用`indexOf()`来定位字符串中某个字符首次出现位置
- 使用`lastIndexOf()`从字符串末尾来定位字符串中某个字符首次出现位置

不论从前还是从末尾找，给出的位置始终是字符串的索引值
```javascript
var str="Hello world, welcome to the welcome.";
var n=str.indexOf("welcome");//输出13
var n=str.lastIndexOf("welcome");//输出28
```

# 内容匹配

`match()`函数用来查找字符串中特定的字符，并且如果找到的话则返回这个字符
{% tabs 样例 %}

<!-- tab 代码  -->

```javascript
var str="Hello world!";
document.write(str.match("world")+"<br>");
document.write(str.match("World")+"<br>");
document.write(str.match("world!"));
```

<!-- endtab -->

<!-- tab 预览  -->

<script>
var str="Hello world!";
document.write(str.match("world")+"<br>");
document.write(str.match("World")+"<br>");
document.write(str.match("world!"));
</script>

<!-- endtab -->

{% endtabs %}

# 替换内容

`replace()`函数在字符串中用某些字符替换另一些字符
```javascript
//Microsoft被Runoob替换
var str="Please visit Microsoft!";
var n=str.replace("Microsoft","Runoob");
```

# 大小写转换

- 转大写`toUpperCase()`
- 转小写`toLowerCase()`
  
该方法不会改变源字符串
```javascript
var txt="Hello World!";       // String
var txt1=txt.toUpperCase();   // txt1 文本会转换为大写
var txt2=txt.toLowerCase();   // txt2 文本会转换为小写
```

# 字符串转数组

使用`split()`函数转数组
```javascript
txt="a,b,c,d,e"   // String
txt.split(",");   // 使用逗号分隔
txt.split(" ");   // 使用空格分隔
txt.split("|");   // 使用竖线分隔 
```
# 字符串属性和方法

>除了上面的几种再补充些我感觉比较常用的

属性:
- prototype查看原型（一个能让外部函数访问到函数私有属性的中介）
- constructor构造函数方法

方法:
- substr()截取字符串
```javascript
var txt="asdadwsda";
var x=txt.substr(1,3);
//截取下标1到3的字符串
//输出x="sda"
```


更多详情在[String对象文档](https://www.runoob.com/jsref/jsref-obj-string.html)