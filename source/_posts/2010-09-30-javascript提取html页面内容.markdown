---
layout: post
status: publish
published: true
title: javascript提取HTML页面内容
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 1389
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=1389
categories:
- WEB前端技术
- Javascript
tags:
- javascript
comments: []
---
<p>今天同事有一个用javascript提取的HTML页面的内容的需求。<br />
经过一段时间的试验。<br />
得到下面的代码。<br />
能提取出来相应的HTML标签内的内容。</p>
<pre name="code" class="js">
var reg = /<[^>]*?>([^>^<]+)<[^>]*?/+[^>]*?>/g;<br />
var res = '<a href="forum-10-1.html" class="prev">&nbsp</a><a href="forum-10-1.html">1</a><strong>2</strong><a href="forum-10-3.html">3</a><a href="forum-10-4.html">4</a><a href="forum-10-5.html">5</a><a href="forum-10-6.html">6</a>'.replace(reg, "$1,");<br />
console.log(res);<br />
</pre></p>
<p>结果:<br />
"&nbsp,1,2,3,4,5,6,"</p>
