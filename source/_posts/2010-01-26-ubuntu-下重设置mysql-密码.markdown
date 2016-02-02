---
layout: post
status: publish
published: true
title: Ubuntu 下重设置mysql 密码
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 122
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=122
categories:
- Ubuntu
tags:
- Mysql
- Ubuntu
comments: []
---
<p>官方解决办法链接:<br />
https://help.ubuntu.com/community/MysqlPasswordReset<br />
主要分成下面几步:<br />
1.关掉mysql</p>
<pre name="code" class="shell">
sudo /etc/init.d/mysql stop<br />
</pre><br />
2.开启无授权的方式</p>
<pre name="code" class="shell">
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &<br />
</pre><br />
3. 以root用户进入</p>
<pre name="code" class="shell">
  mysql -u root<br />
</pre><br />
4.重置密码</p>
<pre name="code" class="sql">
UPDATE mysql.user SET Password=PASSWORD('newpwd') WHERE User='root';<br />
</pre><br />
5.保存改动</p>
<pre name="code" class="sql">
FLUSH PRIVILEGES;<br />
</pre><br />
6. 重启mysql</p>
<pre name="code" class="shell">
sudo /etc/init.d/mysql stop<br />
sudo /etc/init.d/mysql start<br />
 </pre></p>
