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
git的日志提供了很多模板选择
--pretty=raw 显示树对象等
--pretty=fuller 显示作者和提交者
查看提交可以用git cat-file或者git show
```
#### 复习git diff
```
工作区，暂存区，版本库进行比较：
tagA和tagB:git diff B A
工作区和tagA:git diff A
暂存区和tagA:git diff --cached A
比较工作区和暂存区，git diff
比较暂存区和HEAD,git diff --cached
比较工作区和HEAD，git diff HEAD
1.文件不同版本的差异比较
git diff <commitID1> <commitID2> --<paths>
2.非Git目录/文件的差异比较
git diff <path1><path2>
3.逐词比较，而非默认的逐行比较
git diff --word-diff
```
#### 文件追溯：git blame
```
软件开发过程中当发现Bug并定位到具体代码时，此命令可以追溯是谁什么时候以及什么版本引入此BUG
git blame README.md(文件名)
参数-L n,m查看某几行
git blame -L 6,+5 README.MD
```
#### 二分查找：git bisect
```
这种方式定位BUG是建立在测试的基础之上的，基本情况都是最新版本出现BUG，而交付给客户的版本是正常的。那么出问题肯定是这次版本之间提交代码的问题
1.二分查找
1.工作区切换到已知的'好版本'和'坏版本'的中间的一个版本
2.执行测试，如果问题重现，则将版本库当前版本表记未“坏版本”，如果问题没有重现，则将当前版本标记为“好版本”
3.重复1-2，直至最终找到第一个导致问题出现的版本
这种方法一般不使用
```
