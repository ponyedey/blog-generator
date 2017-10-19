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
2. `a`标签中，`target="_top"`或`"_parent"`或`"_self"`或`"_blank"`分别是在最高级页面或`iframe`、父页面或`iframe`、当前页面、新开页面打开网页。
3. `iframe`嵌套标签，理解是在当前页面嵌入一个页面。目前用的较少，相关笔记回家再补。
4. `form`标签，既可以实现GET也可以实现POST。`action`标签决定请求路径，`method`标签决定请求行为。a标签是发起GET请求。都是跳转页面。
5. 当存在`button`元素时，若没有定义`input type`，则`button`会自动升级为提交按钮。
6. `JavaScript伪协议`是为了能够在html中执行`javascript代码`，或者是可以在点击`a`标签时，页面没有跳转。
7. 关于`table`标签需要回去再复习一下，这里做个标记
---------------------------分割线又来了-----------------------------------
## 补充的一些知识
1. `iframe`，例如js bin，你写的代码都是放在`iframe`标签中展示。不信可以去js.jirengu.com去检查
- 用`iframe`嵌套QQ的官网`<iframe src="http://qq.com"frameborder="0"></iframe>`
- `iframe`标签中，当`src="#"`，意味当前页面为空
- `a`标签中的`target`如果指向`iframe`标签的`name`，即在`iframe`中打开`a`标签的网址
- `iframe`标签中，`src`也可以写相对路径。（HTML续第四个视频07:20）

2. `a`标签。blank,self,parent,top都已经说过了（HTML续第四个视频10:12）
- `a`标签也可以进行下载，不进行展示页面，单纯的去下载
- 如果`content-type: applicatiom/octet-stream`时，浏览器接收到请求后就会下载，而不是展现。否则就使用`a`标签的下载吧。
- `a`标签的`href`可以写些什么？
  1. 不可以写成`<a href="qq.com">QQ</a>`会把qq.com当成文件
  2. 可以写成`<a href="http://qq.com">QQ</a>`
  3. 可以写成`<a href="//qq.com">QQ</a>`，这个是无协议绝对地址。会根据文件当前协议，就用什么协议。一般还是指定http
  4. 建议运行`http-server -c-1`，清缓存
  5. 也可以写相对路径。比如当你`href="xxx.html"`，而你现在是处于127.0.0.1:8080/index.html，访问a标签之后，就会跳转为127.0.0.1:8080/xxxhtml而不是127.0.0.1:8080/index.html/xxx.html
  6. 如果`href`后写的是`#xxx`，为锚点作用，是页面内的跳转，不会发起请求  
  7. 如果`href`后写的是`?name=xxx`，则会发起get 请求。`GET /index.html?name=xxx HTTP/1.1
- 伪协议
  1. `<a href="javascript: alert(1);">QQ</a>`此时点击QQ，就会显示JS代码。这个伪协议不存在URL。
  2. `<a href="javascript: ;">QQ</a>`是为了点击`a`标签后，页面什么也不做。
  3. 这时有问到：用#锚点不就行了吗？  --不行的，锚点还是会移动页面到锚点位置，如页面最上方
  4. a标签没有href就成了span了。如果`href=""`，空的href会使页面刷新，跳转到自身。
  5. `<a href="javascript: ">QQ</a>`如果这样写，在写url时写了javascript:xxxx，就会执行js
3. `form`标签
- `form`标签可以GET也可以POST，`a`标签只可以GET
- `form`标签里面如果没有提交按钮，就无法提交
- `action`元素是目标地址，类似`href`。`method`元素管理行为，默认是GET，可以改为POST
- 可以用来进行登录提交账户名和密码，html中只有`form`标签让我们上传内容。（复习到最后一个视频06:06，太困了先睡了zzz）
- 如果不是https，只要有人监听就可以知道你上传的内容
- 上传时，上传的数据会变相应的编码语言，多为Utf8
- 如果`form`标签中，没有提交按钮，就无法提交了
- `input`部分的`name`会带入到提交的第四部分，并且其中的`name`会带入到上传的key
- file协议不支持post
- GET用`a`标签，POST用form标签
- `method`仅可以写GET和POST，不支持其他
- 如果`method`写的GET，那么我们所写的参数不会放在请求的第四部分，而是作为查询参数放在请求的第一部分
- `form`标签想实现有查询参数时，应把查询参数写在`form action`中
- 无法让GET请求有第四部分
- `form`标签也有`target`，用法和`a`标签一样
- `name`写什么，显示的提交就是什么。如`name="xxx"`提交时检查就可以看到提交的信息xxx=
- 如果想在提交的文本前显示文本类别，应在`input type`前写上，如`用户名<input type="text" name="xxx">`

4. `input`标签
- 难点在于type
- `button`与`input type=submit`区别在于：
  1. 如果一个`form`只有一个按钮，它的`input type是button`，它则是一个普通按钮，无法提交。除非改成`submit`。
  2. 如果用的是`button`标签而不是`input type=button`，那么这个`button`标签会自动升级为提交按钮（前提是没有在`button`标签里写`button type=button`，否则将变成无提交功能的按钮，也就没啥用了）
  3. `<input type="checkbox">爱我`，就是一个勾选的东西，一般需在右边写上勾选的文字。如果希望在点“爱我”两个字的时候，会勾选上应该用上label标签`<input type="checkbox" id="xxx"><label for="xxx">爱我</label>`，这里要注意，如果没有写`name="loveme"`，则不会把请求发送给服务器，也就不知道是否有勾选。还可以加一个`value="yes"`，点击勾选后会看到源代码是`loveme=yes`
    - 还可以写
    ```
    喜欢的水果
    <label><input type="checkbox" name="fruit" value="orange">桔子</label>
    <label><input type="checkbox" name="fruit" value="orange">桔子</label>
    ```
    来实现多选框，需要是同一个name
  4. `label for`和`input`标签里的`id`元素对应，如果不想写`id`，可以用`label`把`input`包起来，也能实现。
  5. `input type="radio">`就是一个可以点击的圆点，它和checkbox不一样。它用于单选框比较多。
    ```
    <label><input name="loveme" type="radio" value="yes">YES</label>
    <label><input name="loveme" type="radio" value="no">no</label>
    这样就可以实现单选，同样的name是为了不让他们同时被选中
5. `select`标签，下拉列表标签
  ```
  <select name="分组">
    <option valve="">-</option>
    <option valve="1">第一组</option>
    <option valve="2">第二组</option>
    <option valve="3" disabled>第三组</option>
    <option valve="4" selected>第四组</option>
  ```
  - 第二行是表示空值，也就是可以什么都不选。第五行是表示不可以被选中。第六行是表示打开页面时默认选中该组。
- 还有个用法
  ```
  <select name="分组" multiple>
    <option valve="">-</option>
    <option valve="1">第一组</option>
    <option valve="2">第二组</option>
    <option valve="3" disabled>第三组</option>
    <option valve="4" selected>第四组</option>
  ```
- 即可以被多选
6. `textarea`标签
  `<textarea style="resize:none; width:200px;height:100px;" name="爱好" cols="30" rows="10"></textarea>`
  `resize`表示不可以改变这个文本框的大小。文本框的宽高可以用css来做，也可以用`cols`和`rows`
  - textarea一定要给个name
7. `table`标签
  - HTML规定`table`只能有`thead`,`tbody`,`tfoot`,`colgroup`.
  - 标题用`th`，数据用`td`
  - `colgroup`用于每一列的宽度。
  - `border`用于是不是有边框
  - `col`中还可以写`bgcolor`
  - 注意事项：
    - 无论`tfoot`,`thead`,`tbody`怎么写代码，顺序都是头身体脚
    - 如果没有`tbody`，浏览器会自动补全
    - 可以没有`thead`和`tfoot`，会把内容都放进`tbody`中，但是顺序就是写的顺序了，没有头身体脚的顺序了。
    - `table border`默认有空间，也就是两条线之间是有空间的。用`collapse`可以合并。