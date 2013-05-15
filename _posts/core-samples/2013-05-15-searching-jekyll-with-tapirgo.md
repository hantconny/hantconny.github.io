---
layout: post
title: 使用Tapir给Jekyll博客添加全文搜索
category : Tutorial
tags : [Tapirgo]
description : 记录了用Tapir为Jekyll博客添加搜索功能的步骤
---
{% include JB/setup %}

这篇文章的产生，其实首先要感谢[Dan 单弘昊](http://www.shanhh.com/)，请猛戳[这里](http://www.shanhh.com/blog/2012/11/16/tapir-search-for-jekyll/)查看他写的《使用Tapir实现jekyll的站内搜索功能》。

在这里，仅仅是做一个备忘，并且总结一些错误。

### 修改`atom.xml`文件 ###

{{% raw %}}
    
    ---
    layout: nil
    title : Atom Feed
    ---
    <?xml version="1.0" encoding="utf-8"?>
    <feed xmlns="http://www.w3.org/2005/Atom">
     
     <title>{{ site.title }}</title>
     <link href="{{ site.production_url }}/{{ site.atom_path }}" rel="self"/>
     <link href="{{ site.production_url }}"/>
     <updated>{{ site.time | date_to_xmlschema }}</updated>
     <id>{{ site.production_url }}</id>
     <author>
       <name>{{ site.author.name }}</name>
       <email>{{ site.author.email }}</email>
     </author>
    
     {% for post in site.posts %}
     <entry>
       <title>{{ post.title }}</title>
       <link href="{{ site.production_url }}{{ post.url }}"/>
       <updated>{{ post.date | date_to_xmlschema }}</updated>
       <id>{{ site.production_url }}{{ post.id }}</id>
       <content type="html">{{ post.content | xml_escape }}</content>
       <summary type="html">{{ post.description | xml_escape }}</summary>
     </entry>
     {% endfor %}
     
    </feed>

{{% endraw %}}

以上是修改后的atom.xml文件的全文。与Out of the box的`atom.xml`文件唯一的区别在于，`<entry>`节点的最后添加了一段`<summary type="html">{{ post.description | xml_escape }}</summary>`。添加这段内容的目的在于：搜索出的结果不会直接显示文章的全文，而是只显示文章的摘要。

这么做有一点要求，那就是`_post`目录下，每篇文章的YAML头部都必须包含有`description`信息；否则在本地启动Jekyll进行预览时会报错，那么可想而知，在GitHub上也同样会报错。

    ---
    layout: post
    title: 使用Tapir给Jekyll博客添加全文搜索
    category : Tutorial
    tags : [Tapirgo]
    description : 记录了用Tapir为Jekyll博客添加搜索功能的步骤
    ---

以上是本文的YAML头部，给出以作说明。

### 提交更改到GitHub ###
    git add .
    git commit -m "modify atom.xml"
    git push origin master

### 在Tapir注册atom.xml ###
登录Tapir，并填入atom.xml的位置和自己的邮箱，如下图
<a href="http://www.flickr.com/photos/hantconny/8739174883/" title="Flickr 上 Will.Cai 的 tapir"><img src="http://farm8.staticflickr.com/7282/8739174883_7fc833d856.jpg" width="500" height="408" alt="tapir" class="img-polaroid"></a>