---
title: 使用Hexo和GitHub搭建个人博客
avatar: 'https://tuisemo.github.io/images/favicon.png'
author: tuisemo
authorAbout: 'https://tuisemo.github.io/about/'
authorLink: 'https://tuisemo.github.io/about/'
authorDesc: 一匹爱闯荡的狼
date: 2017-09-11 21:32:57
description:
category:
tags:
---

## 基础配置

### 创建对应仓库

在自己的GitHub账号下创建一个新的仓库，命名为*username*.github.io（username是你的github账号名)

在这里，要知道，GitHub Pages有两种类型：User/Organization Pages 和 Project Pages，而我所使用的是User Pages。

简单来说，User Pages 与 Project Pages的区别是：

+ User Pages 是用来展示用户的，而 Project Pages 是用来展示项目的。
+ 用于存放 User Pages 的仓库必须使用username.github.io的命名规则，而 Project Pages 则没有特殊的要求。
+ User Pages 将使用仓库的 master 分支，而 Project Pages 将使用 gh-pages 分支。
+ User Pages 通过 http(s)://username.github.io 进行访问，而 Projects Pages通过 http(s)://username.github.io/projectname 进行访问。

### 工具安装

### Git安装

如果你已安装了Git，可直接跳过，如果没有，那么建议自学安装，这里跳过。

#### Git配置

当安装完Git，建议配置用户信息（用户名/邮箱地址）。此后每次提交操作，均会携带这部分信息。
`
	git config --global user.name "username"
	git config --global user.email "username@example.com"
`

### 关联GitHub

为了能够在本地使用git管理github上的项目，需要进行一些配置，这里介绍SSH的方法。

#### 检查电脑是否已有SSH KEYS
`ls -al ~/.ssh`

#### 若无SSH KEYS，则生成新的SSH KEYS
`ssh-keygen -t rsa -C "your_email@example.com"`
默认回车，会生成两个文件：id_rsa/id_rsa.pub（前者为私钥，后者为公钥）。

#### 向SSH-AGENT添加KEY
确保ssh-agent可运行
`ssh-agent -s`
添加SSH KEY
`ssh-add ~/.ssh/id_rsa`

#### 在GitHub添加SSH KEY
打开生成的SSH KEY，用编辑器打开新生成的公钥id_rsa.pub（文件默认路劲C:/Users/Administrator/.ssh/id_rsa.pub），复制里面的字符串，添加到GitHub。

测试是否关联成功
`ssh -T git@github.com`

### Hexo安装

Hexo安装前请确保你的电脑已安装了Node.js/Git
`npm install hexo-cli -g`
或
`cnpm i hexo-cli -g` (建议可使用淘宝镜像)

### Hexo站点构建

选择一个空文件夹
`hexo init`
上一步操作需要一点时间，请耐心，完成后会自动在文件夹内建立网站所需要的所有文件。

接下来就是安装依赖了
`npm install`
或
`cnpm i` (减少等待时间)

此时，网站基础demo已经构建完成，我们可通过以下两个指令运行该demo
`hexo generate`或简写指令`hexo g` 生成站点
`hexo server` 运行服务，可在localhost:4000 查看站点。
此时的站点仅是本地查看的站点，之后需部署至GitHub。
