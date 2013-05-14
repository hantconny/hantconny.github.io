---
layout: post
title: 在Windows上使用GitHub和Jekyll搭建博客
category : Tutorial
tags : [GitHub, Jekyll, DISQUS]
description : 使用GitHub的Pages和Jekyll在Windows平台上搭建博客
---
{% include JB/setup %}
### 安装GitHub for Windows ###
可以直接从GitHub[下载](http://windows.github.com/)，简单的双击安装即可。

### 使用Pages ###
在GitHub上新建一个Repository，并将该Repository命名为`username/username.github.io`。这一点可以参考GitHub关于Pages的[说明](https://help.github.com/articles/user-organization-and-project-pages#user--organization-pages)。

需要注意的是：以前使用Pages时，新建的Repository名称是`username/username.github.com`，而现在是`username/username.github.io`。

### 安装Jekyll ###

#### Step One ####
Jekyll的Blog上给出了一个在Windows平台使用Jekyll的[解决方案](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html)，这里只是简单记录一下版本信息。

- Ruby 1.9.2-p290(XP-32) / Ruby 2.0.0-p0(Win7-32)
- DevKit DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe(XP-32) / DevKit DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe(Win7-32)

假定Ruby安装在D盘根目录的Ruby192目录，DevKit解压在D盘根目录的DevKit目录，然后打开CMD。

    cd D:\DevKit
    D:\DevKit>ruby dk.rb init
    D:\DevKit>ruby dk.rb install
    D:\DevKit>gem install jekyll

#### Step Two ####
这一步我觉得在Windows上没有那么繁琐。

- 先clone自己的`username/username.github.io`到本地（虽然里面没什么东西）
- 然后直接去github上[下载](https://github.com/plusjade/jekyll-bootstrap)Jekyll Bootstrap，然后解压到本地的`username.github.io`文件夹里面。
- 然后在Powershell（装好GitHub for Windows就有）里面操作。

没什么复杂的，简单的一套git命令

    git add .
    git commit -m 'initial load'
    git push origin master

#### Step Three ####
最后去浏览器输入`username.github.io`看下效果。

### 注册DISQUS ###
这一步相对简单，天朝骚年的英文水平对付这个注册肯定没有问题，所以简单点写。

- site url填`username.github.io`。
- site name随意。
- site shortname会根据site name生成，但是可以自己改，因为多半情况下是提示已经被占用。
- 取消enable promoted discovery。
- 然后改本地的`username.github.io`根目录下的`_config.yml`文件，找到`disqus : <short_name>`，改成DISQUS生成的site shortname即可。

### 解决Jekyll中文问题 ###
找到`<RUBY_PATH>\lib\ruby\gems\<RUBY_VERSION>\gems\jekyll-<VERSION>\lib\jekyll\convertible.rb`文件，把里面的`self.content = File.read(File.join(base, name))`
换成
`self.content = File.read(File.join(base, name), :encoding => "utf-8")`即可。

需要注意的是这一行的位置根据Ruby版本的不同也不一样，大致在27行～29行的样子。
