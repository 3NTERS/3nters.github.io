---
title: Vscode+tailscale实现远程连接训练
typora-root-url: ssh+tailscale实现远程连接训练
date: 2026-06-29 20:13:47
categories: 计算机基础知识
tags:
- ssh
- 远程连接
---

## Ubuntu端(Server)

### SSH

```
# 安装
sudo apt update
sudo apt install openssh-server

# 启用且设置开机自启动
sudo systemctl enable ssh

# 检查SSH状态
sudo systemctl status ssh

# 生成密钥
ssh-keygen -t 
```

### Tailscale

> 很好用的内网穿透工具

```text
# 一键安装 Tailscale
curl -fsSL https://tailscale.com/install.sh | sh

# 启动 Tailscale 并登录
sudo tailscale up

# 查询tailscale状态与ip
tailscale status
tailscale ip
```

## Windows端(Client)

### SSH

一般`windows11`内置`openssh.client`， 可以通过管理员运行`powershell`命令查询

```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
```

### Tailscale

[Download | Tailscale](https://tailscale.com/download/windows)下载Windows版的`Taiscale`并登录，点击`Add device`将本机添加到局域网即可

### Vscode

- 安装`Remote-SSH`插件

- 点击加号新建远程并输入`ssh name@ip`其中 `name`指的是连接的电脑账户名称,`ip`就是前面`tailscale ip`查出来的`ip`

  ![image-20260629230815842](./../Vscode+tailscale实现远程连接训练/image-20260629230815842.png)![image-20260629230840705](./../Vscode+tailscale实现远程连接训练/image-20260629230840705.png)

- 选择默认`config`配置后输入密码连接就可以了

## Tmux

> 用来保持训练在后台运行，不会因为ssh终端关闭而停止

```
# 创建窗口
tmux new -s throw

# 断开窗口 
# ctrl+b再按d

# 重新连接窗口 
tmux ls # 查看正在运行的窗口
tmux attch -t throw # 连接任务名为 throw 的窗口

# 完全结束窗口进程
# ctrl+d
```

