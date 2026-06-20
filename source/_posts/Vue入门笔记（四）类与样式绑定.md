---
title: Vue入门笔记（四）类与样式绑定
date: 2022-10-04 19:45:24
categories: [Vue,Vue入门]
tags: Vue
---
# 绑定HTML class

## 绑定对象 
可以给`:class(v-bind:简写)`传递一个对象来动态切换`class` 
```html
<div :class="{ active: isActive }"></div>
```
表示`active` 是否存在取决于数据属性`isActive`的真假值

对象中可以存在多个字段来操作多个`class`，且可以和普通`class`共存
```javascript
data(){
    return {
        isActive:true,
        hasError:false
    }
}
```
```html
<div
  class="static", 
  :class="{ active: isActive, 'text-danger': hasError }"
></div>
```
渲染结果为
```html
<div class="static active"></div>
```

绑定对象不一定要是内联字面量，也可以直接绑定一个对象
```javascript
data() {
  return {
    classObject: {
      active: true,
      'text-danger': false
    }
  }
}
```
```html
<div :class="classObject"></div>
```
当然此对象可以是计算方法
```javascript
data() {
  return {
    isActive: true,
    error: null
  }
},
computed: {
  classObject() {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```
```html
<div :class="classObject"></div>
```