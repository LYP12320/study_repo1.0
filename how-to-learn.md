﻿# 系统性技能学习

## git学习链接

+ [廖雪峰老师的Git教程][3]
+ [Git简明指南][4]
+ [图解Git][5]
+ [手把手教你最简单的开源项目托管GitHub入门教程][6]
+ [Github 简明教程][7]
+ [慕课网--版本控制入门，搬进Github][8]
+ [如何高效利用GitHub][9]
+ [专为设计师而写的GitHub快速入门教程][10]
+ [图形化git分支教学][11]
+ ......

  [3]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/
  [4]: http://www.bootcss.com/p/git-guide/
  [5]: http://marklodato.github.io/visual-git-guide/index-zh-cn.html
  [6]: http://jingyan.baidu.com/article/f7ff0bfc7181492e27bb1360.html
  [7]: http://www.runoob.com/w3cnote/git-guide.html
  [8]: http://www.imooc.com/learn/390
  [9]: http://www.yangzhiping.com/tech/github.html
  [10]: http://www.ui.cn/detail/20957.html
  [11]:http://pcottle.github.io/learnGitBranching/

## markdown语法与规范

+ [Markdown——入门指南](http://www.jianshu.com/p/1e402922ee32/)
+ [GitHub上README写法暨markdown语法解读](http://www.tuicool.com/articles/zIJrEjn)



第一次：
建仓库与提交：
初始化一个Git仓库，使用git init命令。

添加文件到Git仓库，分两步：

使用命令git add <file>，注意，可反复多次使用，添加多个文件；
使用命令git commit -m <message>，完成。

git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。


为什么Git添加文件需要add，commit一共两步呢？
   因为commit可以一次提交很多文件，所以你可以多次add不同的文件





第二次：
要随时掌握工作区的状态，使用git status命令。

如果git status告诉你有文件被修改过，用git diff可以查看修改内容。





第三次：
版本回退：
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。

穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。




第四次：
工作区与暂存区
工作区既是我们所看到的被操作文件所在目录结构
暂存区则是隐藏与工作区的.git 文件。被称为stage或者index
弄清工作区与暂存区对理解每次提交（为什么分两个步骤--先add,再commit）有很大的助益。



第五次：
管理修改：
git 跟踪的实修改而非文件。每次修改必须先用add加入暂存区，才能用cmomit提交到master里。
否则文件的修改就不能被提交。master中的文件则还是原版。



第六次
撤回修改：
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库

第七次
删除文件：
1.正确的删除：先删除工作区文件，而后使用rm命令删除版本库文件，最后使用commit提交。
2.误删：可以使用git checkout -- file  命令从版本库中恢复文件。（前提是版本库中没有被删。）



第八次
本地仓库与远程仓库的关联和推送：
1、关联
       *  建仓：  可以先在github上建立空仓，然后在本地git建立仓库，反过来也可以。
       *  关联：   clone 或者 remote add origin

2、推送
       *  推送前一定先pull,如果pull后仍然不能push成功，那就使用git pull --rebase origin master命令再pull一次。
       
       *  pull完成后，可以使用push 推送了。如果出现GH007，那就请在github的个人设置邮箱里面取消（把邮箱设为私有private）这个选项。
      
       *  取消完成后，就可以push了。
              


第九次
创建、合并和删除分支：
查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>
   创建分支后：直接在分支上对文件进行操作，然后推送到远程分支即可！（git push origin branch name）

合并某分支到当前分支：git merge <name>
 切记：要想合并分支到主分支，必须先回到主分支！

删除分支：git branch -d <name>

删除远程分支： git push origin -d <branch name>



第十次：
解决冲突：
当分支无法与主干合并时（对分支和主干都做了修改，且不相同），应该先查看文件内容（cat file），然后手动修改为一致。再将文件提交（add\commit）,合并就完成了。
用git log --graph命令可以看到分支历史

第十一次：

分之管理：
Git分支十分强大，在团队开发中应该充分应用。

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了


第十二次：
BUG修复术：
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场

回到工作现场可以使用 git stash pop 这样不会保留stash。还可以使用 git stash apply恢复，但这样的方式下stash不会删除。

第十三次
开发新功能：
开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。


第十四次：
多人协作：
并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？

master分支是主分支，因此要时刻与远程同步；

dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

总之，就是在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定！


多人协作的工作模式通常是这样：

首先，可以试图用git push origin <branch-name>推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。


小结
查看远程库信息，使用git remote -v；

本地新建的分支如果不推送到远程，对其他人就是不可见的；

从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。


第十五次
创建标签：
命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id（git tag tagname commit id）；

命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；

命令git tag可以查看所有标签。


操作标签：
命令git push origin <tagname>可以推送一个本地标签；

命令git push origin --tags可以推送全部未推送过的本地标签；

命令git tag -d <tagname>可以删除一个本地标签；

命令git push origin :refs/tags/<tagname>可以删除一个远程标签。第一次：
建仓库与提交：
初始化一个Git仓库，使用git init命令。

添加文件到Git仓库，分两步：

使用命令git add <file>，注意，可反复多次使用，添加多个文件；
使用命令git commit -m <message>，完成。

git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。


为什么Git添加文件需要add，commit一共两步呢？
   因为commit可以一次提交很多文件，所以你可以多次add不同的文件





第二次：
要随时掌握工作区的状态，使用git status命令。

如果git status告诉你有文件被修改过，用git diff可以查看修改内容。





第三次：
版本回退：
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。

穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。




第四次：
工作区与暂存区
工作区既是我们所看到的被操作文件所在目录结构
暂存区则是隐藏与工作区的.git 文件。被称为stage或者index
弄清工作区与暂存区对理解每次提交（为什么分两个步骤--先add,再commit）有很大的助益。



第五次：
管理修改：
git 跟踪的实修改而非文件。每次修改必须先用add加入暂存区，才能用cmomit提交到master里。
否则文件的修改就不能被提交。master中的文件则还是原版。



第六次
撤回修改：
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库

第七次
删除文件：
1.正确的删除：先删除工作区文件，而后使用rm命令删除版本库文件，最后使用commit提交。
2.误删：可以使用git checkout -- file  命令从版本库中恢复文件。（前提是版本库中没有被删。）



第八次
本地仓库与远程仓库的关联和推送：
1、关联
       *  建仓：  可以先在github上建立空仓，然后在本地git建立仓库，反过来也可以。
       *  关联：   clone 或者 remote add origin

2、推送
       *  推送前一定先pull,如果pull后仍然不能push成功，那就使用git pull --rebase origin master命令再pull一次。
       
       *  pull完成后，可以使用push 推送了。如果出现GH007，那就请在github的个人设置邮箱里面取消（把邮箱设为私有private）这个选项。
      
       *  取消完成后，就可以push了。
              


第九次
创建、合并和删除分支：
查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>
   创建分支后：直接在分支上对文件进行操作，然后推送到远程分支即可！（git push origin branch name）

合并某分支到当前分支：git merge <name>
 切记：要想合并分支到主分支，必须先回到主分支！

删除分支：git branch -d <name>

删除远程分支： git push origin -d <branch name>



第十次：
解决冲突：
当分支无法与主干合并时（对分支和主干都做了修改，且不相同），应该先查看文件内容（cat file），然后手动修改为一致。再将文件提交（add\commit）,合并就完成了。
用git log --graph命令可以看到分支历史

第十一次：

分之管理：
Git分支十分强大，在团队开发中应该充分应用。

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了


第十二次：
BUG修复术：
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场

回到工作现场可以使用 git stash pop 这样不会保留stash。还可以使用 git stash apply恢复，但这样的方式下stash不会删除。

第十三次
开发新功能：
开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。


第十四次：
多人协作：
并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？

master分支是主分支，因此要时刻与远程同步；

dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

总之，就是在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定！


多人协作的工作模式通常是这样：

首先，可以试图用git push origin <branch-name>推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。


小结
查看远程库信息，使用git remote -v；

本地新建的分支如果不推送到远程，对其他人就是不可见的；

从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。


第十五次
创建标签：
命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id（git tag tagname commit id）；

命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；

命令git tag可以查看所有标签。


操作标签：
命令git push origin <tagname>可以推送一个本地标签；

命令git push origin --tags可以推送全部未推送过的本地标签；

命令git tag -d <tagname>可以删除一个本地标签；

命令git push origin :refs/tags/<tagname>可以删除一个远程标签。