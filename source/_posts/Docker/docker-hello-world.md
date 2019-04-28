---
title: Docker-hello-world
date: 2019-04-28 12:49:43
categories: docker
tags:
    - docker
---

## 系统环境
`windows10 ltsc`

## 安装 `Docker`

[Docker下载]https://hub.docker.com/editions/community/docker-ce-desktop-windows)

安装完毕后再状态栏可以看到小鲸鱼的图标

## Docker Hello World

### 检查是否正常运行
`docker --version` 
正确输出`Docker version 18.09.2, build 6247962` 版本号,安装完毕

### 配置阿里云镜像

右键状态栏小鲸鱼图标-->`Settings`-->`Daemon`-->`Registy Mirrors` 输入 `https://juultkrz.mirror.aliyuncs.com` 

![Settings.png](https://s2.ax1x.com/2019/04/28/EMbUfO.png)
![Registy Mirrors.png](https://s2.ax1x.com/2019/04/28/EMbdpD.png)

### 修改默认存放位置

`Docker` 在 `windows` 下默认存放位置是 `C:\Users\Public\Documents\Hyper-V\Virtual Hard Disks\MobyLinuxVM.vhdx`  若需要修改的话.可移动到其他盘符

![Advanced.png](https://s2.ax1x.com/2019/04/28/EMbw1e.png)

### 拉取镜像

`docker pull hello-world`

运行结果如下

```
Using default tag: latest
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:92695bc579f31df7a63da6922075d0666e565ceccad16b59c3374d2cf4e8e50e
Status: Downloaded newer image for hello-world:latest

```

### 运行镜像
`docker run hello-world`

运行结果
```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

到这里,已经成功运行了第一个`docker image`
