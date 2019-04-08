---
title: mac下配置开发环境
date: 2019-04-06 13:33:21
tags:
    - mac
    - java
    - vscode
    - aria2
---
## 开启 hidpi (黑苹果)

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/athlonreg/one-key-hidpi/master/hidpi.sh)"
```


## 显示隐藏文件

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```

## 关闭隐藏文件显示

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder
```

## 锁定拓展坞
```bash
defaults write com.apple.dock contents-immutable -boolean YES; killall Dock
```

## 解锁拓展坞
```bash
defaults write com.apple.Dock contents-immutable -bool no; killall Dock
```

可通过自动操作->应用程序->运行 shell 脚本,创建程序保存起来

## 下载 Java 并环境变量
[Java 官网](https://www.oracle.com/technetwork/java/javase/downloads/index.html)

```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/Home
export PATH=$PATH:$JAVA_HOME/bin
```

``


## 下载 maven 并环境变量
[maven 官网](http://maven.apache.org/download.cgi)

```bash
export MAVEN_HOME=/Users/ex/Documents/apache-maven-3.6.0
export PATH=$PATH:$MAVEN_HOME/bin
```

``

## maven 使用阿里云的镜像
[阿里云镜像官网](https://maven.aliyun.com/)
```xml
<mirror>
    <id>aliyunmaven</id>
    <mirrorOf>*</mirrorOf>
    <name>阿里云公共仓库</name>
    <url>https://maven.aliyun.com/repository/public</url>
</mirror>
```

## 下载 vscode 配置常用插件
[vscode 官网](https://code.visualstudio.com/)
### 插件
- Chinese (Simplified) Language Pack for Visual Studio Code
- Java Extension Pack 
- One Dark Pro
- vscode-icons
- Auto Rename Tag
- 其他

在环境变量中已经配置了 `JAVA_HOME` `vscode` 中就不需要配置 `java.home` 了

## 安装 下载工具

安装`aria2`

`brew install aria2`

创建配置文件

```bash
cd ~
mkdir .aria2
cd .aria2
touch aria2.conf
touch aria2.session
```

aria2.conf 内容如下 
```conf
## '#'开头为注释内容, 选项都有相应的注释说明, 根据需要修改 ##
## 被注释的选项填写的是默认值, 建议在需要修改时再取消注释  ##

## 文件保存相关 ##

# 文件的保存路径(可使用绝对路径或相对路径), 默认: 当前启动位置
dir=/Users/ex/Downloads
# 启用磁盘缓存, 0为禁用缓存, 需1.16以上版本, 默认:16M
disk-cache=32M
# 文件预分配方式, 能有效降低磁盘碎片, 默认:prealloc
# 预分配所需时间: none < falloc ? trunc < prealloc
# falloc和trunc则需要文件系统和内核支持
# NTFS建议使用falloc, EXT3/4建议trunc, MAC 下需要注释此项
# file-allocation=falloc
# 断点续传
continue=true

## 下载连接相关 ##

# 最大同时下载任务数, 运行时可修改, 默认:5
max-concurrent-downloads=1
# 同一服务器连接数, 添加时可指定, 默认:1
max-connection-per-server=5
# 最小文件分片大小, 添加时可指定, 取值范围1M -1024M, 默认:20M
# 假定size=10M, 文件为20MiB 则使用两个来源下载; 文件为15MiB 则使用一个来源下载
min-split-size=10M
# 单个任务最大线程数, 添加时可指定, 默认:5
split=5
# 整体下载速度限制, 运行时可修改, 默认:0
#max-overall-download-limit=0
# 单个任务下载速度限制, 默认:0
#max-download-limit=0
# 整体上传速度限制, 运行时可修改, 默认:0
#max-overall-upload-limit=0
# 单个任务上传速度限制, 默认:0
#max-upload-limit=0
# 禁用IPv6, 默认:false
disable-ipv6=true

## 进度保存相关 ##

# 从会话文件中读取下载任务 这里的 ex 是我的用户名
input-file=/Users/ex/.aria2/aria2.session
# 在Aria2退出时保存`错误/未完成`的下载任务到会话文件
save-session=/Users/ex/.aria2/aria2.session
# 定时保存会话, 0为退出时才保存, 需1.16.1以上版本, 默认:0
save-session-interval=60

## RPC相关设置 ##

# 启用RPC, 默认:false
enable-rpc=true
# 允许所有来源, 默认:false
rpc-allow-origin-all=true
# 允许非外部访问, 默认:false
rpc-listen-all=true
# 事件轮询方式, 取值:[epoll, kqueue, port, poll, select], 不同系统默认值不同
#event-poll=select
# RPC监听端口, 端口被占用时可以修改, 默认:6800
#rpc-listen-port=6800

## BT/PT下载相关 ##

# 当下载的是一个种子(以.torrent结尾)时, 自动开始BT任务, 默认:true
#follow-torrent=true
# BT监听端口, 当端口被屏蔽时使用, 默认:6881-6999
listen-port=51413
# 单个种子最大连接数, 默认:55
#bt-max-peers=55
# 打开DHT功能, PT需要禁用, 默认:true
enable-dht=false
# 打开IPv6 DHT功能, PT需要禁用
#enable-dht6=false
# DHT网络监听端口, 默认:6881-6999
#dht-listen-port=6881-6999
# 本地节点查找, PT需要禁用, 默认:false
#bt-enable-lpd=false
# 种子交换, PT需要禁用, 默认:true
enable-peer-exchange=false
# 每个种子限速, 对少种的PT很有用, 默认:50K
#bt-request-peer-speed-limit=50K
# 客户端伪装, PT需要
peer-id-prefix=-TR2770-
user-agent=Transmission/2.77
# 当种子的分享率达到这个数时, 自动停止做种, 0为一直做种, 默认:1.0
seed-ratio=0
# 强制保存会话, 话即使任务已经完成, 默认:false
# 较新的版本开启后会在任务完成后依然保留.aria2文件
#force-save=false
# BT校验相关, 默认:true
#bt-hash-check-seed=true
# 继续之前的BT任务时, 无需再次校验, 默认:false
bt-seed-unverified=true
# 保存磁力链接元数据为种子文件(.torrent文件), 默认:false
bt-save-metadata=true
```

新建一个`run_aria2.sh`
```bash
#!/bin/sh#!/bin/sh
aria2c --conf-path="/Users/ex/.aria2/aria2.conf" -D
```

设置权限
`sudo chmod 777 run_aria2.sh`
系统偏好设置->用户与群组->登陆项-点击+把刚才创建的`run_aria2.sh`加进去

Chrome 浏览器安装`Aria2 for Chrome`

本来准备使用自动操作的,但是不清楚为什么 aria2c 一直提示命令找不到
