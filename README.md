# git_new1
这是一个新的仓库

# 什么是git

Git 是分布式版本控制系统     

版本控制系统（version control system 简称VCS）,是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。 (SVN也是一种VCS)

1. 为什么要使用版本控制系统

版本控制工具的功能之一是: *管理不同版本，回退到任何时刻。*

原因二:方便项目协同 (多人开发)
  项目协同本质：代替人工解决部分机械重复的工作，从而大大增加生产力！

1. 什么是分布式
分布式，可以在不同操作系统和不同电脑上去工作

remote 远程服务器 公共仓库   local（每一个人的计算机上面也有一个项目仓库）


# Git的下载与环境配置
https://git-scm.com/ Git官网
https://npm.taobao.org/mirrors/git-for-windows/ 淘宝镜像

# Git环境配置

配置用户名  git config --global user.name 用户名
配置邮箱    git config --global user.email 邮箱 【可作为本地仓库的凭证】

查看配置   
git config --list
git config user.name  查看用户名
git config user.email 查看邮箱

手动配置： C:users/用户/.gitconfig  


## 基础工作流

git init  初始化仓库并产生.git文件夹 (默认隐藏)

.git文件夹非常重要，记录我们的变更内容(objects),分支(refs),日志(logs),脚本(hooks).   若删除该文件夹，则这个仓库也不存在。

> 暂存区意义
   1. 创建索引
   2. 文件分类

U 当前文件未追踪  [untracked file]
A 当前文件已添加到 暂存区 （放入暂存区后可以提交为一个版本） git commit -m "版本描述"
M 当前文件已经修改，与上一个版本不同

git add 文件名称/文件夹   把文件/文件夹中所有文件放入 暂存区 中
    eg : git add index.html  将index.html放入暂存区
         git add . 把当前区间的所有文件放入暂存区
         git add file1 file2   
git reset . 把当前区间内的所有文件从暂存区取出

git reset <file>  从暂存区清空指定文件   . 清空暂存区所有内容


创建文件： .gitignore  配置项目忽略文件/文件夹

git status 查看当前三区状态 （三个区:暂存区 工作目录 本地仓库,最新版本）   

git commit -m <message> 记录提交当前版本的记录 提交变更会有对应日志生成 (-m 信息)

git rm -cached <file> 把指定文件从暂存区移除

git log    用于记录各个版本日志 （查看提交记录，什么人什么时间提交了commit）  
git reflog 用于记录当前版本切换操作

由42位十六进制数组成某次提交的id   前七位就可代表一个版本

## 本地版本库回退

git reset --(soft|mixed|hard) <HEAD~ (num)> | <commit ID> 版本回退
git reset --hard HEAD... 进行版本回退
git reset --hard HEAD^ 回退一个版本 ^^回退两个版本
git reset --hard (commit ID) 切换到指定id的版本， id是一个7位哈希值
git reset --hard HEAD~n 回退n个版本

git checkout -- <file> 撤销工作区修改

## 差异比较

git diff 比较 工作区 和 暂存区
git diff HEAD 比较 工作区 与 本地版本库 中最近一次commit的内容
git diff -- cached 比较 暂存区 与 本地版本库 中最近一次commit的内容
git diff <commit-id> <commit-id> 比较两个commit之间的差异

## 分支

git branch    查看分支(高亮词条代表当前分支)
git branch test 创建新分支test

git checkout 分支名  用于切换分支

git checkout -b 分支名称 模板分支/commit

## 分支合并&处理冲突

> 用于多人协同开发时，合并代码
git merge <branch>  无冲突合并  

git merge test  把当前分支和test分支进行合并 【注：可能存在冲突，需要手动解决】

**git 和 github的区别**
git 类似于快递这个抽象概念，提供服务的工具
github、gitee 类似于 申通 圆通 等具体的快递厂家，基于工具去展示的平台

优点：当某项目有更新时， 用户可以通过git快捷方便的拉取最新版项目。（远程仓库）



# Git 指令

git clone 克隆代码

git push 推送分支到远程

git pull   从远程拉取代码

Pull Request (PR)

**文档查询**
git  help（--help） 展示Git命令大纲及常用命令

git  help  –a  展示Git命令大纲及全部命令列表

git  help <command>  展示具体命令说明手册
 