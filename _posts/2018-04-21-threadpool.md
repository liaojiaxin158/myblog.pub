---
layout: post
title: 学习git命令行工具
---
#### 版本表示法
```
git rev-parse是git的底层命令，很多常用命令都是调用的底层命令
显示分支
git rev-parse --symbolic --branches   == git branch
jagent@ubuntu:~/xin/mytest$ git rev-parse --symbolic --branches
master
git rev-parse --symbolic --tags  == git tag
jagent@ubuntu:~/xin/mytest$ git rev-parse --symbolic --tags
v1
v2
git rev-parse --symbolic --glob=refs/* 目前没找到对应的命令
jagent@ubuntu:~/xin/mytest$ git rev-parse --symbolic --glob=refs/*
refs/heads/master
refs/remotes/origin/HEAD
refs/remotes/origin/master
refs/tags/v1
refs/tags/v2

```
#### 版本范围表示法;git rev-list
```
主要帮助研究git的各种版本范围的语法（略）
```
#### 浏览日志：git log
```
举例说明
1.git log --oneline 
查看当前所有的历史提交（不加参数 默认是HEAD）
2.分支图显示
git log --graph --oneline
可以显示字符界面的提交关系图
3.显示最近的几条日志
git log -3 --pretty=oneline
-n参数显示最近几条
4.显示每次提交的具体改动
git log -p -1
参数-p -n
5.显示每次提交的变更概要
有时候-p参数输出显得非常冗余指只想看改动哪些文件有改动，而不显示内容的话用参数 --stat
git log --stat --oneline 
6.定制输出 
```


