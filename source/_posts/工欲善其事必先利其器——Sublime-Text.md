---
title: 工欲善其事必先利其器——Sublime Text
avatar: 'https://tuisemo.github.io/images/favicon.png'
author: tuisemo
authorAbout: https://tuisemo.github.io/about/
authorLink: https://tuisemo.github.io/about/
authorDesc: 一匹爱闯荡的狼
description: 每个人都有自己喜爱的那个她，陪你白天工作，陪你深夜加班，你们在一起的时光比情侣还漫长。有时候你们总和我说该选这个，该选那个，而我懵懵懂懂，独对她一见倾心。
date: 2017-07-21 11:47:50
category: 前端
tags: 工具
---


### 安装(Installtion)

下载应用程序可前往 [Sublime Text 官方网站](http://www.sublimetext.com/) (官网的下载速度较为感人，没耐心等的小伙伴可自行搜索资源)，目前最新版本为Sublime Text 3，虽然之前的许多插件都还停留在Sublime Text 2版本的支持上，个人建议升级到最新版本，毕竟后期插件也会迭代支持。
官网提供各系统各版本下载，但本人只用过Windows，所以就按照个人为例。

安装目录可根据自己喜好更改，我的习惯是将应用软件统一安装在D盘，记住安装地址，一会儿配置环境会用到。

![安装路径](https://tuisemo.github.io/images/20170721_001.png)

安装时，可勾选**Add to explorer context menu**，这样可将快捷方式加入右键菜单中，以便快速使用Sublime Text打开文件。

![快捷方式](https://tuisemo.github.io/images/20170721_002.png)

### 添加Sublime Text到环境变量

使用`win + r`运行`sysdm.cpl`打开系统属性--高级--环境变量，找到系统变量 Path 点击编辑，将刚才的安装路径

`D:\Program Files\Sublime Text 3`添加到环境变量中。

![添加环境变量](https://tuisemo.github.io/images/20170721_003.png)

(一直使用Sublime Text也没配置变量，感觉不配置这个也用的好好的，待以后发现需求吧~)

### 安装Package Control

Package Control就像是nodejs里的npm，方便用户安装、管理、卸载插件，安装插件前必定先安装Package Control。
具体安装方法在[Package Control 官网](https://packagecontrol.io/installation)也写得比较清楚，可以在线安装也可以下载到本地再配置关联，这里主要介绍一下在线安装的方法：
在Sublime Text中按 ctrl + ` 调出控制台。
将下面的代码粘贴到控制台中，回车，等待安装完成：

	import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

*安装过程是网络环境而定，如果失败多次，建议尝试直接下载。*

等待Package Control安装成功后，重启Sublime Text，使用`ctrl + shift + p`打开命令板，输入Package Control选择install package即可进入安装其他插件。

![Package Control安装成功](https://tuisemo.github.io/images/20170721_004.png)

完成到这一步，我们基本已经可以使用Sublime Text的基础功能了，但这个编辑工具的魅力在于多样的插件，插件的合理使用才使得这个工具显得如此强大，下一步我会介绍一些平时比较常用的插件。

### 插件安装

[Package Control 官网](https://packagecontrol.io)首页一进去，就是各个插件的实时更新列表，里面根据：最新、趋势、最流行等分类展示了各种插件，使用者可以根据各自需求安装。

#### Emmet

#### HTMLBeautify

#### Autoprefixer

这个插件主要用于补全CSS样式中的各类后缀，以前写样式的时候偶尔可能会用到，不过之后改用打包构建工具之后，就不再依靠这个了。

#### CSS3

#### CSScomb

#### FileDiffs

#### HTML-CSS-JS Prettify

#### HTML5

#### jQuery

#### LESS

#### ChineseLocalizations



