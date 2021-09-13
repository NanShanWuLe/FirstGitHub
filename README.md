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


`git branch -r`

查看远程端的branch,不带-r表示查看本地的branch

`git checkout -b xpdev origin/xpdev`

从远程下载branch分支下的代码 第一个xpdev表示存储的文件夹名称，第二个为远程branch的分支名称

`git branch -D xxx`

从本地删除xxx分支

## 更新代码到GitHub  
```
git init                  //初始化仓库  
git add .(文件名)          //添加文件到本地  
git commit -m "备注"       //添加文件描述信息  
git pull origin master     //把本地仓库的变化连接到远程仓库master分支
git push -u origin master  //把本地仓库的文件推送到远程仓库master分支
```
### 小Tips  
<font color="red">进入Please enter a commit message to explain why this merge is necessary</font>  
1.按键盘字母 i 进入insert模式  
2.修改最上面那行黄色合并信息,可以不修改  
3.按键盘左上角"Esc"  
4.输入":wq",注意是冒号+wq,按回车键即可  

![image](https://user-images.githubusercontent.com/48131905/133013129-6b7efb3a-df9f-4d91-b540-c1c1f5a9cded.png)
问题为没有与远程服务器建立连接
`git push  origin dev -u`

这个意思是把本地dev push到origin的dev -u表示同时建立关联，以后再推送到远程只需git push origin

### xp Gerrit
`git commit -s        //提交更新说明`

格式为：
```
[ Modify       ] xpSettings
[ Project      ] D55/D22/D21 | E28
[ Module       ] XUIService
[ Description  ] null
[ Reference    ] http://
[ Company      ] XiaoPeng SH
[ Team         ] 国际化应用组
```
```git log                           //查看提交日志
git push origin HEAD:refs/for/xpdev  //正式提交代码 
git pull --rebase                    //如果push失败，应先从gerrit上重新pull代码
git reset HEAD^                      //删除上一次操作
```
