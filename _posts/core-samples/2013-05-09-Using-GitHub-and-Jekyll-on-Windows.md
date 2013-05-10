---
layout: post
title: 在Windows上使用GitHub和Jekyll搭建博客
category : 简易教程
tags : [GitHub Pages, Jekyll, DISQUS, Windows 7]
---

{% include JB/setup %}
##安装GitHub Windows

[下载](http://windows.github.com/)

##使用Pages
以前是username/username.github.com，现在是username/username.github.io。
具体说明参阅[这里](https://help.github.com/articles/user-organization-and-project-pages#user--organization-pages)

##安装Jekyll
###第一步 
看[这里](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html)
ruby我装的2.0.0
devkit的下载网站和ruby一样
python以下的暂时没装

###第二步
我觉得可以先clone自己的username/username.github.io到本地
然后直接去github上把jekyll下下来解压到本地的username.github.io里面
然后
git add .
git commit -m "initial commit"
git push origin master

###第3步
去浏览器输入username.github.io看下效果

##注册DISQUS
[注册](http://disqus.com/)
点Get This On your site
生成shortname
site url天username.github.io
site name随意
site shortname会根据site name生成，但是可以自己该，因为多半会已经被占用
取消enable promoted discovery
点右边的continue
然后不记得了，好像是选universal code

然后改你的_config.yml文件
找到
disqus :
      short_name : 改成你自己的shortname == site shortname