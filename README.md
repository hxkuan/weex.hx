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
### - 创建weex项目
```shell
weex create projectName
```
### 项目结构
```
.
├── dist         存储js编译后的文件
├── doc          文档文件夹
│ 
├── platforms    平台
│   ├── android  依赖的android项目
│   └── ios
│ 
├── src          js文件
├── temp
├── tools
├── web
……
```
### - 添加平台（platform）
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
### - 运行（android需要翻墙下载架包）
```shell
weex run ios／android
```