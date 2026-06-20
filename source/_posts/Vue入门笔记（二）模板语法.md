---
title: Vue入门笔记（二）模板语法
date: 2022-09-26 13:25:39
categories: [Vue,Vue入门]
tags: Vue
---
# 模板语法
Vue使用基于`html`的模板语法，允许将`DOM`绑定到底层`Vue`实例的数据
## 文本插值
双大括号语法文本插值 (`Mustache`)
- 插数据
```html
<span>message:{{msg}}</span>
<!-- 绑定v-once，一次性插值，不会再变化 -->
<span v-once>这个将不会改变：{{msg}}}</span>
```
- 插`HTML`代码
原始`HTML` 双括号会解释为普通文本而不是`HTML`代码，输出真正的`HTML`需要`v-html`指令 
```html
<p>Using mustaches:{{rawHtml}}</p>
<p>Using v-html idrective:<span v-html="rawHtml"></span></p>
```

## HTML属性(Attribute)绑定
  `Attribute mustache`语法不能作用在`HTML attribute`上，这时候要用`v-bind`指令动态绑定`id`
  ```html
    <div v-bind:id="dynamicId"> </div>
    <!-- dynamicId`为变量) -->
    <button v-bind:disabled="isButtonDisabled">Button</button>
  ```

- `js`表达式支持
  使用`javaScript`表达式 对于所有数据的绑定`vue.js`都提供了完全的`js`表达式支持
  ```html
    {{number+1}}<br>
    {{ok?'Yes':'No'}}<br>
    {{message.split('').reverse().join('')}}
    <div v-bind:id="'list-'+dynamicId"></div>
  ```
  >但不支持js语句和条件控制 （也就是包含关键字的语句），如`var`、`if`、`return`等

