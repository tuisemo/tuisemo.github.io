---
title: gulp常用插件集合
avatar: 'https://tuisemo.github.io/images/favicon.png'
author: tuisemo
authorAbout: 'https://tuisemo.github.io/about/'
authorLink: 'https://tuisemo.github.io/about/'
authorDesc: 一匹爱闯荡的狼
date: 2017-09-12 08:56:51
description:
category: 前端
tags: gulp
---

## gulp-jshint js语法检测

	var jshint = require('gulp-jshint');

## gulp-jshint html语法检测

	var htmlhint = require('gulp-htmlhint');

## gulp-less less编译

	var less = require('gulp-less');

## gulp-rename 文件重命名

	var rename = require('gulp-rename');

## gulp-file-include 文件、代码段插入

	var fileinclude = require('gulp-file-include');

	gulp.task('fileinclude', function() {
	    gulp.src('./src/*.html')
	        .pipe(fileinclude({
	            prefix: '<!--IEhack@',//标签语法前缀
	            suffix: '-->',//标签语法后缀，最终在文档完整标签为：<!--IEhack@include('./include/IEhack.html')-->
	            basepath: '@file',//插入文件地址
	            indent: true
	        }))
	        .pipe(gulp.dest('dist'));
	});

## gulp-inject html中插入js/css

	var inject = require('gulp-inject'); 

	gulp.task('inject', function() {
	    gulp.src('./src/*.html')
	        .pipe(inject(gulp.src(['./src/js/lib/require.js'], { reda: false }), { starttag: '<!-- inject:require:{{ext}} -->', relative: true }))//最终在文档展示:<!-- inject:base:css -->
	        .pipe(gulp.dest('dist'));
	});

## gulp-clean-css css压缩

    var cssmin = require('gulp-clean-css');

	gulp.task('cssmin', function() {
	    return gulp.src('./src/css/*css')
	        .pipe(cssmin({
	            compatibility: 'ie8' //兼容至ie8模式，默认compatibility: '*' Internet Explorer 10+兼容模式
	            debug: true //启用日志打出到控制台
	        }))
	        .pipe(gulp.dest('./public/css'));
	})


更多详细配置可查看[gulp-clean-css](https://github.com/jakubpawlowicz/clean-css#how-to-use-clean-css-api)

## gulp-base64 零碎图片转base64格式图片

    var base64 = require('gulp-base64');
    
    gulp.task('base64', function() {
        return gulp.src('./src/css/*css')
            .pipe(base64({
                baseDir: 'public', //当样式表中有绝对路径的图片，则baseDir将被指定为该路径的根目录（相对于gulpfile文件）
                extensions: ['svg', 'png', /\.jpg#datauri$/i], //希望转化的图片格式，支持扩展名或正则匹配
                exclude: [/\.server\.(com|net)\/dynamic\//, '--live.jpg'], //与extensions不同，此设置项将跳过与此匹配的图片，不转化
                maxImageSize: 8 * 1024, // 设置转化图片的阈值，计量单位:bytes 
                debug: true //启用日志打出到控制台
            }))
            .pipe(gulp.dest('./public/css'));
    })

## gulp-imagemin 图片压缩

    var imagemin = require('gulp-imagemin');

    gulp.task('imagemin', function() {
        return gulp.src('./src/images/*')
            .pipe(imagemin())
            .pipe(gulp.dest('./public/images'));
    })

## gulp-changed 只操作有过修改的文件

    var changed  = require('gulp-changed');

    gulp.task('imagemin ', function() {
        return gulp.src('./src/images/*')
            .pipe(changed ('./public/images'))//与输入目录文件对比，若无差异则不再处理
            .pipe(imagemin())//此处使用图片压缩工作流做例子
            .pipe(gulp.dest('./public/images'));
    })

