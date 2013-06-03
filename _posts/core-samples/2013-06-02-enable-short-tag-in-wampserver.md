---
layout: post
title: 在WampServer中开启短标签
category : 备忘
tags : [Bootstrap, PHP, WAMP]
description : 记录如何在WampServer中开启PHP的短标签
---
{% include JB/setup %}

还是在给公司项目做选型，碰到一个用[Bootstrap](http://twitter.github.io/bootstrap/)作为前端框架的[StartBBS](http://www.startbbs.com/)，正好前段时间得空看过，所以王八看绿豆，直接对上眼了。

不过安装完以后就报错了，论坛里也有相同错误的求助帖，但是都没有提到解决方案，只露出一点关于PHP短标签的线索，所以按图索骥Google了一下，找到了[解决方案](http://blog.gishome.org/post-9.html)。

### 版本及目录信息 ###
OS：`32位 Window7 Ultimate`

WampServer：`(32 bits & PHP 5.3) 2.2E`

WampServer安装目录：`C:\wamp`

### 修改Apache目录下的`php.ini`文件 ###
路径：`C:\wamp\bin\apache\apache2.2.22\bin\php.ini`

找到

    short_open_tag = Off

修改成

    short_open_tag = On

### 修改PHP目录下的`php.ini`文件 ###
路径：`C:\wamp\bin\php\php5.3.13\php.ini`

找到

    short_open_tag = Off

修改成

    short_open_tag = On

### 修改站点目录下的`config.php`文件 ###
例如我把StartBBS安装在`C:\wamp\www3\`下，那么该`config.php`文件的路径就是`C:\wamp\www3\app\config\config.php`

找到

    $config['rewrite_short_tags']

确保该配置的值是

    $config['rewrite_short_tags'] = true;

重启WampServer即可。