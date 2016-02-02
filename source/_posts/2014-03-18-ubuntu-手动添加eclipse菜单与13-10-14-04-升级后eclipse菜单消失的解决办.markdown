---
layout: post
status: publish
published: true
title: ubuntu 手动添加eclipse菜单与13.10 / 14.04 升级后eclipse菜单消失的解决办法
author:
  display_name: 北漂IT民工
  login: admin
  email: calidion@gmail.com
  url: ''
author_login: admin
author_email: calidion@gmail.com
wordpress_id: 1687
wordpress_url: http://www.3gcnbeta.com/wordpress/?p=1687
categories:
- eclipse
tags: []
comments: []
---
因为eclipse的强大的功能，支持几乎所有的开发语言与环境，

最近越来越往eclipse平台上靠了。eclipse + emacs的按键模式可以产生很好的编辑效率。

但是eclipse这么强大的平台，仍会在ubuntu平台上出点状况。

1、ubuntu平台的自带模块因为eclipse的机制关系会产生一些不可控的脏文件数据，导致升级会很麻烦。所以一般都是采用自行下载的方式使用eclipse

平台自带的eclipse会提供一个桌面菜单，而自行下载的eclipse则没有这个福利。

所以需要自行制作桌面菜单。

创建一个eclipse.desktop文件到

~/.local/share/applications/eclipse.desktop

或者

cp /usr/share/applications/eclipse.desktop ~/.local/share/applications/

如果路径上存在的话。

文件的内容如下：

```
[Desktop Entry]

Type=Application

Name=Eclipse

Comment=Eclipse Integrated Development Environment

Icon=/home/[USER]/Program Files/eclipse/icon.xpm

Exec=/home/[USER]/Program\ Files/eclipse/eclipse

Terminal=false

Categories=Development;IDE;Java;

StartupWMClass=Eclipse
```
注意：

[USER]是你用户名

如果你保存的目录类似于Program Files这样带空格的，注意在Exec上带上反斜扛\。具体效果根本自已的测试结果而定。

不过不建议目录带空格。

2、ubuntu最近升级到13.10与14.04后会出现菜单消失的情况。

解决的办法是在Exec加上：

```

env UBUNTU_MENUPROXY=0
```
即：

```

Exec=env UBUNTU_MENUPROXY=0 /home/eric/Program\ Files/eclipse/eclipse
```

最终的效果是：

```
[Desktop Entry]

Type=Application

Name=Eclipse

Comment=Eclipse Integrated Development Environment

Icon=/home/[USER]/Program Files/eclipse/icon.xpm

Exec=env UBUNTU_MENUPROXY=0 /home/[USER]/Program\ Files/eclipse/eclipse

Terminal=false

Categories=Development;IDE;Java;

StartupWMClass=Eclipse
```

所有的内容最初来源于：

http://askubuntu.com/questions/80013/how-to-pin-eclipse-to-the-unity-launcher

对于英语掌握的比较好的同学可以自己查看英文原文。