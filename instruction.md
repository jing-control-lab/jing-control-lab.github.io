# sicphd 资源主页维护说明

网站：https://sicphd.github.io/  
仓库：https://github.com/sicphd/sicphd.github.io  
发布分支：`main`。账号与主页仓库已分别改名为 `sicphd`、`sicphd.github.io`。

这是个人资源与项目目录，仅有一个主内容页面。导航 Home / Resources / Projects 跳转至本页区域；不再展示课题组介绍、个人履历、联系方式或博客。保留旧页面地址的站内跳转。

## 文件与页面对应关系

| 修改内容 | 文件或目录 |
| --- | --- |
| 首页标题、介绍、栏目文字与空状态 | `index.html` |
| 下载文件 | `files/`，支持子目录 |
| 项目链接、名称、说明 | `_data/projects.yml` |
| 页内导航 | `_data/navigation.yml` |
| 字体、颜色、布局、手机适配 | `assets/css/group.css` |
| 页脚、网页标题、通用结构 | `_layouts/default.html` |
| 网站地址与 Jekyll 设置 | `_config.yml` |
| 图标 | `assets/images/favicon.svg` |

## 上传资源：自动显示在首页

1. 在 GitHub 仓库中打开 `files/`，点击 **Add file → Upload files**。
2. 上传 PDF、图片、ZIP、文本等需要公开分享的文件，提交到 `main`。
3. 等待 **Actions → pages build and deployment** 成功。
4. 首页 Resources 会自动列出 `files/` 下的文件，包括子目录内文件，按路径排序。无需手动修改首页链接。

例如上传 `files/notes/control-notes.pdf`，对应地址为 `https://sicphd.github.io/files/notes/control-notes.pdf`。这是路径示例，当前没有发布此文件。建议使用简洁英文文件名、连字符，避免空格。同路径同名上传会替换旧文件，使用新文件名则新增一项。

`files/README.md` 是仓库维护说明，已排除发布，不会作为资源条目。没有上传资源时，首页显示真实的空状态。当前没有示例项目或虚构文件。

文件链接由浏览器决定预览或下载（PDF 通常预览、ZIP 通常下载）。需要强制保存时可右键链接选择“链接另存为”。Markdown 资源若想保留原始文本供下载，不要添加 Jekyll 的 `---` front matter。网站是静态目录，文件通过 GitHub 上传，没有网页上传后台。

## 添加 Project

先在 `sicphd` 账号下创建真实项目仓库并上传代码，然后编辑 `_data/projects.yml`。首次添加时，将空数组 `[]` 替换成以下结构，并将示例改成真实项目：

```yaml
- title: "项目名称"
  description: "一句话说明项目的用途。"
  url: "https://github.com/sicphd/实际仓库名"
  kind: "REPO"
```

增加第二个项目时，再添加一组以 `- title:` 开头的记录。使用空格缩进，字符串加引号。`kind` 可填 `REPO`、`DEMO` 或 `DOCS`，也可省略，默认 `REPO`。如果项目有独立演示网站，`url` 可换成其真实 HTTPS 地址。不要保留示例链接。

项目源码建议放在各自独立仓库，主页只维护入口；发布的附件可以放 `files/项目名/`。上传图片到 `assets/images/`，正文引用真实路径，例如 `/assets/images/实际文件名.png`。

## 修改与发布

GitHub 打开文件 → 铅笔图标 → 编辑 → **Commit changes** 提交到 `main`。也可本地修改后上传覆盖对应文件。首页开头的 `---` 元数据与 Liquid 模板请保留。

Pages 配置：**Settings → Pages → Deploy from a branch → main → / (root)**，HTTPS 开启。不要添加 `.nojekyll`；资源列表在 Jekyll 构建阶段生成。无需数据库或额外依赖。

改动后检查首页、Resources 文件链接、Projects 项目链接和手机布局。若文件未出现，检查上传路径是否以 `files/` 开头、是否被 `_config.yml` 排除、构建是否成功；名称以下划线或点开头的目录可能被 Jekyll 忽略，请使用普通目录名。若仍看到旧页面，可强制刷新：Mac `Cmd+Shift+R`，Windows/Linux `Ctrl+Shift+R`。

## 改名后的地址

原账号名和主页仓库名均已更改。GitHub 对旧仓库链接提供重定向，但旧 Pages 网站地址不会自动跳转，请更新收藏与对外分享链接。

已有本地克隆可更新远端地址：

```sh
git remote set-url origin https://github.com/sicphd/sicphd.github.io.git
```

该账号只维护自己的资源。不要把其他账号的个人资料、代码或链接混入此站。公开仓库中的文件与历史可被访问；改名不会清除 Git 历史。保留 LICENSE 与必要版权声明。

旧 Course、News、Contact 等页面已改为返回资源目录；People、Publications、Research 返回项目区域，没有单独栏目内容。旧联系方式数据与网络插图不再用于网站。
