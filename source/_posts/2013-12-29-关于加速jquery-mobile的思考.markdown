---
layout: post
status: publish
published: true
title: 关于加速jQuery Mobile的思考
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 1667
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=1667
categories:
- 其它
tags:
- HTML5
- PHONEGAP
- APP
- jQuery Mobile
comments: []
---
最近做移动开发app的专题培训，并选择了phonegap与jqm作为主要的实例进行讲解。

原因是jqm功能丰富，社区强大，历史悠久，非常成熟。

phonegap也已经开源，有很长的历史，成熟很高。

但是jqm往往为人们所诟病的是他的速度，

以至于国内有些无良的商家也借机起哄，将自己的产品与基于jqm开发的phonegap应用进行比较。

结果当然是让人贻笑大方了。开这种玩笑的公司，估计也不会长久的。

关于jqm的速度慢的原因主要是由于jqm的机制引起的：

1、一般切换页面可能是远程的页面，网络延时，会让jQM的页面看起来很慢。

2、加载完成页面后，jqm都会执行一次对页面渲染的代码，所以会消耗相当的资源。

3、添加了额外的DOM节点，导致JS的执行，消耗了CPU时间。

这几点导致人们在切换页面时速度非常慢。

所以我认为提高速度的最佳的办法就是不切换页面。

不切换页面就意味着你必须对javascript, dom, jquery mobile的api, 非常熟悉，并且有良好的调试页面的技术。

同时由于jquery mobile是后执行的框架，所以在dom添加完成后，必须重新通过api让添加的dom的UI变为正常，这一点非常重要。

比如对于button，一定要调用$(dom).button()来完成UI的渲染。

当然还可以与前端的mvc框架配合使用，这样可以会更加工业化一些，但是如果对于前端框架不熟悉，也可以先按最原始的形式实现出来功能。

毕竟与框架的成熟度目前都不算很高，再加上jquery mobile的后执行的特点，与框架配合也是比较困难的。

所以综合起来，个人认为提高JQUERY MOBILE性的方式可以直观的表达成：

1、最好只有一个index.html

2、所有的UI变化都在js里实现

3、熟悉JQM的API

4、避免或者减少远程页面的切换.

最后还有一个好消息是1.4的速度与API都有比较明显的提升。并且已经是正式发布了，如果是新项目可以使用1.4。

并且1.4上DOM节点的添加明显减少，更加符合HTML5的口味。

总之基于HTML5相关的架构的混合移动app的开发不管是用什么框架，本地化，脚本化，是提高性能的不二法门，如果有条件的，可以直接自己写响应式的布局与代码，进一步降低开销，如果自己的设计与网页制作团队的技术实力偏弱，则可以用现在有的UI框架先用着，等后期设计与制作团队熟悉了，再补上技术负债。