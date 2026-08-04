# 🌐 nvidiaction 的个人博客

> 永远相信美好的事情即将发生 ✨

基于 [Astro 5](https://astro.build) 和 [Svelte 5](https://svelte.dev) 构建的个人博客，基于 [Fuwari](https://github.com/saicaca/fuwari) 响应式主题打造。

🔗 **在线访问**: [https://nvidiaction.github.io](https://nvidiaction.github.io)

---

## ✨ 博客特性

- 🚀 **极速体验**: 基于 Astro 静态生成 (SSG)，轻量且高性能
- 🎨 **精美设计**: 响应式布局，支持亮色 / 暗色模式及平滑页面过渡
- 🔍 **本地搜索**: 基于 [Pagefind](https://pagefind.app/) 的高效静态全文搜索
- 💬 **评论系统**: 基于 [Giscus](https://giscus.app/) (GitHub Discussions)
- 📝 **丰富扩展**: 支持 Markdown / MDX、Expressive Code 代码高亮与折叠、KaTeX 数学公式渲染、PhotoSwipe 图片预览等
- 🏷️ **分类与标签**: 清晰的内容归档与标签分类整理

---

## 🛠️ 技术栈

- **框架**: Astro (`v5.13.10`) + Svelte (`v5.39.8`)
- **样式**: Tailwind CSS + Stylus + PostCSS
- **包管理器**: pnpm (`v9.14.4`)
- **规范与格式化**: Biome

---

## 💻 本地开发指南

### 前置要求

- Node.js >= 20
- pnpm >= 9 (`npm install -g pnpm`)

### 启动项目

```bash
# 1. 克隆仓库
git clone https://github.com/nvidiaction/nvidiaction.github.io.git
cd nvidiaction.github.io

# 2. 安装依赖
pnpm install

# 3. 启动开发服务器
pnpm dev
```

### 常用命令

| 命令 | 说明 |
| :--- | :--- |
| `pnpm dev` | 启动本地开发服务器 (`http://localhost:4321`) |
| `pnpm build` | 构建生产环境产物并生成 Pagefind 搜索索引 |
| `pnpm preview` | 在本地预览生产构建产物 |
| `pnpm new-post <filename>` | 快速创建一篇新的 Markdown 博客文章 |
| `pnpm check` | 运行 Astro 语法与类型检查 |
| `pnpm format` | 使用 Biome 格式化代码 |

---

## 📝 文章创作说明

可以使用以下命令快速创建新文章：

```bash
pnpm new-post my-first-post
```

生成的 Markdown 文件位于 `src/content/posts/` 目录，Head 元数据 (Frontmatter) 规范示例：

```yaml
---
title: 我的第一篇文章
published: 2026-08-05
description: 这是文章的简要描述
image: ./cover.jpg # (可选) 封面图片路径
tags: [前端, Astro]
category: 技术分享
draft: false # 设置为 true 则不公开发布
---
```

---

## 📄 开源协议

本项目基于 [MIT License](LICENSE) 开源。
