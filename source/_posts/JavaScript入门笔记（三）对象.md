---
title: javaScript入门笔记（三）对象
date: 2022-08-20 08:21:16
categories: [javaScript,javaScript入门]
tags: js
---
> 对象是变量(键值对)的容器

# 定义对象
```javascript
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black"
};
```
# 对象属性
即对象中的键值对
```javaScript
firstName: "Frank",
lastName: "Liang",
age: 21,
eyeColor: "black"
```

# 访问对象属性
两种方法
```javascript
person.firstName;
person["firstName"];
```

# 对象方法
对象内定义的函数
```javascript
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black"
    // 对象方法
    fullName: function(){
        return this.firstName+" "+this.lastName;
    }
};
```
# 访问对象方法

```javascript
Object.methodName();
```
{% tabs 样例 %}

<!-- tab 代码  -->

```javascript
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black",
    // 对象方法
    fullName: function(){
        return this.firstName+" "+this.lastName;
    }
};
var P1=person.fullName();
document.write(P1);
```

<!-- endtab -->

<!-- tab 预览  -->

<script>
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black",
    // 对象方法
    fullName: function(){
        return this.firstName+" "+this.lastName;
    }
};
var P1=person.fullName();
document.write(P1);
</script>

<!-- endtab -->

{% endtabs %}
>不加```()```则会返回函数的定义
{% tabs 样例 %}

<!-- tab 代码  -->

```javascript
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black",
    // 对象方法
    fullName: function(){
        return this.firstName+" "+this.lastName;
    }
};
var P1=person.fullName;
document.write(P1);
```

<!-- endtab -->

<!-- tab 预览  -->

<script>
var person ={
    // key:value
    firstName: "Frank",
    lastName:"Liang",
    age:21,
    eyeColor:"black",
    // 对象方法
    fullName: function(){
        return this.firstName+" "+this.lastName;
    }
};
var P1=person.fullName;
document.write(P1);
</script>

<!-- endtab -->

{% endtabs %}
