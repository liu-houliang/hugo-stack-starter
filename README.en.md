# Hugo Theme Stack Starter Template

[中文](README.md) | **English**

This is a blog template based on [Hugo Theme Stack v4](https://github.com/CaiJimmy/hugo-theme-stack).

## Features

- **Out-of-the-box**: Pre-configured with Chinese (zh) and English (en) environments.
- **Beautification Enhanced**: Integrated personal beautification modifications (continuously updated).
- **Minimalist Installation**: Based on Hugo Modules, easy to upgrade the theme.

## Quick Start

### 1. Install Hugo

Make sure you have **Hugo Extended** version installed (recommended version >= 0.120.0).

### 2. Clone the Repository

```bash
git clone https://github.com/liu-houliang/hugo-stack-starter.git my-blog
cd my-blog
```

### 3. Local Preview

```bash
hugo server
```

Visit `http://localhost:1313` to view your blog.

## Custom Configuration

All configuration files are located in the `config/_default` directory:

- `config.toml`: Basic information configuration (title, domain, etc.)
- `languages.toml`: Multilingual settings
- `params.zh.toml` / `params.en.toml`: Language-specific theme parameters
- `menu.zh.toml` / `menu.en.toml`: Language-specific navigation bars

## Multilingual Configuration Instructions

This template enables Chinese and English support by default. You can adjust it as needed:

### How to delete a language (e.g., delete English)?
1.  **Modify Configuration**: Delete or comment out the `[en]` block in `config/_default/languages.toml`.
2.  **Clean Up Files**: Delete all files with the `.en.` suffix in the `config/_default/` directory (e.g., `params.en.toml`, `menu.en.toml`).
3.  **Refresh Cache**: Restart `hugo server`.

### How to switch the default language?
Edit `config/_default/config.toml` and modify the value of `defaultContentLanguage`. For example, to set English as the default language, set it to `en`.

## License

This project is licensed under the [GPL-3.0](LICENSE) license.
