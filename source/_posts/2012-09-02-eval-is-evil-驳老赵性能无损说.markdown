---
layout: post
status: publish
published: true
title: eval is evil, 驳老赵性能无损说
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 1492
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=1492
categories:
- Javascript
tags: []
comments:
- id: 93
  author: buganshimingne
  author_email: liuxiaoyuff@yahoo.com
  author_url: ''
  content: ! '好高深的探讨&hellip;&hellip;


    我听说eval只是影响了浏览器的优化导致的性能影响，与作用域有关吗？eval本身木有性能影响的'
- id: 94
  author: 校长
  author_email: streamnew@gmail.com
  author_url: ''
  content: 坐等老赵反驳~
- id: 95
  author: 校长
  author_email: streamnew@gmail.com
  author_url: ''
  content: ! '@test

    测试没问题，你说的eval这种用法性能差谁都知道，试都不用试。使用时不会每次都eval，我测试的是Wind.js里的使用方式，我跟那位专家也强调了很多次。


    看我最后一句话：&ldquo;要么不熟悉eval，要么不了解Wind.js&rdquo;。


    散了~~'
- id: 96
  author: hello
  author_email: sdf@sdsfd.com
  author_url: ''
  content: ':)'
- id: 97
  author: 北漂IT民工
  author_email: calidion@gmail.com
  author_url: ''
  content: 老赵所测试的内容根本不会用到eval, 因为在解释期就已经确定了.
- id: 98
  author: 北漂IT民工
  author_email: calidion@gmail.com
  author_url: ''
  content: ! '又一个被误导的. eval本身没有性能影响?为什么我的代码执行时间下降了几十倍?

    你的性能是指的什么? 什么才是性能?'
---
<a href="http://blog.zhaojie.me/2012/08/js-code-from-eval-benchmark.html">http://blog.zhaojie.me/2012/08/js-code-from-eval-benchmark.html</a>

原文把一个固定值传给了eval,

那么经过js的解释器一分析后，由于字符串是固定的，所以优化过的js引擎就会直接解析成函数返回。

因为这里eval不eval根本没有区别。将这个来测试eval性能，只能说是一种行为艺术。

那么如何证明eval在实际上对于性的损失影响很大呢？

方法很简单，两行代码，一个浏览器Chrome:

在Chrome下Ctrl+i打开调试界面，点入console：

复制下面的代码执行：

```
var sum = 0, a = 0, b = 0, i = 0, c = 0; a = new Date(); for(; i < 1000 ; i++) { sum = eval( 'sum + i'); }; b = new Date(); c = b - a; </em></p>

118//结果

var sum = 0, a = 0, b = 0, i = 0, c = 0; a = new Date(); for(; i < 1000 ; i++) { sum = sum + i; }; b = new Date(); c = b - a;</em>

3//结果

```
&nbsp;

在这里相关了118 / 3 ~ 40倍&hellip;&hellip;

还有几次的结果是

119 / 2 ~ 60倍

如果这样是无性能损失的话，那60个人就等于是一个人。

&nbsp;

&nbsp;

受@老赵的错误引导，有下面的结论：



october 2012-08-20 16:26:12

>eval并没有什么性能损失吧. eval只是可以让程序员人为控制编译时机, 但编译消耗的时间还是一样的. 比如某一js文件有10000行代码, 假设需要编译x秒 把后5000行代码用eval包起来后,
js文件:
>1	... 此处5000行js代码 ...
>2	eval("...此处5000行js代码...")
>那么过程就变成了: 编译前5000行 -> 运行前5000行 -> 运行到eval() -> 编译后5000行
>看的出来,只是编译人为置后了, 应该没有性能损失….拙见….
