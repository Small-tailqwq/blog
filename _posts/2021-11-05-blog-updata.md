---
layout: post
title:  "变了，但没完全变"
tags: log
author: Ko_teiru
---

* content
{:toc}

做了一点微小的工作







## 起因

前段时间对博客进行了一点修改，后面在学校机房访问时还是觉得速度不够理想。通过 `F12` 查看发现原来还有几个 js 文件一直加载不出来，看了看一个是 `不算子计数` 的，另外一个是 `MathJax` 的。  

## 开搞

前者因为自身问题更换了域名，之前我自己找到了相关代码然后修改了域名也算就解决了，没想到还有一条没删除干净，属实是走眼了。

后者的话看 js 路径域名是 `cloudflare` ，多少也懂了，换个可以直连的 cdn 就完事了。

不过要换的话还是得知道这玩意是干啥的啊，查了查百度发现这玩意是用来渲染数学公式的……然后想起来最初搭这个博客的时候写的一个测试页，当时就拿那玩意一直测试表达式，就是一直没有成功……最后直接就摆烂放弃了

然后再重头去了解了一下，发现 MathJax 的语法是  `\\[` 和 `\\]` 。而我写的是`$$`，而我尝试把 `$$` 改写成 `\\[` 后依旧无效。（后续查看代码时发现原作者以及加入了替换，所以 `$$` 是可以直接用的）

### 转折

后面索性去原博客主题作者 HYg 的 Github [仓库](https://github.com/Gaohaoyang/gaohaoyang.github.io)里检索了一下，发现一条 `mathjax: true`。

豁然开朗，原来东西其实都没啥问题，就是没用对。

> 要想让文章正确渲染数学公式的话，需要手动开启 `mathjax`。
>
> ```
> mathjax: ture
> ```
>
> 

而这篇文章正是 `jekyll` 默认创建的欢迎文档，也就是说我连说明书都没看就在瞎捣鼓……属于是吃一堑长一智了。

### 别的东西

另外博客详情界面的运作流程大致算是看懂了，感觉还挺方便的。

博文的格式代码在 `post.html` 里面，里面关于评论有一条 `\{\% include comments.html \%\}` ，意思差不多就是**把 `_includes` 目录下的 `comments.html` 加载进当前的 HTML**。

而原本的 `comments.html` 里面有几个 `\{\% if site.xxx \%\}` ，这玩意大致就是**如果 `_config.yml` 内的 xxx 为真的话，则加载直到 `\{\% endif \%\}` 之前的这些代码**。

搞懂了这些就方便多了，在 `_config.yml` 里添加一个名为 `Valine` 的值，设置为 `true` ，另外在下面加上 `appId`、`appKey`、`placeholder` 这些变量，这些都是 Valine 需要用到的值（~~placeholder不是必要）~~。

然后在 `comments.html` 里写一个判断，中间插入 Valine 的一些代码啥的，`appId` 啥的直接用 `\{\{site.appId\}\}` 来获取就行，非常方便。

现在博客结构看起来应该比我之前直接到处乱写标签要来得规范一点了，也算是填了一点坑吧，另外 `head.html` 里面也有 `mathjax` 和 `mermaid` 的判断语句，如果文章开启了对应的功能的话才会加载对应的代码块。另外要想成功渲染 `mermaid` 的话需要使用 `class="mermaid"` 的 `<div>` 标签，不然的话还是不能渲染。暂时还没有找到比较好的解决方法。

就这样吧，其他东西可以直接去 [Github](https://github.com/Small-tailqwq/blog) 看或者去[关于](https://blog.hayasa.org/about/)界面。

另外学校又因为疫情原因封校了，希望早点好起来吧。

