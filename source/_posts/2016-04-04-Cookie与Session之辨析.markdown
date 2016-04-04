title: Cookie与Session之简单辨析
tags:
  - http
  - 浏览器
  - 服务器
  - Cookie
  - Session
categories: ['Web技术']
author:  
	display_name:  北漂IT民工 
date: 2016-04-04 17:28:00
---

### Cookie与Session目标接近，服务对象不同

Cookie与Session是两个目的类似，但面对的对象有所差异的东西。
特别是他们经常相互作用，实现各自的目标，因为有没有真正的理清理他们的实际意义与使用方式前，人们还是非常容易混淆他们之间的区别的。

Cookie的服务对象是：浏览器，用于记录浏览器端用户信息或者相应的状态
Session的服务对象是：服务器，用于记录服务器端用户信息或者相应的状态


### 混淆的原因：Session经常借Cookie来实现
容易混淆他们的原因是：Session经常借助Cookie来实现。  
因为Cookie是HTTP的标准头字段。所以经常我们只要在Cookie里加上一串
XXXsessionid=xxx就可以标志一个session。  
比如：

> php通常是使用PHPSESSID标识一个Session ID。一个简单，完整的Cookie字段表达：
```
Cookie：PHPSESSID=D3223883123;
```
> java通常可以使用jsessionid来标识Session ID。
```
Cookie：jsessionid=D3223883123;
```

所以这时Session信息是隐藏在Cookie里面的，因为导致很多人分不清楚Cookie与Session的区别。

### Session是可以脱离HTTP协议的，但是Cookie是不行的

Session是服务器端的标识，所以抛开安全性的话，可以通过任何方式提交到服务器，并且目前应该没有针对Session的规范，所以如何实现Session完全是服务器非常自主的事情。

比如我们可以通过添加GET参数的方式提交：

```
GET /?sessionid=dfsdfsdfsdfsd
```

也可以通过POST的方式将SessionId当成是参数提交：

```
POST  /

sessionid=xxx
```

但是Cookie是不一样的，Cookie必须是放在HTTP协议的头里面。永远只能是在HTTP头里面，是不能自由的选择如何实现的方式的。
```
Cookie：jsessionid=D3223883123;
```

### Cookie的实现对于任何开发语言是一致的，Session的实现会因为开发语言，项目而不同

根据上面的内容，我们可以得到结论：
* Cookie是通用的技术，对于所有的技术都是通用的
* Session是专用的技术，对于不同的语言项目是不同的。

### Cookie不适合保存大量的数据，Session所对应的保存数据则是可以无限的

基于我们上述的理解，我们可以发现：
* Cookie的数据是全部保存在Cookie字段里，并不会被服务器所保存，但同时服务器又是需要知道当前页面的Cookie的全部信息的，所以Cookie是必须在HTTP传输进程中全面交换的。因此Cookie的长度需要限制，因为如果Cookie量太大，会导致传输的数据变大，导致网络的性能下降
* 但是Session则会好很多，首先Session只要一个ID标识就可以了，并没有类似Cookie的k=v结构。所以sessionid不是数据，而是标识。这跟cookie本身就是数据是不同的。Session ID后面可以对应很多数据，可以是个人或者网站的所有数据，因为可以认为是无限的。

上面讨论的是Cookie与Session的几个比较明显的不同点。

相信通过比较上面的几个点，我们就可以很容易区分Cookie与Session了。



