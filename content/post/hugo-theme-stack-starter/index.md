---
title: "基于 hugo-theme-stack-starter 快速搭建 Hugo 博客"
description: "使用 hugo-theme-stack-starter 模板快速搭建个人博客并部署到 GitHub Pages 的完整指南"
date: 2026-06-18T01:38:11Z
image: 
math: 
license: 
comments: true
draft: fales
build:
    list: always    # Change to "never" to hide the page from the list
---

本文记录了使用 hugo-theme-stack-starter 模板快速搭建个人博客并部署到 GitHub Pages 的完整流程，包括模板使用、配置定制、内容创建和自动化部署等内容。

## 1. 基于 hugo-theme-stack-starter 创建项目

自从使用了HUGO，研究了很多主题，最后对hugo-theme-stack比较青睐，之前一直是本都部署使用，换电脑还是有诸多不方便之处。

本次使用 hugo-theme-stack-starter 模板创建项目，这是最快速的方式：

### 方法一：使用 GitHub Template + Codespace（推荐）

访问 [hugo-theme-stack-starter](https://github.com/CaiJimmy/hugo-theme-stack-starter)
```
点击 “Use this template” -> “Create a new repository”
将仓库命名为 “<用户名>.github.io” -> Choose visibility -> “Public”
创建完成后，点击 “Create codespace” 创建 GitHub Codespace
点击 Settings -> Pages -> Source -> Github Actions 开通自动部署
Codespace 已预装 Hugo extended，直接运行 hugo server 即可预览
```
### 方法二：本地开发

如果不想使用 Codespace，可以克隆到本地开发。需要确保本地已安装 Git、Go 和 Hugo extended。
```
git clone https://github.com/<用户名>/<用户名>.github.io.git
cd <用户名>.github.io
```
注意：hugo-theme-stack-starter 使用 Hugo Modules 功能加载主题，不再使用传统的子模块方式。

## 2. 配置网站

hugo-theme-stack-starter 已经包含了完整的配置结构，主要配置文件位于 config/_default/ 目录：

### 主要配置文件
```
config.toml - 基础站点配置
params.toml - 主题参数配置
menu.toml - 菜单配置
languages.toml - 多语言配置
```
### 编辑 config/_default/config.toml：

```
baseurl = "https://<用户名>.github.io"
languageCode = "zh"
title = "个人博客"
defaultContentLanguage = "zh"
hasCJKLanguage = true
```

### 自定义配置

根据需要修改 config/_default/params.toml 中的参数，如：
```
网站描述、关键词
社交媒体链接
评论系统配置
搜索功能等
```
## 3. 创建第一篇文章

stack-starter 已经包含了示例文章，可以参考 content/post/ 目录下的示例。
```
# 使用 Hugo 命令创建新文章
hugo new post/my-first-post/index.md
```
Stack 主题支持 Page Bundle 结构，推荐使用：
```
content/post/my-first-post/
├── index.md        # 文章内容
├── cover.jpg       # 封面图片
└── images/         # 文章图片
    └── example.png
```
文章前置元数据示例：
```
---
title = "文章标题"
description = "文章简短描述"
date = 2025-10-18T10:00:00+08:00
image = "cover.jpg"
math = false
license = false
hidden = false
comments = true
draft = false
tags = ["标签1", "标签2"]
categories = ["分类"]
---
```
## 4. 本地预览
```
# 不包含草稿
hugo server

# 包含草稿
hugo server -D
```