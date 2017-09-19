---
title: sublime使用常见问题
avatar: 'https://tuisemo.github.io/images/favicon.png'
author: tuisemo
authorAbout: 'https://tuisemo.github.io/about/'
authorLink: 'https://tuisemo.github.io/about/'
authorDesc: 一匹爱闯荡的狼
date: 2017-09-19 15:51:19
description:
category: 前端
tags: 工具
---

### Package install 包管理安装失败

sublime使用中，时常因为网络问题，导致Package install安装失败，程序提示：there are no packages for installation
导致插件无法正常获取安装。解决方案如下：

1. 打开命令提示符，输入`ping sublime.wbond.net`回车，此处ping通[sublime.wbond.net](https://packagecontrol.io/)获取网站ip地址，（访问 :sublime.wbond.net后你会发现，其实就映射到了: packagecontrol.io）
上述操作后，我得到的地址是：[50.116.33.29]

2. 修改hosts指向。在电脑中找到hosts文件，路径`C:\Windows\System32\drivers\etc\` 使用编辑器打开，在最后新增一行：		

		50.116.33.29  sublime.wbond.net
	
3. 保存hosts文件，重启sublime即可。