# git基本操作
## 从GitHub上克隆代码

`git clone [url]`

从GitHub或者gitee上克隆代码

`git pull`

从GitHub更新克隆的代码

## 本地操作GitHub
`git init`

在对应的文件夹git init创建git库

`git status`

查看项目的当前状态。记住每次修改项目前后最好都查看一下当前状态，可以避免不必要的冲突

`git add .`

将整个项目都存入缓存区

`git add hello.js`

将某个文件添加到缓存区

`git commit -m '修改了readme.md文件'`

为本次提交项目的描述信息，但实际上是“记录缓存区的快照”，方便开发失误时能够“回退”

`git push`

提交到git仓库的当前分支，如果这一步能够正常执行，通常意味着您的项目已经成功提交

`git remote add [别名] [远程地址]`

给远程库的地址起别名

`git remote -v`

查看当前所有远程地址别名
