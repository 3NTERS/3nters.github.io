---
title: Hexo + Butterfly 建站记录（二）常用指令及快捷方法
date: 2026-06-20 00:56:33
categories: Hexo + Butterfly 建站记录
tags: 
- Hexo
- 快捷键

---

# Hexo 常用指令

## 创建

- `hexo new` 可缩写为 `hexo n`

- `hexo new post "title"` 创建文章
- `hexo new page --path about/me "name"` 在指定路径创建页面

## 更新上传

- `hexo clean` 清除缓存文件
- `hexo generate` 缩写 `hexo g` 生成静态文件
- `hexo deploy` 缩写 `hexo d` 部署网站

# 快捷键

## typora

`偏好设置`-> `通用`-> `打开高级设置`-> `conf.user.json`-> `keyBinding`

然后参考官方快捷键表设置即可，不在表里面的快捷键不能设置，比如一键运行脚本之类的...

**重点来了**！！安装插件即可实现命令行和脚本的运行

- 安装 `typora_plugin` 以支持插件
- 安装 `typora_terminal_plugin`，然后就可以右键 `交互插件` ->`命令行环境`->你要的`terminal`环境

## powershell

直接属性设置快捷键`Crtl+Alt+T`就能打开了，感觉这个最简单最直接最方便

完了就可以直接在hexo根目录运行`.bat`脚本实现一键上传部署了:D!!
