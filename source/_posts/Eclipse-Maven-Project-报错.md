---
title: Description Resource Path Location Type An error occurred while filtering
date: 2019-04-18 13:08:01
categories: java
tags:
  - java
  - Eclipse
  - maven
---

Eclipse下`springboot maven`项目,报错如下

`Description Resource Path Location Type An error occurred while filtering`

<!--more-->

解决办法
- 右键项目 `Maven -> update project` 快捷键 `alt+f5`//一般情况下可以解决,如果无效请尝试下一个命令
- `mvn eclipse:clean` //重新导入项目

