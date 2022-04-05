---
weight: 3
title: "主题文档 - 内置 Shortcodes"
date: 2020-03-05T16:29:59+08:00
lastmod: 2020-03-05T16:29:59+08:00
draft: false
authors: ["Dillon", "PCloud"]
description: "Hugo 提供了多个内置的 Shortcodes, 以方便作者保持 Markdown 内容的整洁."
featuredImage: "featured-image.webp"

tags: ["shortcodes"]
categories: ["documentation"]
series: ["getting-start"]
series_weight: 3
lightgallery: true
---

**Hugo** 提供了多个内置的 Shortcodes, 以方便作者保持 Markdown 内容的整洁.

<!--more-->

Hugo 使用 Markdown 为其简单的内容格式. 但是, Markdown 在很多方面都无法很好地支持. 你可以使用纯 HTML 来扩展可能性.

但这恰好是一个坏主意. 大家使用 Markdown, 正是因为它即使不经过渲染也可以轻松阅读. 应该尽可能避免使用 HTML 以保持内容简洁.

为了避免这种限制, Hugo 创建了 [shortcodes](https://gohugo.io/extras/shortcodes/).
shortcode 是一个简单代码段, 可以生成合理的 HTML 代码, 并且符合 Markdown 的设计哲学.

Hugo 附带了一组预定义的 shortcodes, 它们实现了一些非常常见的用法.
提供这些 shortcodes 是为了方便保持你的 Markdown 内容简洁.

## 1 figure {#figure}

[`figure` 的文档](https://gohugo.io/content-management/shortcodes#figure)

一个 `figure` 示例:

```markdown
{{</* figure src="/images/lighthouse.webp" title="Lighthouse (figure)" */>}}
```

呈现的输出效果如下:

{{< figure src="/images/lighthouse.webp" title="Lighthouse (figure)" >}}

输出的 HTML 看起来像这样:

```html
<figure>
    <img src="/images/lighthouse.webp"/>
    <figcaption>
        <h4>Lighthouse (figure)</h4>
    </figcaption>
</figure>
```

## 2 gist

[`gist` 的文档](https://gohugo.io/content-management/shortcodes#gist)

一个 `gist` 示例:

```markdown
{{</* gist spf13 7896402 */>}}
```

呈现的输出效果如下:

{{< gist spf13 7896402 >}}

输出的 HTML 看起来像这样:

```html
<script type="application/javascript" src="https://gist.github.com/spf13/7896402.js"></script>
```

## 3 highlight

[`highlight` 的文档](https://gohugo.io/content-management/shortcodes#highlight)

一个 `highlight` 示例:

```markdown
{{</* highlight html */>}}
<section id="main">
    <div>
        <h1 id="title">{{ .Title }}</h1>
        {{ range .Pages }}
            {{ .Render "summary"}}
        {{ end }}
    </div>
</section>
{{</* /highlight */>}}
```

呈现的输出效果如下:

{{< highlight html >}}
<section id="main">
    <div>
        <h1 id="title">{{ .Title }}</h1>
        {{ range .Pages }}
            {{ .Render "summary"}}
        {{ end }}
    </div>
</section>
{{< /highlight >}}

## 4 param

[`param` 的文档](https://gohugo.io/content-management/shortcodes#param)

一个 `param` 示例:

```markdown
{{</* param description */>}}
```

呈现的输出效果如下:

{{< param description >}}

## 5 ref 和 relref {#ref-and-relref}

[`ref` 和 `relref` 的文档](https://gohugo.io/content-management/shortcodes#ref-and-relref)

## 6 tweet

[`tweet` 的文档](https://gohugo.io/content-management/shortcodes#tweet)

一个 `tweet` 示例:

```markdown
{{</* tweet user="SanDiegoZoo" id="1453110110599868418" */>}}
```

呈现的输出效果如下:

{{< tweet user="SanDiegoZoo" id="1453110110599868418" >}}

## 7 vimeo

[`vimeo` 的文档](https://gohugo.io/content-management/shortcodes#vimeo)

一个 `vimeo` 示例:

```markdown
{{</* vimeo 146022717 */>}}
```

呈现的输出效果如下:

{{< vimeo 146022717 >}}

## 8 youtube

[`youtube` 的文档](https://gohugo.io/content-management/shortcodes#youtube)

一个 `youtube` 示例:

```markdown
{{</* youtube w7Ft2ymGmfc */>}}
```

呈现的输出效果如下:

{{< youtube w7Ft2ymGmfc >}}

## 9 tabs

```markdown
{{</* tabs tabTotal="1" */>}}
{{</* tab tabName="Tab 1" */>}}

**Tab 1 Content**

{{</* /tab */>}}
{{</* /tabs */>}}
```

效果如下：

{{< tabs tabTotal="1" >}}
{{< tab tabName="Tab 1" >}}

**Tab 1 Content**

{{< /tab >}}
{{< /tabs >}}

The following is an example of Hugo Dynamic Tabs being used with multiple nested tab shortcodes.

```markdown
{{</* tabs tabTotal="3" tabRightAlign="2"*/>}}
{{</* tab tabName="Tab 1" */>}}

**Tab 1 Content**

{{</* /tab */>}}
{{</* tab tabName="Tab 2" */>}}

**Tab 2 Content**

{{</* /tab */>}}
{{</* tab tabName="Tab 3"*/>}}

**Tab 3 Content**

{{</* /tab */>}}
{{</* /tabs */>}}
```

效果如下：

{{< tabs tabTotal="3" tabRightAlign="2">}}
{{< tab tabName="Tab 1" >}}

**Tab 1 Content**

{{< /tab >}}
{{< tab tabName="Tab 2" >}}

**Tab 2 Content**

{{< /tab >}}
{{< tab tabName="Tab 3">}}

**Tab 3 Content**

{{< /tab >}}
{{< /tabs >}}

### tabs.html

This is the parent shortcodes that wraps around all nested tab shortcodes in the tab group and generates the tab navigation.

| Variable  | Description |
| --------- | ----------- |
| tabTotal | This variable is used to generate the tab navigation. Simply set it to the amount of tab shortcodes you have. In the above example, since there are **three** nested tab shortcodes, you would set **tabTotal** to **three**.|
| tabRightAlign | This is an optional variable that if used will right align the tab number you inputted and all tabs after it. In the above example, since **tabRightAlign** is set to **two**, tabs 2 and 3 will be right aligned.  |

### tab.html

This is a child shortcode that is nested in the tabs shortcodes. Each tab shortcode equals one tab so add as many as you need. Please note, make sure **tabTotal** in the tabs shortcode is equal to the amount of tab shortcodes you use.

| Variable  | Description |
| --------- | ----------- |
| tabName | This variable holds the name of the tab.  |
