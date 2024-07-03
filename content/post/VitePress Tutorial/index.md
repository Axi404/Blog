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

## 项目结构

了解 VitePress 的项目结构是为 VitePress 做贡献的基本事项，一般来说，VitePress 的结构为：

```txt
├───.github
├───docs
│   ├───.vitepress
│   │   ├───cache
│   │   └───theme
│   ├───images
│   ├───public
│   ├───folders
│   └───index.md
├───node_modules
├───.gitignore
├───package.json
├───pnpm-lock.yaml
├───tsconfig.json
```

对于贡献者来说，仅需要关注 `docs` 文件夹即可，`docs` 文件夹下包含了 VitePress 的配置文件，以及所有的 Markdown 文件。其中作为初级的贡献者，需要了解的是 `docs` 中的若干文件夹，并且对于新建的文档按照以下的步骤，在这里以项目 [SurviveXJTU](https://xistudygroup.github.io/SurviveXJTU/) 为例。

## 贡献流程

### 撰写文档

首先，搞清楚自己想要构建哪一部分的文档，例如想要贡献一则 `人生篇` 中的内容，那么前往 `docs` 下的 `人生篇` 文件夹中，新建一个 Markdown 文档，并且撰写其中的内容。在这里需要注意的是，Markdown 文档对于完全的计算机领域初学者来说，可能并不能很好的驾驭，了解一些基础语法有助于帮助读者更好的撰写文档，在这里可以参考较为经典的 [Markdown 官方教程](https://markdown.com.cn/basic-syntax/)。

### 添加至 Sidebar

`SurviveXJTU` 的侧边栏使用人为的创建形式，这是为了更大限度的排版布局自由度，有的时候不同章节之间的内容，在写作的过程中存在顺序之分，而使用如 `vitepress-sidebar` 等插件自动生成 `Sidebar` 虽然快捷，但是很可能导致内容按照如字典序等方式进行排序，从而无法更好的符合写作者的意愿。

前往 `docs/.vitepress/config.mts` 中，可以在找到如下文所示内容，以下以其中的人生篇为例：

```ts
export default defineConfig({
    ...
    themeConfig:{
        sidebar: [
            {
                text: '人生篇',
                link: '/人生篇/',
                collapsed: true,
                items: [
                    ...
                    { text: '关于西交', link: '/人生篇/关于西交' },
                    { text: '开源精神', link: '/人生篇/开源精神' },
                ]
            }
        ]
    }

})
```

在其中找到你想要插入的位置，VitePress 会根据 items 中的顺序来排列 Sidebar，例如读者创建了文档 `人生思考`，并认为在排版布局中应位于 `关于西交` 与 `开源精神` 之间，则加入一列即可：

```ts
export default defineConfig({
    ...
    themeConfig:{
        sidebar: [
            {
                text: '人生篇',
                link: '/人生篇/',
                collapsed: true,
                items: [
                    ...
                    { text: '关于西交', link: '/人生篇/关于西交' },
                    { text: '人生思考', link: '/人生篇/人生思考'}
                    { text: '开源精神', link: '/人生篇/开源精神' },
                ]
            }
        ]
    }

})
```

其中之所以为如下路径，包括几个前提：

- 读者撰写的文档位于 `docs/人生篇/` 文件夹中
- 读者的文档名为 `人生思考.md`
- 读者想要将文档显示为 `人生思考`

更多内容可以参考 SurviveXJTU 中的具体实现。

### 提交 PR

在进行了撰写之后，则可以根据正常的流程进行 PR，前提是读者已经对仓库进行了 fork，如上的修改发生在通过 `git clone` 复制自己的仓库之后的本地内容中，使用 `git add .`, `git commit -m "update"`, `git push -u origin main` 进行推送，并且在 Github 页面提交 PR 即可。

## 结语

限于篇幅以及内容的设计，本篇内容可能暂时截止于此，更多的内容会在后续选择性地在此处更新，或者新建新的博客进行分享，希望本博客可以帮助读者更好的了解 VitePress 的写作流程，并为相关的开源项目做出更多的贡献。