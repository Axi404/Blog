---
title: LLM Talk 2
description: 从一些工作中扫过。
date: 2024-07-26 14:22:00+0800
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

PointLLM 可以是说十分标志的工作了，属于是中规中矩，但是效果确实很不错。就像是一般的 VLM 一样，但是只不过是将图像的模态输入换成了点云，然后使用 point encoder，总体来说改变并不算多。可以说这篇工作的诞生是符合直觉的，点云模态也可以作为一种语言进行建模。