---
title: "Start Writing: Markdown Basics and Multilingual Posts"
description: "Learn how to create your first blog post, master basic Markdown syntax, and write bilingual (Chinese and English) posts."
date: 2026-04-12
lastmod: 2026-04-23
weight: 4
categories:
    - Tutorial
tags:
    - Hugo
    - Markdown
    - Writing
    - Multilingual
---

## Create Your First Post

### Option 1: Using Commands (Recommended)

```bash
# Create an English post
hugo new content post/my-first-post/index.en.md

# Create the corresponding Chinese version
hugo new content post/my-first-post/index.zh.md
```

Hugo will automatically populate initial content based on the `archetypes/default.md` template.

### Option 2: Manual Creation

Create a new folder under `content/post/`, and then create `index.en.md` inside it:

```
content/
└── post/
    └── my-first-post/       ← Post directory (Name becomes the URL)
        ├── index.en.md      ← English body
        ├── index.zh.md      ← Chinese body (Optional)
        └── cover.jpg        ← Cover image (Optional)
```

---

## Front Matter Explanation

The section between the `---` at the top of each article is called Front Matter, used to define article metadata:

```yaml
---
title: "Post Title"
description: "Post summary, displayed on the list page and in SEO descriptions"
date: 2026-04-12          # Publish date
lastmod: 2026-04-23       # Last modified date (optional)
draft: false              # true = draft, will not be published
categories:
    - Technology          # Category (recommended to pick only one)
tags:
    - Hugo                # Tags (can have multiple)
    - Markdown
image: cover.jpg          # Cover image (relative to the post directory)
---
```

> **Tip**: The `date` determines the sort order of posts in lists. Posts with future dates require `hugo server -F` to be visible during local preview.

---

## Basic Markdown Syntax

### Headings

```markdown
## Heading 2
### Heading 3
#### Heading 4
```

> Avoid using Heading 1 (`# H1`) in the article body because the `title` field is already an H1.

### Text Formatting

```markdown
**Bold**          Bold text
*Italic*          Italic text
~~Strikethrough~~ Strikethrough
`Inline code`     Code
```

Result: **Bold**, *Italic*, ~~Strikethrough~~, `Inline code`

### Links and Images

```markdown
[Link text](https://example.com)
[Internal link](/post/hello-world/)

![Image description](image.jpg)          # Relative path (same directory)
![Image description](/img/photo.jpg)     # Absolute path (in static directory)
```

### Lists

```markdown
- Unordered list item
- Second item
  - Nested item

1. Ordered list
2. Second item
3. Third item
```

### Code Blocks

````markdown
```python
def hello():
    print("Hello, World!")
```
````

Supports syntax highlighting for: `python`, `go`, `javascript`, `bash`, `toml`, `yaml`, `markdown`, etc.

### Blockquotes

```markdown
> This is a blockquote.
> It can span multiple lines.
```

Result:

> This is a blockquote.

### Tables

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Content 1| Content 2| Content 3|
| Content 4| Content 5| Content 6|
```

### Horizontal Rule

```markdown
---
```

---

## Multilingual Writing

This template has built-in support for Chinese and English.

### File Naming Convention

| Filename | Language |
|----------|----------|
| `index.en.md` | English |
| `index.zh.md` | Chinese |

Place both files in the same directory, and Hugo will automatically link them as different language versions of the same post.

### Writing Only in English

If you don't want to write a Chinese version, just create `index.en.md`.

### Adding a Chinese Version

1. Create `index.zh.md` in the same directory.
2. Translate the article content (also translate `title` and `description` in the Front Matter).
3. Images and other resources are shared between both language versions; no need to duplicate them.

**Example**:

`index.en.md`:
```yaml
---
title: "My First Post"
description: "This is my first blog post"
date: 2026-04-12
---
Content...
```

`index.zh.md`:
```yaml
---
title: "我的第一篇文章"
description: "这是我的第一篇博客文章"
date: 2026-04-12
---
内容...
```

---

## Inserting Images

### Using Images from the Post Directory (Recommended)

Place the image in the post directory, and reference it using a relative path:

```
content/post/my-post/
├── index.en.md
├── cover.jpg       ← Cover image
└── screenshot.png  ← Image inside the post
```

In Markdown:
```markdown
![Screenshot description](screenshot.png)
```

Specify the cover image in the Front Matter:
```yaml
image: cover.jpg
```

### Using Images from the static Directory

Place the image in `static/img/`, and reference it using an absolute path:
```markdown
![Image](img/photo.jpg)
```

---

## Using Template Shortcodes

### Title Divider

Suitable for separating paragraphs in diary-style posts:

```markdown
{{</* title "Morning Run" "green" */>}}

Ran 5 km today, feeling great.

{{</* title "Afternoon Reading" "blue" */>}}

Read two chapters of "Deep Work".
```

### Timeline

Suitable for showing experiences and growth trajectories:

```markdown
{{</* timeline */>}}
{{</* timeline-item date="2024-01" */>}}
Started learning programming
{{</* /timeline-item */>}}
{{</* timeline-item date="2024-06" */>}}
Completed first project
{{</* /timeline-item */>}}
{{</* /timeline */>}}
```

---

## Writing Tips

1. **The post directory name** becomes the URL. It is recommended to use lowercase English letters and hyphens, like `my-first-post`.
2. **Cover images** are recommended to be 1200×630px, which is the optimal size for social sharing.
3. Keep the **description** under 160 characters for SEO friendliness.
4. Use `hugo server -D` during local preview to view draft posts.

Happy writing! ✍️
