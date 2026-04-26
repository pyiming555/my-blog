# pyiming 的博客

欢迎来到 **pyiming 的博客** 仓库！这是一个基于 [Hugo](https://gohugo.io/) 静态网站生成器和 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题构建的个人博客。

## 📖 关于本站

这里记录我的学习笔记、代码实践和生活思考。

**💡 专注领域：** 算法 / 编程技术 / 个人成长

- **部署地址**: [https://pyiming.pages.dev/](https://pyiming.pages.dev/)
- **主题**: Hugo PaperMod
- **语言**: 中文 (zh-cn)

## ✨ 特性

- 🚀 **快速构建**: 基于 Hugo，生成速度极快
- 📱 **响应式设计**: 完美适配桌面端和移动端
- 🌙 **自动主题切换**: 支持亮色/暗色模式自动切换
- 🔍 **全文搜索**: 集成 Fuse.js 支持中文搜索
- 📝 **代码高亮**: 支持多种编程语言语法高亮
- 🧮 **数学公式**: 支持 LaTeX 数学公式渲染
- 📊 **阅读统计**: 显示字数和阅读时间
- 🔗 **SEO 优化**: 自动生成站点地图和 robots.txt
- 📑 **文章目录**: 长文自动生成目录导航

## 🛠️ 本地开发

### 前置要求

- [Hugo](https://gohugo.io/getting-started/installing/) (推荐最新版)
- Git

### 克隆仓库

```bash
git clone https://github.com/pyiming555/pyiming.pages.dev.git
cd pyiming.pages.dev
git submodule update --init --recursive
```

### 启动本地服务器

```bash
hugo server -D
```

访问 `http://localhost:1313` 即可预览博客。

### 构建生产版本

```bash
hugo --minify
```

生成的静态文件将输出到 `public/` 目录。

## 📁 项目结构

```
.
├── archetypes/          # 文章模板
├── content/             # 博客内容
│   ├── posts/           # 文章目录
│   ├── archives.md      # 归档页面
│   └── search.md        # 搜索页面
├── layouts/             # 自定义布局
├── themes/              # 主题目录
│   └── PaperMod/        # PaperMod 主题
├── hugo.toml            # Hugo 配置文件
└── static/              # 静态资源（图片、favicon 等）
```

## ✍️ 创建新文章

使用 Hugo 命令创建新文章：

```bash
hugo new posts/文章标题.md
```

文章模板位于 `archetypes/default.md`，新建的文章会在 `content/posts/` 目录下。

### 文章头部参数（Front Matter）

```yaml
---
title: "文章标题"
date: 2024-01-01T00:00:00+08:00
draft: false
description: "文章描述"
tags: ["标签 1", "标签 2"]
categories: ["分类"]
---
```

## 🎨 配置说明

主要配置在 `hugo.toml` 文件中：

- **baseURL**: 网站部署地址
- **title**: 网站标题
- **theme**: 使用的主题
- **params**: 网站参数配置
  - 作者信息
  - SEO 设置
  - 社交链接
  - 功能开关等

## 📦 主题子模块

本项目使用 Git 子模块管理主题：

```bash
# 初始化或更新子模块
git submodule update --init --recursive

# 更新主题到最新版本
git submodule update --remote
```

## 🌐 部署

本站部署在 Cloudflare Pages 上。

### 部署步骤

1. 将代码推送到 GitHub 仓库
2. 在 Cloudflare Pages 中连接 GitHub 仓库
3. 设置构建命令：`hugo --minify`
4. 设置输出目录：`public`
5. 自动部署

## 📄 许可证

本博客的内容（`content/` 目录下的 Markdown 文件）采用 [知识共享署名 - 非商业性使用 - 相同方式共享 4.0 国际许可协议](https://creativecommons.org/licenses/by-nc-sa/4.0/) 进行许可。

代码部分采用 [MIT 许可证](LICENSE)。

## 👤 关于作者

- **GitHub**: [@pyiming555](https://github.com/pyiming555)
- **Email**: pyiming555@gmail.com

## 🤝 贡献

欢迎通过 Issue 或 Pull Request 提出建议和问题！

## 📮 联系方式

如有任何问题或合作意向，请通过以下方式联系：

- Email: pyiming555@gmail.com
- GitHub Issues

---

**感谢访问！🎉**
