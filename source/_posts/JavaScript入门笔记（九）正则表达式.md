---
title: JavaScript入门笔记（九）正则表达式
date: 2022-08-29 21:32:05
categories: [javaScript,javaScript入门]
tags: js
---

# 正则表达式
- 正则表达式是由一个字符序列形成的搜索模式
- 正则表达式可以描述要查询的数据内容
- 正则表达式可以是一个简单的字符也可以是一个更复杂的模式
- 正则表达式可用于所有文本搜索和文本替换的操作

# 语法
`runoob`是一个正则表达式主体
`i`是一个修饰符
```javascript
/正则表达式主体/修饰符(可选)
var patt=/runoob/i;
```
## 修饰符
用于执行区分大小写和全局匹配
- `i`执行对大小写不敏感的匹配
- `g`执行全局匹配（查找所有匹配而非在找到第一个后匹配停止）
  >但还是只输出第一个的位置
- `m`执行多行匹配

## 方括号
用于查找某个范围内的字符
- `[abc]`查找括号之间的任何字符
  - `[0-9]`查找`0`到`9`之间的数字
  - `[a-z]`查找从小写`a`到小写`z`的字符
  - `[A-z]`查找从大写`a`到小写`z`的字符
- `[^abc]`查找不在括号之间的字符
  - `[^a-z]`查找除小写`a`到小写`z`的字符
- `(x|y)`查找任何以`|`分隔的选项
  
## 元字符(Metacharacter)
拥有特殊含义的字符（字符较多这里就记录几个常用的）
-  `.`查找单个字符，除了换行和行结束符
-  `\w`查找数字、字母及下划线（这些也称为单词字符）
    ```javascript
        var str="Give 100%!";
        var patt1=/\w/g;
        document.write(str.match(patt1));
        //输出 G，i，v，e，1，0，0
    ```
-  `\W`查找非单词字符
-  `\d`查找数字
-  `\D`查找非数字字符
-  `\b`查找单词边界（常用于匹配以某个单词开头或结尾处）
    ```javascript
    var str="Visit Runooob"; 
    var patt1=/\bRun/g;
    document.write(str.match(patt1));
    //输出 Run
    ```
-  `\n`查找换行符
-  `\uxxxx`查找以十六进制数`xxxx`规定的`Unicode`字符

## 量词

-  `n+`匹配包含至少一个`n`的字符串(这个`n`可以替换成别的字符)
    ```javascript
    var str="Hellooo World! Hello Runoob!"; 
    var patt1=/o+/g;
    document.write(str.match(patt1));
    ```
-  `n*`匹配包含零个或多个`n`的字符串
-  `n？`匹配包含零个或一个`n`的字符串

后面还有好多不细写了（等用上再查）
{% hideToggle 附表格 %}

<table class="reference">
  <tbody><tr>
    <th style="width:20%">量词</th>
    <th>描述</th>
  </tr>
  <tr>
    <td>n{X}</td>
    <td><p>匹配包含 X 个 n 的序列的字符串。</p>
<p>例如，/a{2}/ 不匹配 "candy," 中的 "a"，但是匹配 "caandy," 中的两个 "a"，且匹配 "caaandy." 中的前两个 "a"。</p>
</td>
  </tr>
<tr>
<td>n{X,}</td>
<td><p>X 是一个正整数。前面的模式 n 连续出现至少 X 次时匹配。
</p><p>
例如，/a{2,}/ 不匹配 "candy" 中的 "a"，但是匹配 "caandy" 和 "caaaaaaandy." 中所有的 "a"。</p></td>
</tr>
  <tr>
    <td>n{X,Y}</td>
    <td><p>
X 和 Y 为正整数。前面的模式 n 连续出现至少 X 次，至多 Y 次时匹配。</p><p>
例如，/a{1,3}/ 不匹配 "cndy"，匹配 "candy," 中的 "a"，"caandy," 中的两个 "a"，匹配 "caaaaaaandy" 中的前面三个 "a"。注意，当匹配 "caaaaaaandy" 时，即使原始字符串拥有更多的 "a"，匹配项也是 "aaa"。</p>
</td>
  </tr>
  <tr>
    <td>n$</td>
    <td>匹配任何结尾为 n 的字符串。</td>
  </tr>
  <tr>
    <td>^n</td>
    <td>匹配任何开头为 n 的字符串。</td>
  </tr>
  <tr>
    <td>?=n</td>
    <td>匹配任何其后紧接指定字符串 n 的字符串。</td>
  </tr>
  <tr>
    <td>?!n</td>
    <td>匹配任何其后没有紧接指定字符串 n 的字符串。</td>
  </tr>
</tbody></table>

{% endhideToggle %}

# 方法

## RegExp方法

- `exec()`检索字符串中的指定的值，返回找到的值，没找到就返回`null`
  ```javascript
  var str="Hello world!";//查找Hello
  var patt=/Hello/g;
  var result=patt.exec(str);
  document.write('return:'+result);
  //return:Hello
  ```
- `test()`检索字符串中的指定的值，返回`true`或`false`
  ```javascript
  object.test(string)
  ```
- `toString`将正则表达式转化为字符串（本质上就是转换字符串）

## 支持正则的String对象方法

- `search()`检索与表达式相匹配的值，返回位置
  ```javascript
  var str="Hello world!";
  var n=str.search("world");
  //6
  ```
- `match()`找到一个或多个与表达式匹配的子串
  ```javascript
  var str="The rain in SPAIN stays mainly in the plain"; 
  var n=str.match(/ain/g);
  //ain,ain,ain
  ```
- `replace()`替换与表达式匹配的子串
  示例只替换一次，全部替换加`/g`
  ```javascript
  var str="Visit Microsoft! Visit Microsoft!";
  var n=str.replace("Microsoft","Runoob");
  //Visit Runoob!Visit Microsoft!
  ```
- `split()`把字符串分割为字符串数组
  ```javascript
  var str="How are you doing today?";
  var n=str.split(" ");
  //How,are,you,doing,today?
  ```

  ## RedExp对象属性
- `global()`查看正则表达式是否具有标志`g`返回true或者false
- `ignoreCase()`查看正则表达式是否具有标志`i`返回true或者false
- `multiline()`查看正则表达式是否具有标志`m`返回true或者false

 ```javascript
  var str="Visit RUNOOB!";
  var patt1=/RUN/g;
  patt1.global;
  patt1.ignoreCase;
  patt1.multiline;
  ```
