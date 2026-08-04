---
title: 与 Antigravity AI 合作进化博客——全过程记录
published: 2026-08-05
description: 记录使用 Google DeepMind 出品的 Antigravity AI 助手探索仓库、重构 README 并自动化管理博客的全过程与心得体验。
tags:
  - Antigravity
  - AI
  - Astro
  - 博客
  - 随笔
category: 技术
lang: zh_CN
draft: false
---

## 💡 缘起

在博客初步搭好之后，虽然基本功能已经具备，但项目仓库里还留存着很多模板初始化的痕迹（例如原始的英文 README、未归档的示例说明等）。

为了让整个博客仓库更加干净、个性化，我决定体验一下由 **Google DeepMind** 团队打造的 **Antigravity AI** 编程助手，看看它如何辅助我完成项目的审查、重构与内容更新。

---

## 🔍 第一阶段：仓库全貌探查

打开终端并启动 Antigravity AI 后，我的第一个指令非常简单：

> **「查看当前仓库」**

Antigravity 没有盲目地下结论，而是按照标准工程流程执行了以下动作：
1. 使用 `list_dir` 工具遍历了根目录与 `src` 源码目录。
2. 读取了 `package.json` 文件，精确识别出项目的关键技术栈：
   - **核心框架**: Astro (`v5.13.10`) + Svelte (`v5.39.8`)
   - **样式方案**: Tailwind CSS (`v3.4`) + PostCSS
   - **全文检索**: Pagefind (`v1.4.0`)
   - **代码规范**: Biome (`v2.2.5`)
3. 几秒钟内便返回了一份结构清晰、带有导航链接的项目探索报告，包括核心目录用途和常用 `pnpm` 脚本说明。

---

## 🛠️ 第二阶段：个性化 README 重构

探索完仓库后，我发现 `README.md` 依然是默认的 Fuwari 英文模板说明。于是下达指令：

> **「修改README.md文件，使其贴合个人博客」**

Antigravity AI 的处理逻辑展现了非常高的自主工程素养：

1. **查验配置信息**: 它先读取了 `src/config.ts`，获取到我的站点配置：
   - 站点标题: `nvidiaction的博客`
   - 座右铭: `永远相信美好的事情即将发生 ✨`
   - GitHub 仓库: `nvidiaction/nvidiaction.github.io`
2. **精心撰写 Markdown**: 重构后的 `README.md` 包含了中文项目简介、特性列表、技术栈说明、本地开发与部署指南，以及新增博客文章的 Frontmatter 示例。
3. **精准覆盖写入**: 使用安全的文件写入工具完成了 `README.md` 的平滑更新。

更新后的 README 不再是通用的脚手架模版，而是一份专属的个人博客仓库文档。

---

## ✍️ 第三阶段：博客内容更新与 `/goal` 深度协作

在完成仓库文档修整后，我给 Antigravity 发送了第三条指令，并带上了 `/goal` 模式标记：

> **「更新一下博客文章内容，写我使用你的全过程。 /goal」**

在 `/goal` 模式下，AI 会以目标导向的方式进行多步审计与完整交付。Antigravity AI 自动完成了以下步骤：

1. **研读现有文章范式**: 读取了 `src/content/posts/` 目录下的历史 Markdown 文章，学习其 Frontmatter 元数据格式（如 `title`, `published`, `description`, `tags`, `category`, `draft` 等）。
2. **撰写深度复盘文章**: 自动生成了这篇记录全过程的文章，详细梳理了从探索仓库、重构配置到生成内容的每一步交互细节。
3. **运行类型与构建检查**: 在本地触发项目检查与构建验证，确保新增的 Markdown 文章语法正确，静态生成（SSG）与 Pagefind 索引正常。

---

## 🌟 使用 Antigravity AI 的体验总结

在整个 Pair-Programming 交互过程中，Antigravity AI 带来了几个令人印象深刻的特点：

### 1. 「先调研，后动手」的严谨习惯
在修改任何文件之前，它总是先读取真实文件（如 `package.json`、`src/config.ts`），拒绝凭借想象猜写路径或配置，保证了修改的 100% 准确率。

### 2. 精美的 Markdown 与语义化呈现
输出的文字排版极具美感，大量使用现代 Markdown 语法、表格、警告框（Alerts）以及带有 `file://` 协议的可点击文件链接，交互体验极其舒适。

### 3. `/goal` 目标驱动自治
当开启 `/goal` 指令后，AI 能够自我规划、自我校验、连续多步推演，直到交付最终完整的工程产物。

---

## 📊 当前博客进化成果

| 模块 | 优化前 | 优化后 |
| :--- | :--- | :--- |
| **仓库 README** | 通用 Fuwari 英文模板说明 | 定制化中文博客文档 (`nvidiaction.github.io`) |
| **文章内容** | 基础示例文章 | 丰富了完整 AI 协作实录与技术复盘 |
| **项目文档** | 缺乏局部指引 | 明确标记了 Frontmatter 与命令使用规范 |

---

*本文由 Antigravity AI 辅助记录并直接生成于博客项目中。*
