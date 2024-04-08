---
title: Material for MkDocs
tags:
  - Web
author: Bo Yin
---

本文简单介绍如何使用 [MkDocs](https://www.mkdocs.org/) 以及 [GitHub Pages](https://pages.github.com/) 构建个人网站，并搭配 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 主题。

## 介绍

> 本网站是基于 Material for MkDocs 二次创作，主要用于记录与分享个人学习心得。

MkDocs 是一个基于 Markdown 的静态站点生成器，它允许你使用简单的 Markdown 格式编写文档，并通过一个简单的配置文件快速构建美观的静态网站。Material for MkDocs 是 MkDocs 的一个主题扩展，它基于 Google Material Design 设计原则，提供了现代化的界面风格和丰富的功能，使得生成的文档更加美观和易于阅读。

MkDocs 的优点：

- **简单易用**：MkDocs 使用简单的 Markdown 语法编写文档，并提供一个简单的配置文件，使得构建静态网站变得非常容易。
- **灵活性**：MkDocs 支持丰富的插件和主题，可以根据需求定制和扩展。
- **速度快**：MkDocs 生成的静态网站速度非常快，可以快速呈现大量文档内容。

Material for MkDocs 的优点：

- **现代化界面**：Material for MkDocs 基于 Google Material Design，提供了现代化的界面风格和交互体验。
- **响应式布局**：Material for MkDocs 支持响应式布局，在各种设备上都能够良好地展示文档内容。
- **丰富功能**：Material for MkDocs 提供了丰富的功能和组件，如搜索功能、侧边栏、导航栏等，使得文档更加易于浏览和导航。

## 安装

安装 MkDocs 和 Material for MkDocs 主题

```python
pip install mkdocs mkdocs-material
```

检查是否安装成功

```python
mkdocs --version
```

## 创建新项目

新建一个文件夹，在该路径下打开终端，创建一个新的 MkDocs 项目

```bash
mkdocs new my-project (your project name)
```

当前路径下自动生成以下结构文件

```bash
my-project
├─ docs/
│  └─ index.md # 主页    
└─ mkdocs.yml # 配置文件 
```

## 配置文件

网页基本需求均可在 mkdocs.yml 配置文件中进行设置，相关设置可在 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 官网查询，以下是一个简单的配置

```yaml
# Project information
site_name: WiCa Notes
site_url: https://boyin.pro/wica-notes/
site_author: Bo Yin
site_description: This is technical notes site for me to record my learning thoughts.

# Repository
repo_name: boyin96/wica-notes
repo_url: https://github.com/boyin96/wica-notes/

# Copyright
copyright: Copyright &copy; 2024 ~ now | Bo Yin

# Navigation
nav:
  - Home: index.md
  - WiCa:
  - Technology:
    - Material for MkDocs: technology/mkdocs.md
  - Blog:
    - blog/index.md

# Theme
theme:
  name: material
  palette:
    # Palette toggle for light mode
    - media: "(prefers-color-scheme: light)"
      scheme: default
      primary: deep purple
      accent: deep purple
      toggle:
        icon: material/brightness-7 
        name: Switch to dark mode

    # Palette toggle for dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: black
      accent: indigo
      toggle:
        icon: material/brightness-4
        name: Switch to light mode

  features:
    - header.autohide  # 自动隐藏
    - navigation.instant # 自动隐藏
    - navigation.tracking # 地址栏中的 URL 将自动更新为在目录中突出显示的活动锚点
    - content.code.annotate
    - toc.integrate
    - toc.follow
    - navigation.path
    - navigation.top # 返回顶部的按钮 在上滑时出现
    - navigation.tabs
    - navigation.prune
    - navigation.footer
    - navigation.sections # 启用部分后，顶级部分在边栏中呈现为1220px以上视口的组，但在移动设备上保持原样
    - navigation.expand # 打开Tab时左侧目录全部展开
    - content.code.copy
    - navigation.indexes # 启用节索引页后，可以将文档直接附加到节
    - search.share # 搜索分享按钮
    - search.suggest # 搜索输入一些字母时推荐补全整个单词
    # - search.highlight # 搜索出的文章关键词加入高亮
    # - navigation.tabs.sticky # 启用粘性选项卡后，导航选项卡将锁定在标题下方，并在向下滚动时始终保持可见

  icon: 
    repo: fontawesome/brands/github

  font:
    text: Roboto
    code: Roboto Mono

  language: zh

# Plugins
plugins:
  - search:
      separator: '[\s\u200b\-]'
  - tags:
      tags_file: tags.md
  - blog

extra:
  generator: false # 删除页脚显示“使用 MkDocs 材料制造”

  consent:
    title: Cookie consent
    description: >- 
      We use cookies to recognize your repeated visits and preferences, as well
      as to measure the effectiveness of our documentation and whether users
      find what they're searching for. With your consent, you're helping us to
      make our documentation better.

  analytics: 
    provider: google
    property: G-YPXW9DM0JD
    feedback:
      title: Was this page helpful?
      ratings:
        - icon: material/emoticon-happy-outline
          name: This page was helpful
          data: 1
          note: >-
            Thanks for your feedback!
        - icon: material/emoticon-sad-outline
          name: This page could be improved
          data: 0
          note: >- 
            Thanks for your feedback!

# Latex
markdown_extensions:
  - pymdownx.arithmatex:
      generic: true

extra_javascript:
  - javascripts/mathjax.js
  - https://polyfill.io/v3/polyfill.min.js?features=es6
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```

## 网页生成

MkDocs 可以随时在本地进行网页生成和浏览，因此建议先在本地端调试好之后再上传到服务器。在 mkdocs.yml 同一路径下调用

```yaml
mkdocs serve
```

在浏览器中输入地址 [http://localhost:8000](http://localhost:8000/) 或者 [http://127.0.0.1:8000](http://127.0.0.1:8000/) 来预览网页效果。同样在 mkdocs.yml 同一路径下，使用以下命令生成网页文件夹

```yaml
mkdocs build
```

成功后，将在项目文件夹下生成一个名为 site 的文件夹，其中包含了所有生成的网页。

## 部署网站

关于如何部署网站到 GitHub Pages 上，[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/publishing-your-site/) 以及 [MkDocs](https://www.mkdocs.org/user-guide/deploying-your-docs/) 提供了详尽的说明，以下提供两种方式将网站部署到 GitHub Pages 上。

**1. 手动构建**

首先将上面 site 文件夹下的所有文件拷贝到项目根目录下，当我们部署网页时，只需要将上述内容上传到 Repo 即可。具体而言，首先你需要在本地端使用 markdown 语法写好自己的网页，然后通过 mkdocs build 构建好网页资源，然后将这些资源上传到你的 GitHub Repo 即可。

该方法比较麻烦，因为每次都要自己现在本地构建好静态文件，拷贝到相关目录下，再 push 到仓库。

**2. 自动化构建**

采用 GitHub Action 可以自动帮你完成上述 build 的过程，你只需要关注你的 markdown 网页内容即可。具体而言，首先添加在 GitHub 项目库根目录添加文件 .github/workflows/ci.yml

```yaml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

添加完成后，转到 GitHub Pages 页面将 Branch 源选择 gh-pages 保存即可。

## 总结

总而言之，MkDocs 和 Material for MkDocs 提供了一种简单而强大的方式来创建和管理文档网站。使用 Markdown 语法编写文档，通过简单的命令即可生成美观的静态网站，非常适合用于技术文档、项目文档等场景。通过 GitHub Pages 作为网站服务器，对于诸如个人网站、博客以及教程网站的搭建非常方便。

## 参考文章

1. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)：Material for MkDocs 官网教程。
2. [MkDocs](https://www.mkdocs.org/getting-started/)：MkDocs 官网教程。
