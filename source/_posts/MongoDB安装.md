---
title: MongoDB安装
avatar: 'https://tuisemo.github.io/images/favicon.png'
author: tuisemo
authorAbout: 'https://tuisemo.github.io/about/'
authorLink: 'https://tuisemo.github.io/about/'
authorDesc: 一匹爱闯荡的狼
date: 2017-09-27 20:35:57
description:
category:
tags:
---


## 下载MongoDB

废话不多说，上地址[点这里](https://www.mongodb.com/download-center?ct=false#community)。

## 安装MongoDB

双击打开安装包，一路next，知道选择安装方式时，建议可以选择“Custom”模式自定义,系统默认安装路径是`C:\Program Files\MongoDB\Server\3.4\`，这里个人习惯就更改为`D:\Program Files\MongoDB\Server\3.4\`了，继续next，直至完成。
*这里有另一个建议，就是直接在根目录下安装，即：`D\MongoDB\`，这个一会儿下面会提到*

## 创建数据存放目录

***MongoDB将数据目录存储在 db 目录下。但是这个数据目录不会主动创建，我们在安装完成后需要创建它。请注意，数据目录应该放在根目录下（(如： C:\ 或者 D:\ 等 )。***上面的说明摘抄于[菜鸟教程](http://www.runoob.com/mongodb/mongodb-window-install.html),在网上找了很久，一直不明白为什么强调要将数据存储目录创建在根目录下，或许是考虑要提高数据交互效率？较少路径索引所消耗的时间？

鉴于刚才我已经把MongoDB安装在`D:\Program Files\MongoDB\Server\3.4\`路径下，所以我创建的数据目录为`D:\Program Files\MongoDB\Server\3.4\data\db`，同时，我还创建了一个日志目录，并新建了个空文件MongoDB.log，用于存放软件运行中的日志文件`D:\Program Files\MongoDB\Server\3.4\data\log\MongoDB.log`

## 运行MongoDB

在安装目录的bin\目录（`D:\Program Files\MongoDB\Server\3.4\bin\`）中打开命令工具,运行以下代码：
`mongod --dbpath D:\Program Files\MongoDB\Server\3.4\data\db`
*dbpath后面的存储路径以你的实际安装路径为准*

命令行出现相应的信息，即正常运行。

## 将MongoDB作为Windows服务运行

|参数				    |描述																	
|---------------------- |:----------------------------------------------------------------------
|--bind_ip				|	绑定服务IP，若绑定127.0.0.1，则只能本机访问，不指定默认本地所有IP	
|--logpath				|	定MongoDB日志文件，注意是指定文件不是目录							
|--logappend			|	使用追加的方式写日志												
|--dbpath				|	指定数据库路径														
|--port					|	指定服务端口号，默认端口27017										
|--serviceName			|	指定服务名称														
|--serviceDisplayName	|	指定服务名称，有多个mongodb服务时执行。								
|--install				|	指定作为一个Windows服务安装。										

***在管理员下***执行以下命令：

`mongod.exe --logpath "D:\Program Files\MongoDB\Server\3.4\data\log\MongoDB.log" --logappend --dbpath "D:\Program Files\MongoDB\Server\3.4\data\db"  --serviceName "YourServiceName" --serviceDisplayName "YourServiceName" --install`

以上的*YourServiceName*是由你自定义的服务名称。

## 小技巧

在网上也有看到有人创建了一个mongodb.conf文件，将各个配置放在这个文件中，最后执行`mongod --config "Your mongodb.conf address"`和`mongod --config "Your mongodb.conf address" --serviceName "YourServiceName" --serviceDisplayName "YourServiceName" --install`

这种方法看着更容易理解，也方便配置，对于不擅长敲命令行的小伙伴们还是挺不错的选择，不过我自己还没试过。

## 再次以windows服务方式运行MongoDB

随便打开命令窗口：

`net start MongoDB`


*MongoDB即是你刚才设置的服务名称*