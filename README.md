# Hugo Theme Stack Starter

**中文** | [English](README.en.md)

一个基于 [Hugo Theme Stack v4](https://github.com/CaiJimmy/hugo-theme-stack) 的**开箱即用博客模板**，在原主题基础上做了一系列美化和功能增强。

> 📢 本项目已设置为 **GitHub Template**，点击右上角 **"Use this template"** 即可一键创建你自己的博客仓库，无需 Fork。
> 
> 🌐 **在线预览 (Live Demo)**: [https://liu-houliang.github.io/hugo-stack-starter/](https://liu-houliang.github.io/hugo-stack-starter/)

---

## ✨ 特性

| 功能 | 说明 |
|------|------|
| 🎨 **精致配色** | 深蓝 + 暖米白配色系统，亮色/暗色双模式 |
| 💻 **Mac 风格代码块** | macOS 三色圆点顶栏，悬浮复制按钮，自动折叠长代码 |
| 📐 **首页双栏网格** | PC 端两列卡片式文章列表，附封面图和 hover 动画 |
| 📱 **移动端导航** | 全新顶部导航栏，含明暗切换、语言切换、汉堡菜单 |
| 📊 **Stats 统计页** | GitHub 热力图 + 分类/标签分布 + 写作习惯分析 |
| 🕐 **运行时长** | Footer 显示博客运行天数，点击跳转统计页 |
| 🌐 **中英双语** | 内置中文/英文双语支持，一键切换 |
| 💬 **Waline 评论** | 内置 Waline 评论集成，含阅读量统计 |
| 🚀 **一键部署** | GitHub Actions 自动构建并部署到 GitHub Pages |
| 🧩 **自定义 Shortcodes** | 时间线（Timeline）、标题分割线（Title） |

---

## 🚀 快速开始

### 方式一：GitHub Template（推荐，5 分钟上线）

1. 点击页面右上角 **"Use this template"** → **"Create a new repository"**
2. 仓库设为 **Public**，填写名称后创建
3. 进入新仓库 → **Settings** → **Pages** → **Source** 选择 **"GitHub Actions"**
4. 编辑 `config/_default/config.toml`，修改 `baseurl` 和 `title`
5. 提交代码，等待 1-2 分钟后访问你的 GitHub Pages 地址 🎉

### 方式二：本地开发

```bash
# 安装 Hugo Extended 版本（>= 0.120.0）
brew install hugo          # macOS
scoop install hugo-extended  # Windows

# 克隆仓库
git clone https://github.com/你的用户名/my-blog.git
cd my-blog

# 启动本地服务
hugo server
```

访问 `http://localhost:1313` 预览。

---

## ⚙️ 基础配置

所有配置文件在 `config/_default/` 目录：

```
config/_default/
├── config.toml          # 站点标题、域名 ← 必须修改
├── languages.toml       # 多语言设置
├── params.toml          # 主题参数（评论、首页布局）
├── params.zh.toml       # 中文专属参数（头像、副标题）← 建议修改
├── params.en.toml       # 英文专属参数
├── menu.zh.toml         # 中文导航菜单
└── menu.en.toml         # 英文导航菜单
```

**最小修改清单：**

```toml
# config.toml
baseurl = "https://你的用户名.github.io/仓库名/"
title   = "我的博客"

# params.zh.toml
[sidebar]
    subtitle = "你的个性签名"

# params.toml
[footer]
    launchDate = "2024-01-01"   # 博客建站日期

[comments.waline]
    serverURL = "https://你的waline地址/"
```

> ⚠️ **重要提示**：模板默认配置了作者的 Waline 演示地址（仅供体验）。在正式使用时，请务必将其替换为你自己的 Waline 地址，否则你的评论数据将存放在他人的服务器中！详细部署教程请参考博客内置的《配置 Waline 评论区》文章。

---

## 📝 写第一篇文章

```bash
hugo new content post/my-first-post/index.zh.md
```

文章 Front Matter 示例：

```yaml
---
title: "文章标题"
description: "文章摘要"
date: 2026-01-01
categories:
    - Technology
tags:
    - Hugo
image: cover.jpg
---
```

---

## 📂 目录结构

```
hugo-stack-starter/
├── .github/workflows/deploy.yml   # GitHub Actions 自动部署
├── assets/
│   └── scss/
│       ├── custom.scss            # 颜色变量、全局样式
│       └── partials/custom-components/
│           ├── _code.scss         # 代码块样式
│           ├── _footer.scss       # Footer 运行时长
│           ├── _homepage-grid.scss # 首页网格布局
│           ├── _mobile-menu.scss  # 移动端导航
│           ├── _timeline.scss     # 时间线 Shortcode
│           └── _title.scss        # 标题分割线 Shortcode
├── config/_default/               # 所有配置文件
├── content/
│   ├── post/                      # 博客文章
│   ├── archives/                  # 归档页
│   ├── search/                    # 搜索页
│   └── stats/                     # 统计页
├── layouts/
│   ├── _default/stats.html        # Stats 统计页布局
│   ├── _partials/
│   │   ├── footer/footer.html     # 运行时长 Footer
│   │   └── sidebar/left.html      # 侧边栏（含移动端导航）
│   └── shortcodes/                # 自定义 Shortcodes
└── i18n/                          # 中英文翻译
```

---

## 🗑️ 如果只需要中文

1. 删除 `config/_default/languages.toml` 中的 `[en]` 块
2. 删除所有 `.en.toml` 和 `.en.md` 文件
3. 重启 `hugo server`

---

## 📖 文章导读

博客内置了以下教程文章（按重要性排序）：

1. **快速开始** — Template 部署 + 基础配置
2. **主题美化介绍** — 详解所有改动
3. **配置 Waline 评论** — 评论系统接入
4. **开始写博客** — Markdown 语法 + 多语言写作
5. **样式自定义指南** — 颜色、字体、布局定制
6. **Shortcodes 使用指南** — 时间线、标题分割线实战

---

## 🙏 致谢

- 主题基于 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) by [@CaiJimmy](https://github.com/CaiJimmy)
- 评论系统 [Waline](https://waline.js.org/)
- 静态站点生成器 [Hugo](https://gohugo.io/)

---

## 📄 许可证

本项目采用 [GPL-3.0](LICENSE) 许可证。
