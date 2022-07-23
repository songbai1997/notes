

## 相关链接
[Git教程 廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600)

[官方文档 中文版](https://git-scm.com/book/zh/v2)

[官方文档 英文版](https://git-scm.com/book/en/v2)

## 基础命令

创建git仓库

 `git init`

查看仓库的当前状态 

`git status`

查看提交记录

 `git log [<选项>]`

- `--pretty=oneline` 以简洁格式打印提交记录
- `--graph`命令可以看到分支合并图。

工作区到暂存区 

`git add`

暂存区到仓库 

`git commit <选项>` 

 - `-m` 对提交进行说明

回退版本

仓库到暂存区 `git reset 版本`

- 版本可由版本号和HEAD^形式表示，当前版本：HEAD，上一个版本：HEAD^，上上一个版本：HEAD^^......
- 支持 HEAD~n， HEAD~100 表示回退到往上 100 个版本
- `--hard`
- `--soft`
- `--mixed`


撤销工作区的修改 暂存区到工作区 

`git checkout -- 文件名`

- 暂存区对应的文件没有被提交，则用暂存区的文件替换工作区的文件
- 暂存区没有对应的文件，则用仓库对应的文件替换工作区的文件
- 综上，让这个文件回到最近一次`git add`或`git commit`时的状态

删除工作区的文件 

`git rm 文件名`

查看文件差异 

`git diff`
- `git diff` 不加参数，默认比较工作区与暂存区
- `git diff --cached [<path>...]` 比较暂存区与最新本地版本库（本地库中最近一次 `commit 的内容`）
- `git diff HEAD [<path>...]` 比较工作区与最新本地版本库
- `git diff commit-id [<path>...]` 比较工作区与指定 `commit-id`
- `git diff --cached <commit-id> [<path>...]` 比较暂存区与指定 `commit-id`
- `git diff <commit-id> <commit-id> [<path>...]` 比较两个提交之间的差异


## 分支
创建

`git branch <分支名>`

删除

`git branch [选项] <分支名>`
- `-d` 需要先合并，才能删除
- `-D` 没进行合并的情况下，可强行删除。

查看 

`git branch [<选项>]`

- `-v`：打印分支的详细信息

合并

 `git merge <分支名>` 将参数指定的分支合并到当前分支

切换分支 

`git checkout <分支名>`

`git switch <分支名>`

创建并切换分支

`git checkout -b <分支名>`

`git switch -c <分支名>`

## 标签

查看所有标签 

`git tag`

查看指定标签的详细信息

`git show 标签名`

删除标签

`git tag -d 标签名`

给指定 `commit` 创建标签，默认标签是最新提交的 `commit`

`git tag <标签名> <commit-id>`

给指定的 `commit` 创建带说明的标签

`git tag -a 标签名 -m 说明文字 <commit-id>`

## 远程仓库

克隆远程仓库

`git clone <远程仓库地址>  [<directory>]` 

- `-b --branch <分支名> or <标签名>` 指定克隆的分支，当接收的值为标签时，则克隆默认分支下该标签对应的版本，此时处于 `detached head` 状态 

- `--depth` 指定克隆的版本的历史记录次数

- `directory` 指定克隆到的目录，必须为空目录

添加

`git remote add <远程仓库名> <远程仓库地址>` 远程仓库名是自定义的，一般为origin

删除

`git remote remove/rm <远程仓库名>`

查看

`git remote [<选项>]`
- `-v` 打印详细信息

向远程仓库推送版本

`git push <远程仓库名> <本地仓库分支>:<远程仓库分支>`

从远程仓库拉取最新版本

`git pull <远程仓库名> <远程仓库分支>:<本地仓库分支>`

获取远程仓库的最新版本号

`git fetch <远程仓库名> <远程仓库分支>:<本地仓库分支>`

在本地创建和远程分支对应的分支，本地和远程分支的名称最好一致

`git checkout -b <本地分支> <远程仓库>/<远程分支>`

创建本地分支与远程分支的关联

`git branch --set-upstream-to=远程仓库/远程分支 本地分支`

`git branch --set-upstream 本地分支 远程仓库/远程分支`

## 其他

[`git checkout `指令的几种常用方式](https://segmentfault.com/a/1190000021926763)

[`Git：DETACHED HEAD`的概念](https://www.cnblogs.com/chaiyu2002/p/9417391.html)

`git checkout <版本号> or <标签号>` 分离头指针，使头指针指向指定的提交

[这才是真正的 `Git`——分支合并](https://zhuanlan.zhihu.com/p/192972614)

[`git`合并原理](https://zhuanlan.zhihu.com/p/149287658)

[这才是真正的 `Git`——`Git` 内部原理揭秘！](https://zhuanlan.zhihu.com/p/96631135)

