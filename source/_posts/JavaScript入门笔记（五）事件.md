---
title: JavaScript入门笔记（五）事件
date: 2022-08-21 18:23:27
categories: [javaScript,javaScript入门]
tags: js
---
# HTML事件

>包括浏览器行为和用户行为
- HTML页面加载完成
- HTML`input`字段改变
- HTML按钮被点击
- etc

常见HTML事件
```javascript
onchange//HTML元素改变
onclick//用户点击HTML元素
onmouseover//鼠标悬停
onmouseout//鼠标移开
onkeydown//用户按下键盘按键
onload//浏览器页面加载完成
```

# javaScript作用
javascript可以在事件发生时执行动作
> 前提是在`HTML`元素中添加事件属性

- 页面加载或关闭时触发事件
- 用户点击按钮执行动作
- 验证输入内容合法性
- etc

# 小例子

通过用户点击显示时间
>预览里的文字得点一下

{% tabs 样例 %}

<!-- tab 代码  -->

```html
<button onclick="displayDate() ">点这里</button>
    <script>
    function displayDate(){
        document.getElementById("demo").innerHTML=Date();
    }
    </script>
    <p id="demo"></p>
```

<!-- endtab -->

<!-- tab 预览  -->

<button onclick="displayDate() ">点这里</button>
    <script>
    function displayDate(){
        document.getElementById("demo").innerHTML=Date();
    }
    </script>
    <p id="demo"></p>
<!-- endtab -->

{% endtabs %}
   
{% tabs 样例 %}
