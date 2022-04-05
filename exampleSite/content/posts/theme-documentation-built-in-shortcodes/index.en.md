---
weight: 3
title: "Theme Documentation - Built-in Shortcodes"
date: 2020-03-05T16:29:41+08:00
lastmod: 2020-03-05T16:29:41+08:00
draft: false
authors: ["Dillon", "PCloud"]
description: "Hugo provides multiple built-in shortcodes for author convenience and to keep your markdown content clean."
featuredImage: "featured-image.webp"

tags: ["shortcodes"]
categories: ["documentation"]
series: ["getting-start"]
series_weight: 3
lightgallery: true
---

**Hugo** provides multiple built-in shortcodes for author convenience and to keep your markdown content clean.

<!--more-->

Hugo uses Markdown for its simple content format. However, there are a lot of things that Markdown doesn’t support well. You could use pure HTML to expand possibilities.

But this happens to be a bad idea. Everyone uses Markdown because it’s pure and simple to read even non-rendered. You should avoid HTML to keep it as simple as possible.

To avoid this limitations, Hugo created [shortcodes](https://gohugo.io/extras/shortcodes/).
A shortcode is a simple snippet that can generate reasonable HTML code and conforms to Markdown's design philosophy.

Hugo ships with a set of predefined shortcodes that represent very common usage. These shortcodes are provided for author convenience and to keep your markdown content clean.

## 1 figure {#figure}

[Documentation of `figure`](https://gohugo.io/content-management/shortcodes#figure)

Example `figure` input:

```markdown
{{</* figure src="/images/lighthouse.webp" title="Lighthouse (figure)" */>}}
```

The rendered output looks like this:

{{< figure src="/images/lighthouse.webp" title="Lighthouse (figure)" >}}

The HTML looks like this:

```html
<figure>
    <img src="/images/lighthouse.webp"/>
    <figcaption>
        <h4>Lighthouse (figure)</h4>
    </figcaption>
</figure>
```

## 2 gist

[Documentation of `gist`](https://gohugo.io/content-management/shortcodes#gist)

Example `gist` input:

```markdown
{{</* gist spf13 7896402 */>}}
```

The rendered output looks like this:

{{< gist spf13 7896402 >}}

The HTML looks like this:

```html
<script type="application/javascript" src="https://gist.github.com/spf13/7896402.js"></script>
```

## 3 highlight

[Documentation of `highlight`](https://gohugo.io/content-management/shortcodes#highlight)

Example `highlight` input:

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

The rendered output looks like this:

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

[Documentation of `param`](https://gohugo.io/content-management/shortcodes#param)

Example `param` input:

```markdown
{{</* param description */>}}
```

The rendered output looks like this:

{{< param description >}}

## 5 ref and relref {#ref-and-relref}

[Documentation of `ref` and `relref`](https://gohugo.io/content-management/shortcodes#ref-and-relref)

## 6 tweet

[Documentation of `tweet`](https://gohugo.io/content-management/shortcodes#tweet)

Example `tweet` input:

```markdown
{{</* tweet user="SanDiegoZoo" id="1453110110599868418" */>}}
```

The rendered output looks like this:

{{< tweet user="SanDiegoZoo" id="1453110110599868418" >}}

## 7 vimeo

[Documentation of `vimeo`](https://gohugo.io/content-management/shortcodes#vimeo)

Example `vimeo` input:

```markdown
{{</* vimeo 146022717 */>}}
```

The rendered output looks like this:

{{< vimeo 146022717 >}}

## 8 youtube

[Documentation of `youtube`](https://gohugo.io/content-management/shortcodes#youtube)

Example `youtube` input:

```markdown
{{</* youtube w7Ft2ymGmfc */>}}
```

The rendered output looks like this:

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
