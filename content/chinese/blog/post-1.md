---
title: "标题在这个地方写"
meta_title: ""
description: "posts 文章的介绍"
date: 2025-05-21T05:00:00Z
image: "/images/gallery/01.jpg"
categories: ["hugo", "markdown"]
author: "ruiyu"
tags: ["hugo", "markdown"]
draft: false

---

## 这是第一篇文章

以下是一些基本的 Hugo 文章 Markdown 文件的语法和结构要点：

1. **Front Matter（前置数据）**: 在每个 Markdown 文件的顶部，你需要包含一段 Front Matter，这是元数据区域，用于定义文章的各种属性，如标题、日期、标签等。可以使用 YAML、TOML 或 JSON 格式来写。YAML 格式如下：

   ```yaml
   ---
   title: "我的文章标题"
   date: 2025-05-21T20:55:00+08:00
   draft: false
   tags: ["标签1", "标签2"]
   categories: ["分类1", "分类2"]
   ---
   ```

2. **Markdown 内容**: Front Matter 后面的部分就是文章的正文部分，使用标准的 Markdown 语法来撰写。例如：

   - 标题：使用 `#` 到 `######` 来表示不同级别的标题。
   - 强调文字：使用 `*斜体*` 或 `_斜体_`；`**粗体**` 或 `__粗体__`。
   - 链接：使用 `[链接文本](URL)` 的形式。
   - 图片：使用 `![替代文字](图片路径)`。
   - 列表：无序列表使用 `-`, `+`, 或 `*`；有序列表使用数字加句号，例如 `1.`。
   - 引用：使用 `>` 符号开头的段落。

3. **短代码（Shortcodes）**: Hugo 提供了强大的短代码功能，可以在 Markdown 中插入复杂的 HTML 结构或动态内容。例如：

   深色版本

   ```html
   {{</* figure src="/images/picture.jpg" title="说明文字" */>}}
   ```

   这会在你的文章中添加一张带有标题的图片。

4. **其他特性**:

   - **草稿模式**：在 Front Matter 中设置 `draft: true` 可以将文章标记为草稿，这样在非 `--buildDrafts` 模式下不会被发布。
   - **自定义输出**：可以通过修改主题或者自己添加模板来自定义文章的输出格式。

通过这些基础元素，你可以创建丰富且具有吸引力的内容。记得根据你使用的 Hugo 主题调整某些设置，因为不同的主题可能对 Front Matter 和页面布局有不同的要求。
