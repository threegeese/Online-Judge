---
title: "Read me first!"
date: 2019-10-25T16:41:39+08:00
tags: [Learn]
---

## 关于本站

使用 [Hugo](https://gohugo.io/) + [Hugo Theme Cayman](https://themes.gohugo.io/cayman-hugo-theme/) 搭建，源码放在 [Github](https://github.com/threegeese/dsaa/)，并使用 [Netlify](https://netlify.com/) 托管静态页面。主要用来记录学习算法、数据结构以及刷题的日常。

分为三个大块：`LeetCode`、`Online Judge`、`Learn`。

标题名使用大写字母开头，尽量只使用英文标签名。且第一个标题表明该博文属于哪个块。

博客名字的后面通常会表示使用的是哪种语言，例如 [Prime Number - C](/oj/prime-number/) 表示使用的是 C 语言。

## 魔改主题

自定义了三个类，可以用来显示文章中不同的提示区块。`.diy-info`、`.diy-warning`、`.diy-danger`

<div class="diy-info">
diy-info 区块
</div>
<div class="diy-warning">
diy-warning 区块
</div>
<div class="diy-danger">
diy-danger 区块
</div>

使用 `Highlight Shortcode` 进行代码高亮，语法如下

```
// 请使用双花括号 `{{` 代替下面的 `{`
// linenos=inline 或者 linenos=table 提示显示代码前的行数
// hl_lines 设置高亮代码
// linenostart 设置代码行数的起始数字

{< highlight python "linenos=inline, hl_lines=3 8 12, linenostart=199" >}
# 编写代码
{< /highlight >}
```

使用 `highlight.js` 进行代码高亮

``` HTML
<!-- 注意它们的位置 -->
<link href="https://cdn.bootcss.com/highlight.js/9.15.10/styles/github-gist.min.css" rel="stylesheet">
<script src="https://cdn.bootcss.com/highlight.js/9.15.10/highlight.min.js"></script>
<script>hljs.initHighlightingOnLoad()</script>
```

取消代码注释的斜体

``` CSS
div.highlight pre code .hljs-comment {
    font-style: normal;
    font-size: 14px;
}
```

调整 `linenos=table` 时，代码显示块的宽度

``` CSS
div.highlight table > tbody > tr > td:nth-child(2){
    width: 100%;
}
```

`Highlight Shortcode` 示例

{{< highlight C "linenos=inline, hl_lines=3 8 12, linenostart=10" >}}
bool isPrime (int N) {
    if (N <= 3) {
        return N > 1;
    }

    // 不在 6 的倍数两侧的一定不是素数
    if (N % 6 != 1 && N % 6 != 5) {
        return false;
    }
    // 在 6 的两侧的也不一定是素数，如 25,49
    for (int i=5; i*i<=N; i+=6) {
        if (N % i == 0 || N % (i+2) == 0) {
            return false;
        }
    }
    return true;
}
{{< /highlight >}}

{{< highlight C "linenos=table, hl_lines=3 8 12, linenostart=10" >}}
bool isPrime (int N) {
    if (N <= 3) {
        return N > 1;
    }

    // 不在 6 的倍数两侧的一定不是素数
    if (N % 6 != 1 && N % 6 != 5) {
        return false;
    }
    // 在 6 的两侧的也不一定是素数，如 25,49
    for (int i=5; i*i<=N; i+=6) {
        if (N % i == 0 || N % (i+2) == 0) {
            return false;
        }
    }
    return true;
}
{{< /highlight >}}

## 欢迎交流

我的 [Telegram](https://t.me/xcing)。