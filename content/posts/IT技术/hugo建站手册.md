+++
title = '破土动工'
date = 2024-11-20T09:08:27+08:00
draft = true
categories = ['IT技术']
tags = ['hugo','github','cloudflare']

+++



### 欢迎光临！

记录一下建站时间：2024年11月20日



# 安装手册

 版本  0.129.0 extends，从hugo release 下载安装

好的，下面是使用 Cloudflare Pages + GitHub + Hugo 搭建个人博客的详细步骤。这个过程将涵盖从环境准备到最终部署的所有步骤。

### 步骤 1: 准备工作

#### 1. 注册必要的账号
- **GitHub**: 访问 [github.com](https://github.com) 注册一个账号。
- **Cloudflare**: 访问 [cloudflare.com](https://www.cloudflare.com) 注册一个账号。

#### 2. 安装必要的软件
确保你的计算机上安装了以下软件：
- **Git**: 用于版本控制。
- **Hugo**: 用于生成静态网站。

##### 安装 Hugo
- **Windows**:
  ```bash
  winget install Hugo.Hugo.Extended
  ```
- **macOS**:
  ```bash
  brew install hugo
  ```
- **Linux**:
  ```bash
  sudo apt install hugo
  ```

### 步骤 2: 创建 Hugo 博客

#### 1. 创建新的 Hugo 站点
在命令行中运行以下命令：
```bash
hugo new site my-blog
cd my-blog
```

#### 2. 安装主题
选择一个你喜欢的主题，例如 `PaperMod`：
```bash
git init  # 初始化 Git 仓库
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

#### 3. 配置站点
创建或编辑 `config.toml` 文件，确保包含以下内容：
```toml
baseURL = "https://your-domain.com"  # 替换为你的域名
languageCode = "zh-cn"
title = "我的博客"
theme = "PaperMod"

[params]
  description = "这是我的个人博客"
  keywords = "博客, 技术, 编程"
```

#### 4. 创建第一篇文章
运行以下命令创建一篇新文章：
```bash
hugo new posts/my-first-post.md
```
编辑 `content/posts/my-first-post.md` 文件，添加内容：
```markdown
---
title: "我的第一篇文章"
date: 2024-01-20
draft: false
---

这是我的第一篇博客文章内容。
```

### 步骤 3: 本地测试

在本地运行 Hugo 服务器以预览博客：
```bash
hugo server -D
```
在浏览器中访问 `http://localhost:1313` 查看效果。

### 步骤 4: 部署到 GitHub

#### 1. 创建 GitHub 仓库
- 登录 GitHub，创建一个新的仓库，名称可以是 `my-blog` 或其他。

#### 2. 推送代码到 GitHub
在命令行中运行以下命令：
```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/my-blog.git  # 替换为你的仓库地址
git push -u origin main
```

### 步骤 5: 部署到 Cloudflare Pages

#### 1. 登录 Cloudflare
- 访问 [Cloudflare Dashboard](https://dash.cloudflare.com) 并登录。

#### 2. 创建 Cloudflare Pages 项目
- 在 Cloudflare Dashboard 中，选择 "Pages"。
- 点击 "Create a project"。
- 选择 "Connect to Git"。

#### 3. 授权 GitHub
- 授权 Cloudflare 访问你的 GitHub 账户。
- 选择刚刚创建的 GitHub 仓库。

#### 4. 配置构建设置
- **Framework preset**: 选择 "Hugo"。
- **Build command**: 输入 `hugo --gc --minify`。
- **Build output directory**: 输入 `public`。

#### 5. 部署设置
- 点击 "Save and Deploy"。
- 等待 Cloudflare 完成构建和部署。

### 步骤 6: 配置自定义域名

#### 1. 添加自定义域名
- 在 Cloudflare Pages 项目设置中，找到 "Custom domains"。
- 点击 "Add custom domain"，输入你的域名。

#### 2. DNS 设置
- 如果你的域名已经在 Cloudflare 管理，DNS 记录会自动配置。
- 如果域名在其他服务商，添加 CNAME 记录指向 Cloudflare Pages 地址。

### 步骤 7: 日常使用

#### 1. 创建新文章
```bash
hugo new posts/新文章标题.md
```

#### 2. 编辑文章
使用 Markdown 编辑器编辑文章内容。

#### 3. 发布更新
```bash
git add .
git commit -m "Add new post"
git push
```
推送后，Cloudflare 会自动重新部署。

### 补充建议

1. **SEO 优化**: 在 `config.toml` 中添加网站描述和关键词。
2. **评论系统**: 可以集成 Disqus 或 Giscus。
3. **统计分析**: 使用 Google Analytics 或 Cloudflare Analytics。

### 总结

通过以上步骤，你可以成功搭建一个使用 Cloudflare Pages + GitHub + Hugo 的个人博客。如果在过程中遇到任何问题，请随时询问，我会提供进一步的帮助。


# 使用手册
我将为你提供一个详细的 Hugo 博客管理教程。

### 1. 目录管理

#### 创建目录
```bash
# 创建文章分类目录
hugo new content/posts/tech/_index.md
hugo new content/posts/life/_index.md

# 创建页面目录
hugo new content/about/_index.md
hugo new content/links/_index.md
```

#### 目录配置示例
在 `_index.md` 中可以添加目录描述：
```markdown
---
title: "技术分享"
description: "记录技术成长的点点滴滴"
---
```

### 2. 文章管理

#### 创建文章
```bash
# 创建技术类文章
hugo new content/posts/tech/hugo-tutorial.md

# 创建生活类文章
hugo new content/posts/life/daily-thinking.md
```

#### 文章模板（Archetype）
在 `archetypes/posts.md` 创建文章模板：
```markdown
---
title: "{{ .Name | title }}"
date: {{ .Date }}
draft: true
tags: [""]
categories: [""]
description: ""
---

文章内容
```

#### 文章前置元数据（Front Matter）
```markdown
---
title: "文章标题"
date: 2024-01-20
draft: false  # false 表示发布，true 表示草稿
tags: ["Hugo", "博客"]  # 标签
categories: ["技术"]   # 分类
weight: 1     # 排序权重
summary: "文章摘要"   # 文章摘要
---
```

### 3. 网站配置

#### 站点基本信息
`config.toml` 配置：
```toml
baseURL = "https://example.com"
languageCode = "zh-cn"
title = "我的博客"
theme = "PaperMod"

[params]
  description = "个人技术博客"
  keywords = "Hugo,博客,技术"
  author = "Your Name"
  
  # 社交链接
  [[params.socialIcons]]
    name = "github"
    url = "https://github.com/yourusername"
  
  [[params.socialIcons]]
    name = "twitter"
    url = "https://twitter.com/yourusername"

# 菜单配置  
[menu]
  [[menu.main]]
    identifier = "home"
    name = "首页"
    url = "/"
    weight = 1

  [[menu.main]]
    identifier = "archives"
    name = "归档"
    url = "/archives"
    weight = 2

  [[menu.main]]
    identifier = "categories"
    name = "分类"
    url = "/categories"
    weight = 3

  [[menu.main]]
    identifier = "tags"
    name = "标签"
    url = "/tags"
    weight = 4
```

### 4. 页脚配置
在 `layouts/partials/footer.html` 创建自定义页脚：
```html
<footer>
  <div>
    © {{ now.Year }} 你的博客名称 | 
    <a href="/about">关于</a> | 
    <a href="/links">友链</a>
  </div>
  <div>
    Powered by Hugo | Theme by PaperMod
  </div>
</footer>
```

### 5. 常用命令

#### 文章管理
```bash
# 创建新文章
hugo new content/posts/new-post.md

# 删除文章
rm content/posts/old-post.md

# 本地预览
hugo server -D

# 构建站点
hugo --gc --minify
```

### 6. 图片和资源管理

#### 图片存储
```
content/
└── posts/
    └── my-post/
        ├── index.md
        └── images/
            ├── cover.jpg
            └── image1.png
```

#### 引用图片
```markdown
![图片描述](/posts/my-post/images/cover.jpg)
```

### 7. 常见问题处理

#### 草稿发布
```bash
# 构建时包含草稿
hugo -D

# 本地预览草稿
hugo server -D
```

#### 文章排序
```toml
# config.toml
[frontmatter]
  date = ["date", "publishDate", "lastmod"]
  lastmod = [":git", "lastmod", "date", "publishDate"]
```

### 8. 建议的目录结构
```
my-blog/
├── archetypes/     # 内容模板
├── assets/         # 资源文件
├── content/        # 网站内容
│   ├── posts/      # 文章目录
│   └── pages/      # 独立页面
├── layouts/        # 自定义布局
├── static/         # 静态资源
├── themes/         # 主题
└── config.toml     # 站点配置
```

### 总结
这个教程涵盖了 Hugo 博客的基本管理。随着使用的深入，你可以逐步探索更多高级功能。

建议：
1. 经常备份你的内容
2. 使用 Git 进行版本控制
3. 保持内容的一致性和质量

如需更详细的指导，随时告诉我。


## hugo配置手册(验证有效)
#### 相关文件备注
- themes\主题\layout\partials
	- single.html
		- 文章阅读页面的设置
	- list.html
		- 文章列表页面的设置
	- summary.html
		- 文章列表中单个项目的设置
	- terms.html
		- 在标签列表/目录列表中单个项目的设置
	- head-additions.html
		- 页面最上方可自定义添加的内容
	- site-header.html
		- 页面标题部分可自定义配置的内容
- hugo.toml
	- 配置hugo的相关参数
	- 配置hugo的菜单