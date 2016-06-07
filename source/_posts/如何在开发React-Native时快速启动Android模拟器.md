title: 如何在开发React Native时快速启动Android模拟器?
date: 2016-06-07 20:25:39
tags:
---
## 缘起

通常我们配置好了Android的开发环境后都需要打入android命令启动SDK管理器，然后再点到AVD管理器中才能启动一个模拟器。  
或者我们在IDE里启动模拟器。  
这些都不算麻烦，但是偶尔我们也会想通过命令行启动命令。  
一方面习惯于Linux下工作的同学会更加习惯于命令行工作，  
另一方面对于react native的开发的同学来说也需要不断的打开不同的android模拟器进行测试。  
通常开发react native是不需要打开IDE的。

## 解决方法
所以我查找了相关资料，找到了几个解决方法。

### 列出所有的avd
下面的命令列表出所有的avd
```bash
emulator -list-avds
````
### 处理一个avd
一开始我们只有一个avd，所以只要打入如下的命令就可以了。
```bash
emulator @`emulator -list-avds`
```
### 多个AVD的处理
但是实际上我们通常会有2个或者更多的AVD。所以能够必须多处多个AVD方法才是我们真正需要的。相对来说多个AVD的处理办法要复杂一点。  
主要思路就是先列出所有的avd，然后选择一个。
代码如下：
```bash
IFS='  ' read -r -a avds <<< `emulator -list-avds | xargs`   #列出所有的
emulator @${avds[0]}
```
其中avds[0]就是用来选择的。0表示第一个，1表示第二个。根据实际的情况选择你想要的index就可以了。
### 成为一个命令
为了更加方便的使用，我们需要将上面的内容变成是一个命令。  
方法很简单：
1. 将这面的内容放到一个文件
2. 再将这个文件放在PATH变里所在目录

对于我的情况来说，我将它命名成
```
lavd   # 即launch avd
```
然后放在了
```
～/Android/Sdk/tools
```
目录下面，这样只要Android配置好，这个命令就是可用的。  
文件的内容如下：
```bash
#!/usr/bin/env bash
IFS=' '
read -r -a avds <<< `emulator -list-avds | xargs`
echo "show avds"
for avd in "${avds[@]}"; do 
    echo $avd
done
echo "show selected avd: "
echo ${avds[$1]}
echo "running emulator..."
emulator @${avds[$1]}
echo "emulator stop."
```
然后执行
```
chmod +x lavd
emulator -list-avds
./lavd 1   # 或 lavd 1
```
就可以快速启动你的AVD映像了。

效果图如下：

![2016-06-03 21 12 34](https://cloud.githubusercontent.com/assets/131776/15779680/4851fcf0-29d0-11e6-83cf-14d4dba111a1.png)


## 信息来源
本文来自于微信公共号：frontend-guru。
想阅读到更多的关于React Native，移动开发相关，移动互联网，Nodejs，全栈Web开发，开源项目等相关文章，
欢迎搜索公共号：frontend-guru或者扫描下面的图片关注
![](http://res.cloudinary.com/dawjytvkn/image/upload/v1464858605/qrcode_for_gh_6f66da401fef_430_b1rr96.jpg)

同时文章作者也是一个开源爱好者，目前主要关注nodejs开发源。  
主导的项目地址如下：  
https://github.com/calidion/projects  
同时也开通了QQ交流群：   
nodejs开源项目交流QQ群：312685910  
也欢迎有更多的nodejs开发的同学一起加入开源项目中来。
