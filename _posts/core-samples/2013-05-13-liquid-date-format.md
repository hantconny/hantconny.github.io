---
layout: post
title: Liquid日期格式
category : Tutorial
tags : [Liquid]
description : 调整了Jekyll里面的Liquid时间戳，并且小小探究了如何在转义Liquid代码
---
{% include JB/setup %}
不是太喜欢archive.html页面里的时间戳，所以修改一下。

    01-Sep-2012
    31-May-2013
    ...

修改为

    2012-09-01
    2013-05-31
	...

Google一下，找到Liquid关于日期格式的[说明](http://liquid.rubyforge.org/classes/Liquid/StandardFilters.html#M000012)。至于修改，不能直接修改`archive.html`页面，要修改`_includes\JB\posts_collate`文件才可以。

找到

{% raw %}
`<span>{{ post.date | date_to_long_string }}</span>`
{% endraw %}

修改为

{% raw %}
`<span>{{ post.date | date:"%Y-%m-%d" }}</span>`
{% endraw %}

同样适用于修改`_includes\themes\twitter\`目录下的`post.html`模板，但是，`post.html`文件中是`page.date`，而不是`post.date`。

#### PS: ####

在写这篇日志的时候还发现，如果要在文章中以文本的形式写Liquid代码的话，可以用`{{ "{" }}% raw %}`和`{{ "{" }}% endraw %}`将Liquid代码包裹起来进行转义，这是一个由Jekyll提供的plugin，很便捷。

如果不用Jekyll提供的插件，也可以参考[这里](http://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)的做法。目前我对这个处理方法的理解是：

可以使用花括号加双引号的组合`{{"{{"}}"{{"}}"}}`来转义Liquid代码的前半个花括号，这样后半部分的`% raw %}`就会被当成文本处理掉。