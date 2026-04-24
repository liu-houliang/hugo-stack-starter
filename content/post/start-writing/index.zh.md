---
title: "开始写博客：Markdown 入门与多语言写作"
description: "学习如何创建第一篇博客文章，掌握 Markdown 基本语法，以及如何编写中英双语文章。"
date: 2026-04-12
lastmod: 2026-04-23
weight: 4
categories:
    - Tutorial
tags:
    - Hugo
    - Markdown
    - 写作
    - 多语言
---

## 创建第一篇文章

### 方式一：使用命令创建（推荐）

```bash
# 创建中文文章
hugo new content post/my-first-post/index.zh.md

# 同时创建对应的英文版
hugo new content post/my-first-post/index.en.md
```

Hugo 会根据 `archetypes/default.md` 模板自动填充初始内容。

### 方式二：手动创建

在 `content/post/` 下新建一个文件夹，然后在其中创建 `index.zh.md`：

```
content/
└── post/
    └── my-first-post/       ← 文章目录（名称即 URL）
        ├── index.zh.md      ← 中文正文
        ├── index.en.md      ← 英文正文（可选）
        └── cover.jpg        ← 封面图（可选）
```

---

## Front Matter 说明

每篇文章顶部的 `---` 之间的部分叫 Front Matter，用于定义文章元数据：

```yaml
---
title: "文章标题"
description: "文章摘要，显示在列表页和 SEO 描述中"
date: 2026-04-12          # 发布日期
lastmod: 2026-04-23       # 最后修改日期（可选）
draft: false              # true = 草稿，不会发布
categories:
    - Technology          # 分类（建议只选一个）
tags:
    - Hugo                # 标签（可多个）
    - Markdown
image: cover.jpg          # 封面图（相对于文章目录）
---
```

> **提示**：`date` 决定文章在列表中的排序顺序，未来日期的文章在本地预览时需要 `hugo server -F` 才能显示。

---

## Markdown 基本语法

### 标题

```markdown
## 二级标题
### 三级标题
#### 四级标题
```

> 文章正文中不使用一级标题（`# H1`），因为文章的 `title` 字段已经是 H1。

### 文字样式

```markdown
**粗体**          加粗
*斜体*            斜体
~~删除线~~        删除线
`行内代码`        代码
```

效果：**粗体**、*斜体*、~~删除线~~、`行内代码`

### 链接和图片

```markdown
[链接文字](https://example.com)
[内部链接](/post/hello-world/)

![图片描述](image.jpg)          # 相对路径（同目录下）
![图片描述](/img/photo.jpg)     # 绝对路径（static 目录下）
```

### 列表

```markdown
- 无序列表项
- 第二项
  - 嵌套项

1. 有序列表
2. 第二项
3. 第三项
```

### 代码块

````markdown
```python
def hello():
    print("Hello, World!")
```
````

支持语言高亮：`python`、`go`、`javascript`、`bash`、`toml`、`yaml`、`markdown` 等。

### 引用块

```markdown
> 这是一段引用内容
> 可以多行
```

效果：

> 这是一段引用内容

### 表格

```markdown
| 列1   | 列2   | 列3   |
|-------|-------|-------|
| 内容1 | 内容2 | 内容3 |
| 内容4 | 内容5 | 内容6 |
```

### 分割线

```markdown
---
```

---

## 多语言写作

本模板默认开启中英双语支持。

### 文件命名规则

| 文件名 | 对应语言 |
|--------|---------|
| `index.zh.md` | 中文 |
| `index.en.md` | 英文 |

两个文件放在同一目录下，Hugo 会自动关联为同一篇文章的不同语言版本。

### 只写中文版

如果你不想写英文版，只创建 `index.zh.md` 即可。

### 添加英文版

1. 在同一目录下创建 `index.en.md`
2. 翻译文章内容（Front Matter 的 `title`、`description` 也要翻译）
3. 图片等资源两个语言版本共享，无需复制

**示例**：

`index.zh.md`：
```yaml
---
title: "我的第一篇文章"
description: "这是我的第一篇博客文章"
date: 2026-04-12
---
内容...
```

`index.en.md`：
```yaml
---
title: "My First Post"
description: "This is my first blog post"
date: 2026-04-12
---
Content...
```

---

## 插入图片

### 使用文章目录下的图片（推荐）

将图片放在文章目录下，然后用相对路径引用：

```
content/post/my-post/
├── index.zh.md
├── cover.jpg       ← 封面图
└── screenshot.png  ← 文章内图片
```

在 Markdown 中：
```markdown
![截图说明](screenshot.png)
```

封面图在 Front Matter 中指定：
```yaml
image: cover.jpg
```

### 使用 static 目录下的图片

将图片放在 `static/img/` 下，用绝对路径引用：
```markdown
![图片](img/photo.jpg)
```

---

## 使用本模板的 Shortcodes

### 标题分割线

适合日记类文章的段落分隔：

```markdown
{{</* title "早晨跑步" "green" */>}}

今天跑了 5 公里，状态不错。

{{</* title "下午阅读" "blue" */>}}

读了两章《深度工作》。
```

### 时间线

适合展示经历、成长轨迹：

```markdown
{{</* timeline */>}}
{{</* timeline-item date="2024-01" */>}}
开始学习编程
{{</* /timeline-item */>}}
{{</* timeline-item date="2024-06" */>}}
完成第一个项目
{{</* /timeline-item */>}}
{{</* /timeline */>}}
```

---

## 写作建议

1. **文章目录名**即是 URL，建议用英文小写加连字符，如 `my-first-post`
2. **封面图**建议尺寸 1200×630px，这也是社交分享时的最佳尺寸
3. **description** 不超过 160 个字符，对 SEO 友好
4. 本地预览时使用 `hugo server -D` 可以看到草稿文章

祝写作顺畅！✍️
