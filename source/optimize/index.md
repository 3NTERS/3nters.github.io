---
title: 优化
date: 2022-08-06 23:34:33
type: "optimize"
---
<h1>已完成</h1>

{% timeline 2026 %}

<!-- timeline 06-20 -->
升级nodejs后:

 - pages顶部图片透明  

 - 整体footer透明 

 - 优化页面信息栏错位(标签用错后的渲染错误)

 - 修复评论区不能用的问题

 - 关闭底部播放器歌词并更新了歌单

  <!-- endtimeline -->
  {% endtimeline %}

{% timeline 2022 %}

<!-- timeline 08-12 -->
 - pages顶部图片透明  
 - 整体footer透明 
<!-- endtimeline -->

<!-- timeline 08-13 -->
 - 导航页的优化
<!-- endtimeline -->

<!-- timeline 08-14 -->
 - 页脚养鱼  
    {% hideToggle 具体操作 %}
    
    ​	主题配置文件的`inject`下`bottom`的第一行先引入`jquery`
    
    ```html
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    ```
    
    ​	开启pjax
    
    ```html
    <script defer data-pjax src="https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fishes.js"></script>
    ```
    
    ​	未开启pjax
    
    ```html
    <script  src="https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fishes.js"></script>
    ```
    
    ​	最终效果在本页面页脚
    
    ​	若要更换为彩色鱼则将src改为
    
    ​	`src="https://uuuuu.cf/js/fishes.js"` 
    
    {% endhideToggle %} 
    
- 配置vscode代码块代码

- 标签外挂(Tag plugins)的使用

- 修改博客字体 
    {% hideToggle 效果对比 %}
        ![](/img/默认字体效果.png) 
        ![](/img/zhuziAwa1n字体效果.png)
    {% endhideToggle %}

- 加入文章搜索 
  <!-- endtimeline -->

  <!-- timeline 08-16 -->

- 添加图床

- 更换Valine评论为Twikoo

- 添加标题样式
  <!-- endtimeline -->

  <!-- timeline 08-19 -->

- 删除```toc```插件，否则会与hexo自带```toc```冲突
  <!-- endtimeline -->
  {% endtimeline %}

