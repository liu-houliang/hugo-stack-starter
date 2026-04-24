---
title: "Set Up Waline Comments"
description: "Add free comment functionality to your blog using Waline. This guide will help you deploy it following the official documentation and configure it in this template."
date: 2026-04-11
lastmod: 2026-04-23
weight: 3
categories:
    - Tutorial
tags:
    - Hugo
    - Waline
    - Comments
    - Vercel
---

[Waline](https://waline.js.org/en/) is a safe and concise comment system that supports Markdown, offers free deployment, and allows users to comment without registering.

This template has built-in integration for Waline. You just need to deploy the server-side application and fill in one line of configuration to enable it.

---

## Step 1: Deploy Waline Server

Please refer to the **Waline Official Quick Start Guide** to complete the server deployment:

👉 [https://waline.js.org/en/guide/get-started/](https://waline.js.org/en/guide/get-started/)

The official documentation provides a **free one-click deployment** solution on Vercel. The entire process takes about 5 minutes.

Once deployed, you will receive a Waline service address, such as:
- `https://your-waline-project.vercel.app/` (Default Vercel domain)
- Or your bound custom domain

Save this address; you will need it in the next step.

---

## Step 2: Configure in This Template

Edit `config/_default/params.toml` and fill in your service address:

```toml
[comments]
    enabled  = true
    provider = "waline"

[comments.waline]
    serverURL = "https://your-waline-project.vercel.app/"  # ← Fill in your address here
    pageview  = true       # Also enable article pageview statistics

    # Optional: Custom emoji package (default is Weibo emoji)
    emoji = ["https://unpkg.com/@waline/emojis@1.0.1/weibo"]

    # Required fields for comments
    requiredMeta = ["name"]

    [comments.waline.locale]
        admin = "Admin"    # Administrator badge
```

Save and restart `hugo server`, and the comment section will appear at the bottom of your article pages.

---

## Features Overview

### Pageview Statistics
After setting `pageview = true`, pageviews will automatically be displayed at the top of the article (Requires Waline server support).

### Comment Management Dashboard
Visit `https://your-waline-project.vercel.app/ui/` to access the management interface. The first registered account automatically becomes the administrator, who can review and delete comments.

### Email Notifications
You can be notified via email when someone replies. This requires configuring SMTP information in Vercel environment variables. See the [Official Documentation - Notification](https://waline.js.org/en/guide/features/notification.html) for details.

---

## FAQ

**Comment section not showing up?**  
Check if there is a trailing slash `/` at the end of `serverURL`, and ensure the Vercel service is running normally (you should see the Waline welcome page when visiting the serverURL directly).

**Cookie banner blocking the comment section?**  
If you have enabled the Cookie consent feature, users must accept "Functional Cookies" before the comment section will appear. You can disable the Cookie prompt in `params.toml` or instruct users to accept it.
