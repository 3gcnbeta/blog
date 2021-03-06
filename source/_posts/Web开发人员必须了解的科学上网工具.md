title: Web开发人员必须了解的科学上网工具
date: 2016-06-07 20:24:29
tags:
---
由于众所周知的原因，我们的网络环境是相对受限的。这样导致我们无法获得足够的信息作出比较全面的价值判断。

# 背景
而对于技术人员来讲，则是我们无法获得一手的资料，从而产生各种传播的错误。  
其中传播最为广泛的错误是DIV+CSS的错误，正确的表述应该是HTML+CSS。
同时最近又出现前后端分离这种国外基本没有人提的错误，严重影响着国内的技术圈的认知。  

特别是最近百度魏则西事件的曝光，突显了国内搜索引擎误导性。因此有条件的要使用谷歌，没条件创造条件也要使用谷歌对于我们Web开发人员来说是至关重要的技术能力。当然，还有bing.com可以作为临时性的搜索引擎。毕竟折腾是需要时间的。

在这里我将向大家介绍一些常用的免费科学上网工具，助力你更好的获取你所需要的知识。

## Lantern
 ![](http://webfullstack.me/images/lantern.png)
首先是最简单易用的上网软件lantern。
### 项目地址
  https://github.com/getlantern/lantern
### 安装方法
  直接下载安装
### 优点
  它是最简单易用的上网软件，通过自动代理系统的网络访问请求，从而实现无逢科学上网。门槛最低
### 缺点
  有时候网络会比较慢，同时存在错误代理网站，导致访问极慢的情况。
### 适合人群
   对网络相对不是很熟悉，使用国外网站需求相对比较少的人群
## XX-Net 
![](http://webfullstack.me/images/xx-net.png)
XX-Net是一个基于Google Appengine的Web代理，是goagent的升级版。
### 项目地址
  https://github.com/XX-net/XX-Net
### 安装方法
  见项目地址。相对于lantern来说复杂了很多。需要申请appengine与创建appengine的项目。由于近期google appengine似乎已经无法注册了，这个项目的可用性在未来将会受到考验。但是目前公共帐号应该是有一些可以使用的。
### 优点
  单个APPENGINE 项目可用的流量每天有1G，只要注册足够多的帐号，基本上不用担心流量的问题。比如我有10个左右的帐号，因此观看Youtube视频是足够的。对于经常要看Youtube的同学来说拥有XX-Net是至关重要的。
### 缺点
  配置相对复杂，要注册帐号（这个可能会卡住很多人，并且现在Google的App Engine已经不再继续了），同时访问时带有appengine的id或者项目信息，容易暴露自己的隐然信息，并不是一个安全的科学上网工具
### 适合人群
  爱折腾的IT开发人员或者其它有能力解决问题的人员
## Tor 
![](http://webfullstack.me/images/tor-logo.jpg)
Tor是一个浏览器应用，使用Tor可以很好的隐藏你的网络访问行踪，是一个安全级别很高的浏览器。
### 项目地址
  https://www.torproject.org/
### 安装方法
  同lantern，下载安装即可。针对不同的OS有很多的版本，可以根据自己的OS选择一个适合的版本。
### 优点
  有效的保护你的访问位置等隐私，配置相对于XX-Net要简单很多
### 缺点
  由于采用了很多安全措施，导致访问时的速度不高，但是新版本已经有所改善。
### 适合人群
  对隐私敏感，服务于安全机构的工作人员

## SoftEther
 ![](http://webfullstack.me/images/softether.ico)
SoftEther顾名思义就是软网，软件实现的以太网，也就是通常的VPN。只不过这个VPN是开源的，是公共的。任何人都可以构建一个VPN服务器供其它的VPN客户端访问，并且开放用户名与密码。
### 项目地址
  https://www.softether.org/
### 安装方法
  Windows用户直接下载安装。
这个项目的软件分成服务器与客户端，服务器用来建设一个公共VPN网络，客户端用来连接一个公共VPN网络。对于要科学上网的我们来说，只需要客户端就可以了。
目前SoftEther的最方便的使用环境是Windows环境，在Linux/Mac下，由于更新机制不完善，所以不是很推荐使用。
在Windows下面，客户可以自动刷新公共VPN服务器，并且点击就可以连接VPN，所以很方便找到可用的VPN服务器。
### 优点
  跟Tor类似，客户端与服务器之间有安全的信道。支持包括HTTP协议的所有的协议，所以对于被禁的其它协议也有很强的抵抗能力。这是其它上述3个软件所无法实现的。同时速度非常快，正常情况下比XX-NET要快很多，所以看Youtube一点也不卡。同时可以很好的保护自己的上网位置。
### 缺点
  不是非常稳定，由于众所周知的原因，有时候一个IP可能会随时被断掉。这种方法同时会让HTTP代理显得没有意义。跟HTTP代理比，缺少灵活性。

# 总结
上述的科学上网工具都是免费或者开源免费的，他们有着不尽相同的属性与难易程度，你可以根据你的实际情况选择一个使用，让自己可以更加自由地获取知识与思想。

对于比较健忘的同学，可以记住下面的网站:
http://webfullstack.me
上面有全部这四个工具导航地址，方便你随时找到你想要的网站。并且提供了很多全栈开发工程师必备的网址。

更多关于网络或者Web的知识欢迎关注微信公共号：frontend-guru
或者扫描下面的图片
![](http://res.cloudinary.com/dawjytvkn/image/upload/v1464858605/qrcode_for_gh_6f66da401fef_430_b1rr96.jpg)
