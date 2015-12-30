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
  
  
  
  
  
  
