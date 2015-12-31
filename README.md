##### 常用命令 1
* git config -l
* git status
* git log
* git log --graph --oneline
* git reflog: 查看所有分支的所有操作记录

##### 常用命令 2
* git init
* git add sample.txt
* git rm --cached sample.txt
* git commit -m "first commit"

##### 常用命令 3
* git remote add origin https://github.com/nickevin/tutorial.git
* git push -u origin master
* git clone https://github.com/nickevin/tutorial.git tutorial2
* git pull origin master

##### 常用命令 4
* git branch: 显示分支列表，前面有 * 的就是现在的分支
* git branch issue1: 创建名为 issue1 的分支
* git checkout issue1: 切换到 issue1 分支
* git merge issue1: 先切换 master 分支，然后把 issue1 分支导入到 master 分支
* git branch -d issue1: 删除 issue1 分支
* git rebase master
* git rebase --continue: rebase 的时候，修改冲突后的提交不是使用 commit 命令，而是执行 rebase 命令指定 --continue 选项。若要取消 rebase，指定 --abort 选项。

##### 常用命令 5
* git fetch
* git pull: fetch + merge
* git commit
* git push

##### 常用命令 6
* git tag -n: 显示标签的列表和注解
* git tag apple
* git log --decorate
* git tag -am "tag 注解" orange
* git tag -d orange

#### 配置 .gitconfig

* alias

     glog = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --
     
    gloglast = log -1 HEAD --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --

##### Git 分支介绍

作为 Git 的分支的用例 ，这里介绍 [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)

这个用例主要分为
* 主分支
* 特性分支
* release 分支
* hotFix 分支

##### 分别使用 4 个种类的分支来进行开发的。
![http://backlogtool.com/git-guide/cn/img/post/stepup/capture_stepup1_5_6.png](http://backlogtool.com/git-guide/cn/img/post/stepup/capture_stepup1_5_6.png)

* 主分支
    
  主分支有两种：master 分支和 develop 分支
  * master: master 分支只负责管理发布的状态。在提交时使用标签记录发布版本号。
  * develop: develop 分支是针对发布的日常开发分支。刚才我们已经讲解过有合并分支的功用。

* 特性分支

  特性分支就是我们在前面讲解过的 topic 分支的功用。
  这个分支是针对新功能的开发，在 bug 修正的时候从 develop 分支分叉出来的。基本上不需要共享特性分支的操作，所以不需要远端控制。完成开发后，把分支合并回 develop 分支后发布。
  
* release 分支

  release 分支是为 release 做准备的。通常会在分支名称的最前面加上 release-。release 前需要在这个分支进行最后的调整，而且为了下一版 release 开发用 develop 分支的上游分支。
  一般的开发是在 develop 分支上进行的，到了可以发布的状态时再创建 release 分支，为 release 做最后的 bug 修正。
  到了可以 release 的状态时，把 release 分支合并到 master 分支，并且在合并提交里添加 release 版本号的标签。
  要导入在 release 分支所作的修改，也要合并回 develop 分支。

* hotFix 分支

  hotFix 分支是在发布的产品需要紧急修正时，从 master 分支创建的分支。通常会在分支名称的最前面加上 hotfix-。
  例如，在 develop 分支上的开发还不完整时，需要紧急修改。这个时候在 develop 分支创建可以发布的版本要花许多的时间，所以最好选择从 master 分支直接创建分支进行修改，然后合并分支。
  修改时创建的 hotFix 分支要合并回 develop 分支。 
  
  
  
  
  
  
