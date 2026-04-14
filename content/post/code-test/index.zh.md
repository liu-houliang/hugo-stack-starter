---
title: "代码块样式测试文章"
description: "这是一篇包含多种编程语言代码块和折叠代码功能的文章，用于测试代码高亮、Mac 样式代码块和代码折叠功能。"
date: 2026-04-09
categories:
    - Tutorial
tags:
    - 代码
    - 样式
    - Shortcodes
---

## 普通代码块

以下是几种常见编程语言的代码块展示：

### Python 示例

```python
def hello_world():
    print("Hello, Hugo!")
    
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# 打印前10个斐波那契数
for i in range(10):
    print(f"F({i}) = {fibonacci(i)}")
```

### JavaScript 示例

```javascript
const stack = "Theme Stack v4";
console.log(`Working on ${stack}`);

// 异步函数示例
async function fetchData(url) {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error:', error);
        throw error;
    }
}
```

### HTML 示例

```html
<section class="article-list -grid">
    <div class="article-details">
        <h2 class="article-title">文章标题</h2>
        <p class="article-description">文章描述内容</p>
    </div>
</section>
```

### CSS 示例

```css
.article-content .highlight {
    background-color: var(--pre-background-color);
    border-radius: 10px;
    margin: 1.5rem 0;
    box-shadow: 0 2px 12px rgba(0, 0, 0, 0.04);
}

.article-content .highlight:before {
    content: "";
    display: block;
    background: url(/code-header.svg);
    height: 35px;
    background-size: 52px;
    background-repeat: no-repeat;
    background-position: 12px center;
}
```

## 折叠代码块

使用 `foldcode` Shortcode 可以创建可折叠的代码块，适合展示较长的代码或可选阅读的内容。

### 默认折叠代码

{{< foldcode >}}
```go
package main

import (
    "fmt"
    "net/http"
    "time"
)

func main() {
    // 创建一个简单的 HTTP 服务器
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Hello, World! Current time: %s", time.Now().Format(time.RFC3339))
    })
    
    fmt.Println("Server starting on :8080...")
    if err := http.ListenAndServe(":8080", nil); err != nil {
        fmt.Printf("Server error: %v\n", err)
    }
}
```
{{< /foldcode >}}

### 自定义展开/折叠文字

{{< foldcode "查看完整配置" "收起配置" >}}
```yaml
# Hugo 配置文件示例
baseURL: 'https://example.com'
languageCode: 'zh-cn'
title: '我的博客'
theme: 'stack'

params:
  mainSections:
    - post
  featuredImageField: 'image'
  rssFullContent: true
  
  # 侧边栏设置
  sidebar:
    compact: false
    emoji: 🚀
    subtitle: '这是一个基于 Hugo Theme Stack 的博客'
    
  # 文章设置
  article:
    math: true
    toc: true
    readingTime: true
    
  # 评论设置
  comments:
    enabled: true
    provider: 'giscus'
    
  # 搜索设置
  search:
    enable: true
    type: 'fuse'
```
{{< /foldcode >}}

### 嵌套在列表中的折叠代码

1. 第一步：安装依赖

   {{< foldcode "查看安装命令" >}}
   ```bash
   # 使用 npm 安装
   npm install -g @angular/cli
   
   # 或使用 yarn
   yarn global add @angular/cli
   
   # 或使用 pnpm
   pnpm add -g @angular/cli
   
   # 验证安装
   ng version
   ```
   {{< /foldcode >}}

2. 第二步：创建新项目

   {{< foldcode "查看创建命令" >}}
   ```bash
   # 创建新项目
   ng new my-angular-app
   
   # 进入项目目录
   cd my-angular-app
   
   # 启动开发服务器
   ng serve --open
   ```
   {{< /foldcode >}}

### 包含长代码的折叠块

{{< foldcode >}}
```rust
// Rust 实现的链表
use std::rc::Rc;
use std::cell::RefCell;

type Link<T> = Option<Rc<RefCell<Node<T>>>>;

struct Node<T> {
    elem: T,
    next: Link<T>,
}

pub struct List<T> {
    head: Link<T>,
}

impl<T> List<T> {
    pub fn new() -> Self {
        List { head: None }
    }

    pub fn push(&mut self, elem: T) {
        let new_node = Rc::new(RefCell::new(Node {
            elem,
            next: self.head.clone(),
        }));
        self.head = Some(new_node);
    }

    pub fn pop(&mut self) -> Option<T> {
        self.head.take().map(|old_head| {
            if let Some(next) = old_head.borrow_mut().next.take() {
                self.head = Some(next);
            }
            Rc::try_unwrap(old_head).ok().unwrap().into_inner().elem
        })
    }

    pub fn peek(&self) -> Option<Ref<T>> {
        self.head.as_ref().map(|node| {
            Ref::map(node.borrow(), |node| &node.elem)
        })
    }
}

impl<T> Drop for List<T> {
    fn drop(&mut self) {
        let mut cur_link = self.head.take();
        while let Some(boxed_node) = cur_link {
            cur_link = boxed_node.borrow_mut().next.take();
        }
    }
}
```
{{< /foldcode >}}

## 代码块特性总结

本文档测试了以下代码块特性：

| 特性 | 说明 |
|------|------|
| Mac 样式标题栏 | 红黄绿三个圆点，经典的 Mac 窗口风格 |
| 语法高亮 | 支持多种编程语言的语法高亮 |
| 复制按钮 | 右上角常显的复制按钮，点击可复制代码 |
| 卡片样式 | 圆角、阴影、边框，与正文区分明显 |
| 代码折叠 | 使用 `foldcode` Shortcode 实现可折叠代码块 |

所有代码块都支持深色模式自动适配，复制按钮在深色模式下也有良好的视觉效果。
