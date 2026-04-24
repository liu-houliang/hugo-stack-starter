---
title: "样式自定义指南"
description: "如何修改本模板的颜色、字体和各组件样式，使博客具有你的个人风格。"
date: 2026-04-13
lastmod: 2026-04-23
categories:
    - Tutorial
tags:
    - Hugo
    - SCSS
    - 样式定制
---

本模板的样式系统基于 SCSS，所有自定义样式都在 `assets/scss/` 目录下，**不需要修改主题源文件**。

---

## 修改主题色

打开 `assets/scss/custom.scss`，修改 `:root` 中的 CSS 变量：

```scss
:root {
    /* 亮色模式 */
    --accent-color: #1B365D;           /* 主色调：按钮、链接、高亮 */
    --accent-color-darker: #202A44;    /* 主色调深色版：hover 状态 */
    --accent-color-text: #FFF;         /* 主色调上的文字颜色 */
    --body-background: #f8f7f2;        /* 页面背景 */
    --card-background: #fdfdfb;        /* 卡片背景 */
    --body-text-color: #2D3748;        /* 正文文字颜色 */

    &[data-scheme="dark"] {
        /* 暗色模式覆盖 */
        --body-background: #101214;
        --card-background: #1c2128;
        /* ... */
    }
}
```

保存后 Hugo 自动重新编译，浏览器立即刷新。

### 常用配色方案参考

**紫色系**：
```scss
--accent-color: #7C3AED;
--accent-color-darker: #6D28D9;
```

**绿色系**：
```scss
--accent-color: #059669;
--accent-color-darker: #047857;
```

**橙色系**：
```scss
--accent-color: #EA580C;
--accent-color-darker: #C2410C;
```

---

## 修改代码块样式

代码块相关样式在 `assets/scss/partials/custom-components/_code.scss`。

### 关闭 Mac 风格顶栏

如果不喜欢 macOS 三色圆点，注释掉以下代码：

```scss
/* 注释掉这个 before 伪元素即可关闭顶栏 */
/*
.article-content .highlight:before {
    ...
}
*/
```

### 修改折叠阈值

在 `_code.scss` 和 `layouts/_partials/footer/custom.html` 中，将 `600` 改为你想要的像素值：

```scss
/* _code.scss */
&.collapsed {
    max-height: 400px;  /* 改为你想要的高度 */
}
```

```js
/* custom.html 中的 JS */
const MAX_HEIGHT = 400;  /* 与 CSS 保持一致 */
```

---

## 添加自定义字体

在 `assets/scss/custom.scss` 中添加 Google Fonts 并设置字体：

```scss
/* 引入字体 */
@import url('https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;700&display=swap');

/* 应用到正文 */
body {
    font-family: 'Noto Serif SC', serif;
}

/* 应用到文章内容 */
.article-content {
    font-family: 'Noto Serif SC', serif;
    line-height: 1.9;
}
```

> **注意**：国内访问 Google Fonts 可能较慢，可以考虑使用 jsDelivr 加速或自托管字体。

---

## 组件样式文件说明

| 文件 | 作用 |
|------|------|
| `custom.scss` | 全局变量、TOC 滚动条 |
| `_code.scss` | 代码块全部样式 |
| `_footer.scss` | Footer 运行时长按钮 |
| `_homepage-grid.scss` | 首页双栏网格 |
| `_mobile-menu.scss` | 移动端顶部导航栏 |
| `_timeline.scss` | 时间线 Shortcode 样式 |
| `_title.scss` | 标题分割线 Shortcode 样式 |

每个文件职责单一，可以独立修改，不互相影响。

---

## 关闭首页网格布局

如果偏好传统的单列列表，编辑 `params.toml`：

```toml
[homepage]
    grid = false
```

---

## 覆盖主题布局

如果需要修改主题的其他布局文件，在 `layouts/` 目录下创建同名文件即可覆盖：

例如，要修改文章页布局，在 `hugo-theme-stack-v4/layouts/single.html` 中查看原文件，然后复制到 `layouts/single.html` 并修改。

> Hugo 的覆盖机制会优先使用项目根目录下的同名文件，主题文件作为后备。
