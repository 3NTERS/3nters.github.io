---
title: Vue入门笔记（三）计算属性
date: 2022-09-26 13:54:14
categories: [Vue,Vue入门]
tags: Vue
---
说白了所谓`计算方法`就是添加一个方法
如下例子，想要展示已出版书籍
```javascript
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  }
```
```html
<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>
```
但是因为耦合较高不好维护，所以将`HTML`内的表达式改成方法
改进如下
```javascript
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // 一个计算属性的 getter
    publishedBooksMessage() {
      // `this` 指向当前组件实例
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}
```
```html
<p>Has published books:</p>
<span>{{ publishedBooksMessage }}</span>
```
`HTML`显示内容为定义的计算方法名称`publishedBooksMessage`,方便后期维护