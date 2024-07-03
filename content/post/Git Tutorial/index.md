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

由于 Github 的更新，Github 的上传不再支持使用账号密码的身份验证，而是转为使用个人访问令牌或者 SSH 的方式，而其中毫无疑问，使用 SSH 是最为优雅的解决方案。SSH 生效的原理是，在本地生成的公钥私钥对，其中的公钥被上传至 Github，而在 SSH 之后，本地与 Github 建立安全连接，从而进行相关的操作。

在这里首先给出初始化 Github SSH 的详细步骤，之后再进行解释，以解决部分初学者的误区。

### 详细步骤

首先，使用 SSH 创建密钥对：

```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
# 或者 ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

其中 `ed25519` 以及 `rsa` 均是密钥生成的算法，其中 `ed25519` 是更新的算法，假如说本地不支持，则可以使用 `rsa`，本身的安全性均很高。输入之后默认回车即可，密钥会被生成至 `~/.ssh/` 中。使用 `cat` 指令可以进行查看：

```shell
cat ~/.ssh/id_ed25519.pub
# 或者 cat ~/.ssh/id_rsa.pub
```

将生成的公钥复制至 Github 中，在 Github 的 `Settings` 中的 `SSH and GPG keys` 中，点击 `Add SSH key` 进行添加即可。

### 理解误区

在这一过程中，我们注意到，包括说互联网中绝大多数的常见教程，均会使用 `-C "your_email@example.com"` 这一行指令，而与此同时，`git config` 以及 Github 均存在邮箱地址这一配置内容。

