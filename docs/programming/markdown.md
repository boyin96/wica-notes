---
tags:
  - Programming Language
  - Markdown
author: Bo Yin
---

# Markdown 语法简介

本文简单介绍并记录了常见的 [Markdown](https://www.markdownguide.org/basic-syntax/) 基础语法，并对 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 中的 Python Markdown 以及 Python Markdown Extensions 作简单拓展。

## 介绍

> 本网站是基于 Markdown 语法制作，再经由 MkDocs 构建。

Markdown 是一种轻量级的标记语言，设计用于简单快速地写作和排版。它使用简单的纯文本标记来表示文档的结构，具有易读易写、格式转换方便等特点。Markdown 文件可以通过各种工具转换为 HTML、PDF、Word 等格式，广泛用于编写文档、博客、论坛帖子等。

## 分级标题

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

或者

```markdown
这是一个一级标题
============================

这是一个二级标题
--------------------------------------------------
```

## 段落

要创建段落，请使用空行分隔一行或多行文本

```markdown
这是段落1

这是段落2
```

## 分隔线

你可以在一行中用三个以上的星号、减号、下划线来建立一个分隔线，行内不能有其他东西，你也可以在星号或是减号中间插入空格。

``` markdown
* * *
- - -
```

??? example
    
    `***`
    * * *

## 超链接

Markdown 支持以下形式的链接语法

### 行内式

语法为 `[链接文字](链接地址 "链接标题")` 其中 `[]` 里写链接文字，`()` 里写链接地址，`()` 中的 `""` 可以为链接指定title属性，title属性可加可不加，效果是鼠标悬停在链接上会出现指定的 title文字。

??? example
    
    ```markdown
    [Markdown Syntax](https://www.markdownguide.org/basic-syntax/)
    ```

    [Markdown Syntax](https://www.markdownguide.org/basic-syntax/)

    ```markdown
    [Markdown Syntax](https://www.markdownguide.org/basic-syntax/ "Markdown Syntax")
    ```

    [Markdown Syntax](https://www.markdownguide.org/basic-syntax/ "Markdown Syntax")

### 参考式

如果某一个链接在文章中多处使用，那么使用引用的方式创建链接将非常好，它可以让你对链接进行统一的管理，其语法为 `[链接文字][链接标记]`，在文本的任意位置添加 `[链接标记]:链接地址 "链接标题"`。

??? example

    ```markdown
    全球最大的搜索引擎网站是[Google][1]。

    [1]: https://www.google.com "Google"
    ```

    全球最大的搜索引擎网站是 [Google][1]。

    [1]:https://www.google.com "Google"

### 自动链接

Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用 `<>` 包起来，Markdown 就会自动把它转成链接。

??? example

    ```markdown
    <https://google.com/>
    <bborg.yin@gmail.com>
    ```

    <https://google.com/>

    <bborg.yin@gmail.com>

### 锚点

链接本文档内部的某些元素，从而实现当前页面中的跳转。这里采用了 [MkDocs](https://hellowac.github.io/mkdocs-docs-zh/user-guide/writing-your-docs/) 中提供的方式

??? example

    ```markdown
    **[⬆ top](markdown.md)**
    ```

    **[⬆ top](markdown.md)**

## 区块引用

区块引用需要在被引用的文本前加上 `>` 符号。

> 这是一个区块引用实例。

Markdown 也允许你只在整个段落的第一行最前面加上 `>`：

> The Markdown Guide is a free and open-source reference guide that explains how to use Markdown, 
the simple and easy-to-use markup language you can use to format virtually any document.

## 强调

Markdown 使用星号 `*` 和底线 `_` 作为标记强调字词的符号。

### 斜体

??? example

    ```markdown
    *这是斜体*
    ```

    *这是斜体*

### 粗体

??? example

    ```markdown
    **这是粗体**
    ```

    **这是粗体**

### 删除线

??? example

    ```markdown
    ~~这是删除线~~
    ```

    ~~这是删除线~~

## 列表

使用 `*`，`+`，`-` 表示无序列表。

### 无序列表

??? example

    ```markdown
    - 这是第一点
    - 这是第二点
    - 这是第三点
    ```

    - 这是第一点
    - 这是第二点
    - 这是第三点

### 有序列表

有序列表则使用数字接着一个英文句点。

??? example

    ```markdown
    1. 这是第一点
    2. 这是第二点
    3. 这是第三点
    ```

    1. 这是第一点
    2. 这是第二点
    3. 这是第三点

## 代码

### 行内代码

使用 (\`) 将其包围即可，`Markdown` 是一个轻量级标记语言。

### 行间代码

使用 ` ``` ``` `

??? example

    ```python
    import numpy as np
    print("NumPy 版本:", np.__version__)
    ```

## Python Markdown

Python Markdown 是一个 Python 库，允许以各种方式将 Markdown 文本转换为 HTML，与基本的 Markdown 语法有一些差别。Python Markdown Extensions 则是为 Python Markdown 提供额外功能的集合。

接下来简单介绍 Material for MkDocs 中的常用的 Markdown 语法。

首先如果要在 Material 中使用上述额外的功能，需要在配置文件中添加

```yaml
markdown_extensions:
  - pymdownx.arithmatex: # latex支持
      generic: true
  - admonition # admonition
  - abbr
  - pymdownx.caret    
  - pymdownx.details # admonition
  - pymdownx.keys
  - pymdownx.mark
  - pymdownx.tilde
  - pymdownx.tabbed:
      alternate_style: true 
  - md_in_html
  - toc:
      permalink: true # 固定标题位置为当前位置
      title: On this page
  - pymdownx.highlight: # 代码块高亮
      anchor_linenums: true
      linenums: true # 显示行号
      # auto_title: true # 显示编程语言名称
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
  - pymdownx.superfences # 代码块高亮插件 and admonition
  - meta # 支持Markdown文件上方自定义标题标签等
  - tables
```

上述配置针对 Markdown 功能的各个方面，可根据 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 官网自行选择搭配。

### [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)

Material for MkDocs 提供了几种不同类型的警告，并允许包含和嵌套任意内容。

!!! note

    The best of prophets of the future is the past.

!!! abstract

    The best of prophets of the future is the past.

!!! tip

    The best of prophets of the future is the past.

!!! info

    The best of prophets of the future is the past.

!!! success

    The best of prophets of the future is the past.

!!! question

    The best of prophets of the future is the past.

!!! warning

    The best of prophets of the future is the past.

!!! failure

    The best of prophets of the future is the past.

!!! example

    The best of prophets of the future is the past.

!!! quote

    The best of prophets of the future is the past.

!!! bug

    The best of prophets of the future is the past.

!!! danger

    The best of prophets of the future is the past.

### Icons && Emojis

!!! quote "Icon"

    :fontawesome-regular-face-laugh-wink:

!!! quote "Emoji"

    :smile:

### LaTex

!!! quote "math"

    $$
    \operatorname{ker} f=\{g\in G:f(g)=e_{H}\}{\mbox{.}}
    $$

可以看到 Python Markdown 提供了丰富且简单的渲染方式，有关图像、表格、注脚等更多功能就不一一展开，以后在需要的时候再做详解，其他更多配置请参考 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/reference/) 教程。

## 参考文章

1. [Markdown Guide](https://www.markdownguide.org/basic-syntax/)：Markdown 指南。
2. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)：Material for MkDocs 官网教程。
