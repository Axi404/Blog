---
title: LLM Talk 2
description: 从一些工作中扫过。
date: 2024-08-08 23:01:00+0800
image: cover.jpg
categories:
    - AI Talk
tags:
    - AI Talk
    - LLM
    - VLM
    - Embodied AI
weight: 5       # You can add weight to some posts to override the default sorting (date descending)
---

## 前言

在代表性工作之余，也有必要阅读一些其他的内容，这当然也需要总结，所以新开设一个章节，记录在这里。

## [PointLLM](https://arxiv.org/pdf/2308.16911)

![The pipeline of PointLLM](PointLLM.png)

PointLLM 可以是说十分标志的工作了，属于是中规中矩，但是效果确实很不错。就像是一般的 VLM 一样，但是只不过是将图像的模态输入换成了点云，然后使用 point encoder，总体来说改变并不算多。可以说这篇工作的诞生是符合直觉的，点云模态也可以作为一种语言进行建模。

## [EmbodiedGPT](https://arxiv.org/pdf/2305.15021)

![The pipeline of EmbodiedGPT](EmbodiedGPT.png)

EmbodiedGPT 也是一篇比较符合直觉的工作，但是不是那么的极简。本身是按照 BLIP2 的范式来的，用了一个 Embodied-Former（其实也就是 Q-former）来连接 ViT 和 LLaMA3，来做一个桥梁，之后输出一个 instance information，一个 CNN 处理图像输出一个 global information，两个 concat 一下作为 low-level policy 的输入。

本身值得说的是，一方面这种设计，为什么不单独通过 embodied-former 直接输出的 instance information 呢？毕竟也是通过了 ViT 的信息编码的，之所以还需要一个 CNN，大概率是这样做了之后发现表征能力不强，所以需要更加显式的提供一些信息。

## [RT-Trajectory](https://arxiv.org/pdf/2311.01977)

![The pipeline of RT-Trajectory](RT-Trajectory.png)

RT-Trajectory 是一个输出 low-level policy 的模型，使用了 RT-1 的框架作为动作的输出，在此之前会输入之前和当前的帧以及一个工作轨迹，这里面动作轨迹通过 R 和 G 两个通道表征了时间顺序以及高度信息，和图像一起输入。因为从文字 prompt 改为了图像（轨迹），所以本质上具有更高的细粒度，性能更好也很正常。