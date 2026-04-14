# 📖 广东财经大学飞跃手册

由广财学子自发维护的真实经验分享平台。静态站点，零后端，极致轻量。

## 项目结构

```
飞跃手册/
├── docs/                       # 产品文档（与代码分离）
│   ├── PRD.md                  # 产品需求文档
│   ├── Backlog.md              # 功能迭代清单
│   └── BugTracker.md           # Bug 修复记录
├── src/
│   ├── content/articles/       # Markdown 文章存放目录
│   │   ├── zhuan-zhuanye-jingyan-2024.md
│   │   ├── bao-yan-bei-kao-zhinan.md
│   │   └── ...                 # 每篇一个 .md 文件
│   ├── components/             # Astro 组件
│   │   ├── Header.astro        # 顶部导航 + 主题切换
│   │   ├── Footer.astro        # 页脚
│   │   ├── Hero.astro          # 首页 Hero 区
│   │   ├── Features.astro      # 特色卡片区
│   │   ├── Categories.astro    # 分类入口
│   │   ├── CTA.astro           # 投稿引导区
│   │   └── ArticleCard.astro   # 文章卡片组件
│   ├── layouts/
│   │   └── BaseLayout.astro    # 基础布局（HTML 骨架）
│   ├── pages/
│   │   ├── index.astro         # 首页
│   │   └── articles/
│   │       ├── index.astro     # 文章列表页
│   │       └── [slug].astro    # 文章详情页
│   └── styles/
│       └── global.css          # 全局样式 + 设计系统变量
├── public/                     # 静态资源
├── astro.config.mjs            # Astro 配置
├── content.config.ts           # 内容集合定义
├── package.json
└── tsconfig.json
```

## 快速开始

### 安装依赖

```bash
npm install
```

### 启动开发服务器

```bash
npm run dev
```

访问 http://localhost:4321 查看效果。修改文件会自动热更新。

### 构建生产版本

```bash
npm run build
```

构建产物输出到 `dist/` 目录，可直接部署到任意静态托管平台。

### 本地预览构建结果

```bash
npm run preview
```

## 如何添加新文章

在 `src/content/articles/` 目录下新建一个 `.md` 文件：

```markdown
---
title: "你的文章标题"
author: "作者名"
date: "2025-04-14"
category: "考研"                # 必须是以下之一：转专业 / 保研 / 考研 / 出国留学 / 就业 / 其他
tags: ["标签1", "标签2"]         # 可选
excerpt: "文章摘要，用于列表展示"  # 必填
---

正文内容...支持完整的 Markdown 语法：
- 标题、列表、代码块
- 表格、引用、图片
- **粗体**、*斜体*
```

保存文件后，重新构建或刷新开发服务器即可看到新文章。

**注意事项：**
- 文件名建议用英文或拼音（如 `kao-yan-math-gonglue.md`），避免中文路径问题
- `category` 字段必须是枚举值之一，否则会校验失败
- `excerpt` 用于文章列表页展示，建议控制在 50 字以内

## 设计系统

### 双主题

| 属性 | 亮色 | 暗色 |
|------|------|------|
| 背景 | 米白 `#FAFAF5` | 深蓝紫 `#0F0E1A` |
| 强调色 | 黄色 `#E5B044` | 蓝紫 `#8B7CF6` |
| 卡片 | 白色 `#FFFFFF` | 深色 `#1A1932` |

点击导航栏右侧的 ☀️/🌙 按钮切换主题，偏好自动保存到浏览器本地存储。

### 技术栈

- **框架**: Astro 6 — 零 JS 默认输出
- **样式**: 原生 CSS 变量 — 无运行时开销
- **内容**: Content Collections (glob loader) — Markdown 即文章
- **部署**: 纯静态 HTML — 可托管到 Vercel/GitHub Pages/Cloudflare Pages 等

## 产品文档

产品相关文档统一放在 `docs/` 目录：

| 文档 | 说明 |
|------|------|
| [docs/PRD.md](docs/PRD.md) | 产品需求文档（功能定义、设计规范、信息架构） |
| [docs/Backlog.md](docs/Backlog.md) | 功能迭代清单（当前进度 + 远期规划） |
| [docs/BugTracker.md](docs/BugTracker.md) | Bug 修复记录表 |

每次功能迭代或 Bug 修复时，同步更新对应文档。

## 部署

### Vercel

1. 将仓库推送到 GitHub
2. 在 Vercel 导入项目，Build Command 设为 `npm run build`
3. Output Directory 设为 `dist`
4. 自动部署

### GitHub Pages

1. 运行 `npm run build`
2. 将 `dist/` 目录推送到 `gh-pages` 分支
3. 在仓库 Settings → Pages 中选择 `gh-pages` 分支

### Cloudflare Pages

连接 GitHub 仓库，Build Command: `npm run build`, Output Directory: `dist`
