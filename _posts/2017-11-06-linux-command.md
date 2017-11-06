---
layout: post
title: "常用Linux命令行"
categories: linux
---
1. 删除端口为port的进程process
```c
//比如说删除8000端口对应的进程
lsof -i tcp:8000
kill -9 [PID]
```