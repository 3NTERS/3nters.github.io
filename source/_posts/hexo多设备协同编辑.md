---
title: hexo多设备协同编辑
date: 2026-06-20 12:50:44
typora-root-url: hexo多设备协同编辑
categories: Hexo + Butterfly 建站记录
tags:
- git
- 多设备协同
---



# Nodejs版本

Test：不同电脑的nodejs版本不同，不知道git pull之后用了新版本的nodejs会不会影响部署

草！显然影响到了，主页page和底部不再是透明了，头像也不见了(如下图所示)。还是修修bug然后统一更新到最新版本吧。

![image-20260620132100478](./image-20260620132100478.png)



## 修复图片不显示问题

- 安装hexo-renderer-marked

- 在`_config.yaml`文件中按照如下设置

  ```yaml
  post_asset_folder: true #启用hexo自带功能，创建文章自动生成同名文件夹
  marked: #启用插件功能，markdwon图片格式转为hexo专用插入格式
   prependRoot: true
   postAsset: true
  ```

- 在`scaffolds `文件夹的`post.md`中添加如下设置

  ```yaml
  typora-root-url: {{ title }}
  ```

这样就会在`.md`文章同级目录中创建同名文件夹来保存图片，即使文章名为中文也可以导入图片,并且会将typora的格式转换为`hexo`专用的图片插入格式。

非常抽象的过程。

1. 格式转换即 `![example](./example.png)`会被插件先转换为`{% asset_img example.png 这是一张示例图片 %}`，

2. 由于开启了`post_asset_folder`功能所以`hexo`会自动在title同名文件夹下找名为`example.png`的图片

**问题来了**！！踏马的`typora`预览图片不显示了，因为图片正确的位置在`./title/example.png`,所以为了能够正确预览故操作如下

3. `post`模板文件中加入图片根目录，让`![example](./example.png)`实际变成`![example](./title/example.png)`

## 修复背景不透明

> 设置主页背景与全站页脚为透明

`source`新建`css`文件夹，创建`my.css`后如下设置

```
/* 强制将顶部导航和页脚背景设为透明 */
#page-header.full_page {
    background: transparent !important;
}
#footer {
    background: transparent !important;
}
```

因为查看主页`header`属性为`<class="full_page" id="page-header">`而文章`header`则是`<class="post-page" id=“page-header”>`所以`css`直接根据属性来设置了。
