---
layout: post
title: Liquid日期格式
category : Tutorial
tags : [Liquid]
---

{% include JB/setup %}

刚跌跌烂冲（请忽视这个靖江方言）地把Page弄好，就注意到archive.html页面里的时间戳实在碍眼。不对齐啊！！！魂淡！！！强迫症怎么受得了啊！！！魂淡！！！

    1-Sep-2012
    10-May-2013
    ...

于是去Google了一下，找到了Liquid关于日期格式的[说明](http://liquid.rubyforge.org/classes/Liquid/StandardFilters.html#M000012)。

至于修改，不能直接修改`archive.html`页面，要去修改`_includes\JB\posts_collate`文件才可以。

找到

{% raw %}
`<span>{{ post.date | date_to_long_string }}</span>`
{% endraw %}
修改为

{% raw %}
`<span>{{ post.date | date:"%Y-%m-%d" }}</span>`
{% endraw %}

当然了，同样的方法也适用于修改`_includes\themes\twitter\`目录下的`post.html`模板。不过要注意的是，这个是<em>`page.date`</em>，而不是`post.date`。


另外，就在写这篇日志的时候还发现，如果要在文章内以用文本的形式写Liquid的话，可以用`{{ "{" }}% raw %}`和`{{ "{" }}% endraw %}`来转义Liquid代码，这是由Jekyll提供的一个plugin。

如果只是单纯使用Liquid的话，那么可以[这样](http://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)做。

目前的理解是：可以使用花括号加双引号的组合`{{"{{"}}"{{"}}"}}`来转义Liquid代码的前半个花括号，这样后半部分的`% raw %}`就会被当成文本处理掉。