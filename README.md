# PresentJo

Hugo + PaperMod 个人博客。源文件由 Git 管理，GitHub Actions 构建后发布到 GitHub Pages。

- 本地目录：`/Users/jo/workspace/presentjo-blog`
- 目标网址：https://jocelyn66.github.io/presentjo.github.io/
- Hugo：`0.170.0`（与 CI 保持一致）
- 主题：`themes/PaperMod`，Git 子模块固定版本

## 本地预览

安装 Hugo 0.170.0 或更高的兼容版本，然后运行：

```sh
git submodule update --init --recursive
hugo server -D
```

打开终端显示的本地地址。`-D` 会显示草稿，正式构建默认不会发布草稿。

## 写文章

```sh
hugo new content posts/my-post.md
```

编辑 `content/posts/my-post.md`，填写标题、日期、摘要、标签及正文。
图片可放在 `static/images/`，在 Markdown 中使用相对链接 `../../images/图片名.png`。
预览确认后，将 `draft: true` 改为 `draft: false`。
`content/posts/first-post.md` 是草稿模板，不会出现在正式站点中。

## 构建与发布

```sh
hugo --gc --minify --panicOnWarning
```

首次发布需要在 GitHub 仓库 **Settings → Pages → Source** 中选择 **GitHub Actions**。
将确认过的修改提交并推送到 `main` 后，工作流会自动构建和发布；PR 只构建，不发布。
可在仓库 Actions 页面检查结果。`public/` 是生成目录，不提交到 Git。

## 修改站点

站名、首页文案、菜单和站点地址都在 `hugo.yaml` 中。
当前仓库是项目站点，URL 包含 `/presentjo.github.io/`；修改仓库名或绑定域名时同步修改 `baseURL`。

## 参考

- [Hugo 官方部署指南](https://gohugo.io/host-and-deploy/deploy-to-github-pages/)
- [PaperMod 文档](https://github.com/adityatelange/hugo-PaperMod/wiki)
