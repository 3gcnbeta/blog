title: npm自建服务器
tags:
  - nodejs
  - npm
  - 服务器
categories:
  - nodejs
  - 服务器
date: 2016-04-28 08:54:00
---
nodejs开发给开发者带来的最大的好处是丰富多彩的各种npm包。我们经常会很高兴某个包已经被其他的开发者开发完成，并且质量也很高，我们直接拿过来用就可以了。这也是很多开发者喜欢nodejs的原因。即使是曾经包机制最完善的ruby语言，也会发展他已经远远落后于nodejs的npm了。

除了上面讲到的开放包，npmjs.com也提供私有包管理方案，每个月只要交10几美元就可以轻松建立自己的私有npm库了。

在了解了这么多npm的好处之后，其实我们发现还是有不太满意的地方。比如需要每月交钱，比如npmjs.com有时候会被GFW墙掉，速度非常慢。

特别的，如果我们有私有的包，不想公开，也不想交钱，那么这个时候我们就可以通过自建私有的服务器来实现。

实现的过程很简单，就是通过sinopia包搭建一个服务器。

[sinopia](https://github.com/rlidwka/sinopia)项目地址：https://github.com/rlidwka/sinopia

步骤如下：

1. 安装sinopia
```sh
$ npm install -g sinopia
```
2. 启动运行sinopia  
可以默认启动
```sh
$ sinopia > /dev/null 2>&1
``` 
也可以指定IP与端口
```sh
$ sinopia -l 0.0.0.0:8080 > /dev/null 2>&1
```
3. 访问sinopia  
浏览器打开： http://localhost:4873/

4. 添加用户  
```sh
npm adduser --registry http://localhost:4873/
```

5. 登录npm服务器  
```sh
npm login --registry http://localhost:4873/
```
6. 发布npm包  
```sh
npm publish --registry http://localhost:4873/
```
7.  下载npm包  
xxx是你发布的包名。  
```sh
npm install xxx --registry http://localhost:4873/
```

通过以上几个命令你就可以在你的服务器上玩起来了。