---
title: Hexo + Butterfly 建站记录（一）日常写作
date: 2022-08-20 15:06:36
categories: Hexo + Butterfly 建站记录
tags: 
- Hexo
- Butterfly 
---
在根目录`git bash`使用`hexo new 文章名称`创建新文件
使用的都是`markdown`文档，后缀为`.md`

# Front-matter

- `title`: 文章标题
- `date`: 写作时间，编译器会将文档修改时间作为更新时间
- `categories`: 文章分类，语法为`categories: [A,B]`，表示本文属于`A`类下的`B`类
- `tags`:文章标签，语法为`tags: [A,B]`,表示文章有`A`和`B`两个标签

# Markdown语法

`Markdown`是一种轻量级标记语言，语法十分简单，可与HTML混编，可导出 HTML、PDF 以及本身的 `.md` 格式的文件
> 我推荐用```VsCode```来编辑文档
> 两三个插件就可以快速上手```Markdown All in One```、```Markdown Math```、```Markdown PDF```

{% hideToggle Markdown基本 %}

## 标题

用```#```来设置标题，有多少个```#```就代表是多少级标题

{% tabs 样例 %}

<!-- tab 代码  -->
~~~markdown
    # 这是一级标题
    ## 这是二级标题
    ### 这是三级标题
    #### 这是四级标题
    ##### 这是五级标题
    ###### 这是六级标题
~~~

<!-- endtab -->

<!-- tab 预览  -->
由于效果演示会破坏目录整齐性  
效果还是自己试试吧
嘤嘤嘤~
<!-- endtab -->

{% endtabs %}

## 字体

字体样式有：加粗、倾斜、删除线，可相互叠加
{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
    **这是加粗的文字**
    *这是倾斜的文字*
    ***这是斜体加粗的文字***
    ~~这是加删除线的文字~~
    ~~*这是斜体删除的文字*~~
~~~

<!-- endtab -->

<!-- tab 预览  -->

**这是加粗的文字**
*这是倾斜的文字*
***这是斜体加粗的文字***
~~这是加删除线的文字~~
~~*这是斜体删除的文字*~~

<!-- endtab -->

{% endtabs %}

## 引用

{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
> 这是引用
> >这是嵌套引用
~~~

<!-- endtab -->

<!-- tab 预览  -->

> 这是引用
> >这是嵌套引用

<!-- endtab -->

{% endtabs %}

## 列表

### 无序列表

{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
- 项目1
- 项目2
- 项目3
~~~

<!-- endtab -->

<!-- tab 预览  -->

- 项目1
- 项目2
- 项目3

<!-- endtab -->

{% endtabs %}

### 有序列表

{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
1. 项目1
2. 项目2
3. 项目3
~~~

<!-- endtab -->

<!-- tab 预览  -->
1. 项目1
2. 项目2
3. 项目3
<!-- endtab -->

{% endtabs %}

## 分割线
用`-`或`*`三个及以上都行
{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
---
***
~~~

<!-- endtab -->

<!-- tab 预览  -->
---
***
<!-- endtab -->

{% endtabs %}

## 链接

{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
[哔哩哔哩](https://www.bilibili.com/)
~~~

<!-- endtab -->

<!-- tab 预览  -->
[哔哩哔哩](https://www.bilibili.com/)
<!-- endtab -->

{% endtabs %}

## 图片

注意是`!`不是`！`

{% tabs 样例 %}

<!-- tab 代码  -->

~~~markdown
![](/img/头像.jpg)
~~~

<!-- endtab -->

<!-- tab 预览  -->
![](/img/头像.jpg)
<!-- endtab -->

{% endtabs %}

## 代码

### 行内代码

{% tabs 样例 %}

<!-- tab 代码  -->
~~~markdown
`markdown`行内代码,`<`是引用
~~~

<!-- endtab -->

<!-- tab 预览  -->

`markdown`行内代码,`<`是引用

<!-- endtab -->

{% endtabs %}


### 代码块

{% tabs 样例 %}

<!-- tab 代码  -->
~~~markdown  
```
    <p>一段话</p>
```
~~~
<!-- endtab -->
<!-- tab 预览  -->

~~~HTML
    <p>一段话</p>
~~~
<!-- endtab -->

{% endtabs %}

{% endhideToggle %}

# 标签外挂
> 标签外挂(Tag Plugins)不是标准的`markdown`格式

本文标签外挂只用于`buttefly`主题
标签外挂能为主题带来一些额外的功能和`UI`强化，但也有明确的限制
以下仅为我常用的几个，更多详情在[官方文档](https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89)

## 折叠栏(Toggle)

- 代码:
  
```markdown
{% hideToggle 点击以打开 %}

内容

{% endhideToggle %}

```

- 预览:
  

{% hideToggle 点击以打开 %}

内容

{% endhideToggle %}

## 选项卡(Tabs)

- 代码:
  
```markdown
{% tabs 样例 %}

<!-- tab 代码  -->

这里是代码

<!-- endtab -->

<!-- tab 预览  -->

这里是预览

<!-- endtab -->

{% endtabs %}
```

- 预览:
  

{% tabs 样例 %}

<!-- tab 代码  -->

这里是代码

<!-- endtab -->

<!-- tab 预览  -->

这里是预览

<!-- endtab -->

{% endtabs %}

## 时间轴(Timeline)

- 代码:
  
```markdown
{% timeline 2022 %}
<!-- timeline 01-02 -->
这是测试页面
<!-- endtimeline -->
{% endtimeline %}
```

- 预览:
  
  {% timeline 2022 %}
  <!-- timeline 01-02 -->
  这是测试页面
  <!-- endtimeline -->
  {% endtimeline %}



