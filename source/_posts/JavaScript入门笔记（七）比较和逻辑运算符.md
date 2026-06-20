---
title: JavaScript入门笔记（七）比较和逻辑运算符
date: 2022-08-22 13:23:03
categories: [javaScript,javaScript入门]
tags: js
---

# 比较和逻辑运算符

## 比较符号

较为常规的有
- `> < >= <= == !=`

javaScript特有的`绝对等于`和`不绝对等于`
- `===`绝对等于，指值和类型都相同
- `!===`不绝对等于，指值和类型任一不相同或都不相同

## 逻辑运算符

- `&&` 与(and)
- `||` 或(or)
- `! ` 非(not)
  
## 条件运算符

如果变量 age 中的值小于 18，则向变量 voteable 赋值 "年龄太小"，否则赋值 "年龄已达到"。
```javascript
var age;
var voteable=(age<18)?"年龄太小":"年龄已达到";
```