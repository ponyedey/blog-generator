---
title: html续笔记
date: 2017-10-18 23:02:48
tags:
---
# 此文章摘自写代码啦的HTML课程
- 个人域名怎么买就不说了，自己搜索引擎吧
- 寻找一个合适的简历模板，详见方方选择的这款
## html标签
- 建议的学习方法：标签+mdn+google，事半功倍！  
- 这一课没有特别详细的内容，主要都是自己学习标签为主
------------------------------我是分割线---------------------------------
## 标签的一些笔记，目前还在上班，回去继续更新
1. div和span标签，实在很难理解其他标签或者记不住的话，就记这两个，一招鲜吃遍天。
2. a标签中，target="_top"或"_parent"或"_self"或"_blank"分别是在最高级页面或iframe、父页面或iframe、当前页面、新开页面打开网页。
3. iframe嵌套标签，理解是在当前页面嵌入一个页面。目前用的较少，相关笔记回家再补。
4. form标签，既可以实现GET也可以实现POST。action标签决定请求路径，method标签决定请求行为。a标签是发起GET请求。都是跳转页面。
5. 当存在button元素时，若没有定义input type，则button会自动升级为提交按钮。
6. JavaScript伪协议是为了能够在html中执行javascript代码，或者是可以在点击a标签时，页面没有跳转。
7. 关于table标签需要回去再复习一下，这里做个标记
---------------------------分割线又来了-----------------------------------
## 补充的一些知识
1. iframe，例如js bin，你写的代码都是放在iframe标签中展示。不信可以去js.jirengu.com去检查
- 用iframe嵌套QQ的官网`<iframe src="http://qq.com"frameborder="0"></iframe>`
- iframe标签中，当src="#"，意味当前页面为空
- a标签中的target如果指向iframe标签的name，即在iframe中打开a标签的网址
- iframe标签中，src也可以写相对路径。（HTML续第四个视频07:20）

2. a标签。blank,self,parent,top都已经说过了（HTML续第四个视频10:12）
- a标签也可以进行下载，不进行展示页面，单纯的去下载
- 如果`content-type: applicatiom/octet-stream`时，浏览器接收到请求后就会下载，而不是展现。否则就使用a标签的下载吧。
- a标签的href可以写些什么？
  不可以写成`<a href="qq.com">QQ</a>`会把qq.com当成文件
  可以写成`<a href="http://qq.com">QQ</a>`
  可以写成`<a href="//qq.com">QQ</a>`，这个是无协议绝对地址。会根据文件当前协议，就用什么协议。一般还是指定http
  建议运行http-server -c-1，清缓存
  也可以写相对路径。比如当你href="xxx.html"，而你现在是处于127.0.0.1:8080/index.html，访问a标签之后，就会跳转为127.0.0.1:8080/xxxhtml而不是127.0.0.1:8080/index.html/xxx.html
  如果href后写的是#xxx，为锚点作用，是页面内的跳转，不会发起请求  
  如果href后写的是?name=xxx，则会发起get 请求。`GET /index.html?name=xxx HTTP/1.1
- 伪协议
  `<a href="javascript: alert(1);">QQ</a>`此时点击QQ，就会显示JS代码。这个伪协议不存在URL。
  `<a href="javascript: ;">QQ</a>`是为了点击a标签后，页面什么也不做。
  这时有问到：用#锚点不就行了吗？  --不行的，锚点还是会移动页面到锚点位置，如页面最上方
  a标签没有href就成了span了。如果`href=""`，空的href会使页面刷新，跳转到自身。
  `<a href="javascript: ">QQ</a>`如果这样写，在写url时写了javascript:xxxx，就会执行js
3. form标签
- form标签可以GET也可以POST，a标签只可以GET
- form标签里面如果没有提交按钮，就无法提交
- action元素是目标地址，类似href。method元素管理行为，默认是GET，可以改为POST
- 可以用来进行登录提交账户名和密码，html中只有form标签让我们上传内容。（复习到最后一个视频06:06，太困了先睡了zzz）
