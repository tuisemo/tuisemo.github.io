---
title: Markdown入门
date: 2017-07-10 11:14:05
tags:
avatar: https://tuisemo.github.io/images/favicon.png
author: tuisemo
authorAbout: https://tuisemo.github.io/about/
authorLink: https://tuisemo.github.io/about/
authorDesc: 一匹爱闯荡的狼
---
# 标题1
## 标题2
### 标题3
#### 标题4
> this is blockquote.
> this is an empty line
> 
> ## 被包含的标题2
> 

有些词汇比较*重要*。
需要使用_明显_的标记符来突出显示
后面是一个**更重要**的标记
__更重要的__

以下是三种不同的列表写法：
* 001
* 002
* 003
+ 001
+ 002
+ 003
- 001
- 002
- 003
带层级关系的无序列表：
+ 001
	- 0001
	- 0002
+ 002
	- 0001
	- 0002
	- 0003
+ 003
+ 004

有序列表的写法：
1. 001
2. 002
3. 003

这是一个带[链接](http://www.baidu.com).
这是一个带title的[链接](http://www.baidu.com "this is a title")

与链接不同的是，图片写法需要在方括号前面增加！
例如![我是图片](https://unsplash.it/100/100/)

好了，现在开始我们的代码吧
`< this is a html template>`

创建代码区块：
	
	$.ajax({
	    url: 'https://api.douban.com/v2/movie/in_theaters',
	    type: 'GET',
	    dataType: 'jsonp',
	    data: {},
	    success: function(data) {
	        that.lists = [];
	        for (var i = 0; i < data.subjects.length; i++) {
	            that.lists.push({
	                id: data.subjects[i].id,
	                alt: data.subjects[i].alt,
	                imgsrc: data.subjects[i].images.medium,
	                title: data.subjects[i].title,
	                year: data.subjects[i].year
	            });
	        }
	    },
	    erroe: function() {}
	});
以上结束入门部分。