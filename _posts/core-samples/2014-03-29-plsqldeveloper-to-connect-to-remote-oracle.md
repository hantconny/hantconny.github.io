---
layout: post
title: PLSQL Developer安装及配置
category : 备忘
tags : [Oracle, PLSQL Developer]
description : 记录了如何使用PLSQL Developer连接到局域网内的Oracle
---
{% include JB/setup %}
### 安装PLSQL Developer ###
可以直接从allroundautomations的网站[下载PLSQL Developer](http://www.allroundautomations.com/plsqldev.html)，双击安装即可。

假定PLSQL Developer的安装目录为`C:\Program Files (x86)\PLSQL Developer`，本文其余内容均以`$PLSQL_HOME`来指代该路径。

<img src="http://hantconny.github.io/assets/images/2014-03-29/plsql-alert-info.jpg" alt="PLSQL Developer提示信息">

> 值得注意的是，在安装PLSQL Developer时，如果路径中带有括号，会提示你确认PLSQL Developer将来连接的Oracle版本必须是11g及以后版本。

### 解压Oracle Instant Client ###
从Oracle的网站[下载Instant Client](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)，并解压到本地目录。为了方便携带PLSQL Developer，可以直接解压到`$PLSQL_HOME\instantclient_11_2`，本文其余内容均以`$INSTANTCLIENT_HOME`指代该路径。

> 值得注意的是，即使是在64位的操作系统，也应该选择32位的Instant Client。

在`$INSTANTCLIENT_HOME`下建立`\NETWORK\ADMIN`的目录结构，然后将Oracle的`tnsnames.ora`文件拷贝进来。

<img src="http://hantconny.github.io/assets/images/2014-03-29/instant-client-structure.jpg" alt="Instant Client结构">

### 配置PLSQL Developer ###
首次启动PLSQL Developer时，因为没有进行配置，所以没法登录。

<img src="http://hantconny.github.io/assets/images/2014-03-29/plsql-login.jpg" alt="PLSQL Developer登录窗口">

点击Cancel进入PLSQL Developer后，依次点击*Tools > Preferences*，设置好*Oracle Home*和*OCI library*，并且选中*Check connection*，确认后退出PLSQL Developer。

<img src="http://hantconny.github.io/assets/images/2014-03-29/plsql-setting.jpg" alt="PLSQL Developer设置页面">

重启PLSQL Developer，会发现在Database中已经可以看到tnsnames.ora中的信息了。

<img src="http://hantconny.github.io/assets/images/2014-03-29/configured-login.jpg" alt="PLSQL Developer配置后的登录窗口">

填入Username和Password，应该能正常登录到远程的Oracle。

### 配置Windows防火墙 ###
有的时候，局域网内的机器A通过PLSQL Developer无法连接到机器B的Oracle，原因可能有很多，这里只说明如何配置机器B的防火墙入站规则。

打开防火墙的高级设置，选择*入站规则*，等待视图刷新后，点击右侧的*新建规则*

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule.jpg" alt="入站规则">

选择端口，点击下一步。

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule-1.jpg" alt="新建入站规则 Step 1">

如果使用Oracle的默认端口，那么输入1521，如果自定义了Oracle的端口，输入自定义端口。

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule-2.jpg" alt="新建入站规则 Step 2">

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule-3.jpg" alt="新建入站规则 Step 3">

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule-4.jpg" alt="新建入站规则 Step 4">

<img src="http://hantconny.github.io/assets/images/2014-03-29/inbound-rule-5.jpg" alt="新建入站规则 Step 5">

配置完成后，可以在机器A上使用`telnet IP port`进行测试

#### 其他PLSQL Developer配置 ####

- 自动大写

<img src="http://hantconny.github.io/assets/images/2014-03-29/uppercase.jpg" alt="自动大写">

- 单行执行

<img src="http://hantconny.github.io/assets/images/2014-03-29/single-row.jpg" alt="单行执行">