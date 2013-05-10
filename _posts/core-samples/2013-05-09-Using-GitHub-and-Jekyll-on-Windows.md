---
layout: post
title: 在Windows上使用GitHub和Jekyll搭建博客
category : Tutorial
tags : [GitHub, Jekyll, DISQUS]
---

{% include JB/setup %}
###安装GitHub for Windows


可以直接从GitHub[下载](http://windows.github.com/)



###使用Pages


新建一个Repository，并将该Repository命名为username/username.github.io。这一点可以参考GitHub关于Pages的说明。需要注意的是：以前使用Pages，新建的Repository名称是username/username.github.com，而现在是username/username.github.io。

具体说明见[这里](https://help.github.com/articles/user-organization-and-project-pages#user--organization-pages)



###安装Jekyll


####Step One
Jekyll的Blog上给出了一个在Windows平台使用Jekyll的[解决方案](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html)
- Ruby  2.0.0-p0
- DevKit DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe（因为我的电脑是XP 32位的）
- 其他的都没有安装


####Step Two

这一步我觉得在Windows上没有那么繁琐。
- 先clone自己的username/username.github.io到本地（虽然里面没什么东西）
- 然后直接去github上[下载]Jekyll Bootstrap，然后解压到本地的username.github.io里面。
- 然后再Powershell（装好GitHub for Windows就有）里面操作
- git add .
- git commit -m "initial load"
- git push origin master


####Step Three

去浏览器输入username.github.io看下效果

###注册DISQUS

这一步相对简单，天朝骚年的英文水平对付这个注册肯定没有问题，所以简单点写。
先去DISQUS[注册](http://disqus.com/)，点Get this on your site，然后生成shortname。
- site url填username.github.io
- site name随意
- site shortname会根据site name生成，但是可以自己改，因为多半情况下是提示已经被占用
- 取消enable promoted discovery
- 然后改本地的username.github.io根目录下的_config.yml文件
找到
disqus :
      short_name : 改成你自己的shortname（就是DISQUS生成的site shortname）
