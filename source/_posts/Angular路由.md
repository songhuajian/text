---
title: Angular路由
date: 2016-10-11 12:48:22
tags:
---
    1. 什么是routing（路由）
        设置页面不同于控制页面，登录页面不同于账号信息页面。
        （一个应用很多功能不同的页面）
---
    2. 安装
        使用angular的路由功能需要安装routing模块......（引入angular-route.js就可以了）
---
    3. 定义
        angular.module('myApp', ['ngRoute'])
        .config(function($routeProvider) {});
---
    4. when()
        when()方法有两个参数，我们希望匹配的浏览器url和路由操作对象。
        一般main route经常使用“/”来表示，也可以定义URL参数，
        在controller里面就使用$routeParams获取url参数。
---
    5. templateUrl: 表示路由跳转的view模板
        controller: 控制器

        angular.module('myApp', ['ngRoute'])
        .config(function($routeProvider) {
        $routeProvider
            .when('/', {
              templateUrl: 'views/main.html',
              controller: 'MainCtrl'
            })
            .when('/day/:id', {
              templateUrl: 'views/day.html',
              controller: 'DayCtrl'
            })
---
    6. otherwise()
        otherwise()定义了当应用找不到指定路由的时候跳转的路由

        angular.module('myApp', ['ngRoute'])
        .config(function($routeProvider) {
         $routeProvider
            .when('/', {
              templateUrl: 'views/main.html',
              controller: 'MainCtrl'
            })
            .when('/day/:id', {
              templateUrl: 'views/day.html',
              controller: 'DayCtrl'
            })
            .otherwise({
              redirectTo: '/'
            });
        })
---
    7. 使用
        定义好了路由需要怎么使用呢?
        我们要告诉angular页面的哪一个部分是我们希望转换的，
        这需要使用到ng-view指令\
        <div class="header">My page</div>
        <div ng-view></div>
        <span class="footer">A footer</span>
        这样就只有<div ng-view></div>会被更新， header/footer都始终保持不变
---

