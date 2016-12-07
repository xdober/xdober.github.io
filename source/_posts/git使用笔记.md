---
title: git使用笔记
date: 2016-11-29 19:17:36
tags: git github
---
## 开始之前：
- 配置自己的user.name和user.email  

## 开始项目：
-  #### 在文件夹里执行：  
`
$ git init
`  

- coding and coding   


- #### 提交版本:   
`
$ git add .
`  
`
$ git commit
`

- #### push到github：  
`
$ git remote add origin master https://github.com/xxxxxx/xxxxx.git
`  
*仅第一次push需要，之后只需要：*  
`
$ git push
`
- #### 查看项目状态：
`
git status
`  

## 分支管理：
- #### 创建一个分支：
`
$ git branch branchname
`

- #### 切换到分支：
`
$ git checkout branchname
`

- #### 创建并切换到分支：
`
$ git checkout -b branchname
`
- #### 查看当前分支：
`
$ git branch
`

- #### 提交到当前分支：
`
$ git add .`  
`
$ git commit
`

- #### push到github：
`
$ git push origin branchname
`  
*如果github的仓库中不存在这个分支，会自动创建*  

- #### 重命名分支：
`
$ git branch -m branchname newname
`  
- #### 删除分支(未合并的分支)：  
`
$ git branch -D branchname
`  
- #### 删除分支(已合并)：  
`
$ git branch -d branchname  
`
- #### 删除远程分支：  
`
$ git push origin :branchname
`
