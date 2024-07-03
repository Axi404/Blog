---
title: Git 的常见操作
description: 日常使用的 Git 操作，丝滑小连招。
date: 2024-07-03 00:00:00+0000
image: cover.jpg
categories:
    - Tech Talk
tags:
    - Tech Talk
weight: 1       # You can add weight to some posts to override the default sorting (date descending)
---

## 前言

本篇内容写作的初衷，是由于，笔者在生活中的见闻。不少的 Git 的初学者，毫无疑问，是了解关于 Git 的大多数的基本操作的，但是对于其背后的流程却知之甚少。因此，在实际的操作中的时候，假如说进行正常的 `git clone` 之后的`add`, `commit`, `push` 操作，那么多半问题不大，但是假如说遇到了更加复杂的需求，则难免束手无策。

这便是笔者写作本内容的初衷，即尝试通过更加复杂的 Git 任务，尝试帮助读者了解一个更加完整的 Git 工作流，并丝滑地处理日常的一些基础内容之外的常见需求。

## 初始化 Github SSH

初始化 Github SSH 是每一个 Git 用户与 Github 进行交互的第一步，但是在这其中的不少流程往往引人迷惑，使得在后续的日常使用中，常常困惑于自己的配置是否合理。

