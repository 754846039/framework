# angular
## 什么是angular
AngularJS 是一个 JavaScript 框架，是一种MVVM框架。它可通过 `<script>` 标签添加到 HTML 页面。<br>
AngularJS 通过 指令 扩展了 HTML，且通过 表达式 绑定数据到 HTML。
## 发展历程
谷歌推出自己的前端框架，将对DOM的直接操作释放，通过directive来实现复杂的DOM修改
其整体作为一个MVVM框架显得过重，不适用于对性能要求较高的站点，比如移动的web站，UI组件封装相对复杂，不利于重用

## MVVM
MVVM是Model-View-ViewModel的缩写。

MVVM的设计思想：关注Model的变化，让MVVM框架去自动更新DOM的状态，从而把开发者从操作DOM的繁琐步骤中解脱出来！

MVVM最早由微软提出来，它借鉴了桌面应用程序的MVC思想，在前端页面中，把Model用纯JavaScript对象表示，View负责显示，两者做到了最大限度的分离。

把Model和View关联起来的就是ViewModel。ViewModel负责把Model的数据同步到View显示出来，还负责把View的修改同步回Model。

ViewModel如何编写？需要用JavaScript编写一个通用的ViewModel，这样，就可以复用整个MVVM模型了。

双向数据绑定：填写表单就是一个最直接的例子。当用户填写表单时，View的状态就被更新了，如果此时MVVM框架可以自动更新Model的状态，那就相当于我们把Model和View做了双向绑定

## MVC
Model-View-Controller，中文名“模型-视图-控制器”。实现了后端数据、模板页面和控制器的分离。

Controller负责业务逻辑，比如检查用户名是否存在，取出用户信息等等；

View负责显示逻辑，通过简单地替换一些变量，View最终输出的就是用户看到的HTML。

Model是用来传给View的，这样View在替换变量的时候，就可以从Model中取出相应的数据

## 特点
- 以模块化的方式来开发自己的应用
  - 根据功能不同划分不同的模块方便开发，重复调用，提高了代码的可复用性，有利于多人协作开发和后期维护。
- 双向数据绑定
	- HTML中呈现的view与AngularJS中的数据是一致的。 修改其一, 则对应的另一端也会相应地发生变化
- 依赖注入
  - 依赖于某个模块就注入这个模块，使得所有模块的引入顺序不再重要

## 作用
- AngularJS 使得开发现代的单一页面应用程序（SPAs：Single Page Applications）变得更加容易。
- AngularJS 把应用程序数据绑定到 HTML 元素。
- AngularJS 可以克隆、重复、隐藏和显示 HTML 元素。
- AngularJS 可以在 HTML 元素"背后"添加代码。
- AngularJS 支持输入验证。

## 安装引用
- 在 http://www.bootcdn.cn/ 中搜索 angular
- 下载 1.6.1/angular.js
- 打开链接
- ctrl+s保存
- 在html页面中引入anjular.js
>解析angular.js会把页面重新解析一次
