---
title: "Quick Start: Deploy Your Blog with One Click"
description: "Use this GitHub Template to deploy your Hugo blog quickly via GitHub Actions, no local installation required."
date: 2026-04-09
lastmod: 2026-04-23
weight: 1
categories:
    - Tutorial
tags:
    - Hugo
    - Getting Started
    - Deployment
    - GitHub Pages
---

## Welcome to Hugo Theme Stack Starter

This is a ready-to-use blog template based on **Hugo Theme Stack v4**, featuring enhanced styling, bilingual support, and GitHub Actions auto-deployment. **You can get started without installing anything locally.**

---

## Option 1: GitHub Template — One Click Deploy (Recommended)

> The easiest way — everything happens in your browser.

### Step 1: Create your repository from this template

1. Open this project's GitHub page
2. Click the green **"Use this template"** button → **"Create a new repository"**
3. Enter a repository name (e.g., `my-blog`), select **Public** (required for free GitHub Pages)
4. Click **"Create repository"**

### Step 2: Enable GitHub Pages

1. In your new repository, go to **Settings** → **Pages**
2. Under **"Source"**, select **"GitHub Actions"**
3. Save

### Step 3: Update your configuration

Edit `config/_default/config.toml` directly on GitHub:

```toml
# Replace with your GitHub Pages URL
baseurl = "https://your-username.github.io/repo-name/"
title   = "My Blog"
```

### Step 4: Push to trigger auto-deployment

Every commit triggers GitHub Actions to build and deploy automatically. Wait 1–2 minutes, then visit your GitHub Pages URL to see your blog live!

---

## Option 2: Local Development

If you prefer to write and preview locally:

### Install Hugo (Extended edition)

```bash
# macOS
brew install hugo

# Windows (Scoop)
scoop install hugo-extended

# Linux (apt)
sudo apt install hugo
```

Verify it's the extended edition:

```bash
hugo version
# Output should include "extended"
```

### Clone and run

```bash
git clone https://github.com/your-username/my-blog.git
cd my-blog
hugo server
```

Visit `http://localhost:1313` to preview your blog.

---

## Configuration Guide

All config files are in `config/_default/`:

| File | Purpose |
|------|---------|
| `config.toml` | Site title, base URL, default language |
| `languages.toml` | Multilingual settings (zh/en) |
| `params.toml` | Theme parameters (comments, homepage layout) |
| `params.en.toml` | English-specific parameters (avatar, subtitle) |
| `menu.en.toml` | English navigation menu |

### Required changes

**1. Site title and URL** (`config.toml`):
```toml
baseurl = "https://your-domain.com/"
title   = "My Blog"
```

**2. Your avatar and bio** (`params.en.toml`):
```toml
[sidebar]
    subtitle = "Your personal tagline"
    avatar   = "img/avatar.jpg"  # replace assets/img/avatar.jpg
```

**3. Blog launch date** (`params.toml`):
```toml
[footer]
    launchDate = "2024-01-01"  # your blog's start date
```

---

## Project Structure

```
my-blog/
├── .github/workflows/    # GitHub Actions (no changes needed)
├── assets/scss/          # Style customization
│   ├── custom.scss       # Colors, global styles
│   └── partials/custom-components/  # Component styles
├── config/_default/      # All configuration files
├── content/
│   └── post/             # Blog posts (write here)
├── layouts/              # Custom layouts and Shortcodes
└── static/               # Static assets (images, etc.)
```

---

## What's Next

- 📖 [**Theme Customizations**](/post/theme-customization/) — What this template changes from the original
- 💬 [**Set Up Waline Comments**](/post/waline-setup/) — Add a comment section to your blog
- ✏️ [**Start Writing**](/post/start-writing/) — Learn Markdown and multilingual posts

Happy blogging! 🎉
