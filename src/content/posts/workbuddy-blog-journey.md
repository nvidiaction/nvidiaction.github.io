---
title: 用 WorkBuddy 搭了一个个人博客——全过程记录
published: 2026-07-18
description: 从选型到上线的完整记录：用 AI 搭一个 Astro 静态博客，集成可视化 CMS，一键 GitHub Pages 部署。
tags:
  - WorkBuddy
  - Astro
  - 博客
  - 教程
category: 技术
lang: zh_CN
---

## 缘起

一直想有个自己的博客，写写技术、生活、各种想法。这件事拖了很久——总觉得要"先想好再动手"，于是永远在想。

这次决定换一种方式：找一个 AI 帮我一起搭。打开 WorkBuddy，告诉它「我要一个个人博客网站」，然后开始。

## 选型：为什么要选 fuwari

WorkBuddy 没有直接猜我的需求，而是先给了 4 条路线，让我做选择题：

| 路线 | 特点 | Stars | 更新 |
|---|---|---|---|
| astro-paper | 纯博客、SEO 友好 | 4.8k | 11 天前 |
| fuwari | 极简美观、暗色友好 | 4.8k | 4 个月前 |
| astrowind | 博客+落地页一体、Astro v6 | 5.8k | 6 周前 |
| tailwind-nextjs-starter-blog | Next.js 技术博客标杆 | 10.5k | 5 个月前 |

我下意识的反应是「选 Stars 最多的」，但 WorkBuddy 用 GitHub API 拉了真实的最后提交时间（`pushed_at`），数据摆在面前让我自己做判断。

最后我选了 **fuwari**——它足够轻、颜值在线、暗色模式开箱即用，作为一个纯博客场景，定位最干净。

## 搭建过程（和踩的坑）

### 第 1 坑：corepack 路径

环境是受管的 Node 22.22.2，Git Bash 下裸调 `corepack` shim 会把路径拼成 `C:\c\Users\...`，直接崩掉。

**解决**：用 `node <corepack.js> pnpm <cmd>` 直接调 JS 入口，再加 `COREPACK_ENABLE_DOWNLOAD_PROMPT=0`。

### 第 2 坑：preinstall 守卫

fuwari 的 `package.json` 里有 `preinstall: npx only-allow pnpm`，裸 pnpm 跑时 `npx` 不在 PATH 里又崩。

**解决**：`pnpm install --ignore-scripts`——反正我们本就用 pnpm，守卫没用。

### 第 3 坑：pagefind 二进制

`--ignore-scripts` 跳过了 pagefind 的 postinstall 下载，本地 `build` 会缺少搜索二进制。

**不解决**（有意识地选择）：这个只影响本地构建，CI 部署时 pagefind 会正常下载。本地开发用 `astro dev` 完全不受影响。

这些坑 WorkBuddy 都记到了项目记忆里——下次重来时不会再踩一遍。

## 可视化写作管理：Pages CMS

博客搭好了，但我不想像传统方式那样每次写文章都开代码编辑器改 `.md` 文件。我想要一个「点点就能写」的界面。

WorkBuddy 帮我调研了几种方案：

| 方案 | 特点 |
|---|---|
| **Pages CMS**（我选的） | 开源 MIT、原生支持 Astro、类 Notion 编辑器、GitHub 登录即用 |
| Decap CMS | 老牌、成熟、后台部署在站内 `/admin` |
| Keystatic / Tina | 也不错但更重 |

WorkBuddy 写好了 `.pages.yml` 配置文件，把 fuwari 的所有文章字段（标题、日期、标签、分类、正文等）都映射好。以后我在浏览器就能写文章，保存即提交 GitHub、触发重新部署。

## 部署到 GitHub Pages

部署选了最简单的路——GitHub Pages，免费、零运维。

WorkBuddy 帮我写了一整套 CI/CD 工作流（`.github/workflows/deploy.yml`）：

```
push main → pnpm build（含 pagefind 搜索索引）→ upload artifact → 上线
```

之后每次写完文章、点保存，自动完成从提交到上线的全过程。

唯一的手动操作是给仓库改了个名字：从 `fuwari-2026` 改成了 `nvidiaction.github.io`，这样博客就能在根域名访问，路径更干净。

最终地址：**https://nvidiaction.github.io/**

## 个性化

一套橘色主题、改了站点名和简介、换了自己的头像——不到 5 分钟就搞定。

比较有趣的一个细节：头像放在 `src/assets/images/` 里，Astro 构建时自动优化成 webp 格式并加了内容 hash，用户不用管图片优化的事。

## 对 WorkBuddy 的感受

整个过程中 WorkBuddy 的角色更像一个**有经验的技术伙伴**，而不是搜索引擎的升级版。几个让我印象深刻的点：

1. **不说"我可以帮你"的废话**——直接给结论和方案，不行就换一个方向。
2. **自己先踩坑然后记下来**——corepack 路径问题、preinstall 守卫、pagefind 二进制，每一个坑都记录了具体原因和解决方式，不会重复踩。
3. **有观点**——在几个候选模板、CMS 方案、部署方式上，都有明确的推荐和理由，而不是丢一堆选项让我自己懵。
4. **能接住"然后呢"这种模糊指令**——不需要每次都把需求重新解释一遍。
5. **项目记忆是真的在积累**——同一个 session 里的上下文、踩坑记录、决策历史，后面都能用上。

当然也有不能做的：GitHub 认证相关的事情（需要我手动登录）、配置文件中 TS 类型之外的改动。但这些本来就是该用户自己控制的边界。

## 现在的成果

| 维度 | 当前状态 |
|---|---|
| 框架 | Astro 5 + fuwari 模板 |
| 写作 | Pages CMS 可视化编辑器（浏览器操作） |
| 评论 | 👆 已接入 Giscus（用 GitHub 登录评论） |
| 部署 | GitHub Pages，自动 CI/CD |
| 搜索 | Pagefind 全文搜索 |
| 主题 | 橘色调、深色/浅色自适应 |
| 统计 | 已接入访问统计 |

## 下一步

- 多写点文章把内容填起来
- 如果需要，换成自定义域名

如果你也在犹豫要不要搭一个自己的博客，我的建议是：别想太多，找一个 AI 陪你一起，从选模板到上线，半天就能搞定。

---

*这篇文章本身就是用 WorkBuddy 写的。*
