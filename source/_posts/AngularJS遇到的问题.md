---
title: AngularJS遇到的问题
date: 2016-10-5 16:58:40
tags:
---
### transclude
---
    嵌入的意思,也就是说你是否需要将你的指令（内部）的元素嵌入到你的（模板）中去，默认为false。
    如果你需要的话，那么就需要将transclude设置为true。
    如果将这个值设置为true的话，就要配合angular的ng-transclude指令来进行使用，

---
### 代码实现
---
    1.html中的代码
    <!--  指令a-transclude 内部含有元素-->
    <breadcrumb>指令（内部）内容</breadcrumb>
---
    2.js中的代码
    myApp.directive('breadcrumb', ['$parse', function($parse) {
        return {
            templateUrl: 'tmpls/breadcrumb.html',
            transclude:true
        }
    }]);

---

    3.tmpls/breadcrumb.html模板中的代码
    <ol>
        <li>
            <a href="#" ng-transclude>模板1</a>
            <a href="#">模板2</a>
        </li>
    </ol>
    模板由两部分组成，一部分是含有ng-transclude指令的，一部分是不含有这个指令的
---
### ng-if 跟 ng-show/hide 的区别
---
    1. ng-if 在后面表达式为 true 的时候才创建这个 dom 节点。
    ng-show 是初始时就创建了，用 display:block 和 display:none 来控制显示和不显示。
---
    2. ng-if 会（隐式地）产生新作用域。
     ng-switch 、 ng-include 等会动态创建一块界面的也是如此。
     这样会导致，在 ng-if 中用基本变量绑定 ng-model ，
     并在外层 div 中把此 model 绑定给另一个显示区域，
     内层改变时，外层不会同步改变，因为此时已经是两个变量了。
---
    <p>{{name}}</p>
    <div ng-if="true">
        <input type="text" ng-model="name">
    </div>
    ng-show 不存在此问题，因为它不自带一级作用域。
---
    避免这类问题出现的办法是，始终将页面中的元素绑定到对象的属性（data.x）
    而不是直接绑定到基本变量（x）上。
---