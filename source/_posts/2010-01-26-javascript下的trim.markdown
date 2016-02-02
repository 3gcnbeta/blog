---
layout: post
status: publish
published: true
title: javascript下的trim
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 153
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=153
categories:
- Javascript
tags:
- javascript
- 正则
comments: []
---
<p>实际上只要在string下面添加一下下面的语句：</p>
<pre name="code" class="js">
replace(/^s+/ig, '').replace(/s+$/ig, '')<br />
</pre><br />
就可以了。</p>
<p>如果 </p>
<pre name="code" class="js">
var str = "               hello    world               ";<br />
str = str.replace(/^s+/ig, '').replace(/s+$/ig, '');<br />
alert(str);<br />
</pre><br />
str等于hello   world</p>
