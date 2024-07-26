---
title: 奇奇怪怪的 Bug 集散地
description: 平时遇到的奇怪代码问题，记录并整理。
date: 2024-07-26 14:44:00+0800
image: cover.jpg
categories:
    - Tech Talk
tags:
    - Tech Talk
    - Bug Report
weight: 5       # You can add weight to some posts to override the default sorting (date descending)
---

## 前言

平时遇到一些奇怪的代码问题，记录并整理。

## 博客渲染超时

在 Hugo 中，如果博客文章较多，渲染时间会非常长，导致渲染超时。具体考量可能是因为担心无限递归之类的，hugo 使用了粗暴的解决方法，超时就中断并且报错。所以解决方法也很简单，修改 `config.toml` 文件中的 `timeout` 配置项，增加渲染超时时间，单位貌似是秒。之前一直没有看 Github 详细报错，之前又出现过 Github Actions 瘫痪，我还以为又出现了，re-run 之后也就好了，估计是因为当初体量卡在临界点上，现在彻底超时了，也就发现了这个问题。