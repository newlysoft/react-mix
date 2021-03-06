# React Mix 

React Mix enables you to build all platform application base on React-Native. We create a mid-layer to support all CSS gramma, all JS dom event, all H5 framework on React-Native, and We have done these:
- support CSS className
- support CSS unit, px, pt, rem, em
- unify box model measurement on all platform by CSS rem
- support CSS two or more className combine or inherit, such as (.className1 .className2 .className3...)inhreit , (.className1.className2.className3)combine
- support CSS selector(part done, progress), have support #id, .className, tagName
- support DOM selector(part done, progress), have support $('#id'), $('.className'), $('TagName'), $('CSS3 selector')(by sizzle)
- support DOM event, like onTouchXXXX, onLoad, onClick...eg(done)
- support DOM Manipulation API like JQuery(part done, progress), have support part JQuery DOM API, all done until February
- support ReactNative Bundle into two part, not single release, one is like common part, include nessesary component, bigger one, another is business code, smaller.(done, read react-native.js.split.build.js)
- and more...

- add a big game demo 2048 , can both run  iOS/Android/H5 , more detail see sourcecode

Both support ReactNative Android and IOS, more UI component is still in dev!

We promise , we do not change any react-native core code, we only do auto translate tools!

## Have Support CSS Function
- className
- css unit, px , pt, em , rem
- #id
- .className
- TagName
- .className combine, like .a.b.c
- .className inherit like .a .b .c

## Have Support JQuery API
- $, you can use $('#id'), $('.className') to find a instance
- addClass
- removeClass
- hasClass
- css
- before
- append
- html
- offset
- attr
- parent, because we simulate a DOM tree
- on(=addEventListener)
- off(=removeEventListener)

## Have Support LocalStorage
- API like web browser localstorage, example see ./reactnative/example_localstorage.js

## Have Support Animation API
- requestAnimationFrame
- setInterval
- setTimeout

## Introduction

很高兴给大家介绍我们基于ReactNative框架实现的，目标是完全兼容现有的H5开发方式的新一代框架ReactMix, 相信大家已经使用ReactNative去开发各自的应用有一段时间了，在这段时间，因为ReactNative的API频繁变动，且文档不全，而对于已经习惯写js,css开发的前端工作者来说，ReactNative又是一种新的开发模式，现在ReactMix就是为了解决大家现在遇到的这些问题而来了。

我们通过中间层，来使得ReactNative，能支持现有的HTML5的js+ dom api + css的开发模式，完美的支持常用的
- css className
- 支持了css基本单位px, pt, rem
- 彻底解决了ios安卓尺寸样式不统一的问题，基于rem的度量方式，而且自适应不同的屏幕和分辨率，再也不用为未来更大屏的设备写兼容代码了
- 多个className的组合，或者className继承关系
- css选择器，支持id, className, tag选择器
- 支持Dom选择器，你可以使用#id, .className, TagName去定位和查找节点
- 支持常用的js dom event api，支持例如onclick
- 支持常用的dom操作api，比如insertBefore, html等等，你经常使用的api
- 支持ReactNative代码的分割打包，这样你可以把reactnative的框架代码保存在app本地，但是业务代码通过在线直连的方法更新，保证网络传输量最小

- 添加游戏2048的例子，现在启动默认进入2048,如果要修改其他例子，请修改index.ios.js的引用指向, 安卓修改index.android.js

而且我们是基于自动化脚本动态翻译的方式，使得现有的HTML+CSS+JS的代码可以无修改的直接转换成为reactnative代码，且一套不需要修改的代码，直接在iOS,andorid,winphone,H5,PC平台实现展现完全一致

## Getting Started

- 从github上下载工程，然后在根目录执行一遍npm install，再进入reactnative目录执行一遍npm install
- Mac的同学，可以直接执行install.sh,功能第一条类似，分别在更目录执行npm install和在./reactnative目录执行npm install
- 根目录的npm主要是用来执行css动态翻译，以及web用的js动态翻译的，./reactnaitve的npm主要用来执行reactnative
- 从根目录开始，reactnative目录是主要的业务开发代码，web目录是H5相关的代码
- 我们通过代号为lightningStorm的框架代码使得reactnative支持类似html标签，和模拟css，和模拟dom api，框架地址为./reactnative/common/LightningStorm.js
- 你可以打开安卓或者ios的reactnative的项目，来查看demo的例子，来了解我们的工作模式
- 我们模拟了HTML常用的多个节点，比如Div替代了reactnative的View，Span替换了reactnative的Text, Img替换了reactnative的Image，其中Div, Span, Img的用法和HTML语法的基本用法保持一致
- 主要文件说明如下: iOS入口文件还是index.ios.js,安卓同理index.android.js，但是里面只是壳子，import了框架的lightningStorm，大家都引用的index.js，这个是真正的业务入口
- H5的入口文件也是html的壳子，在./web/index.html，同理引用的是index.build.js，这个文件基于webpack.config.js打包同步自动生成的，打包文件有详细的入口是依赖和iOS同样的index.ios.js
- 项目中的三个重要的打包文件一个同步翻译css到react使用的css，是react.css.build.js，基于node实现的css同步翻译脚本
- webpack.config.js是用来实现H5平台的同步翻译，把reactnative的index.ios.js同步翻译成为H5平台的业务代码
- H5和app共用一套css代码，在./css目录里面，在文件中加载css的API暂定为includeCSS
- 未来会支持所有现有的CSS的功能，包括ReactNative不支持的display，甚至是伪类等等，还有media query都会计划支持到
- 目前拆出来的js文件，不包括完整的UI Component部分，UI部分计划另外开源，即时你不适用我们的ReactMix框架，你可以适用我们的UI在React或者ReactNative上面


## Getting Help

- 你可以提交issue，或者邮件我xueduanyang1985@163.com[mailto:xueduanyang1985@163.com]，来反馈遇到的问题和寻求帮助

## Documentation

第一篇原理揭秘文章在http://www.cnblogs.com/xueduanyang/p/5125781.html

系列学习文章连载中http://www.cnblogs.com/xueduanyang/p/5128690.html

更多的文档和例子正在完善中。。。

## react-native目录主要文件介绍

这里保持和官方的reactnative代码完全一致
- css目录是存放通过根目录的react.css.build.js脚本同步编译过来的reactjs的css文件
- 保留了官方原有的index.ios.js做入口
- common目录是框架文件，以及UI组件的文件
- index.js是页面入口文件，业务逻辑
- common/LightningStorm.js是框架文件
- common/rn目录是reactnative的UI组件文件，适配与native组件
- 对应的在根目录web目录也有一个叫做common/html对应的是适配与H5的UI组件文件,和common/rn目录的API保持一致，但是不同实现
- reactnative目录增加了一些demo的例子

## Demo

你可以发现，我们的代码基本类似现有的js+ html的开发模式
![](http://statics1.jiaru.club/react-native-example/demo3.jpg)

![](http://statics1.jiaru.club/react-native-example/demo4.jpg)

![](http://statics1.jiaru.club/react-native-example/demo1.jpg)

![](http://statics1.jiaru.club/react-native-example/demo2.jpg)



