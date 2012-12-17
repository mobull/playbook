请确认您已经安装并设置好 Git，如果没有，请参照 [GitHub 帮助](https://help.github.com/articles/set-up-git) 进行操作。

本文主要参考 [GitHub 的协作模式](http://scottchacon.com/2011/08/31/github-flow.html)。这份参考资料极为重要，请尽早阅读。

## 必须遵守的原则

* 为了确保 master 始终处于可部署状态（所有测试通过）。所有功能开发都需要新建分支，且分支命名要确清晰明，能清楚地阐明分支上所开发的功能。
* 每一次的 commit 都应足够小，以确保一句话 commit message 能将所做的修改描述清楚；如果一句话无法进行准确描述（如前端工程里常常会出现较大修改），应在 commit message 里提供多行备注。
* 当某一分支需要合并到 master 分支时，请发送 pull request 到主分支。
* 将 pull request 并入 master 分支前，需要对代码进行同侪审阅（peer review)。如果发现问题，应通知原作者进行修改，完成后再并入 master 分支。
* 为了让分支间的历史关系清晰明了，分支间的合并（`merge`）请使用 `--no-ff` 参数，以避免出现 fast forward。您也可以在终端里使用 `git config --global merge.ff false` 命令，将 --no-ff 设置成默认参数（设置后则不需要在每次使用 `merge` 命令的时候带上 `--no-ff` 参数）。
* 配合使用 `fetch` 与 `rebase` 命令更新本地分支，以获取远端上游（origin）分支中的代码更新，不应使用 `pull` 命令（加 `--rebase` 参数除外）。
* 不要 `rebase` 非映射关系的分支。

如遇任何问题，或有好的建议，请在 Campfire 上讨论。有价值的部分，整理后添加到 Wiki。

## 日常使用实例

### 克隆仓库

访问项目首页，找到项目 `clone` 地址， 如： `git@github.com:mobull/MDM.git`。

打开你喜欢的终端程序（如：Mac 下的 [iTerm2](www.iterm2.com)），输入以下命令克隆远程仓库：

    $ cd ~/Projects                                                  # 进入你用来存放项目的路径
    $ git clone git@github.com:mobull/MDM.git
    Cloning into 'MDM'...
    remote: Counting objects: 521, done.
    remote: Compressing objects: 100% (243/243), done.
    remote: Total 521 (delta 245), reused 512 (delta 236)
    Receiving objects: 100% (521/521), 81.93 KiB | 40 KiB/s, done.
    Resolving deltas: 100% (245/245), done.

### 获取上游仓库的更新

从远端（remote）克隆过来的项目会自动把克隆地址设置名为 origin 的远端：

    $ cd ~/Project/MDM                                               # 进入项目路径
    $ git remote -v                                                  # 列出所有的 remotes
    origin	git@github.com:mobull/MDM.git (fetch)
    origin	git@github.com:mobull/MDM.git (push)

此时，远端分支并没有同步进你的本地仓库，运行以下命令获取远端分支数据：

    $ git fetch origin                                               # 获取名为 origin 的远端数据
    From github.com:mobull/MDM
    * [new branch]      master     -> origin/master
    * [new branch]      tenant-info -> origin/tenant-info

实际上，系统为您创建了几个隐蔽的本地分支，这些分支被命名为“remotes/#{远端名}/#{远端仓库里的分支名}”，使用以下命令可以查看本地所有分支：

    $ git branch -a
    * master
      tenant-info
      remotes/origin/master
      remotes/origin/tenant-info

要把远端的更新应用到本地工作分支，使用以下命令：

    $ git rebase origin/master                                       # 可以省略“remotes/”
    Current branch master is up to date.

如果 rebase 出现冲突，则按照屏幕提示解决冲突后，继续完成 rebase 操作。

注意，rebase 应该发生在有映射关系的分支上（如：master 与 origin/master，tenant-info 与 origin/master），请不要 `rebase` 非映射关系的分支。

更多关于使用 fork 协作的信息，请参考 [GitHub 帮助](https://help.github.com/articles/fork-a-repo)。

## 其他资料与延展阅读

（本准则虽未实际采用，但其仍具有很高的参考价值。）

* http://nvie.com/posts/a-successful-git-branching-model/
* http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/
* http://www.eqqon.com/index.php/Collaborative_Github_Workflow
