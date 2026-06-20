---
title: git命令使用
date: 2026-06-20 09:14:29
typora-root-url: git命令使用
categories: 计算机基础知识
tags:
- git
---

# 常用Git命令

### 初始化

`git init` 

`git config --global user.name "lzh"`

`git config --global user.email "lzh@qq.com"`

`git config list`

## 关联远程仓库

`git remote add origin 仓库地址`  关联仓库

 `git push --set-upstream origin master`    关联分支

`git clone 仓库地址`

## 提交拉取

`git add .`

`git status`

`git commit -m "注释"`

`git push`

`git pull`

## 版本控制

`git log`

![image-20260618163807399](./image-20260618163807399.png)

`git reset --hard  "序列号"`  将版本强制指向所选序列号

`git checkout abc1234 -- docs/`  把 `docs/` 文件夹恢复到 `abc1234` 这个提交时的状态

`git add docs/`  上传单个文件夹

`git clean -fdn`  -n 表示 dry-run，只显示会删什么，不实际执行

`git clean -fd`  实际去执行

`git diff HEAD~1 HEAD -- predict3_onnx.py`  对比上次提交与上上次提交的文件变化

`git diff HEAD -- predict3_onnx.py`  对比当前修改与上次提交的文件变化

## 分支

`git checkout -b dev` 创建名为`dev`分支 

## 常用commit类型

- feat: 新功能、新特性
- fix: 修改 bug
- perf: 更改代码，以提高性能（在不影响代码内部行为的前提下，对程序性能进行优化）
- refactor: 代码重构（重构，在不影响代码内部行为、功能下的代码修改）
- docs: 文档修改
- style: 代码格式修改, 注意不是 css 修改（例如分号修改）
- test: 测试用例新增、修改
- build: 影响项目构建或依赖项修改
- revert: 恢复上一次提交
- ci: 持续集成相关文件修改
- chore: 其他修改（不在上述类型中的修改）
- release: 发布新版本
- workflow: 工作流相关文件修改

