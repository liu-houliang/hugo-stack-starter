# Hugo Theme Stack Starter

[中文](README.md) | **English**

A **ready-to-use blog template** based on [Hugo Theme Stack v4](https://github.com/CaiJimmy/hugo-theme-stack), with a series of visual enhancements and new features on top of the original theme.

> 📢 This project is a **GitHub Template**. Click **"Use this template"** in the top right to create your own blog repo instantly — no Fork needed.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎨 **Refined Color System** | Deep blue + warm off-white palette, with light/dark mode |
| 💻 **Mac-style Code Blocks** | macOS traffic-light header, floating copy button, auto-collapse for long code |
| 📐 **Homepage Grid Layout** | Two-column card layout on desktop with cover images and hover animations |
| 📱 **Mobile Navigation** | Brand new top navigation bar with dark mode toggle, language switch, and hamburger menu |
| 📊 **Stats Dashboard** | GitHub-style heatmap + category/tag charts + writing habit analysis |
| 🕐 **Site Runtime** | Footer shows days since launch, clicking goes to the Stats page |
| 🌐 **Bilingual (zh/en)** | Built-in Chinese/English support with one-click switching |
| 💬 **Waline Comments** | Integrated Waline comment system with pageview counting |
| 🚀 **One-click Deploy** | GitHub Actions auto-build and deploy to GitHub Pages |
| 🧩 **Custom Shortcodes** | Timeline and Title divider shortcodes |

---

## 🚀 Quick Start

### Option 1: GitHub Template (Recommended — live in 5 minutes)

1. Click **"Use this template"** → **"Create a new repository"** at the top right
2. Set the repo to **Public**, enter a name, and create it
3. Go to **Settings** → **Pages** → **Source** → select **"GitHub Actions"**
4. Edit `config/_default/config.toml` to update `baseurl` and `title`
5. Commit your changes and wait 1–2 minutes for your GitHub Pages site to go live 🎉

### Option 2: Local Development

```bash
# Install Hugo Extended (>= 0.120.0)
brew install hugo           # macOS
scoop install hugo-extended  # Windows

# Clone the repository
git clone https://github.com/your-username/my-blog.git
cd my-blog

# Start local server
hugo server
```

Visit `http://localhost:1313` to preview.

---

## ⚙️ Basic Configuration

All config files are in `config/_default/`:

**Minimum required changes:**

```toml
# config.toml
baseurl = "https://your-username.github.io/repo-name/"
title   = "My Blog"

# params.en.toml
[sidebar]
    subtitle = "Your personal tagline"

# params.toml
[footer]
    launchDate = "2024-01-01"   # When did your blog start?

[comments.waline]
    serverURL = "https://your-waline-url/"
```

> ⚠️ **Important Note**: The template includes the author's demo Waline URL by default (for preview purposes only). For your actual blog, please **make sure to replace it with your own Waline server URL**, otherwise your comments will be stored on a public demo server! See the built-in tutorial post for Waline deployment instructions.

---

## 📝 Write Your First Post

```bash
hugo new content post/my-first-post/index.en.md
```

Example Front Matter:

```yaml
---
title: "My First Post"
description: "A brief description"
date: 2026-01-01
categories:
    - Technology
tags:
    - Hugo
image: cover.jpg
---
```

---

## 📂 Project Structure

```
hugo-stack-starter/
├── .github/workflows/deploy.yml   # GitHub Actions auto-deploy
├── assets/
│   └── scss/
│       ├── custom.scss            # Color variables, global styles
│       └── partials/custom-components/
│           ├── _code.scss         # Code block styles
│           ├── _footer.scss       # Footer runtime display
│           ├── _homepage-grid.scss # Homepage grid layout
│           ├── _mobile-menu.scss  # Mobile navigation
│           ├── _timeline.scss     # Timeline shortcode styles
│           └── _title.scss        # Title divider shortcode styles
├── config/_default/               # All configuration files
├── content/
│   ├── post/                      # Blog posts
│   ├── archives/                  # Archive page
│   ├── search/                    # Search page
│   └── stats/                     # Stats dashboard page
├── layouts/
│   ├── _default/stats.html        # Stats page layout
│   ├── _partials/
│   │   ├── footer/footer.html     # Runtime footer
│   │   └── sidebar/left.html      # Sidebar with mobile nav
│   └── shortcodes/                # Custom shortcodes
└── i18n/                          # zh/en translations
```

---

## 🗑️ Single Language Setup (Chinese only)

1. Remove the `[en]` block from `config/_default/languages.toml`
2. Delete all `.en.toml` and `.en.md` files
3. Restart `hugo server`

---

## 🙏 Credits

- Theme based on [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) by [@CaiJimmy](https://github.com/CaiJimmy)
- Comment system: [Waline](https://waline.js.org/)
- Static site generator: [Hugo](https://gohugo.io/)

---

## 📄 License

This project is licensed under [GPL-3.0](LICENSE).
