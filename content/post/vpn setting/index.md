---
title: 校园 VPN 连接实录
description: EasyConnect + SSH 校外链接服务器。
date: 2024-08-01 19:49:00+0000
image: cover.jpg
categories:
    - Tech Talk
tags:
    - Tech Talk
    - VPN
weight: 5
---

## 前言

简单来说，这是一篇成分复杂的文章，阅读到这篇文章的读者，多半并不符合这篇文章所属的条件。简单来说，需要是，你在校外出差 + 你在校内有跳板机 + 你需要使用校内服务器跑程序，不知道会不会对一些人有帮助。

本人电脑小白一枚，所以使用的方法极有可能绕了远路，而且我没有 sftp 需求，也就懒得研究更加优雅的方式了，欢迎大家在下方评论进行补充。

## 下载 Easy Connect

学校的 SSH 分为两种，一种是 WebVPN，只能活在浏览器里面，本质上是在一个浏览器里面套了个壳子，在里面访问校内网；另一种是 SSLVPN，通过 SSL/TLS 访问内部资源的方法。