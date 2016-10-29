##配置git用户和邮箱(只需要配置一次)
```
$ git config --global user.name "你的github用户名"    
$ git config --global user.email "你的github邮箱"
```
- 不配置用户名和邮箱的话无法提交,因为git不知道你是谁
##查看配置
```
$ git config --list
```
##cd命令
change directory
##git bash下进入文件夹
```
cd e:
```
##cmd命令下进入文件夹
```
e:
```
##clear清屏
##mkdir 创建目录
```
mkdir <file>
```
##初始化git(找到需要git所管理的文件夹,初始化)
```
git init
```
##初始化文件并写入内容'hello'
```
echo hello > index.txt
```
- 一个大于号表示清空并写入内容 ；>> 表示 追加内容
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
- 比较(工作区)和(暂存区)的区别
```
git diff
```
- 比较[工作区]和 [版本库（历史区）]的区别
```
git diff master
```
- 比较[暂存区]和[版本库（历史区）]的区别
```
git diff --cached
```

##查看版本库信息
```
git log --oneline
```
##撤销回本次git add的内容 
```
git reset Head <file>
```
##撤回文件
- 先从缓存区撤销,缓存区无内容，从历史区域撤销
```
    $ git checkout <file>
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
## 快速版本回退
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
git branch <分支名>
```
- 切换分支
```
git checkout <分支名>
```
- 创建并切换分支
```
git checkout -b <分支名>
```
- 删除分支
在分支上开发提交了代码，需要切换到主干上，在主干上合并，最后到主干上就可以把分支删除

```
git branch -d <分支名> 

git branch -D <分支名>
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
    - 查看链接版本信息
    ```
    git remote -v
    ```
- 将代码推送到远程仓库上
```
git push aaa gh-pages
```
{eg：
git init
git remote add origin https://github.com/ABCzmc/-node.git
git commit -m'初识node1'
git checkout -b gh-node
git add .
git commit -m 'git1'
git push aaa gh-pages
git push origin gh-node
}
##合并分支产生冲突
- 在主干的某个版本上进行分支开发，在分支上开发1.txt这个文件(drag),在主干上也开发1.txt(limit)，此时需要手动解决按照下面例子操作
##从工作区中提交到历史区(首次提交不可以这样写)
```
git commit -a -m 'drag'
```
{eg：
  525  git init
  526  touch index.txt
  527  git commit -a -m 'wirte ok'
  528  git add .
  529  git commit 
  530  git commit 
  531  git log
  532  git commit -m''
  533  git commit -m' '
  534  clear
  535  git log
  536  cat index.txt 
  537  echo drag > index.txt 
  538  git commit -a -m 'write drag'
  539  git log
  540  git checkout -b dev
  541  echo slider >> index.txt 
  542  cat index.txt 
  543  git commit -a -m'write slider'
  544  git checkout master
  545  git log
  546  cat index.txt 
  547  echo menu >> index.txt 
  548  git commit -a -m 'write menu'
  549  git merge dev
  550  git commit -a -m 'menu + slider'
  551  cat index.txt 
  552  git log
}
- 打印族谱（显示操作结构）
```
 git log -- graph --oneline --decorate
```
- git cherry-pick
- git rebase 变基
##创建忽略文件
将项目提交到github上，需要在github上创建一个空的仓库
##添加远程仓库的连接
```
git remote add 连接名字 地址
```
##upstream
- -u 下次提交或者拉取代码可以直接git push 或者git pull
##fork
把别人的项目原封不动的拷贝一份，pull文件

##leader
.touch gitignore
git init
git add .
git commmit -m 'first'
git remote add origin https://github.com/zhufengzhufeng/zhufeng_homework9
(git remote -v)
git push origin master
##组长
https://github.com/zhufengzhufeng/zhufeng_homework9
=》fork
git clone https://github.com/wakeupmypig
cd 
在克隆的文件夹下 根目录 增加文件自己组员的信息
git add . 
git commmit -m '0 team'
git push origin master（组长自己的仓库）
new pull request  ---->发送

自己的仓库 setting->callorbrators ->添加贡献者 仓库地址发给组员
【组长再次提交代码给老师的过程：
1.将自己租的仓库更新到最新状态
2.建立老师仓库的联系
3.拉去老师最新代码
4.提交到自己的仓库
pull request--》 new pull request--》title】
##组员
git clone 组长仓库地址 zuyuan
（进入文件夹找到自己组，自己的作业要添加）
cd zuyuan 
git add.
git commit -m 'zuyuan '
git pull origin master
git push origin master(自己的仓库名账号)


新建仓库
##组长给组员添加权限
setting->callorbrators ->添加贡献者
##组员提交代码
- 先将代码clone到本地 ，创建自己的文件夹 
- 提交之前需要拉去组长的最新代码
```
git pull origin master
```
- 提交到组长的仓库
git 








