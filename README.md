# weex第一步
## Mac 无法安装weex-toolkit
如果你确定你的不是网络问题，那么很有可能是因为你电脑目录的权限问题；
具体原因不是很清楚，不过weex-toolkit的依赖真不是一般的多，有什么乱七八糟的操作，谁知道呢。
具体解决方法如下：
```shell
sudo chmod -R 777  /Users/userName(自己电脑的用户)
sudo chmod 777 /usr/local/lib/node_modules
```

## 创建项目（weex版本 v1.0.9）
- ### 创建weex项目
```shell
weex create projectName
```
### 项目结构
```
.
├── dist／         存储js编译后的文件
├── doc／          文档文件夹
│ 
├── platforms／    平台
│   ├── android  依赖的android项目
│   └── ios
│ 
├── src／          js文件
├── temp／
├── tools／
├── web／
│ 
├── android.config.json   android配置文件（与platforms对应，会映射到res/xml/app_config.xml中）
├── ios.config.json       ios配置文件（与platforms对应）
│ 
├── start（start.bat）     开启js服务窗口
……
```
- ### 添加平台（platform）
```shell
weex platform add ios
weex platform add android
```
安装模版之后，会在工程目录下增加如下模版目录
```shell
projectName
├── platforms
│   ├── ios
│   └── android
```
- ### 运行（android需要翻墙下载架包）
```shell
weex run ios／android
```
- ### 其他指令
```shell
npm run dev    #开发模式（自动监听编译文件）
npm run serve  #开启js服务
npm run build  #编译js
```
- ### 机子上调试
1. 配置android/ios.config.json中的WeexBundle
2. 开启./start (默认weex run * 的时候自动会开启，建议在start中加入npm run dev，否则需要手动编译文件)
3. 手机端刷新： "菜单"->"refresh"

## ios 配置
### 什么是CocoaPods
每种语言发展到一个阶段，就会出现相应的依赖管理工具，例如 Java 语言的 Maven，nodejs 的 npm。随着 iOS 开发者的增多，业界也出现了为 iOS 程序提供依赖管理的工具，它的名字叫做：CocoaPods。

- ### CocoaPods的安装（需要翻墙）
这是因为ruby的软件源rubygems.org因为使用亚马逊的云服务，被我天朝屏蔽了，需要更新一下ruby的源，过程如下：
```shell
gem sources -l #(查看当前ruby的源)
gem sources --remove https://rubygems.org/ #(移除当前ruby的源)
gem sources -a https://ruby.taobao.org/ #(设置当前ruby的源为我天朝的)
gem sources -l #(再次查看当前ruby的源)
```
如果Terminal输出：
```shell
*** CURRENT SOURCES ***
https://ruby.taobao.org/
```
就证明ruby的软件源已经设置OK了。

接下来安装：
```shell
sudo gem install -n /usr/local/bin cocoapods
```
- ### 下载WeexSDK
切换到Podfile所在目录，运行 pod install，然后运行。
注意：我的是weex v1.0.9, 自动配置是有问题的，需要将Podfile中的ATSDK-Weex改为ATSDK后再次pod install。