---
layout: post
status: publish
published: true
title: ! 'Ubuntu非root安装软件(mysql篇)'
author:
  display_name: 北漂IT民工
author_email: calidion@gmail.com
categories:
- 数据库技术
tags: ['数据库', 'MYSQL', 'root', 'UBUNTU']
comments: []
---

对于任何的非系统软件的安装，本人都是比较推荐非root权限安装的。
所以虽然ubuntu的apt包管理机制很方便，但是对于大部分软件，特别是开发软件最好还是通过源码安装，方便修改安装。
下面是在Ubuntu下面非root安装mysql-server的步骤：


```bash
#保证必要的库文件包
sudo apt-get install cmake libncurses5-dev

#得到mysql-server源代码
apt-get source mysql-server

cd mysql-x.x.xx     #我的是mysql-5.5.41/

#生成makefile，同时需要指定的连接库与库文件头的位置
#同时指定好安装的位置，个人一般比较喜欢安装在~/local下面。
cmake  -DCMAKE_INSTALL_PREFIX=~/local/mysql -DMYSQL_DATADIR=~/local/mysql/data -DSYSCONFDIR=~/local/mysql/etc -DCURSES_LIBRARY=/usr/lib/libncurses.so -DCURSES_INCLUDE_PATH=/usr/include

#或者，要明确好curses的位置

cmake  -DCMAKE_INSTALL_PREFIX=~/local/mysql -DMYSQL_DATADIR=~/local/mysql/data -DSYSCONFDIR=~/local/mysql/etc -DCURSES_INCLUDE_PATH=/usr/include -DCURSES_LIBRARY=/usr/lib/x86_64-linux-gnu/libncurses.so

#编译代码
make

#安装
make install

#进入安装好的MYSQL目录
cd ~/local/mysql

#复制配置文件
#选择一个support-files目录下面的配置文件，这里选择medium
#这里要注册清空其它地方的my.cnf文件，比如根目录下的etc/my.cnf
mkdir etc
cp support-files/my-medium.cnf etc/my.cnf

```

对my.cnf进行如下修改：

```conf
[client]
#password	= your_password
port		= 3306

#这里是需要修改的地方
socket		= /home/seiya/local/mysql/mysql.sock

[mysqld]
port		= 3306
skip-external-locking
key_buffer_size = 16M
max_allowed_packet = 1M
table_open_cache = 64
sort_buffer_size = 512K
net_buffer_length = 8K
read_buffer_size = 256K
read_rnd_buffer_size = 512K
myisam_sort_buffer_size = 8M

#这里是需要修改的地方
log-error=/home/seiya/local/mysql/log/error.log
pid-file=/home/seiya/local/mysql/mysql.pid
socket		= /home/seiya/local/mysql/mysql.sock
```

一般最重要的是对端口的修改。

* 同时如果之前安装过mysql-server，一定要将所有的地方的.cnf文件清楚。否则启动时会优先使用之前的cnf。


最后安装MYSQL。

```bash

#安装MYSQL数据库
scripts/mysql_install_db --user=$USER --basedir=. --datadir=data --no-defaults 

#启动mysql
bin/mysqld_safe &

#登录mysql
bin/mysql -uroot

#如果需要修改密码
bin/mysqladmin -u root password 'newpassword'

```
安照上面的步骤这样mysql就安装完成了
