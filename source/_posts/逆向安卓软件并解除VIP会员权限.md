---
title: 逆向安卓软件并解除VIP会员权限
typora-root-url: 逆向安卓软件并解除VIP会员权限
date: 2026-06-20 21:37:28
categories: 逆向工程
tags:
- jadx
- apktool
- Android
- java
---



# ApkTool

> 解包安卓安装包的基础工具

- 安装java环境

- 设置到环境变量

- `github`下载并安装[iBotPeaches/Apktool: A tool for reverse engineering Android apk files](https://github.com/iBotPeaches/Apktool)
- 开始解包`APK`安装包

```
java -jar .\apktool_3.0.2.jar d D:\Workspace\Andriod\moneyReverse\base.apk -o D:\Workspace\Andriod\moneyReverse\test
```

调用`apktool`工具将`base.apk`解包到`test`文件夹，通过解包后的smali文件可以看出函数逻辑

![image-20260621090827042](./image-20260621090827042.png)

# Jadx

> 用于逆向smali文件为java文件，更便于分析逻辑

- `gui`且带`jre`环境的版本无需过多解释，拖进去直接解包

![image-20260620235256559](./image-20260620235256559.png)

- 牛大了！直接解包成`Java`项目，里面每一条代码都清晰可读（除了`so`文件），用`Android SDK`开发更是舒服

  ![image-20260621090915614](./image-20260621090915614.png)

  显然，比`APKTool`解包出来的结构要清晰多了。

# IDA Pro

> 反编译成汇编，可读性一般但也能读

# Sandboxie-Plus

> 经典国产软件装沙箱防流氓

- 夸克是真沙避啊在`D`盘创建个`ProgramData`塞他喵的`VedioCache`，设置为`C`盘创建也无效那你给我这个设置干嘛？？进沙箱吧孩子......

# 解包分析过程

- 用`Jadx`解为`Java`项目后可读性好很多，于是直接`file`搜索”双紫擒龙“这个功能，发现其实际为 “追踪主力”即`SKILL_ZLZZ`
- 顺着往下摸到了`NewIndexMathTool.java`这个整合指标和数据的库文件

- 于是让Copilot帮我分析完整个`SKILL_ZLZZ`计算流程

  ![image-20260621093659651](./image-20260621093659651.png)

- 至此就挖到了这个指标的计算公式，由于计算指标所需要的数据普通用户也可以获取，所以接下来想用这个功能就得解除`VIP`权限来显示了。
- 通过`isVip`关键词查找验证逻辑（待完成）































