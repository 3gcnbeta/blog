title: Python vs Node.js
tags:
  - Python
  - Nodejs
categories:
  - Python
  - Nodejs
date: 2016-04-16 21:04:00
---
对于语言或者开发环境的比较总是让人乐此不彼的。我在这里呢通过数据比较Python与Nodejs，让更多的人可以更好的作出来自己的决策。从主观的角度来讲，我当然认为总体上Nodejs要优于Python。但是这种主观的东西必须要有相应的数据支持吧？所以我在这里尽量选择客观的数据来进行比较。

### 首先是语言的创建时间与创始人
Python: 1991, Guido van Rossum  
Nodejs： 2009, Ryan Lienhart Dahl

点评： Python25岁，Nodejs7岁

### 软件包数量
Python: 78690  
来源： https://pypi.python.org/pypi  
Nodejs:  270,278  
来源： https://www.npmjs.com/

点评： 在很短的时间内, npm包数量远远超过了Python的pip，可见包的热度与影响度远高于Python.

### 几个Benchmark的数据

例子1： http://szborows.blogspot.com/2016/03/mini-restjson-benchmark-python-351-vs.html
结论： python/node/c++ = 1/2/4

例子1：http://blog.kgriffs.com/2012/11/13/python-vs-node-vs-pypy-benchmarks.html
结论： python < node

点评：虽然不能完全看Benchmark，但是数据是一个有力的武器。

### Web领域支持
##### Web服务器
Python: Django, Twisted, Tornado等
Nodejs: express, sails, meteor, koa等

点评：总体相关不大，但是nodejs的框架相对更加新一些，用户关注度更高一点。

##### HTML模板
Python: Airspeed, jinja2等，
具体：https://wiki.python.org/moin/Templating
Nodejs: jade, ejs等
具体：http://paularmstrong.github.io/node-templates/，这个表并不全面，JS的模板包括最新的react, handlebars, mustache等很多。

点评：总体相差不大。

#### HTML提取，抓取
Python:  BeatifulSoup
Nodejs: Cheerio

点评：Cheerio比BeatifulSoup操作DOM更加方便，特别是可以很方便的使用CSS选择器。


###  移动端支持
Python: None
Nodejs: nativescript, react native, cordova/phonegap

结论: Python完败

### 前端工具链接支持
Python: None
Nodejs: yo, grunt, gulp, webpack, requirejs, browserify, etc.

结论：Python完败

### Linux/运维工具支持
Python: 成熟
Nodejs: 不成熟

结论：Python胜出，但是Nodejs在这个方面的潜力是相当的，未来在一些性能要求更高的地方，go/Node.js将会更多的取代Python，目前很多工具Ruby已经参与进来，但是Ruby目前的性能尚不太理想，未来的发展空间受限。

### 桌面UI支持
Python: wxPython, Python-qt, TkInter
Nodejs: Electron.js, NW.js, APP.js, Node-qt

结论：两者旗鼓相当，但是基于Electron的Atom与Visual Studio Code已经开始流行起来，未来Nodejs胜出的可能性更大。因为Electron的技术栈是基于Web的。而Web是最成熟的领域。

### Python转Node.js的理由
1. http://geekforbrains.com/post/why-im-switching-from-python-to-node-js
2. https://www.quora.com/What-are-the-benefits-of-developing-in-Node-js-versus-Python

结论：越来越多的人意识到Nodejs的优势。

### Node.js转Python的理由
暂时未搜索到


### 总结

Python目前仍占有很重要的位置，但是除了在Linxu/运维领域中由于积累所造成的优势外，在其它领域的优势并不明显，特别是在Web领域会慢慢的让位于Node.js。在Web Assembly标准出来，并被实现之前，Nodejs将是最重要的编程语言或者开发环境。

此文在主观上是认为Python不如Nodejs的，但是我尽量客观的使用数据。
任何东西都是可以比较的，只有比较才能分出来优势与劣势。但是选择是自由的，本文并不强制任何人从Python转到Nodejs.
欢迎基于数据的讨论与分析。