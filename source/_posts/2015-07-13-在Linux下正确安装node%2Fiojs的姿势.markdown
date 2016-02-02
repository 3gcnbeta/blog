---
layout: post
status: publish
published: true
title: ! '在Linux下正确安装node/iojs的姿势'
author:
  display_name: Admin
author_email: calidion@gmail.com
categories:
tags: ['nodejs', 'nvm', 'linux', 'node', 'iojs']
comments: []
---


无论是在使用node还是在安装node时，都尽量避免安装成root/管理员权限。
不管是在linux下面还是在windows下面。

原因有几点：

1. 一般不要用root安装node，除非你知道自己在做什么
2. 不要在root下工作，除非你的工作就是管理整个系统
3. 不要在root下运行node程序，除你知道你的软件没有bug

>centos/ubuntu等用户，尽量不要将node安装到/bin, usr/bin等目录下面。

在linux/unix下面有一个非常方便的工具叫nvm。可以帮助node用户很好的安装与管理他的node安装与版本。

这个工具的项目地址：

https://github.com/creationix/nvm

安装方法很简单（教程原项目上都有，如果对于英文比较吃力的可以继续看下去):

1.安装

用curl:

```sh
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.25.4/install.sh | bash
```

用wget:

```sh
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.25.4/install.sh | bash
```

2.source到你的shell里

执行

```sh
. ~/.nvm/nvm.sh
```
或者

```sh
source ~/.nvm/nvm.sh
```

3.查找远程的node/iojs版本

```sh
nvm ls-remote
```


4.选择适合你的版本安装



```sh
nvm install 0.12.6
nvm install iojs
```

5.设置一个默认的版本

```sh
nvm alias default 0.12.6
```

这样你的一个nodejs安装就完成了。

如果你还想管理更多的版本，可以自己对照原项目帮助进一步的学习如何使用nvm.
