---
title: "Theme Customizations: What I Have Changed"
description: "A detailed introduction to the beautification and feature enhancements made on top of Hugo Theme Stack v4 in this template, including code blocks, homepage layout, mobile navigation, etc."
date: 2026-04-10
lastmod: 2026-04-23
weight: 2
categories:
    - Tutorial
tags:
    - Hugo
    - Customization
    - Theme
---

This template is developed based on [Hugo Theme Stack v4](https://github.com/CaiJimmy/hugo-theme-stack). While maintaining the integrity of the original features, a series of visual and interactive enhancements have been made.

All modifications are implemented using Hugo's override mechanism (by creating files with the same names in `assets/` and `layouts/`), **without modifying the original theme's source code**, making it easy to upgrade the theme version at any time.

---

## 1. Global Color System

The entire set of color variables has been redefined, adopting a deep blue + warm off-white color scheme:

**Light Mode**:
- Background color: Warm off-white `#f8f7f2` (easier on the eyes than pure white)
- Accent color: Deep sea blue `#1B365D`
- Card background: `#fdfdfb` (slightly warm white)

**Dark Mode**:
- Background color: `#101214` (dark grayish-black)
- Card background: `#1c2128` (GitHub dark style)
- In dark mode, images are automatically dimmed, restoring brightness on hover

Modification location: `:root` variables in `assets/scss/custom.scss`.

---

## 2. Mac-Style Code Blocks

The original theme's code blocks are quite simple, but this template comprehensively beautifies them:

### Top Title Bar
A macOS-style three-color dot decoration (red, yellow, green) has been added to every code block, simulating a terminal window appearance.

### Redesigned Copy Button
- Changed from an inconspicuous icon button to a text button floating on the right side of the title bar
- Light mode: Frosted glass style (`backdrop-filter: blur`)
- Dark mode: Dark translucent background
- Clicking the button changes the text to "✓ Copied!"

### Auto-Collapse Long Code Blocks
Code blocks taller than 600px automatically collapse, with an "Expand Code" button at the bottom:
- When collapsed, a gradient overlay appears at the bottom
- After expanding, the button text changes to "Collapse Code"
- When collapsing, it automatically scrolls back to the top of the code block, preventing page layout confusion

### Beautified Scrollbars
The horizontal scrollbar of code blocks is transparent by default and only appears on hover, keeping the interface clean.

---

## 3. Homepage Two-Column Grid Layout

On desktop screens (width ≥ 1024px), the homepage article list changes to a 2-column grid display:

- Each article is presented as a card containing a cover image, title, summary, and meta information
- Cards have a slight floating animation on hover
- Long article titles and summaries are automatically truncated (2 lines)
- Automatically reverts to a single-column list on mobile devices

To enable: Set it in `params.toml`:
```toml
[homepage]
    grid = true
```

---

## 4. Redesigned Mobile Navigation

The original theme's mobile navigation is relatively basic. This template completely rewrites the mobile experience:

### Sticky Top Navigation Bar
- Fixed to the top (sticky), remaining visible as you scroll down the page
- Left side: Avatar + Site name (click to return home)
- Right side: Dark mode toggle, language switch, search, and hamburger menu

### Hamburger Menu
- Clicking expands the side menu with a fade-in animation
- The top bar title fades out when the menu expands to prevent overlap
- The current page's menu item is highlighted
- Automatically closes when the screen width recovers (e.g., rotating device)

### Search Box
The search box in the desktop sidebar has been redesigned to match the card style.

---

## 5. Blog Stats Page

A feature-rich `/stats/` statistics page has been added, including:

- **Summary Cards**: Total articles, total words, running days (animated scrolling numbers)
- **Category Distribution**: Category list with progress bars, clickable to enter category pages
- **Popular Tags**: Tag cloud display (top 30 tags)
- **Writing Habits**: Posting habit analysis by day of the week and time of day (based on Git commit times)
- **Yearly Heatmap**: GitHub-style contribution heatmap (publishing record for the past year)

Configuration page entry: Set `layout: stats` in `content/stats/index.en.md`.

---

## 6. Footer Runtime

The footer now displays the blog's runtime, calculating the days, hours, and minutes since the launch date.

Clicking it navigates to the Stats page.

Configure launch date:
```toml
[footer]
    launchDate = "2024-09-09"
```

---

## 7. Custom Shortcodes

### Timeline

Suitable for displaying growth history, tech stack evolution, etc.:

```markdown
{{</* timeline */>}}
{{</* timeline-item date="2024-01" */>}}
Started learning Hugo
{{</* /timeline-item */>}}
{{</* timeline-item date="2024-06" */>}}
Blog officially launched
{{</* /timeline-item */>}}
{{</* /timeline */>}}
```

### Title Divider

Suitable for separating content sections like diaries or fitness logs:

```markdown
{{</* title "Morning Run" "green" */>}}
```

Supported colors: `red`, `orange`, `yellow`, `green`, `teal`, `blue`, `indigo`, `purple`, `pink`, `gray`

---

## How to Customize Colors

Edit `assets/scss/custom.scss`, modifying the variables in `:root`:

```scss
:root {
    --accent-color: #1B365D;        /* Accent color (buttons, links, etc.) */
    --body-background: #f8f7f2;     /* Page background */
    --card-background: #fdfdfb;     /* Card background */
}
```

After saving, Hugo will automatically recompile and refresh the browser in real-time.
