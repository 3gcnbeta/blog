title: 什么是RESTful APIs?
date: 2016-06-07 13:33:10
tags:
---
REST的概念从提出到现在已经10年多了，它对互联网的企业级计算产生了非常重大的影响。

REST是从WDSL，SOAP等架构发展而来的，是目前企业级开发中使用最广泛的架构之一。

下面我们来考查一下什么是REST。

## 什么是REST?

参考： [wiki](https://en.wikipedia.org/wiki/Representational_state_transfer)
下面我将基于对WIKI的翻译，阐述REST相关的概念。如有错误，欢迎指正。

REST是指Representational State Transfer，中文意义是可重新表达的状态转移。
>个人认为其它的翻译比如：表征状态转移，表现层状态转移都是不准确或者是错误的. Representional表达的是一个RE的概念，即可以重新或者重复表达。有了可或者重，其它的如何翻译反而不重要。

所以你可以翻译成可重现状态转移或者可重现状态转换,中文翻译成表现，实际上英语里隐含有重新，重现的意思，即对原物理的一个复制表达。
在这里是对计算机存储的资源的重复表达。所以翻译成可重现状态转移或者可重现的状态转换更加准确。

通常对于术语我不建议翻译成汉语，因为很多时候翻译会缺失原文的意思，特别是复杂的词组。

REST是一种指对WWW的软件架构的风格。就是你的体系架构是面向资源来表达的。  
对于目前的互联网很多接口确实都是可以用资源来表达的。因为这种软件架构风格是受到欢迎的。

REST架关注的点有：
性能(Performance),   
可规模化(Scalability),  
简单性(Simplicity)，//指API  
可修改(Modifiability)，  
可见性(Visibility)，  
可移植性(Portability)，  
可靠性(Reliability).

除此之外，REST有一些核心的约束：
1. 客户端-服务器模式(Client–server)
通过统一的API分开客户端与服务器，即我们通常说的RESTful APIs.从而提高客户端的移植性。
2. 无状态(Stateless)
不为请求的客户端保存数据，客户端所有访问性数据，session数据由客户端自己保存
3. 可缓存(Cacheable)，
返回数据可缓存。对于提高性能很有好处
4. 可层级化系统(Layered system)
客户端可以访问最终服务器，也可以访问中间服务器。同时方便了在中间添加代理服务器或者缓存服务器。
5. 统一接口(Uniform interface)
统一接口是REST里面非常重要的一个部分。他用于简单化并且解耦整个架构，让每个部分可以独立的演进。统一接口包含以下几个重要部分：
    1. 资源识别(Identification of resources)
资源通过请求识别。对于Web来说就是通过URI来识别。资源与他的表达之间是分离的。服务器的资源与服务器发送的数据格式之间没有关联。
    2. 通过资源的表示者来操控资源(Manipulation of resources through these representations)
当客户端拥有一个资源的表达，包括附带的metadata时，它就有充分的信息修改并删除一个资源。
    3. 可以自描述的消息(Self-descriptive messages)
返回中包含了对足够多的信息告诉客户端如何处理。比如MIME信息。
    4. 将超媒体当成是应用状态的引擎(Hypermedia as the engine of application state (HATEOAS))  
客户端只能通过在超媒体(hypermedia)中被服务器动态识别的动作来实现状态转换。比如，通过超文本(hypermedia)里的超链接。 也就是说返回的数据就是一个资源的状态，同时也可以看成是一个应用的状态。而这个状态信息就在返回的超媒体内。通常对于API来说我们会使用JSON表示。

所以满足上述风格的软件架构系统可以称之为RESTful。通常RESTful系统的沟通是基于HTTP协议与HTTP的动作(verbs)来实现的。  
因为他的创始人是Roy Fielding，他使用REST来设计HTTP 1.1协议和URI，是HTTP协议的主要维护者之一。
 
## 什么是RESTful APIs？
遵从跟REST约束的Web服务的API就称为RESTful APIs.  
基于HTTP协议的API从下面几个方面进行了定义：
1.基URI，比如http://example.com/resources/
2. 数据媒体类型，通常是JSON，但是也可以是其它媒体
3. 标准的HTTP方法，(比如，OPTIONS, GET, PUT, POST, and DELETE)
4. 一个参考状态的链接
   (个人理解：比如 http://example.com/resources/?age>1)
5. 一个参考相关的资源的链接
  (个人理解： 比如 http://example.com/resources/item100?age>1)

## URI与HTTP方法之间的关系

URI分成Collection与Element  
作用于Collection时，会成批的变更  
作用于Element时，只会变更一个  

HTTP方法：  
PUT/DELETE操作会导致完全相同的结果，无论作用多少次。  
GET作用后不会产生任何状态变化  
 POST会创建新的数据。  
PUT会替换数据或者创建数据


## RESTful APIs没有标准

REST是架构，所以并没有出来相关的标准。
但是RESTful APIs使用了HTTP，JSON，XML，URI等标准。

## 总结

RESTful架构对于构建大型的互联网服务来说已经表现出了很多优越性，但是同时带来了一些困难。
下一篇我将将继续讨论REST给开发者带的困难。