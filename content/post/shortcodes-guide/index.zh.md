---
title: "Shortcodes 使用指南"
description: "本模板内置了时间线、标题分割线等自定义 Shortcodes，本文展示所有 Shortcode 的实际渲染效果。"
date: 2026-04-14
lastmod: 2026-04-23
categories:
    - Tutorial
tags:
    - Hugo
    - Shortcodes
---

Hugo Shortcodes 是在 Markdown 中嵌入特殊组件的方式。本文展示所有自定义 Shortcode 的**实际渲染效果**。

---

## 标题分割线 (title)

适合日记、健身记录、学习笔记等需要分段小标题的内容。

**用法：**
```markdown
{{</* title "标题文字" "颜色" */>}}
```

**实际效果——不同颜色展示：**

{{< title "绿色标题" "green" >}}

这是绿色分割线下的内容，适合运动、健康类记录。

{{< title "蓝色标题" "blue" >}}

这是蓝色分割线下的内容，适合技术、学习类记录。

{{< title "橙色标题" "orange" >}}

这是橙色分割线下的内容，适合创意、设计类记录。

{{< title "紫色标题" "purple" >}}

这是紫色分割线下的内容，适合日记、随笔类记录。

{{< title "自定义颜色 #E91E63" "#E91E63" >}}

也可以直接使用十六进制颜色值。

---

## 时间线 (timeline)

适合展示个人经历、项目里程碑、技术成长轨迹等。

**用法：**
```markdown
{{</* timeline */>}}
{{</* timeline-item date="2024-01" */>}}
内容...
{{</* /timeline-item */>}}
{{</* /timeline */>}}
```

**实际效果：**

{{< timeline >}}

{{< timeline-item date="2024-01" >}}
开始学习 Hugo，了解静态博客的优势与生态。
{{< /timeline-item >}}

{{< timeline-item date="2024-06" >}}
博客正式上线，发布第一篇技术文章，收获了第一批读者。
{{< /timeline-item >}}

{{< timeline-item date="2025-01" >}}
引入 Waline 评论系统，与读者建立互动，评论区逐渐活跃。
{{< /timeline-item >}}

{{< timeline-item date="2025-09" >}}
对博客主题进行美化改造，添加 Mac 风格代码块、Stats 统计页等功能。
{{< /timeline-item >}}

{{< /timeline >}}

时间线内容支持完整 Markdown，如 **粗体**、`行内代码`、[链接](#) 等。

---

## 代码块功能（主题增强）

代码块本身不是 Shortcode，但本模板对其进行了增强：

### 复制按钮

每个代码块右上角都有复制按钮（在代码块的 macOS 顶栏内）：

```javascript
// 点击右上角的复制按钮试试
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Hugo"));
```

### 自动折叠长代码

超过 600px 高度的代码块会自动折叠，底部出现「展开代码」按钮。这是一段用于测试折叠功能的长代码：

```python
# 这段代码足够长，会触发自动折叠
import os
import sys
import json
import time
import datetime

class BlogStats:
    def __init__(self, posts_dir: str):
        self.posts_dir = posts_dir
        self.posts = []
        self.total_words = 0
        self.categories = {}
        self.tags = {}

    def scan_posts(self):
        """扫描所有文章目录"""
        for root, dirs, files in os.walk(self.posts_dir):
            for file in files:
                if file.endswith('.md'):
                    filepath = os.path.join(root, file)
                    self.parse_post(filepath)

    def parse_post(self, filepath: str):
        """解析单篇文章的 front matter"""
        with open(filepath, 'r', encoding='utf-8') as f:
            content = f.read()

        # 提取 front matter
        if content.startswith('---'):
            end = content.find('---', 3)
            if end > 0:
                front_matter = content[3:end].strip()
                body = content[end+3:].strip()
                self.total_words += len(body.split())
                self.parse_front_matter(front_matter)

    def parse_front_matter(self, front_matter: str):
        """解析 YAML front matter"""
        for line in front_matter.split('\n'):
            if line.startswith('categories:'):
                pass  # 简化处理
            elif line.startswith('tags:'):
                pass  # 简化处理
            elif line.startswith('    - '):
                tag = line.strip().lstrip('- ')
                self.tags[tag] = self.tags.get(tag, 0) + 1

    def get_report(self) -> dict:
        """生成统计报告"""
        return {
            'total_posts': len(self.posts),
            'total_words': self.total_words,
            'categories': sorted(
                self.categories.items(),
                key=lambda x: x[1],
                reverse=True
            ),
            'tags': sorted(
                self.tags.items(),
                key=lambda x: x[1],
                reverse=True
            )[:20],
        }

if __name__ == '__main__':
    stats = BlogStats('./content/post')
    stats.scan_posts()
    report = stats.get_report()
    print(json.dumps(report, ensure_ascii=False, indent=2))
```


## 如何创建自己的 Shortcode

在 `layouts/shortcodes/` 下新建 HTML 文件即可。例如创建 `badge.html`：

```html
<!-- layouts/shortcodes/badge.html -->
<span style="
  display: inline-block;
  padding: 2px 10px;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 600;
  background: {{ .Get 1 | default `var(--accent-color)` }};
  color: {{ .Get 2 | default `#fff` }};
">{{ .Get 0 }}</span>
```

使用：`{{</* badge "New" "#059669" */>}}`
