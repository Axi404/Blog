---
title: VitePress 贡献指南
description: 如何对于 VitePress 项目进行贡献，快速看懂项目结构，并构建自己的项目。
date: 2024-07-03 00:00:00+0000
image: cover.jpg
categories:
    - Tech Talk
tags:
    - Tech Talk
weight: 1       # You can add weight to some posts to override the default sorting (date descending)
---

## 前言

惯例的写一下前言，关于为什么要写这篇内容，以及这篇内容的主旨是什么。

笔者最近开设了几个 VitePress 项目的网站，并且作为开源项目，开放给社区以及每一个人。毫无疑问，诸如 VitePress 类型的静态网页生成器，是一种极大的对于创作的便利，使得创作者无需关注于网站的构建，只需要专注于内容的创作。但是对于完全没有互联网基础的同学来说，这种内容甚至也已经超纲了，我们迫切需要一种类似于 Word 或者说 Markdown 编辑器这样子的开箱即得的记录方式，使得最不了解技术的创作者也可以尽情的创作。

事实上这种内容是存在的，使用前后端的博客可以很轻易的达到这种效果，但是明显，目前因为种种原因而选择使用 VitePress 之后，一个为不了解技术的同学设计的 VitePress 贡献指南是有必要的，这可以帮助读者了解 VitePress 的基本结构，并且可以快速上手，对于 VitePress 项目进行贡献。

## 什么是 VitePress

VitePress 是一个基于 Vite 的静态网页生成器，它使用 Vue 作为其核心，并使用 Markdown 作为其内容格式。VitePress 的主要目标是提供一个简单而高效的方式来创建和维护静态网站，同时提供丰富的插件和主题来满足不同用户的需求。

换句话来说，使用 VitePress，可以很轻易地通过 Markdown 格式的内容生成精美的静态网页，因此是很好的百科/博客类内容的载体。