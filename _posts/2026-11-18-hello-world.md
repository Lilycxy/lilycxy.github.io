---
title: Hello World：我的第一篇博客
tags: [随笔, 写作]
article_header:
  type: overlay
  theme: dark
  align: center
  background_color: '#2c3e50'
  background_image: false
# 想用图片当封面，就把上面这几行换成：
#   type: cover
#   image:
#     src: /assets/images/cover.jpg
# 想让首页卡片也带封面图，在头部另加一行：
# cover: /assets/images/cover.jpg
---

> 这是一篇写作示例，用来展示 TeXt 主题常用的 Markdown 写法和增强语法。
> 真正写文章时，把这个文件复制一份、改掉文件名和内容即可。

这是摘要部分，只有「more 注释」之前的内容会出现在首页列表和顶部标题栏里，所以第一段建议写成一句话概括。

<!--more-->

摘要之后就是正文了，这里的内容不会进摘要。

## 标题与文字

一级到六级标题都可以用，`##` ~ `###` 会自动出现在右上角的目录（TOC）里。

支持**粗体**、*斜体*、~~删除线~~、`行内代码`，以及[超链接](https://lilycxy.github.io/)。

## 列表

无序列表：

- 第一项
- 第二项
  - 可以嵌套
- 第三项

有序列表：

1. 第一步
2. 第二步
3. 第三步

## 引用

> 引用块适合放名言、摘录或者需要强调的段落。
>
> 引用里也可以有多段。

## 代码块

写代码时在三个反引号后面加上语言名，就会有语法高亮（这里的高亮主题由 `_config.yml` 的 `highlight_theme` 控制）：

```javascript
function hello(name) {
  return `Hello, ${name}!`;
}

console.log(hello('World'));
```

```bash
git add _posts/2026-11-18-hello-world.md
git commit --no-verify -m "docs: add first post"
git push
```

## 表格

| 文件名写法 | 发布日期 | 文章地址 |
| --------- | ------- | ------- |
| 2026-11-18-hello-world.md | 2026-11-18 | `/2026/11/18/hello-world.html` |
| 2026-12-01-my-trip.md | 2026-12-01 | `/2026/12/01/my-trip.html` |

## 提示样式

主题内置了四种提示块，在一段话后面紧跟一行 `{:.样式名}` 就行（注意中间**不能空行**）：

这是一条普通提示。
{:.info}

操作成功。
{:.success}

注意这里可能有问题。
{:.warning}

出错了。
{:.error}

也可以给行内文字上色：`info`{:.info}、`success`{:.success}、`warning`{:.warning}、`error`{:.error}。

## 图片

图片放在 `assets/images/` 目录下，用 `/` 开头的绝对路径引用（下面这张是仓库根目录自带的示例图，换成你自己的即可）：

![示例图片](/screenshot.jpg){:.border.rounded}

`{:.border.rounded}` 是给图片加圆角边框，还可以用 `.shadow`（阴影）、`.circle`（圆形裁剪），能叠加使用，比如 `{:.circle.shadow}`。

## 公式、流程图、图表

默认是关闭的，需要在这篇文章的头部打开对应开关，然后在代码块里写内容：

```yaml
---
title: 一篇文章
mathjax: true   # 开启后可用 $$ ... $$ 写 LaTeX 公式
mermaid: true   # 开启后可用 mermaid 代码块画流程图
chart: true     # 开启后可用 chart 代码块画图表
---
```

## 脚注

正文里可以加脚注[^note]，点击会跳到页面底部。

[^note]: 这就是脚注的内容，写在文章任意位置都可以，语法是 `[^note]: 内容`。

## 关于 Liquid 转义

Jekyll 会先把文件里的「双花括号」和「花括号加百分号」当作模板语法执行掉，再转成 Markdown。**在文章里演示这类语法或者分享这类代码时，必须用 raw 标签（开始标签 raw、结束标签 endraw）把那一段内容包起来**，否则整站构建会直接失败（本站第一次部署返回 404 就是这个原因）：

{% raw %}
```liquid
主题名：{{ site.text_skin }}
{% include footer.html %}
```
{% endraw %}

上面代码块里的花括号被 raw 标签包住了，所以会原样显示；不加的话 Jekyll 会尝试执行它们，一旦文件路径写错就报错中断。

## 写作流程小结

1. 在 `_posts/` 新建 `年-月-日-英文短标题.md`（日期不能写未来，否则不会生成）。
2. 头部写 `title` 和 `tags`，正文正常写 Markdown，用「more 注释」把摘要和正文分开。
3. `git add` → `git commit --no-verify -m "docs: ..."` → `git push`。
4. 等 1~2 分钟，GitHub Pages 会自动重新构建并发布。

更多可选字段（封面、作者、目录、评论开关等）见主题文档 `docs/_docs/zh/2.3-layouts.md`。
