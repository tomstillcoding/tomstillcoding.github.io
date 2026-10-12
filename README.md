# 01的博客

该博客是通过 GitHub Pages + [Astro](https://astro.build)（主题是 [Fuwari](https://github.com/saicaca/fuwari)）搭建而成的。
2026 年之前使用的是 Jekyll + Chirpy，旧文章的链接保持不变。

## 本地运行

```sh
pnpm install
pnpm dev            # 本地预览，修改后自动刷新
pnpm build          # 构建到 dist/（含 Pagefind 搜索索引）
pnpm preview        # 预览构建结果
```

## 写文章

```sh
pnpm new-post 文章文件名
```

会在 `src/content/posts/` 下生成带模板的 Markdown：

```yaml
---
title: 标题
published: 2026-10-12
description: ''     # 留空则首页自动截取正文
image: ''
tags: []
category: ''
draft: false
lang: ''
# slug: 自定义网址  # 可选，默认由文件名生成（转小写）
---
```

- 图片放在 `public/assets/blog_res/<文章名>.assets/`，文中用 `/assets/blog_res/...` 引用。
  Typora 用户可在 front matter 中加 `typora-root-url: ../../../public` 以便本地预览。
- 关于页面在 `src/content/spec/about.md`，站点信息在 `src/config.ts`。

## 部署

推送到 `main` 后由 `.github/workflows/deploy.yml` 自动构建并发布到 GitHub Pages
（仓库 Settings → Pages → Source 需设为 “GitHub Actions”）。
