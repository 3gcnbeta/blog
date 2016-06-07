title: 利用QQ浏览器与nginx配置微信支付服务器
date: 2016-06-07 13:56:42
tags:
---
在微信支付开发的过程中，最困难的部分是对微信支付的调试。  
由于微信支付对支付域名与目录都有严格的要求,并且微信支付的测试域名基本上是没有用的，所以一般在本地调试微信支付基本不可能。

之后QQ浏览器中自带了穿透软件，可以实现本地的公共号测试。  
详细内容可以参考：  
http://blog.qqbrowser.cc/wei-xin-gong-zhong-hao-ben-di-diao-shi/

有了这个工具后，我们可以很方便的将本地服务器API或者本地的网页展示给远程使用了。   

但是这时访问的地址并不是我们自己的服务器。  

目前访问地址的格式是：  
http:///xxxxx.wechat.qq.com  
这样的。

所以我们在调试支付时还是不能直接调试，但是我们可以通过web服务器的代理功能实现。  

代码示例如下，我们可以设定一个目录当成是测试目录，在这里的目录名是test，  
通过这段代码，我们就可以将对test的访问引入到本地服务器，从而实现对微信支付的测试。  

```nginx
	location /test {
		access_log off;
		rewrite /test/(.*)$ /$1 break;
		proxy_pass http://xxxx.wechat.qq.com;
		proxy_set_header   X-Real-IP        $remote_addr;
		proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;

	}
```
