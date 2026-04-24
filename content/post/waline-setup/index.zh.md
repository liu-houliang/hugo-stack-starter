---
title: "配置 Waline 评论区"
description: "使用 Waline 为你的博客添加免费的评论功能，本文引导你参考官方文档完成部署，并在本模板中完成配置。"
date: 2026-04-11
lastmod: 2026-04-23
weight: 3
categories:
    - Tutorial
tags:
    - Hugo
    - Waline
    - 评论
    - Vercel
---

[Waline](https://waline.js.org/) 是一款安全、简洁的评论系统，支持 Markdown，免费部署，无需用户注册即可评论。

本模板已内置 Waline 集成，只需部署好服务端并填写一行配置即可启用。

---

## 第一步：部署 Waline 服务端

请参考 **Waline 官方快速上手文档** 完成服务端的部署：

👉 [https://waline.js.org/guide/get-started/](https://waline.js.org/guide/get-started/)

官方文档提供了在 Vercel 上的**免费一键部署**方案，整个过程大约 5 分钟。

部署完成后，你会获得一个 Waline 服务地址，类似：
- `https://your-waline-project.vercel.app/` （默认 Vercel 域名）
- 或者你绑定的自定义域名

记录这个地址，下一步会用到。

---

## 第二步：在本模板中配置

编辑 `config/_default/params.toml`，填入你的服务地址：

```toml
[comments]
    enabled  = true
    provider = "waline"

[comments.waline]
    serverURL = "https://your-waline-project.vercel.app/"  # ← 填入你的地址
    pageview  = true       # 同时开启文章阅读量统计

    # 可选：自定义表情包（默认微博表情）
    emoji = ["https://unpkg.com/@waline/emojis@1.0.1/weibo"]

    # 评论必填字段
    requiredMeta = ["name"]

    [comments.waline.locale]
        admin = "Admin"    # 管理员标识
```

保存后重启 `hugo server`，文章页面底部会出现评论区。

---

## 功能说明

### 阅读量统计
设置 `pageview = true` 后，文章头部会自动显示阅读量（需要 Waline 服务端支持）。

### 评论管理后台
访问 `https://your-waline-project.vercel.app/ui/` 进入管理界面，第一个注册的账号自动成为管理员，可以审核、删除评论。

### 邮件通知
有人回复时可以通过邮件通知博主，需要在 Vercel 环境变量中配置 SMTP 信息，详见 [官方文档 - 评论通知](https://waline.js.org/guide/features/notification.html)。

---

## 常见问题

**评论区不显示？**  
检查 `serverURL` 末尾是否有斜杠 `/`，以及 Vercel 服务是否正常运行（直接访问 serverURL 应该能看到 Waline 欢迎页）。

**Cookie 提示遮住评论区？**  
如果开启了 Cookie 同意功能，用户需先接受「功能性 Cookie」后评论区才会显示。可以在 `params.toml` 中关闭 Cookie 提示，或引导用户接受。
