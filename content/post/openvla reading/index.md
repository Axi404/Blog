---
title: OpenVLA 代码笔记
description: OpenVLA 纯小白代码阅读记录。
date: 2024-07-23 09:00:00+0800
image: cover.jpg
categories:
    - AI Talk
tags:
    - Tech Talk
    - LLM
    - Code Reading
    - Embodied AI
weight: 5       # You can add weight to some posts to override the default sorting (date descending)
---

因为要开始入门具身智能，所以说要阅读代码，显然选择了开源的 OpenVLA，于是在这里记录一下代码的阅读过程。

本人代码水平为，掌握 Pytorch 大多数语法，对于 Hugging Face 不太了解。故部分内容会省略，尽量做到大多数内容均详实。

## OpenVLA

OpenVLA 是一个具身智能大模型，Open 在这里就是 Open Source 的意思，于是使用其开源代码，开源网址为 [https://github.com/openvla/openvla](https://github.com/openvla/openvla)。

## 代码结构

直接运行一个 `tree`，看一下代码结构：

```txt
├───prismatic
│   ├───conf
│   ├───extern
│   │   └───hf
│   ├───models
│   │   ├───backbones
│   │   │   ├───llm
│   │   │   │   └───prompting
│   │   │   └───vision
│   │   ├───vlas
│   │   └───vlms
│   ├───overwatch
│   ├───preprocessing
│   │   └───datasets
│   ├───training
│   │   └───strategies
│   ├───util
│   └───vla
│       └───datasets
│           └───rlds
│               ├───oxe
│               │   └───utils
│               └───utils
├───scripts
│   ├───additional-datasets
│   └───extern
└───vla-scripts
    └───extern
```

其中首先关注如何从头训练，于是关注 `vla-scripts/train.py` 这个文件。

## 模型训练

### 主文件

