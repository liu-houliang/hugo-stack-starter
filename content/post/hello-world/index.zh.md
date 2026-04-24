---
title: "快速开始：使用 Template 一键部署博客"
description: "使用本 GitHub Template 模板，无需本地安装，直接通过 GitHub Actions 快速部署你的 Hugo 博客。"
date: 2026-04-09
lastmod: 2026-04-23
weight: 1
categories:
    - Tutorial
tags:
    - Hugo
    - 入门
    - 部署
    - GitHub Pages
---

## 欢迎使用 Hugo Theme Stack Starter

这是一个基于 **Hugo Theme Stack v4** 的开箱即用博客模板，内置美化增强、双语支持和 GitHub Actions 自动部署，**无需本地安装任何工具就能快速上手**。

---

## 方式一：GitHub Template 一键部署（推荐）

> 这是最简单的方式，全程在浏览器中完成。

### 第 1 步：使用模板创建你的仓库

1. 打开本项目 GitHub 页面
2. 点击右上角绿色按钮 **"Use this template"** → **"Create a new repository"**
3. 填写仓库名称（如 `my-blog`），选择 **Public**（GitHub Pages 免费版需要公开仓库）
4. 点击 **"Create repository"**

### 第 2 步：开启 GitHub Pages

1. 进入你新建的仓库，点击 **Settings** → **Pages**
2. 在 **"Source"** 下选择 **"GitHub Actions"**
3. 保存

### 第 3 步：修改配置

在 GitHub 网页上直接编辑 `config/_default/config.toml`：

```toml
# 改为你的 GitHub Pages 地址
baseurl = "https://你的用户名.github.io/仓库名/"
title   = "我的博客"
```

### 第 4 步：推送触发自动部署

任何一次代码提交都会触发 GitHub Actions 自动构建并部署。稍等 1-2 分钟后，访问你的 GitHub Pages 地址即可看到博客！

---

## 方式二：本地开发

如果你想在本地预览和编写：

### 安装 Hugo（扩展版）

```bash
# macOS
brew install hugo

# Windows（使用 Scoop）
scoop install hugo-extended

# Linux（apt）
sudo apt install hugo
```

验证安装（需要 Extended 版本）：

```bash
hugo version
# 输出应包含 extended
```

### 克隆并运行

```bash
git clone https://github.com/你的用户名/my-blog.git
cd my-blog
hugo server
```

访问 `http://localhost:1313` 即可预览。

---

## 基本配置说明

所有配置文件在 `config/_default/` 目录下：

| 文件 | 作用 |
|------|------|
| `config.toml` | 站点标题、域名、语言 |
| `languages.toml` | 多语言设置（中/英） |
| `params.toml` | 主题参数（评论、首页布局等） |
| `params.zh.toml` | 中文专属参数（头像、副标题） |
| `menu.zh.toml` | 中文导航菜单 |

### 必须修改的配置

**1. 站点标题和域名** (`config.toml`)：
```toml
baseurl = "https://你的域名/"
title   = "我的博客"
```

**2. 你的头像和介绍** (`params.zh.toml`)：
```toml
[sidebar]
    subtitle = "你的个性签名"
    avatar   = "img/avatar.jpg"  # 替换 assets/img/avatar.jpg
```

**3. 运行时间** (`params.toml`)：
```toml
[footer]
    launchDate = "2024-01-01"  # 博客建站日期
```

---

## 目录结构

```
my-blog/
├── .github/workflows/    # GitHub Actions 自动部署（无需修改）
├── assets/scss/          # 样式定制
│   ├── custom.scss       # 颜色、全局样式
│   └── partials/custom-components/  # 组件样式
├── config/_default/      # 所有配置文件
├── content/
│   └── post/             # 博客文章（在这里写作）
├── layouts/              # 自定义布局和 Shortcodes
└── static/               # 静态资源（图片等）
```

---

## 下一步

- 📖 [**主题美化介绍**](/post/theme-customization/) — 了解本模板做了哪些改动
- 💬 [**配置 Waline 评论**](/post/waline-setup/) — 为博客添加评论功能
- ✏️ [**开始写第一篇博客**](/post/start-writing/) — 学习 Markdown 和多语言写作

祝你写作愉快！🎉
