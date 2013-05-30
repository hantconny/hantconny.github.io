---
layout: post
title: 使用WampServer搭建WAMP环境
category : 备忘
tags : [Apache, PHP, WAMP, PHPWIND]
description : 记录使用WampServer整合安装包搭建WAMP环境, 并安装PHPWIND论坛
---
{% include JB/setup %}
### 版本及目录信息 ###
OS：`32位 Window7 Ultimate`

Microsoft Visual C++：`2010 SP1 Redistributable Package (x86)`

WampServer：`(32 bits & PHP 5.3) 2.2E`

PHPWind：`v9.0`

WampServer安装目录：`C:\wamp`

### WampServer部分 ###
#### WampServer下载 ####
下载[WampServer](http://www.wampserver.com/)

#### WampServer安装 ####

- 安装Microsoft Visual C++ 2010 SP1 Redistributable Package (x86)

- 安装火狐

- 安装WampServer
#### WampServer配置 ####
为了允许非本机访问，需要修改Apache和phpMyAdmin的两个配置文件。

- 修改Apache的`httpd.conf`文件

路径：`C:\wamp\bin\apache\apache2.2.22\conf\`

找到如下代码

    <Directory "c:/wamp/www/">
        ...省略若干注释
        #    onlineoffline tag - don't remove
        Order Deny,Allow
        Deny from all
        Allow from 127.0.0.1
    </Directory>

修改为
    
    <Directory "c:/wamp/www/">
        ...省略若干注释
        #    onlineoffline tag - don't remove
        #    Order Deny,Allow
        #    Deny from all
        #    Allow from 127.0.0.1
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>

- 修改phpMyAdmin的`phpmyadmin.conf`文件

路径：`C:\wamp\alias\`

找到

    <Directory "c:/wamp/apps/phpmyadmin3.5.1/">
        #    Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order Deny,Allow
        Deny from all
        Allow from 127.0.0.1
    </Directory>

修改为

    <Directory "c:/wamp/apps/phpmyadmin3.5.1/">
        #    Options Indexes FollowSymLinks MultiViews
        #    AllowOverride all
        #    Order Deny,Allow
        #	 Deny from all
        #	 Allow from 127.0.0.1
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>

另外，由于WampServer默认没有设置MySQL的密码，所以还需要把MySQL的密码设置起来。

- 设置MySQL密码

在火狐中输入`localhost/phpmyadmin`进入phpMyAdmin的界面，切换到SQL页面。

先查询mysql.user表中关于root的信息：

    select * from mysql.user where User = 'root';
然后利用password函数加密明文密码并更新root的密码：

    update mysql.user set Password = password('ok') where User = 'root';
最后使修改生效：

    flush privileges;
重启WampServer

- 设置phpMyAdmin的`config.inc.php`文件

路径：`C:\wamp\apps\phpmyadmin3.5.1\`

找到

    $cfg['Servers'][$i]['password'] = '';
修改为

    $cfg['Servers'][$i]['password'] = 'ok';
重启WampServer


### PHPWind部分 ###
#### PHPWind下载 ####
下载[PHPWind](http://www.phpwind.com/index.php?m=downloads&a=downloadsphpwind)

#### PHPWind安装 ####
解压压缩包，并把`upload`目录下的所有内容复制到`C:\wamp\www\`目录下

    PHPWind v9.0不要复制upload\.htaccess文件

访问`localhost/install.php`开始安装
