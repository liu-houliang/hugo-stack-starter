---
title: "Style Customization Guide"
description: "How to modify colors, fonts, and component styles in this template to give your blog a personal touch."
date: 2026-04-13
lastmod: 2026-04-23
categories:
    - Tutorial
tags:
    - Hugo
    - SCSS
    - Styling
---

The styling system of this template is based on SCSS. All custom styles are located in the `assets/scss/` directory, so you **do not need to modify the original theme files**.

---

## Modify Theme Colors

Open `assets/scss/custom.scss` and modify the CSS variables inside `:root`:

```scss
:root {
    /* Light Mode */
    --accent-color: #1B365D;           /* Accent color: buttons, links, highlights */
    --accent-color-darker: #202A44;    /* Darker accent: hover states */
    --accent-color-text: #FFF;         /* Text color on top of the accent color */
    --body-background: #f8f7f2;        /* Page background */
    --card-background: #fdfdfb;        /* Card background */
    --body-text-color: #2D3748;        /* Body text color */

    &[data-scheme="dark"] {
        /* Dark Mode Overrides */
        --body-background: #101214;
        --card-background: #1c2128;
        /* ... */
    }
}
```

After saving, Hugo automatically recompiles and the browser refreshes instantly.

### Popular Color Palette References

**Purple Scheme**:
```scss
--accent-color: #7C3AED;
--accent-color-darker: #6D28D9;
```

**Green Scheme**:
```scss
--accent-color: #059669;
--accent-color-darker: #047857;
```

**Orange Scheme**:
```scss
--accent-color: #EA580C;
--accent-color-darker: #C2410C;
```

---

## Modify Code Block Styles

Code block related styles are in `assets/scss/partials/custom-components/_code.scss`.

### Disable Mac-Style Title Bar

If you don't like the macOS three-color dots, comment out the following code:

```scss
/* Comment out this before pseudo-element to disable the title bar */
/*
.article-content .highlight:before {
    ...
}
*/
```

### Change Collapse Threshold

In `_code.scss` and `layouts/_partials/footer/custom.html`, change `600` to your desired pixel value:

```scss
/* _code.scss */
&.collapsed {
    max-height: 400px;  /* Change to your desired height */
}
```

```js
/* JS in custom.html */
const MAX_HEIGHT = 400;  /* Keep consistent with CSS */
```

---

## Add Custom Fonts

Add Google Fonts in `assets/scss/custom.scss` and set the font family:

```scss
/* Import font */
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;700&display=swap');

/* Apply to body */
body {
    font-family: 'Outfit', sans-serif;
}

/* Apply to article content */
.article-content {
    font-family: 'Outfit', sans-serif;
    line-height: 1.9;
}
```

---

## Component Style Files Overview

| File | Purpose |
|------|---------|
| `custom.scss` | Global variables, TOC scrollbar |
| `_code.scss` | All code block styles |
| `_footer.scss` | Footer runtime button |
| `_homepage-grid.scss` | Homepage two-column grid |
| `_mobile-menu.scss` | Mobile top navigation bar |
| `_timeline.scss` | Timeline Shortcode styles |
| `_title.scss` | Title divider Shortcode styles |

Each file has a single responsibility and can be modified independently without affecting others.

---

## Disable Homepage Grid Layout

If you prefer the traditional single-column list, edit `params.toml`:

```toml
[homepage]
    grid = false
```

---

## Overriding Theme Layouts

If you need to modify other layout files of the theme, simply create a file with the same name in the `layouts/` directory to override it:

For example, to modify the article page layout, view the original file at `hugo-theme-stack-v4/layouts/single.html`, then copy it to `layouts/single.html` in your project root and modify it.

> Hugo's override mechanism prioritizes files in the project's root directory over the theme's files.
