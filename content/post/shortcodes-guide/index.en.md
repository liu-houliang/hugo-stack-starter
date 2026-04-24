---
title: "Shortcodes Guide"
description: "This template includes built-in custom Shortcodes like timelines and title dividers. This article demonstrates the actual rendering effects of all Shortcodes."
date: 2026-04-14
lastmod: 2026-04-23
categories:
    - Tutorial
tags:
    - Hugo
    - Shortcodes
---

Hugo Shortcodes are a way to embed special components within Markdown. This article demonstrates the **actual rendering effects** of all custom Shortcodes included in this template.

---

## Title Divider (title)

Ideal for content that requires section headings, such as diaries, workout logs, or study notes.

**Usage:**
```markdown
{{</* title "Heading Text" "color" */>}}
```

**Actual Effects — Different Colors:**

{{< title "Green Heading" "green" >}}

This is the content under the green divider, suitable for sports or health-related logs.

{{< title "Blue Heading" "blue" >}}

This is the content under the blue divider, suitable for tech or study-related logs.

{{< title "Orange Heading" "orange" >}}

This is the content under the orange divider, suitable for creative or design-related logs.

{{< title "Purple Heading" "purple" >}}

This is the content under the purple divider, suitable for diaries or essays.

{{< title "Custom Color #E91E63" "#E91E63" >}}

You can also use hex color codes directly.

---

**All Built-in Colors:**

| Color Name | Preview |
|------------|---------|
| `red` | {{< title "Red" "red" >}} |
| `orange` | {{< title "Orange" "orange" >}} |
| `yellow` | {{< title "Yellow" "yellow" >}} |
| `green` | {{< title "Green" "green" >}} |
| `teal` | {{< title "Teal" "teal" >}} |
| `blue` | {{< title "Blue" "blue" >}} |
| `indigo` | {{< title "Indigo" "indigo" >}} |
| `purple` | {{< title "Purple" "purple" >}} |
| `pink` | {{< title "Pink" "pink" >}} |
| `gray` | {{< title "Gray" "gray" >}} |

---

## Timeline

Suitable for showcasing personal experiences, project milestones, tech growth trajectories, etc.

**Usage:**
```markdown
{{</* timeline */>}}
{{</* timeline-item date="2024-01" */>}}
Content...
{{</* /timeline-item */>}}
{{</* /timeline */>}}
```

**Actual Effect:**

{{< timeline >}}

{{< timeline-item date="2024-01" >}}
Started learning Hugo and understanding the benefits of static blogs.
{{< /timeline-item >}}

{{< timeline-item date="2024-06" >}}
Blog officially launched. Published the first technical article and gained the first batch of readers.
{{< /timeline-item >}}

{{< timeline-item date="2025-01" >}}
Integrated the Waline comment system to interact with readers. The comment section is becoming active.
{{< /timeline-item >}}

{{< timeline-item date="2025-09" >}}
Beautified the blog theme, adding features like Mac-style code blocks and a comprehensive Stats page.
{{< /timeline-item >}}

{{< /timeline >}}

Timeline content supports full Markdown, such as **bold**, `inline code`, [links](#), etc.

---

## Code Block Features (Theme Enhancement)

Code blocks are not Shortcodes themselves, but this template has enhanced them:

### Copy Button

Every code block has a copy button in the top right corner (inside the macOS title bar):

```javascript
// Try clicking the copy button in the top right corner
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Hugo"));
```

### Auto-Collapse Long Code

Code blocks taller than 600px automatically collapse, and an "Expand Code" button appears at the bottom. Here is a long snippet to test the collapse feature:

```python
# This code is long enough to trigger the auto-collapse
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
        """Scan all article directories"""
        for root, dirs, files in os.walk(self.posts_dir):
            for file in files:
                if file.endswith('.md'):
                    filepath = os.path.join(root, file)
                    self.parse_post(filepath)

    def parse_post(self, filepath: str):
        """Parse front matter of a single article"""
        with open(filepath, 'r', encoding='utf-8') as f:
            content = f.read()

        # Extract front matter
        if content.startswith('---'):
            end = content.find('---', 3)
            if end > 0:
                front_matter = content[3:end].strip()
                body = content[end+3:].strip()
                self.total_words += len(body.split())
                self.parse_front_matter(front_matter)

    def parse_front_matter(self, front_matter: str):
        """Parse YAML front matter"""
        for line in front_matter.split('\n'):
            if line.startswith('categories:'):
                pass  # Simplified handling
            elif line.startswith('tags:'):
                pass  # Simplified handling
            elif line.startswith('    - '):
                tag = line.strip().lstrip('- ')
                self.tags[tag] = self.tags.get(tag, 0) + 1

    def get_report(self) -> dict:
        """Generate statistical report"""
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

---

## Hugo Built-in Shortcodes

Hugo comes with some very useful Shortcodes:

### Figure (Enhanced Images)

```markdown
{{</* figure src="image.jpg" title="Image Title" caption="Image Caption" */>}}
```

This adds titles and captions, which the standard `![](image.jpg)` doesn't support easily.

### Gist

```markdown
{{</* gist username gist-id */>}}
```

Embeds a GitHub Gist code snippet directly.

---

## How to Create Your Own Shortcode

Simply create an HTML file under `layouts/shortcodes/`. For example, create `badge.html`:

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

Usage: `{{</* badge "New" "#059669" */>}}`
