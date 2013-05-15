---
layout: post
title: Jekyll页面的HTML验证
category : Tutorial
tags : [Jekyll]
description : 记录Jekyll页面通过W3C验证需要注意的问题
---
{% include JB/setup %}
在使用Markdown写作时，使用如下语法是一件再平常不过的事情。

    # 一级标题 #
    ## 二级标题 ##
    ### 三级标题 ###
    ...

但是，如果我们在文章中使用了如下标题，就需要注意了，这样无法通过W3C的验证。

    #### 安装Jekyll ####
    #### 解决Jekyll中文编码 ####
    ...

其原因在于，当Markdown被解释后，生成了如下的HTML代码，很明显ID重复了。

{% raw %}

    <h3 id="jekyll">安装Jekyll</h3>
    <h3 id="jekyll">解决Jekyll中文编码</h3>

{% endraw %}

但是，以下情形Markdown却可以很好处理。

    ### 我是标题 ###
    ### 我也是标题 ###
    ...

这样的Markdown被解释后会生成类似如下的HTML代码：

    <h3 id="id1">我是标题</h3>
    <h3 id="id2">我也是标题</h3>

所以，在使用Markdown写作时，如果某个标题中出现了英文单词，就要尽量避免在多个标题中出现相同的单词。

这对于经常写科技文的码农还真不是一个好消息。