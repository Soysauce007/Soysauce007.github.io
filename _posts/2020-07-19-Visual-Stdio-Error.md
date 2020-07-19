---
layout:     post
title: "无法下载许可证,请检查你的网络连接或代理设置"
subtitle:   " \"Visual Studio许可证过期\""
date: 2020-07-19 20:15:01 +0800
author:   "Yummy"
category: Visual Studio
catalog: true
tags:
    - Yummy
    - Visual Studio 2017 
---

本文参考:

[打开Visual Studio 提示"无法下载许可证,请检查你的网络连接或代理设置](https://www.cnblogs.com/bibi-feiniaoyuan/p/13131644.html)

[Visual Studio 2015 社区版提示过期](https://jingyan.baidu.com/article/0bc808fc58e5b11bd485b9a9.html)

# 内容介绍

![Visual Studio Error](https://img2020.cnblogs.com/blog/994461/202006/994461-20200615161706888-1336774199.png)

恰巧发现Visual Studio 2017过期了，于是百度一番，成功找到解决方案。为方便以后自己仍然遇到这个问题，所以记录下来。

百度经验里给的解决方法是：重新登陆Vs账号，进行检查更新的许可证即可。经过一番测试发现并不能。

所以有幸查到第二篇博主贴出的方法：

- 登录成功后点击检查更新的许可证时,提示"无法下载许可证,请检查你的网络连接或代理设置"。
- 只需找到目录C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE的DDConfigCA.exe（程序路径决定于自己安装时选择的，找不到就全局搜索一下），使用管理员运行该程序。
- 重新打开Visual Stdio 2017。

做个记录，方便以后查阅。