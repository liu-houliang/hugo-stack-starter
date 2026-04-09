# Hugo Theme Stack 开源模板 (Starter)

**中文** | [English](README.en.md)

这是一个基于 [Hugo Theme Stack v4](https://github.com/CaiJimmy/hugo-theme-stack) 的博客模板。

## 特点

- **开箱即用**：预设了中文 (zh) 环境和常用的配置。
- **美化增强**：集成了作者个人的美化修改（持续更新中）。
- **极简安装**：基于 Hugo Modules，方便升级主题。

## 快速开始

### 1. 安装 Hugo

确保你安装了 **Hugo Extended** 版本 (建议版本 >= 0.120.0)。

### 2. 克隆仓库

```bash
git clone https://github.com/liu-houliang/hugo-stack-starter.git my-blog
cd my-blog
```

### 3. 本地预览

```bash
hugo server
```

访问 `http://localhost:1313` 查看你的博客。

## 自定义配置

所有的配置文件都位于 `config/_default` 目录下：

- `config.toml`: 基础信息配置（标题、域名等）
- `languages.toml`: 多语言设置
- `params.zh.toml` / `params.en.toml`: 分语言的主题参数
- `menu.zh.toml` / `menu.en.toml`: 分语言的导航栏

## 多语言配置说明

本模板默认开启中英双语支持。你可以根据需要进行调整：

### 如何删除一种语言（例如删除英文）？
1.  **修改配置**：在 `config/_default/languages.toml` 中删除或注释掉 `[en]` 块。
2.  **清理文件**：删除 `config/_default/` 目录下所有带有 `.en.` 后缀的文件（如 `params.en.toml`, `menu.en.toml`）。
3.  **刷新缓存**：重启 `hugo server`。

### 如何切换默认语言？
编辑 `config/_default/config.toml`，修改 `defaultContentLanguage` 的值。例如，若想以英文为默认语言，设置为 `en`。

## 许可证

本项目采用 [GPL-3.0](LICENSE) 许可证。
