---
title: "我的第一篇博客"
date: 2026-03-29
description: "这是 pyiming 博客的第一篇文章，详细介绍了如何搭建 Hugo 博客。"
keywords: ["Hugo", "教程", "Cloudflare"]
tags: ["教程", "日常"]
draft: false
---
# 从 0 搭建我的个人博客（Hugo + Cloudflare Pages 全流程记录）

## 一、为什么要搭建博客

一直想有一个属于自己的博客，用来记录：

- 技术学习笔记
- 算法与编程思考
- 日常的一些想法

相比第三方平台，自己搭建博客最大的优势是：

- 完全可控（内容、样式、域名）
- 免费（几乎 0 成本）
- 自动部署（写完直接上线）

于是我选择了：

- Hugo（静态博客生成器）
- Cloudflare Pages（免费部署 + CDN）
- GitHub（代码管理）

---

## 二、整体架构

整个博客的工作流程其实很简单：

写文章 → Git 推送 → Cloudflare 自动部署 → 网站更新

具体结构：

- 本地：Hugo 生成静态网站
- GitHub：存储源码
- Cloudflare Pages：自动构建 + 提供访问域名（*.pages.dev）

---

## 三、环境准备

需要准备：

- Git
- Hugo（建议 extended 版本）
- GitHub 账号
- Cloudflare 账号

检查 Hugo：

```bash
hugo version
```

---

## 四、创建 Hugo 博客

```bash
hugo new site my-blog
cd my-blog
git init
```

---

## 五、选择主题（关键）

一开始我用的是 **Stack 主题**，但遇到了一个大坑：

> ❌ Stack 需要 Hugo ≥ 0.157  
> ❌ 我的系统 GLIBC 太旧，无法升级 Hugo

直接导致：

- panic 报错
- 页面空白
- 完全无法使用

### ✅ 最终解决方案：换成 PaperMod

```bash
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

---

## 六、基础配置（hugo.toml）

核心配置如下：

```toml
baseURL = "https://my-blog.pages.dev/"
languageCode = "zh-cn"
title = "pyiming 的博客"
theme = "PaperMod"
hasCJKLanguage = true

[outputs]
  home = ["HTML", "RSS", "JSON"]

[params]
  env = "production"
  description = "记录技术、学习与生活"
  author = "pyiming"

  ShowReadingTime = true
  ShowShareButtons = true
  ShowCodeCopyButtons = true
  ShowBreadCrumbs = true
```

---

## 七、创建文章

```bash
hugo new posts/hello.md
```

记得把：

```yaml
draft: false
```

否则不会显示！

---

## 八、本地预览

```bash
hugo server -D
```

访问：

```
http://localhost:1313/
```

---

## 九、部署到 GitHub

```bash
git add -A
git commit -m "init blog"
git remote add origin https://github.com/你的用户名/my-blog.git
git push -u origin main
```

---

## 十、部署到 Cloudflare Pages

### 创建项目

- Workers & Pages → Pages
- Connect to Git
- 选择仓库

### 构建配置

```text
Build command: hugo --minify
Output directory: public
```

### 环境变量（重要）

```text
HUGO_VERSION = 0.147.8
HUGO_ENV = production
```

部署完成后得到：

```
https://你的项目名.pages.dev
```

---

## 十一、搜索功能踩坑（重点）

一开始搜索框能显示，但**搜不到内容**。

原因：

👉 没有生成 index.json

解决方法：

```toml
[outputs]
  home = ["HTML", "RSS", "JSON"]
```

然后重新构建：

```bash
hugo --minify
```

访问：

```
/index.json
```

能打开说明成功 ✅

---

## 十二、我踩过的坑总结

### 1️⃣ Stack 主题报错

原因：Hugo 版本不够  
解决：换 PaperMod

---

### 2️⃣ GLIBC 版本过低

原因：系统太旧  
解决：使用较低版本 Hugo（0.147.8）

---

### 3️⃣ 页面空白 / 无布局

原因：theme 没配置  
解决：

```toml
theme = "PaperMod"
```

---

### 4️⃣ 搜索功能无结果

原因：没有 index.json  
解决：

```toml
[outputs]
home = ["HTML", "RSS", "JSON"]
```

---

### 5️⃣ 部署成功但打不开

原因：访问了 workers.dev  
正确地址：

```
✅ pages.dev
❌ workers.dev
```

---

## 十三、最终效果

我现在的博客具备：

- ✅ 全中文界面
- ✅ 自动部署
- ✅ 搜索功能
- ✅ SEO（sitemap + robots）
- ✅ 全球 CDN 加速

---

## 十四、总结

搭建博客的核心其实只有三步：

1. Hugo 生成静态页面  
2. GitHub 管理代码  
3. Cloudflare Pages 自动部署  

最大的难点不是技术，而是：

👉 踩坑（版本、主题、配置）

但一旦跑通流程，后面写文章就非常爽：

```bash
hugo new posts/xxx.md
git push
```

2分钟上线 🚀

---

## 十五、下一步计划

- 自定义域名
- 评论系统（giscus）
- 文章 SEO 优化
- 自动化写作流程

---

如果你也想搭博客，这一套完全够用了 👍