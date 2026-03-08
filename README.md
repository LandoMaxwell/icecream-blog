# ICECREAM 博客

使用 Hugo + 自定义布局搭建的个人博客，与 Obsidian 完美联动。

## 快速开始

### 本地预览

```bash
# 进入博客目录
cd icecream-blog

# 安装 Hugo（如果未安装）
# macOS: brew install hugo
# Windows: winget install --id Hugo.Hugo.Extended -e
# Windows: choco install hugo-extended
# Linux: sudo apt install hugo

# 启动本地服务器
hugo server -D

# 访问 http://localhost:1313
```

### 创建新文章

```bash
hugo new content posts/your-post-title.md
```

默认会自动套用 `archetypes/posts.md` 模板；也可复制 `content/posts/_template.md` 进行手动写作。

### 从已有 Markdown 发布

1. 将已有 `.md` 文件复制到 `content/posts/` 下（建议英文短横线文件名）。
2. 确保文件包含 Front Matter（至少：`title/date/draft/description`）。
3. 本地执行 `hugo --minify` 验证可构建。
4. 提交并推送到仓库默认分支，等待 GitHub Actions 自动部署。

## Obsidian 联动

### 方案：创建软链接

```bash
# 假设你的 Obsidian vault 在 ~/Obsidian
# 创建软链接将博客目录连接到 Obsidian
ln -s ~/Obsidian/01-Posts ~/Projects/icecream-blog/content/posts
```

### 写作流程

1. 在 Obsidian 中创建新笔记
2. 使用模板（可选）
3. 添加 tags 和 categories
4. 手动复制到 `content/posts/` 目录（或通过软链接）
5. 本地预览 `hugo server -D`
6. 提交到 GitHub 自动部署

### Front Matter 模板

```yaml
---
title: "文章标题"
date: 2024-01-01T10:00:00+08:00
lastmod: 2024-01-01T10:00:00+08:00
draft: false
description: "文章简介"
summary: "用于列表页与 SEO 摘要"
keywords: ["关键词1", "关键词2"]
tags: ["标签1", "标签2"]
categories: ["分类"]
images: ["/images/cover.png"]
author: "chebf"
---
```

## 部署到 GitHub Pages

1. 创建 GitHub 仓库（如 `icecream-blog`）
2. 推送代码到仓库默认分支
3. 在仓库设置中启用 GitHub Pages
4. 选择 "GitHub Actions" 作为来源（工作流：`.github/workflows/deploy.yml`）
5. 访问 `https://yourusername.github.io/icecream-blog/`

**注意**: 首次部署可能需要 1-2 分钟。

## 目录结构

```
icecream-blog/
├── content/
│   ├── posts/            # 博客文章
│   ├── about.md          # 关于页面
│   └── images/           # 文章图片
├── archetypes/           # hugo new 自动模板
├── static/               # 静态资源
├── assets/               # 资源（CSS 等）
├── layouts/
│   ├── _default/         # 页面模板
│   ├── partials/         # 可复用片段（含 SEO）
│   └── robots.txt        # 站点 robots 模板
├── hugo.toml             # 配置文件
└── .github/
    └── workflows/        # 自动部署
```

## 自定义

### 修改博客信息

编辑 `hugo.toml`：
- `title`: 博客名称
- `author`: 作者名
- `params.description`: 博客描述

### 自定义样式

在 `assets/css/extended/custom.css` 中添加自定义 CSS。

### 社交链接

在 `hugo.toml` 的 `params.socialIcons` 中添加更多社交链接。

### SEO 与抓取

- 已启用 `robots.txt`（`enableRobotsTXT = true`）
- 站点地图由 Hugo 生成：`/sitemap.xml`
- 页面级 SEO（title/description/OG/Twitter/JSON-LD）在 `layouts/partials/seo.html`

## 常用命令

```bash
# 新建文章
hugo new content posts/new-post.md

# 本地预览
hugo server -D

# 构建静态文件
hugo --minify

# 查看帮助
hugo --help
```

## 相关链接

- [Hugo 文档](https://gohugo.io/documentation/)
- [Hugo Templates](https://gohugo.io/templates/)
- [GitHub Pages](https://docs.github.com/pages)

---

祝写作愉快！
