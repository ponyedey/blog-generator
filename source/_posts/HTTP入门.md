---
title: HTTP入门
date: 2017-10-17 19:01:05
tags:
---
# 何为HTTP
超文本传输协议（HTTP，HyperText Transfer Protocol)是互联网上应用最为广泛的一种网络协议。所有的WWW文件都必须遵守这个标准。设计HTTP最初的目的是为了提供一种发布和接收HTML页面的方法。
# 何为万维网
建议你们查阅一下[维基百科](https://en.wikipedia.org/wiki/History_of_the_Internet#Use_and_culture)
# URI,URL,URN
## Google URI 维基百科 即可查看全称。
- URI 分为 URL 和 URN，我们一般使用 URL 作为网址。
## Google URN 维基百科 即可查看全称。
- ISBN: 9787115275790 就是一个 URN，通过 URN 你可以确定一个「唯一的」资源，ISBN: 9787115275790 对应的资源的是《JavaScript 高级程序设计（第三版）》这本书。你去是介绍任何一个图书馆、书店，他们都知道是这本书。
## Google URL 维基百科 即可查看全称。
- [https://www.baidu.com/s?wd=hello&rsv_spt=1#5](https://www.baidu.com/s?wd=hello&rsv_spt=1#5) 就是一个 URL，通过 URL 你可以确定一个「唯一的」地址（网址）。
- 下为域名的直观解释
![](https://imgchr.com/i/YpKU0)
## DNS
- 输入域名
- 输出ip
- 还不懂就维基

# 请求与相应
![](https://imgchr.com/i/YplCT)
- 由浏览器发出请求
- 服务器在80端口接收请求
- 服务器返回内容（响应）
- 浏览器下载响应内容
## 请求示例
`curl -s -v -H "Frank: xxx" -- "https://www.baidu.com"`
- 得到的请求内容为
```
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
```
`curl -X POST -s -v -H "Frank: xxx" -- "https://www.baidu.com"`
- 得到的请求内容为
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
```

可以发现，这两段请求，得到的请求内容是一样的。是因为，第二个请求虽然是上传请求，但是并没有上传的内容。接下来给一段有内容的案例。
`curl -X POST -d "1234567890" -s -v -H "Frank: xxx" -- "https://www.baidu.com"`
- 得到的请求内容为
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
Content-Length: 10
Content-Type: application/x-www-form-urlencoded

1234567890
```
可以看到请求上传的内容为1234567890

可以发现请求的格式为
```
1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据
```
1. 请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
2. 第三部分永远都是一个回车（\n）
3. 动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等
4. 这里的路径包括「查询参数」，但不包括「锚点」
5. 如果你没有写路径，那么路径默认为 /
6. 第 2 部分中的 Content-Type 标注了第 4 部分的格式
- 除了自己搭建服务器外，也可以通过网站的源代码检查看到请求
## 用chrome
1. 打开 Network
2. 地址栏输入网址
3. 在 Network 点击，查看 request，点击「view source」
4. 点击「view source」
5. 点击「view source」
6. 点击「view source」
7. 终于点了？可以看到请求的前三部分了
8. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到
## 响应
- 没有响应，要么断网，要么服务器宕机了。
- 前三个请求中，以下两个响应分别对应前两个
```
HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

<!DOCTYPE html>
<!--STATUS OK--><html> <head> 后面太长，省略了……
```

```
HTTP/1.1 302 Found
Connection: Keep-Alive
Content-Length: 17931
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:19:47 GMT
Etag: "54d9749e-460b"
Server: bfe/1.0.8.18

<html>
<head>
<meta http-equiv="content-type" content="text/html;charset=utf-8"> 后面太长，省略了……
```

1. GET 请求和 POST 请求对应的响应可以一样，也可以不一样
2. 响应的第四部分可以很长很长很长

## 相应的格式
```
1 协议/版本号 状态码 状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容
```
- 状态码自己背去
- 第 2 部分中的 Content-Type 标注了第 4 部分的格式
- 第 2 部分中的 Content-Type 遵循 MIME 规范
## 用 Chrome 查看响应
1. 打开 Network
2. 输入网址
3. 选中第一个响应
4. 查看 Response Headers，点击「view source」，点击「view source」，点击「view source」
5. 你会看到响应的前两部分
6. 查看 Response 或者 Preview，你会看到响应的第 4 部分
# HTML
标记语言，非常酷炫，自己维基吧。

HTML 一开始的意图只是用来写文章和页面跳转，没想到现在的开发者已经用 HTML 做一切东西了。

以下软件都在使用 HTML 做界面：

手机微信、手机QQ、PC微信、PC QQ、钉钉、淘宝、支付宝、美团……

所有 App 都会内置一个浏览器（WebView）用来展示 HTML，而 HTML 都是通过 HTTP 下载的，而如果你要使用 HTTP 一般都会用到 URL。

这是一个简单而完美的系统