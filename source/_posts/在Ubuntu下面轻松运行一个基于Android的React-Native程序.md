title: 在Ubuntu下面轻松运行一个基于Android的React Native程序
date: 2016-06-07 20:22:51
tags:
---
## 废话
React Native火遍大江南北，五湖四海。基于React的组件化思想，通过JS就可以轻松的制作出来界面精良，体验真实的移动应用，对于开发Web应用为主的广大js开发人员来说还是非常有吸引力的。
同时React让界面变动大的移动应用变的更加的自如。所以作为一个移动+Web开发者，没有理由不上上手实作一下。

## 主体
在实作的过程中也遇到了点小问题，不过克服起来还是比较容易的。
下面我将我如何成功运行React Native的过程记录下来，希望给对React Native感兴趣的同学一个借鉴，少走些弯路。

### 过程
由于我的开发环境是Ubuntu，所以我基于Ubuntu来介绍我的实现过程。

对于英语熟练的同学可以直接访问：
http://facebook.github.io/react-native/docs/getting-started.html

我在这里不再详细介绍上面页面已经有的内容。
只将步骤列出来，方便新手连贯起来走完全程。

1. 首先是安装基本的支持包
```bash
sudo apt-get install -y build-essential default-jdk git-all lib32stdc++6
```
2. 然后是安装nodejs
由于本人特别反感nodejs通过root权限安装，所以强烈推荐使用nvm安装。
如果你现在坚持要使用root安装，请确保你能应对所有可能出现的安全问题。
如果你现在是root用户，建议马上创建非root用户，可以适当的加上sudo权限。
安装nodejs的过程详细见：
```
http://blog.3gcnbeta.com/2015/07/13/%E5%9C%A8Linux%E4%B8%8B%E6%AD%A3%E7%A1%AE%E5%AE%89%E8%A3%85nodejs%E7%9A%84%E5%A7%BF%E5%8A%BF/
```
我只在这里按步骤列出命令：
```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.25.4/install.sh | bash
. ~/.nvm/nvm.sh
nvm ls-remote
nvm install v4
nvm alias default v4
```
这样你的nodejs就安装好了。
打入npm如下：
```bash
npm
```
应该会出现一堆提示，表明你已经安装成功。
3.  安装react native 命令行工具
```bash
npm install -g react-native-cli
```
4. 安装Android Studio
下载[Android Studio](http://developer.android.com/sdk/index.html)
地址：http://developer.android.com/sdk/index.html
详细安装见官方链接
5. 配置下环境变量ANDROID_HOME与路径
在 ~/.bashrc, ~/.bash_profile, ~/.profile其中一个里加
```bash
export ANDROID_HOME=~/Android/Sdk
PATH="~/Android/Sdk/tools:~/Android/Sdk/platform-tools:${PATH}"
export PATH
```
即可。
source 一下刚才的文件，然后打入
```bash
echo $ANDROID_HOME
```
这时如果出现路径，说明配置成功！
比如
```
home/eric/Android/Sdk
```
然后再打入
```bash
android
```
这时会出来Android的SDK配置对话框，说明你的android路径配置正确。
6.  创建React Native项目
```bash
react-native init AwesomeProject
cd AwesomeProject
```
7. 运行开发服务器
```bash
react-native start
```
8.  运行程序
```bash
react-native run-android
```

### 问题解决
React Native启动后可能会出现红屏。
就目前我遇到的情况来说都比较容易解决。  
1. 一个问题是开发服务器找不到。
需要晃动手机调出选项，对于不支持晃动的手机，可以通过命令：
```bash
adb shell input keyevent 82  
```
调用。
然后进入Dev Settings => BEBUGGING => Debug server host & port for devices

这时输入你启动react-native start所在的机器的IP与端口即可解决问题。
通常是 IP:8081这样的格式
参考start的提示，一般提示会包含这样的文字
```
Running packager on port 8081
```
这样重新加载，这个问题服务器的问题就没有了。  
2. 热加载的问题。
问题提示是：
```
locales[0] does not appear to be a `module`
```
可以考虑暂时禁用。
方法还是晃动手机调出选项。然后点击Disable Hot Reloading
这样这个问题就解决了。

### 成功
通过解决两个问题， 我就看到了：
```text
Welcome to React Native!
```
的字样.

然后就可以轻松的边修改，边看结果了。

## 结束

React Native的安装与使用总体是很简单的，但是需要有一定的Android和Nodejs的开发经验，然后能理解基本的网络开发原理，否则初次安装还是有比较大的理解困难。
希望本文能帮助更多的初学者快速的安装React Native并速度的使用起来。
