---
title: JSON Server——30秒搭建一个本地的REST API服
avatar: 'https://tuisemo.github.io/images/favicon.png'
author:  慎独
authorAbout: 'https://tuisemo.github.io/about/'
authorLink: 'https://tuisemo.github.io/about/'
authorDesc: 一匹爱闯荡的狼
date: 2018-09-18 21:09:23
description: 快速搭建一个本地的REST API服务
category: 前端
tags: 工具
---

在平时的开发过程中，前端往往都需要与服务端进行数据对接，接口联调是耗时较长的一个部分，开发中时长会发生以下情况：

> 前端：“这个接口帮我加一条数据”
>
> 后端：“好，稍等一会儿”
>
> 后端：“加了，你试试”
>
> ...
>
> 前端：“再加一条，状态要不一样的”
>
> 后端：“emmm......你等等吧”
>
> ...

很显然，这样的开发方式很费时，而且这一切还要基于服务端已经完成接口开发，而往往实际工作情况都是前后端同步开发的，所以这时候前端的“本地服务”就很重要了！

今天要推荐的是一个~~自己就可以挠痒痒的神器“不求人”~~可快速搭建的本地模拟数据接口服务——**JSON-Server**

JSON Server是一个基于本地json文件模拟数据库的服务，支持CORS和JSONP跨域请求，支持GET/POST/ PUT/PATCH/DELETE的请求方式。



### 安装

1. 新建项目并初始化项目

   ` npm init ` 生成packsge.json文件

2. 安装json-server模块

   ` npm install json-server -S`

3. 配置package.json

   安装模块完毕后打开package.json文件，添加服务启动命令。例如：

   ```javascript
   {
     "name": "demo",
     "version": "1.0.0",
     "description": "",
     "main": "index.js",
     "scripts": {
       "json-server": "json-server --watch db.json"
     },
     "author": "tuisemo",
     "license": "ISC",
     "dependencies": {
       "json-server": "^0.14.0"
     }
   }
   ```

4. 创建db.json

   从上面的步骤可以看出来，项目里需要一个db.json文件，这个json文件就是之后我们将会使用到的“数据库”，于是我们创建一个db.json文件并在里面添加一些请求路由和响应的模拟数据。

   ```javascript
   {
       "getRequset":
       {
           "success": true,
           "msg": "",
           "data": [
           {
               "id": 1,
               "name": "张三"
           },
           {
               "id": 2,
               "name": "二娃"
           },
           {
               "id": 3,
               "name": "赵四"
           },
           {
               "id": 4,
               "name": "老王"
           }]
       }
   }
   ```

5. 启动

   准备工作完成，执行` npm run json-server ` 命令，运行服务可到以下结果

   ![img](http://tuisemo.github.io/images/20180918_001.png)

   可以看到，json-server服务已经开启运行在3000端口，我们可使用postman测试请求一下。

   ![img](http://tuisemo.github.io/images/20180918_002.png)

   至此，一个最简单的get请求模拟响应数据服务已经完成。json-server还支持其他请求类型，如post请求可以向db.json文件添加数据，相关的升级配置后续使用过程中会补充上来，感兴趣的朋友也可以直接访问该项目[github地址 : https://github.com/typicode/json-server](https://github.com/typicode/json-server)

   



