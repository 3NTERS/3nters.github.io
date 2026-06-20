---
title: SQL数据库安装失败总结
date: 2022-10-24 17:07:40
categories: [SQL,环境搭建]
tags: SQL
---
> 信息技术课程要求学习使用`SQL`数据库的增删查改，我学习前端那必然是要多总结点啦！

# 前言
`SQL`安装失败,报错信息为`等待数据库引擎恢复句柄失败`，搜索尝试过一些，最后在知乎大佬的回答下找到了我的解决办法。
我将把成功的方法、已知的和尝试过的方法都写出来。
## 强制模拟扇区大小为4KB（成功方法）
- 以管理员身份打开PowerShell并输入:
    ```
    New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" -Name   "ForcedPhysicalSectorSizeInBytes" -PropertyType MultiString -Force -Value "* 4095"
    ```
- 验证修改是否完成:
    ```
    Get-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\stornvme\Parameters\Device" -Name   "ForcedPhysicalSectorSizeInBytes"
    ```
    没有报错则表明修改成功，重启安装即可。

## 格式化硬盘，删除分区并重新指定扇区大小（已知的）
（待我百度一下如何重新指定扇区大小）

## 完全删除SQL相关文件后重装（尝试但失败.）
- 控制面板卸载所有`SQL`程序。
- 在`C:\Program Files`和`C:\Program Files(x86)`中找到`SQL`相关文件删除
- 检查自定义的安装路径的文件夹并删除。
- 重启后安装。

# 分析

## 问题内容
`等待数据库引擎恢复句柄失败`

## 问题发生场景
Windows 11或较新版本的Windows 10中，安装SQL Server 2019可能失败，出现”等待数据库引擎恢复句柄失败“的错误。通常是在尝试将其安装到NVME固态硬盘上时出现问题。

## 问题发生原因
一些较新的硬件设备磁盘扇区大小在4KB以上，而SQL Server仅支持只512字节和4096字节大小的扇区。
如果要检查自己的硬盘扇区大小是否符合要求，以检查D盘为例，以管理员身份打开PowerShell并输入：
fsutil fsinfo sectorinfo D:
在返回的信息中，PhysicalBytesPerSectorForAtomicity这个值即为扇区大小。


