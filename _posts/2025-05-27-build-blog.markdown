---
layout: post
title:  "Build Blog."
date:   2025-05-27 23:04:45 +0800
categories: jekyll update
---

# 不同框架下快速在github博客发表新文章的方法

在当今数字化时代，拥有一个个人博客是分享知识、展示自我的好方式。而利用 GitHub 来托管博客，不仅免费，还能借助其强大的版本控制功能。常见的博客框架如 Jekyll、Hugo、Hexo 都能与 GitHub 很好地结合。以下将详细介绍在这些框架下快速在 GitHub 博客发表新文章的方法。

**本文内容由Coze AI生成，少部分内容经过本人实际操作后进行了修改和完善哦！本按照里面的Jekyll框架教程顺利无痛归回博客写作~ 好用！谢谢AI！**

## 一、Jekyll 框架

Jekyll 是一个简单的博客形态的静态站点生产机器，它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown ）和 Liquid 渲染器转化成一个完整的可发布的静态网站。

### 1. 环境准备

- **安装 Ruby**：Jekyll 是基于 Ruby 开发的，所以需要先安装 Ruby。对于 Windows 用户，可从 [RubyInstaller](https://rubyinstaller.org/downloads/) 下载 Ruby+Devkit(x64) 版本，下载完后一路默认安装完成即可。安装后在 cmd 打开命令行工具 ，执行 `ruby -v` 命令，检测是否安装成功。
- **安装 RubyGems**：RubyGems 是 Ruby 的包管理器，可从 [官网](https://rubygems.org/pages/download) 下载 zip 文件到本地，然后解压。在 cmd 打开命令行工具，cd 到解压目录，执行 `ruby setup.rb` 命令进行安装，安装完成后执行 `gem -v` 命令检测是否安装成功。
- **安装 Jekyll**：在 cmd 打开命令行工具，执行 `gem install jekyll` 命令进行安装，安装完成后执行 `jekyll -v` 命令检测是否安装成功。

### 2. 创建文章

- **创建Jekyll项目**: 首先定位到一个合适的根目录，然后使用`jekyll new xxx`创建一个名为xxx的新项目，该命令会在当前根目录下生成项目文件夹。

- **创建文章文件**：在 Jekyll 项目的 `_posts` 文件夹里写博客，文件名命名规范必须和里面自带的一致，例如：`2016-10-27-XXXXX.markdown` 。也可以使用命令来创建文章，如 `rake post title="about this blog"` 。
- **编辑文章内容**：使用文本编辑器打开文章文件，设置 `title`、`description`、`category`、`tags` 等信息，再用 Markdown 来写文章内容。

### 3. 本地预览

在博客模板的路径下，执行 `jekyll server` 命令启动本地服务，然后在浏览器访问 `http://127.0.0.1:4000/` ，即可预览博客内容。

### 4. 发布到 GitHub

- **创建 GitHub 仓库**：在 GitHub 上创建一个名为 `username.github.io` 的仓库，其中 `username` 是你的 GitHub 用户名。

- **推送文件**：将本地的 Jekyll 项目文件推送到 GitHub 仓库。在本地项目目录下，执行以下命令：

  首次执行：

  ```bash
  git init
  git checkout --orphan gh-pages  // jekyll需要用gh-pages分支
  ```

```bash
git add .
git commit -m "post a new article"
git push origin gh-pages
```

推送成功后，在浏览器中输入 `https://username.github.io` ，即可看到你写的博客。

每次修改/写了新文章后，执行下面这三行代码：

```
git add .
git commit -m "post a new article"  // "xxx"内的内容是注释信息
git push origin gh-pages
```

我的博客：https://ruoxuan-li.github.io/

## 二、Hugo 框架

Hugo 是一个用 Go 语言编写的静态网页生成器，可以在几秒钟内（通常更短）呈现完整的网站。

### 1. 环境准备

- **安装 Hugo**：Hugo 支持多种安装方式，如包管理器安装、二进制文件安装等。以 Windows 系统为例，可从 [GitHub 发布页面](https://github.com/gohugoio/hugo/releases) 下载扩展版的预编译二进制文件，解压到目标目录后，将目标目录添加到环境变量 `PATH` 中，然后在终端执行 `hugo version` 命令验证安装是否成功。
- **安装 Git**：从 [Git 官网](https://git-scm.com/) 下载适合你操作系统的安装包进行安装，安装完成后在命令行中输入 `git --version` ，若显示 Git 的版本信息，则表明安装成功。

### 2. 创建文章

- **创建站点**：在命令行中，运行 `hugo new site <站点名称>` 来创建一个新的 Hugo 站点，这将创建一个包含所有必要文件和目录的新文件夹。
- **添加主题**：Hugo 使用主题来控制站点的外观和感觉。你可以从 [Hugo 主题库](https://themes.gohugo.io/) 中选择一个主题，并将其添加到你的站点中。例如，将主题仓库克隆到你的 `themes` 目录中：

```bash
git clone <主题仓库地址> themes/<主题名称>
```

- **配置站点**：在站点根目录中，编辑 `config.toml`（或 `config.yaml`、`config.json`）文件来配置站点设置，如站点标题、URL、主题等。
- **创建文章**：使用 `hugo new <内容类型>/<文件名>.md` 命令来创建新的内容文件，如文章或页面。例如：

```bash
hugo new post/my-article.md
```

创建完成后，打开生成的 Markdown 文件，将 `draft` 字段的值从 `true` 改为 `false` ，表示这不是一篇草稿。

### 3. 本地预览

在命令行中，运行 `hugo server` 命令来启动一个本地服务器，并预览站点。你可以通过浏览器访问 `http://localhost:1313` 来查看站点。

### 4. 发布到 GitHub

- **创建 GitHub 仓库**：在 GitHub 上创建一个名为 `username.github.io` 的仓库，其中 `username` 是你的 GitHub 用户名。
- **生成静态文件**：在本地项目目录下，执行 `hugo` 命令生成静态文件，这将在站点目录中创建一个 `public` 文件夹，其中包含所有静态文件。
- **推送文件**：将 `public` 文件夹中的内容推送到 GitHub 仓库。在 `public` 目录下，执行以下命令：

```bash
git init
git add .
git commit -m "publish new article"
git remote add origin git@github.com:username/username.github.io.git
git push -u origin master
```

## 三、Hexo 框架

Hexo 是一个基于 Node.js 的快速、简洁且高效的博客框架，它使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

### 1. 环境准备

- **安装 Node.js**：从 [Node.js 官网](https://nodejs.org/) 下载适合你操作系统的安装包进行安装，安装完成后在命令行中输入 `node -v` 和 `npm -v` ，若显示相应的版本信息，则表明安装成功。
- **安装 Git**：从 [Git 官网](https://git-scm.com/) 下载适合你操作系统的安装包进行安装，安装完成后在命令行中输入 `git --version` ，若显示 Git 的版本信息，则表明安装成功。
- **安装 Hexo**：在命令行中，执行 `npm install -g hexo-cli` 命令全局安装 Hexo，安装完成后执行 `hexo -v` 命令检测是否安装成功。

### 2. 创建文章

- **初始化项目**：在本地选择一个合适的目录，执行 `hexo init <项目名称>` 命令初始化 Hexo 项目，然后进入项目目录，执行 `npm install` 命令安装依赖。
- **创建文章**：执行 `hexo new "文章标题"` 命令创建新的文章，文章文件将生成在 `source/_posts` 目录下。
- **编辑文章内容**：使用支持 Markdown 语法的编辑器打开文章文件，编写文章内容。

### 3. 本地预览

在项目根目录下，执行 `hexo server` 命令启动本地服务器，然后在浏览器访问 `http://localhost:4000` ，即可预览博客内容。

### 4. 发布到 GitHub

- **创建 GitHub 仓库**：在 GitHub 上创建一个名为 `username.github.io` 的仓库，其中 `username` 是你的 GitHub 用户名。
- **配置部署信息**：打开项目根目录下的 `_config.yml` 文件，修改 `deploy` 配置如下：

```yaml
deploy:
  type: git
  repo: git@github.com:username/username.github.io.git
  branch: master
```

- **安装部署插件**：在项目根目录下，执行 `npm install hexo-deployer-git --save` 命令安装部署插件。
- **部署文章**：执行 `hexo clean` 命令清除缓存文件，然后执行 `hexo generate` 命令生成静态文件，最后执行 `hexo deploy` 命令将本地文件发布到 GitHub 仓库。

通过以上步骤，你可以在不同的博客框架下快速在 GitHub 博客发表新文章。选择适合自己的框架，并按照相应的步骤操作，就能轻松地分享自己的知识和见解。"