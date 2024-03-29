# git基本操作
## 从GitHub上克隆代码

`git clone [url]         //从GitHub或者gitee上克隆代码`



`git pull                //从GitHub更新克隆的代码`



## 本地操作GitHub
`git init                //在对应的文件夹git init创建git库`


`git status              //查看项目的当前状态。记住每次修改项目前后最好都查看一下当前状态，可以避免不必要的冲突`



`git branch -m oldName newName               //修改分支名`



`git add .               //将整个项目都存入缓存区`



`git add hello.js        //将某个文件添加到缓存区`



`git commit -m '修改了readme.md文件'          //为本次提交项目的描述信息，但实际上是“记录缓存区的快照”，方便开发失误时能够“回退”`



`git push origin "远程分支"                   //提交到git仓库的当前分支，如果这一步能够正常执行，通常意味着您的项目已经成功提交`



`git remote add [别名] [远程地址]             //给远程库的地址起别名`



`git remote -v                  //查看当前所有远程地址别名`


`git branch -r                  //查看远程端的branch,不带-r表示查看本地的branch`


`git checkout -b xpdev origin/xpdev         //从远程下载branch分支下的代码 第一个xpdev表示存储的文件夹名称，第二个为远程branch的分支名称`


`git branch -D xxx              //从本地删除xxx分支`


`git checkout -b [branch name]              //创建分支的同时切换到该分支上`


`git clean -fd                 //删除untracked文件,连同目录一起删除`


`git push origin [branch name]              //将新分支推送到github上`


```
git reset --hard HEAD^    //回退到上个版本
git reset --hard HEAD~3    //回退到前三次提交之前
git reset --hard commit_id   //回退到指定log_id的版本 通过指令git log 可以查看相应id
```


```
//撤销git reset --hard操作

git reflog              //查看所有的HEAD历史记录
git reset --hard xxxxxx   //回溯到相应版本
```

```
//commit之后，需要撤销本次commit
git reset --soft HEAD^   //仅撤回commit，代码没有改动

//参数的表示
--mixed
不删除工作空间改动代码，撤销commit和add . 操作

--soft
不删除工作空间改动代码，撤销commit,不撤销add . 操作

--hard
删除工作空间改动代码，撤销commit，撤销add . ，恢复到上次commit的状态
```

```
git commit --amend     //commit编写错误，需要修改commit，并直接进入vim编辑器
```

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

> git push 出现 The current branch dev has no upstream branch.的问题

![image](https://user-images.githubusercontent.com/48131905/133013129-6b7efb3a-df9f-4d91-b540-c1c1f5a9cded.png)

问题为没有与远程服务器建立连接
`git push  origin dev -u`

这个意思是把本地dev push到origin的dev -u表示同时建立关联，以后再推送到远程只需git push origin

>git push 出现Everything up-to-date 解决方法

因为你没有git add 和 git commit.或者是需要重新执行

> git push 出现黄色提示

![image](https://user-images.githubusercontent.com/48131905/133574640-2992e455-2161-4720-9c21-2a718d606e83.png)

该问题为远程服务器的代码与本地代码不同步，先pull服务器的代码后在push
`git pull origin master`

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
