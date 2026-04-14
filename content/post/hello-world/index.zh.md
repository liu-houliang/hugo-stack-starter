---
title: "快速入门指南"
description: "从下载本 Starter 开始，快速搭建你的 Hugo 博客，包含运行、配置和写作的完整教程。"
date: 2026-04-09
categories:
    - Tutorial
tags:
    - Hugo
    - 入门
    - 配置
    - 部署
---

## 欢迎使用 Hugo Theme Stack Starter

这是一个基于 **Hugo Theme Stack v4** 的开源博客模板 Starter。本指南将帮助你从下载本仓库开始，快速运行并自定义你的博客。

### 特性概览

- **Mac 风格代码块** - 美观的代码高亮与复制功能
- **代码折叠** - 使用 Shortcode 折叠长代码
- **标题分割线** - 使用 `title` Shortcode 创建日记/锻炼记录
- **响应式设计** - 完美适配桌面和移动设备
- **深色模式** - 自动适配系统主题
- **多语言支持** - 内置中英文支持

---

## 快速开始

### 1. 下载 Starter

```bash
# 克隆仓库
git clone https://github.com/liu-houliang/hugo-stack-starter.git my-blog
cd my-blog

# 或者下载 ZIP 解压后进入目录
```

### 2. 安装依赖

确保你已安装 Hugo（扩展版）：

```bash
# macOS (使用 Homebrew)
brew install hugo

# Windows (使用 Chocolatey)
choco install hugo-extended

# Linux
sudo apt install hugo
```

验证安装：

```bash
hugo version
```

### 3. 启动开发服务器

```bash
hugo server -D
```

访问 http://localhost:1313 查看效果。

---

## 个性化配置

### 站点基本信息

编辑 `config/_default/config.toml`：

```toml
baseURL = 'https://yourdomain.com'
languageCode = 'zh-cn'
title = '我的博客'
```

### 侧边栏信息

编辑 `config/_default/params.toml`：

```toml
[sidebar]
    compact = false
    emoji = "🚀"
    subtitle = "记录生活，分享技术"
    avatar = "img/avatar.jpg"  # 替换为你的头像
```

### 主题色

编辑 `assets/scss/custom.scss`：

```scss
:root {
    --accent-color: #1B365D;        /* 主色调 */
    --body-background: #f4f6f9;     /* 背景色 */
    --card-background: #FFF;        /* 卡片背景 */
}
```

---

## 创建文章

### 使用命令创建

```bash
# 创建中文文章
hugo new content post/my-first-post/index.zh.md

# 创建英文文章
hugo new content post/my-first-post/index.en.md
```

### 文章 Front Matter

```markdown
---
title: "文章标题"
description: "文章描述，会显示在列表页"
date: 2026-04-09
categories:
    - Tutorial
tags:
    - 标签1
    - 标签2
image: cover.jpg  # 特色图片（可选）
---

文章内容...
```

---

## 常用 Shortcodes

### 1. 折叠代码块

{{< foldcode "展开代码" "收起代码" >}}
```python
def hello():
    print("Hello, World!")
```
{{< /foldcode >}}

### 2. 标题分割线

用于日记或锻炼记录的分段：

```markdown
{{</* title "晨练 - 跑步5公里" "green" */>}}
```

效果：

{{< title "晨练 - 跑步5公里" "green" >}}

支持的颜色：red、orange、yellow、green、teal、blue、indigo、purple、pink、gray

---

## 目录结构

```
my-blog/
├── assets/              # 自定义资源（SCSS、JS）
│   └── scss/
│       ├── custom.scss              # 主样式入口
│       └── partials/
│           └── custom-components/   # 组件样式
├── config/              # 配置文件
│   └── _default/
│       ├── config.toml      # 站点配置
│       ├── params.toml      # 主题参数
│       ├── languages.toml   # 语言配置
│       └── menu.zh.toml     # 菜单配置
├── content/             # 文章内容
│   ├── post/            # 博客文章
│   ├── categories/      # 分类页面
│   └── archives/        # 归档页面
├── layouts/             # 自定义布局
│   └── shortcodes/      # 自定义 Shortcodes
├── static/              # 静态文件
│   └── img/             # 图片资源
└── README.md            # 项目说明
```

---

## 部署

### 部署到 Vercel

1. 在 GitHub 创建新仓库，推送代码
2. 在 Vercel 导入项目
3. 构建设置：
   - Framework: Hugo
   - Build Command: `hugo --gc --minify`
   - Output Directory: `public`

### 部署到 GitHub Pages

使用 GitHub Actions，创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true
          
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true
          
      - name: Build
        run: hugo --gc --minify
        
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

---

## 自定义进阶

### 修改代码块样式

编辑 `assets/scss/partials/custom-components/_code.scss`

### 添加新 Shortcode

在 `layouts/shortcodes/` 创建新的 `.html` 文件

### 修改布局

在 `layouts/` 目录下创建同名文件覆盖主题模板

---

## 示例文章

- **代码块样式演示** → [查看](/post/code-test/)
- **日记模板示例** → [查看](/post/diary-template/)
- **样式自定义指南** → [查看](/post/custom-style/)

---

## 相关资源

- [Hugo 官方文档](https://gohugo.io/documentation/)
- [Hugo Theme Stack 主题](https://github.com/CaiJimmy/hugo-theme-stack)
- [本 Starter 仓库](https://github.com/liu-houliang/hugo-stack-starter)

祝你写作愉快！🎉
