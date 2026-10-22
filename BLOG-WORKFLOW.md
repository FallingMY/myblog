# 博客维护手册

写给以后的我（和接手的 agent）。三条链路：本地改 → GitHub 构建 → Pages 发布。

## 1. 仓库与部署

| 角色 | 位置 |
| --- | --- |
| 源码（唯一要改的） | `D:\Git\myblog-2026` → github.com/FallingMY/myblog |
| 产物（不要手改） | github.com/FallingMY/FallingMY.github.io（Pages 从 main 根目录发布） |
| 站点 | https://fallingmy.github.io |

push 到 `myblog` 的 main 后，`.github/workflows/deploy.yml` 会自动：`npm ci` → `hugo --minify --gc` → rsync 到产物仓库 → 提交 `Deploy myblog@<sha>`。
产物仓库的 `puzzle/` 目录不在源码里，CI 用 `--exclude` 保着；其余文件每次整份替换。

## 2. 本地环境

- Hugo 0.152.2 extended（系统已装）。**不要升到 0.156+**：主题 v1.13.3 还在用 `.Site.Author`，0.156 起已移除，构建直接崩。
- 依赖装过就在 `node_modules`（Windows 侧装，别在 WSL 里装，会缺 `.cmd` 垫片）。
- 构建/预览一律走 npm 脚本，不要直接敲 `hugo`——Hugo 从 PATH 找 postcss，只有 npm 脚本会把 `node_modules/.bin` 加进去。

```
npm run preview   # http://localhost:1313，改文件自动刷新
npm run build     # 产出 public/
```

## 3. 写一篇新闻（content/news）

新建 `content/news/<slug>/index.md`：

```yaml
---
title: 标题
date: 2026-10-22T23:20:00+08:00
url: /news/2026/10/<slug>/     # 可选：不加就是中文标题当 URL
draft: false
comment: true
toc: false
reward: false
pinned: false      # true = 列表置顶
carousel: false
series: News
categories: []
tags: [News]
images: []
authors: Falling_MY
---
```

正文第一段下面放一行 `<!--more-->`，它之前的内容会作为列表摘要。

**URL 规则**：`config/_default/config.yaml` 里 `permalinks.news` 是 `/news/:year/:month/:title/`，`:title` 取的是**标题**不是文件名。想要英文 URL 就在 front matter 写 `url:` 覆盖。

## 4. 写一篇文档（content/docs）

- 新分区：建目录 + `_index.md`

  ```yaml
  ---
  title: '分区名'
  weight: 3            # 分区在 Docs 里的顺序
  main:
    weight: 3
    params:
      icon: '<i class="fas fa-fw fa-book"></i>'
  ---
  ```

- 分区里的页面：`content/docs/<分区>/<文件名>.md`，front matter 用 `title` / `date` / `weight`。

**排序规则（容易踩）**

- Docs 左侧导航：先按 `navWeight` **降序**，没有 navWeight 的再按标题字母序。只写 `weight` 在这里不起作用。
- 分区首页的卡片列表：按 `weight` 升序。
- 两者都要控制时，两个都写（例：第 1 期 `weight: 1` + `navWeight: 4`）。

## 5. 提交与发布

```
git status                 # 先看有没有意外改动
git add <文件>
git commit -m "content: ..."
git push                   # 触发 CI
```

发布后确认两件事：

1. https://github.com/FallingMY/myblog/actions 最近一次 run 是绿的；
2. https://github.com/FallingMY/FallingMY.github.io/commits/main 出现 `Deploy myblog@<sha>`。

Pages 构建还要再等 1–2 分钟，期间新 URL 可能 404，属正常。

## 6. 坑清单

- **日期在未来** → Hugo 不生成该页（`buildFuture` 默认关）。用当前时间或更早。
- **中文标题** → 中文 URL。介意就写 `url:`。
- **构建后 `git status` 变脏**：`resources/_gen/`、`hugo_stats.json` 被构建改写，提交前 `git restore resources/ hugo_stats.json`。
- **PUBLISH_TOKEN**：90 天过期，过期后 CI 卡在 "Checkout publish target"，重新建 token 覆盖 secret 即可。
- **CI 与本地产出可能不同**：CI 用 `npm ci`（按 lock 文件锁 2024 年的依赖），本地 `npm install` 会装新版本。要完全一致就在本地也跑 `npm ci`。
- **不要直接改产物仓库**：除 `puzzle/` 外的改动都会被下次部署覆盖。
- **旧目录 `D:\Git\myblog`**：origin 指向上游模板库，里面所有内容都未提交，别再往那儿写。
