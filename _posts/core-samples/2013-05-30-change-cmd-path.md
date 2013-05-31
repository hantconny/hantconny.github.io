---
layout: post
title: 更改CMD的起始路径
category : 备忘
tags : [CMD]
description : 记录如何更改Windows命令行的起始位置
---
{% include JB/setup %}
打开注册表，展开「HKEY_CURRENT_USER\Software\Microsoft\CommandProcessor」，新建一个名为AutoRun的字符串值，设置该字符串值为「CD /D C:\」，这样下次使用CMD的时候，默认路径就是C盘根目录了。