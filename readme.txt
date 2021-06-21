Git 笔记
1.创建一个文件夹作为git仓库，cd到此目录，Git init：初始化仓库，会创建.git隐藏目录
2.git add <filename>：(需要在仓库文件夹中)，添加文件
3.git commit -m "discription"： 提交所有add过的文件，添加备注
4.git status ：查有哪些当前修改但未提交的文件
5.git diff <filename> ：查看文件修改情况，比较的是当前工作区文件和版本库最新文件
6.git log ：查看提交日志
7.git reset --hard HEAD~X： 回退到上前X个版本
  git reset HEAD <filename>： 将此文件从暂存区回退到工作区
8.git reset --hard 版本号： 回退到该版本号对应版本
9.git reflog :查看每次所提交的命令（方便回退）
10.git 管理的对象是修改，并非文件，每次add都是添加到存储区，提交才会到版本库
11.git checkout --<filename> ：丢弃工作区的修改（也可以认为是从版本库恢复）
12.git rm <filename> :删除文件，该修改添加到存储区，再用git commit 提交删除版本库里的文件
13.git remote add origin git@server-name:path/repo-name.git(或者使用git remote add origin 远程库url)：用于连接一个远程库，origin一般默认指远程库
14.git push -u origin master ：首次提交本地库到远程库（之后再更新远程库无需-u）
15.git clone git@server-name:path/repo-name.git（或者用git clone 远程库url）：用于从远程库拷下一份库，默认只会包括master分支
16.git branch 查看分支
17.git branch -d <branchname>: 删除分支；-D则表示强行删除未合并的分支
18.git branch <branchname>:创建分支
19.git checkout <branchname>:切换到分支
20.git checkout -b <branchname>:创建分支并切换到此分支
21.git merge <branchname>:合并某分支到当前分支
22.git merge --no-ff -m "discription" <branchname>:合并某分支到当前分支，添加备注，且禁用fast forward模式合并，这样会保留修改，分支指针不会与master合并。
23.git log --graph --pretty=oneline --abbrev-commit： 图表形式查看分支合并情况
24.git stash ：保存当前工作现场，可以跳往其他分支操作。
25.git stash pop ：回到工作现场，并删除stash内备份
26.git stash apply：回到工作现场，不删除备份
27.git stash drop ：删除stash中的备份
28.git stash list ：查看stash里备份了哪些现场
    注：转换分支的时候，若当前分支有过修改，则必须commit后或者stash后才可以切换分支，否则文件可能被覆盖
29.git remote -v ：查看远程库信息
   git remote add origin <urlofremote> :关联本地库和远程库
30.git push origin <branchname> :提交分支至远程库，出现错误说明你的分支没远程分支新，需要先pull
31.git pull （<remote> <branchname>）:从远程抓取分支合并，有冲突要先处理冲突，再合并
32.git checkout -b <branchname> origin/branchname :建立本地分支并对应远程分支
33.git branch --set-upstream <branchname> origin/<branchname> : 建立本地分支与远程分支的关联，方便pull
    注：一般多人合作的工作模式如下
        a.首先试图用git push origin <branchname> 推送自己的修改
        b.若推送失败，因远程分支比本地新，需要先git pull试图合并；
        c.如果合并有冲突，则解决冲突，并在本地commit；
        d.没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功。
34.git rebase ：rebase操作可以把本地未push的分叉提交历史整理成直线；
35.git tag <tagname> （commit_id）：新建一个标签默认指向head，或者commit_id
36.git tag -a <tagname> -master "discription" : 为一个标签添加discription 
37 git show <tagname> ：查看标签信息
38.git push origin <tagname> :推送某标签到远程
39.git push origin --tags ：推送所有未推送到远程的本地标签
40.git tag -d <tagname> ：删除本地tag
41.git push origin :refs/tags/<tagname> ：删除远程tag时，先删除本地tag，再用此命令

      
