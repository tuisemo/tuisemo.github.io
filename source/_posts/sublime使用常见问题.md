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

### 关于sublime中编写Vue组件时，文档的格式化工具

当我们开发vue.js的相关程序时，严格的eslint要求编码规则需完全符合才能正常运行vue工程，网上搜了一下，也没有发现合适的sublime插件专门用于格式化vue文件，后面找到一个方法：

***配置`HTML/CSS/JS Prettify`插件***
正常前端开发html/js都会安装HTML/CSS/JS Prettify插件，我们仅需在原有基础上，增加一些配置，即可支持vue文件格式化。

1. 打开sublime的tools菜单，选择HTML/CSS/JS Prettify插件，选择Plugin Options（网上给的方案是选择prettify preference，但我并未在该配置文件里找到可配置项）

2. 打开默认配置文件，或者你可以打开用户配置，找到"global_file_rules"这一项，你会发现有html/js/css/json等格式化规则（这些规则可在prettify preference里调整），每个规则会有对应"allowed_file_extensions"，表示规则支持的文件拓展类型。

3. 将"vue"添加进刚才的"allowed_file_extensions",这里我在html/js均添加了对vue文件的支持，大家可以自己决定。

至此，在vue文件中执行HTML/CSS/JS Prettify也可以完成对代码的格式化了。