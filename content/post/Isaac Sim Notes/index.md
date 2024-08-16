---
title: Isaac Sim 踩坑日记
description: 关于 Isaac Sim，注定还有一段漫长的路。
date: 2024-08-16 19:20:00+0800
image: cover.png
categories:
    - Tech Talk
tags:
    - Tech Talk
    - Embodied AI
    - Isaac Sim
weight: 5       # You can add weight to some posts to override the default sorting (date descending)
---

## 前言

因为科研的需要，所以说需要安装一下仿真的环境，领域里面最通用的环境就是 Isaac Sim 了，但是据说也比较复杂，老师推荐了另一个 simulator（Sapien），说是比较轻量级，但是为了以后和其他工作更好地对接，以及之后估计半年多一年还是远程，有必要成为模拟器大师，于是挑战一下自己。

这篇日记依然和 LLM Talk 系列一样，应该是无限期更新的，包括说正常的安装以及操作的一些记录（对于一些涉密的内容，不会涉及），一些模块的学习，以及一些报错的整理。一方面是给自己作为一个笔记，一方面也是假如说有将来的同学进组，可以有一些更加明确的指引。毕竟本人是英文苦手，看英文的速度完全做不到“扫过”，所以还是有必要记录一下的。

## 安装 Isaac Sim

首先先简单说一下什么是 Isaac Sim，这是一个在 Nvidia 的 omniverse 下的一个 App，可以完成各种的仿真，也支持 ROS 的接口（虽然我目前还不知道 Embodied 的这一套流程是否和 ROS 有接壤），所以说做机器人这方面，用这个的比较多。而且这个东西是可以生成 image（镜像）并且运行在服务器上的，所以说各种意义上的符合具身智能领域的各种需求。

既然是 Nvidia 的产品，拥有一个 Nvidia 的账号也就是必须的事情了，一般来说还是推荐通过谷歌邮箱之类的 Mail 去注册，在这里不去赘述这个事情。

### 环境概述

按照常规的教程来说，反正首先概述一下环境。本人的环境如下，作为参考，当然，这套环境貌似在一些性能上不是很可以，不知道能否坚持到最后：

以下是 CPU 以及系统信息：

```text
root:~$ linuxlogo -a
              .-. 
        .-'``(|||) 
     ,`\ \    `-`.               88                         88 
    /   \ '``-.   `              88                         88 
  .-.  ,       `___:    88   88  88,888,  88   88  ,88888, 88888  88   88 
 (:::) :        ___     88   88  88   88  88   88  88   88  88    88   88 
  `-`  `       ,   :    88   88  88   88  88   88  88   88  88    88   88 
    \   / ,..-`   ,     88   88  88   88  88   88  88   88  88    88   88 
     `./ /    .-.`      '88888'  '88888'  '88888'  88   88  '8888 '88888' 
        `-..-(   ) 
              `-` 

Linux Version 5.15.0-117-generic, Compiled #127~20.04.1-Ubuntu
16 2.14GHz Intel i7 Processors, 128TB RAM, 73728 Bogomips Total
```

以下是显卡信息，因为是笔记本，我的显卡是 8GB 的 RTX 3070 Laptop：

```text
root:~$: nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2022 NVIDIA Corporation
Built on Mon_Oct_24_19:12:58_PDT_2022
Cuda compilation tools, release 12.0, V12.0.76
Build cuda_12.0.r12.0/compiler.31968024_0
```

我的电脑是 Dell 的 Alienware m15 R6。

### 下载 omniverse-launcher

