---
layout: post
category : hello world
tagline: "所谓的tag line"
tags : [hello, world, test, ignore-me]
---
{% include JB/setup %}

上面的时间应该是根据文件名生成的

#测试一级标题
# 测试一级标题（#号后有空格）

##测试一级标题
## 测试一级标题（#号后有空格）

###测试一级标题
### 测试一级标题（#号后有空格）

测试超链接[饭否](http://www.fanfou.com).

**测试Strong**

测试列表
- 列表项1（带空格）
- 列表项2（带空格）
- 列表项3（带空格）
-列表项4（无空格）
-列表项5（无空格）
-列表项6（无空格）

测试代码
Jekyll expects your website directory to be laid out like so:

    .
    |-- src
    |--_includes(去了空格)
    |-- _layouts
    |   |-- default.html
    |   |-- post.html
    |-- _posts
    |   |-- 2011-10-25-open-source-is-good.markdown
    |   |-- 2011-04-26-hello-world.markdown
    |-- _site
    |-- index.html
    |-- assets
        |-- css(不能用tab)
            |-- style.css
        |-- javascripts


这个不清楚是什么`@YEAR-MONTH-DATE-title.MARKUP@`.

## Next Steps

Please take a look at [{{ site.categories.api.first.title }}]({{ BASE_PATH }}{{ site.categories.api.first.url }}) 
or jump right into [Usage]({{ BASE_PATH }}{{ site.categories.usage.first.url }}) if you'd like.
category和tag出现了，定义在该文件中
category是hello world
tags是hello, world, test, ignore-me