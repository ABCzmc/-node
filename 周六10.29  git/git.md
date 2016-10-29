##配置git用户和邮箱
```
$ git config --global user.name "你的github用户名"    
$ git config --global user.email "你的github邮箱"
```
- 不配置用户名和邮箱的话无法提交,因为git不知道你是谁
###查看配置
```
$ git config --list
```
##cd命令
change directory
###git bash下进入文件夹
```
cd e:
```
###cmd命令下进入文件夹
```
e:
```
##clear清屏
##mkdir 创建目录
```
mkdir
```
##初始化git
```
git init
```
##初始化文件并写入内容hello
```
echo hello > index.txt
```
- 一个大于号表示清空并写入 ；>> 表示 追加
##查看当前文件目录下有哪些文件
```
ls
```
##查看file文件里的内容

```
cat file
```

##工作区到暂存区
```
git add
```
##从暂存区删除本次的add
```
git reset HEAD file
```
##历史区覆盖（拉回）工作区
```
git checkout file
```
##暂存区到历史区
```
git commit
```
##将文件加入到暂存区
```
git add file 
git add ./git add -A
```
##提交commit  
```
git commit -m"描述内容"
```
##提交commit？？？
```
git commit
```
##vi控制台
如果进入编辑模式可以i键进入插入模式
- i表示编辑
- 退出esc+:wq

## 查看状态
```
git status
```
##比较代码差异
- 比较工作区和暂存区的区别
```
git diff
```
- 比较工作区和版本库（历史区）的区别
```
git diff master
```
- 比较暂存区和版本库（历史区）的区别
```
git diff --cached
```

##查看版本库信息
```
git log --oneline
```
##撤销回git add的内容 
```
git reset Head "文件名"
```
##撤回文件
- 先从缓存区撤销,缓存区无内容，从历史区域撤销
```
    $ git checkout "文件名"
```
- 有的时候我们希望提交时合并到上一次的提交 git commit --amend
##删除暂存区和工作区
删除暂存区中的内容,并且保证工作区中的内容已经不存在
```
$ git rm "文件名"
```
- 若本地文件存在则不能删除，需要通过-f参数删除

## 仅删除缓存区
```
 git rm --cached "文件名"
```
-恢复某个版本文件
```
$ git checkout commit_id filename 某个文件
```
- 通过版本id恢复
```
$ git reset --hard commit_id
```
## 恢复未来

- 查看当时回滚时的版本
```
$ git reflog
```
10.4 快速版本回退
```
$ git reset --hard HEAD^
$ git reset --hard HEAD~3
```
#查看未来的版本
```
git reflog
```
##分支
- 查看所有分支
```
git branch
```
- 创建分支
```
git branch a
```
- 切换分支
```
git checkout a
```
- 创建并切换分支
```
git checkout -b c
```
- 删除分支

```
git branch -d a 

git branch -D a
```
##合并分支
```
git merge 分支名
```
在主干上拉取一条分支，在分支上进行开发，开发后，在主干上将代码进行合并，主干上目前没有人开发，可以使用快转的方式，将我们的指针直接指向到分支的最新装态 fast-forward
#在github上部署静态页面
需要将特定的内容推送到git-hub上的gh-pages分支上
- 创建一个gh-pages的分支
```
git checkout -b gh-pages
```
- 将代码commit 到这个分支上
```
git add .
git commit -m 'ok'
```
- 连接远程仓库和本地仓库
```
git remote add aaa 地址
```
- 将代码推送到远程仓库上
```
git push aaa gh-pages
```
