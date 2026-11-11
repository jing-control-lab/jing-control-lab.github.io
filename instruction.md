# JCL 单页网站维护说明

这是由我个人维护的代码与学习记录首页。网站只有一个内容页面，导航 Home、Code、Contact 分别跳转到同一页的对应区域。

- 网站：https://jing-control-lab.github.io/
- 仓库：https://github.com/jing-control-lab/jing-control-lab.github.io
- 发布分支：`main`

## 修改入口

| 内容 | 文件 |
| --- | --- |
| 个人用途说明、学习方向、代码和学习记录介绍 | `index.html` |
| 代码仓库链接 | `index.html` 的 Code repositories 区域 |
| 联系邮箱、地址 | `_data/contact.yml` |
| 页内导航 | `_data/navigation.yml` |
| 字体、颜色、布局、圆角导航和手机样式 | `assets/css/group.css` |
| 网络示意图 | `_includes/network.html` |
| 页脚及通用页面结构 | `_layouts/default.html` |
| 图片 | `assets/images/` |

## 如何编辑

1. 登录本账号，在仓库中打开对应文件并点击铅笔图标。
2. 修改内容，点击 **Commit changes** 提交到 `main`。
3. 打开 **Actions**，等待 `pages build and deployment` 成功后刷新网站。

也可以在本地使用 VS Code 编辑后，通过 GitHub 的 **Add file → Upload files** 上传。同名、同路径会更新原文件，新文件使用新的名称。不要删除文件开头的 `---` 元数据，YAML 使用空格缩进。

## 只维护本账号内容

添加代码入口时，使用本账号实际存在的仓库地址。不要复制其他账号的资源、身份信息或链接。当前首页的代码入口指向 `https://github.com/jing-control-lab`。

新增学习记录可直接写在 `index.html` 的 Learning records 区域，保持单页结构，不需要额外文章系统。较长的代码说明可写在本账号相应代码仓库的 README 中，然后从首页链接过去。

旧的栏目地址仅用于跳转回首页相应位置，没有单独的栏目内容。文章目录、文章布局和文章模板已经移除。

## 联系方式

编辑 `_data/contact.yml`：

```yaml
email: "zhjin201@gmail.com"
address: "Nanjing, Jiangsu, China"
```

邮箱会显示为可点击的邮件链接；地址是江苏南京的英文写法。

## 图片

将图片上传至 `assets/images/`，使用唯一英文文件名，在首页这样引用：

```html
<img src="{{ '/assets/images/example.png' | relative_url }}" alt="图片说明">
```

把示例路径替换成真实文件路径，注意大小写。网络图是 SVG，缓慢动画会尊重系统“减少动态效果”设置。

## Pages 配置

**Settings → Pages → Deploy from a branch → main → / (root)**。不要添加 `.nojekyll`。网站地址不变，HTTPS 保持启用。

本地已有 Ruby、Bundler 时可运行：

```sh
bundle install
bundle exec jekyll serve
```

生成目录 `_site/` 无需上传。保留 `LICENSE` 中必要的版权和许可声明。
