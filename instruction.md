# JCL 网站维护说明

网站使用 Jekyll + HTML + CSS，由 GitHub Pages 自动构建。正文以英文为主，维护说明为中文。

- 网站地址：https://jing-control-lab.github.io/
- 仓库：https://github.com/jing-control-lab/jing-control-lab.github.io
- 默认发布分支：`main`

## 一、修改入口

| 要修改的内容 | 对应文件 |
| --- | --- |
| 首页标题、简介、About the Group、Research Overview | `index.html` |
| 四个研究方向（同时更新首页研究兴趣链接） | `_data/research.yml` |
| Research 页的说明、Projects、Open Courses 区域 | `_pages/research.html` |
| 已确认项目 | `_data/projects.yml` |
| 成员资料 | `_data/people.yml` |
| 三种状态的论文 | `_data/publications.yml` |
| 首页和 News 页的动态 | `_data/news.yml` |
| 博客正文 | `_blogs/` |
| 博客写作模板 | `_blogs/template.md` |
| 联系邮箱和地址 | `_data/contact.yml` |
| 导航名称及顺序 | `_data/navigation.yml` |
| 字体、颜色、宽度、移动端样式 | `assets/css/group.css` |
| 网络示意图 | `_includes/network.html` |
| 通用导航和页脚 | `_layouts/default.html` |
| 博客正文布局 | `_layouts/post.html` |
| 图片 | `assets/images/` |

## 二、在 GitHub 网页上直接修改

1. 登录 `jing-control-lab`，打开上面的仓库。
2. 找到需要编辑的文件，点击铅笔图标。
3. 修改后点击 **Commit changes**，写清这次改动，并提交到 `main`。
4. 打开 **Actions**，等待 `pages build and deployment` 运行成功，再刷新网站。

先在本地编辑也可以：下载或克隆仓库，用 VS Code 修改，再通过 GitHub 的 **Add file → Upload files** 上传，或使用 Git 提交推送。上传时保留目录结构。

**同一路径、同一文件名会更新原文件，不会自动创建另一篇文章，也不会覆盖整个仓库。** 新文章、新图片请使用新的文件名。一次上传多个文件前检查改动列表，避免选中不相关内容。

文件开头的 `---` 区域是 YAML 元数据，不要删掉。YAML 使用空格缩进，不使用 Tab；包含冒号等符号的文本建议用双引号包裹。

## 三、修改首页和研究方向

`index.html` 中 `<h1 id="group-title">JCL</h1>` 是主标题，`group-name` 段落是小字名称。简介、About the Group 和 Research Overview 可直接改英文段落。不要删除 Liquid 模板语法 `{% ... %}` 和 `{{ ... }}`。

四个方向集中在 `_data/research.yml`：

```yaml
- id: system-identification
  title: System Identification
  focus: Learning models from observations
  description: "这里换成确认后的英文研究介绍。"
```

`id` 是页面锚点，用小写英文和连字符，保持唯一。修改 `title` 会同步改变首页横向研究兴趣栏和 Research 页面标题。

项目确认后，把 `_data/projects.yml` 的空列表 `[]` 替换为：

```yaml
- title: "已确认的项目名称"
  description: "项目说明。"
  url: "https://example.org/project"
```

以上 URL 只是写法示例，使用时必须改成真实地址；不需要链接就删除 `url` 行。Open Courses 已链接到外部仓库，不需要复制其代码。

## 四、添加成员

目前成员列表为空。确认成员姓名、身份和公开信息后，将 `_data/people.yml` 的 `[]` 替换为：

```yaml
- name: "成员姓名"
  role: "已确认的身份"
  interests: "研究兴趣简介"
  photo: "/assets/images/member-name.jpg"
  url: "https://example.org/profile"
```

每位成员以 `- name:` 开始。`role`、`interests`、`photo`、`url` 均可省略。没有照片就删除 `photo` 行，不要填不存在的文件。没有确认的导师、职位或机构不要补写。

## 五、添加论文

`_data/publications.yml` 有三个列表：

- `published`：已经正式发表。
- `under_review`：在审，不代表录用。
- `in_preparation`：准备中，不代表已投稿。

例如，把对应的 `[]` 替换成条目，保留其他分类：

```yaml
published:
  - title: "已确认的论文标题"
    authors: "作者列表"
    venue: "期刊或会议"
    year: 2026
    url: "https://doi.org/替换为真实DOI"
under_review: []
in_preparation: []
```

`url`、`venue`、`year` 可省略。`note` 可写补充说明。这里的示例文字不能直接作为论文发布。只添加确认属于课题组的条目，个人过往论文不要自动搬进来。

## 六、发布 News

编辑 `_data/news.yml`，每条动态格式如下：

```yaml
- date: "2026-11-12"
  text: "这里替换成实际动态。"
  lang: en
```

日期按北京时间（Asia/Shanghai）填写实际日期。中文动态可写 `lang: zh-CN`。首页显示最近三条；News 页面自动按日期倒序显示全部。建站动态应始终对应实际首次发布日；首次部署如果跨天，请同步修正这一条日期。

## 七、通过 Markdown 写博客

1. 打开 `_blogs/template.md`，复制内容。
2. 新建文件，例如 `_blogs/2026-11-12-feedback-and-agents.md`。文件名用小写英文、数字和连字符，每篇不同。
3. 改写标题、日期、分类和摘要，替换全部示例正文。
4. 准备好发布后，把 `published: false` 改成 `published: true`。
5. 提交到 `main`，等待 GitHub Pages 构建成功。

文章头部示例：

```yaml
---
layout: post
title: "Feedback and agents"
date: 2026-11-12 09:00:00 +0800
category: "Technical note"
description: "文章的一句话摘要。"
lang: en
published: true
---
```

之后直接写 Markdown：二级标题用 `##`，列表用 `-`，代码使用三个反引号围起来。作者名可用可选的 `author` 字段，确认后再添加。

文章按日期倒序排列，地址形式为 `/blogs/文件名/`（去掉 `.md`）。以后改标题不会改 URL，改文件名会改 URL。

`_blogs/README.md` 和 `_blogs/template.md` 已在 `_config.yml` 排除，模板另有 `published: false` 双重保护，**它们不会作为正式文章出现**。其他草稿可设 `published: false`，但仓库是公开的，草稿源码仍然可被人查看，不要上传私人内容。

若需要中英文两篇文章，可新建 `topic-en.md` 和 `topic-zh.md`，分别设置 `lang: en`、`lang: zh-CN`，并在正文开头互相链接。当前框架不包含自动翻译或全站语言切换。

## 八、上传和引用图片

1. 在仓库打开 `assets/images/`。
2. **Add file → Upload files**，上传 JPG、PNG、WebP 或 SVG。
3. 使用简洁、唯一的英文文件名，例如 `network-experiment.png`，建议先压缩图片。
4. Markdown 中这样引用：

```markdown
![解释图片内容，方便读屏用户]({{ '/assets/images/network-experiment.png' | relative_url }})
```

HTML 页面中这样引用：

```html
<img src="{{ '/assets/images/network-experiment.png' | relative_url }}"
     alt="解释图片内容" loading="lazy">
```

绝对路径、大小写、扩展名必须与上传的文件一致。首页网络图是 SVG 代码，可以在 `_includes/network.html` 调整。慢速动画会自动尊重系统的“减少动态效果”设置。

## 九、修改联系方式、导航和样式

- 在 `_data/contact.yml` 的空字符串中填写确认后的邮箱和地址。未填写时页面显示 `To be added.`。
- `_data/navigation.yml` 控制导航顺序，保持 News 倒数第二、Contact 最后。
- `assets/css/group.css` 顶部的 `--paper`、`--accent` 等变量控制颜色。正文为 20px，辅助文字通常为 18px。
- 小屏布局通过 1100px、900px、700px 三个断点调整。改样式后检查手机，避免导航溢出。

## 十、GitHub Pages 配置与排错

1. 仓库必须是公开的 `jing-control-lab.github.io`，后缀为 `.io`。
2. 进入 **Settings → Pages**。
3. **Build and deployment → Source** 选 **Deploy from a branch**。
4. Branch 选 `main`，目录选 `/ (root)`，保存。
5. 等待 **Actions → pages build and deployment** 成功。

不要创建 `.nojekyll`；它会跳过 Jekyll，导致模板和 Markdown 不能正确渲染。`_config.yml` 中的 `url` 是 `https://jing-control-lab.github.io`，`baseurl` 保持空字符串。

如果显示旧版，先确认提交已成功部署，再强制刷新浏览器。如果构建失败，在 Actions 打开失败步骤，常见原因是 YAML 缩进、引号、Liquid 语法或日期格式。若图片 404，核对文件路径和大小写。

本地已有 Ruby、Bundler 时可运行：

```sh
bundle install
bundle exec jekyll serve
```

Jekyll 生成的 `_site/` 无需上传。站点不需要数据库、登录系统、JavaScript 框架或构建后端。

## 十一、来源和许可证

页面布局与必要样式参考 `zjin73/zjin73.github.io`，具体版本见 `NOTICE.md`。保留 `LICENSE` 内原有 MIT 版权声明和来源说明。改动仅面向本课题组仓库；个人网站独立维护。
