在开始前，你需要安装并设置好 Git。

## 必须遵守的原则

* 开始工作前，请 fork 一个你要参与的项目。您所有的代码提交都需要在自己的 fork 里完成，当可以合并到主仓库时，请发送 pull request。
* 将 pull request 并入主仓库前，需要对代码进行同侪审阅（peer review)。如果发现问题，应通知原作者进行修改，完成后再并入主仓库。
* 确保 master 分支所有测试全部通过，且处于可部署状态。所有功能开发都需要新建分支，且分支命名要确清晰明，能清楚地阐明分支上所开发的功能。
* 为了让分支间的历史关系清晰明了，分支间的合并（`merge`）请使用 `--no-ff` 参数，以避免出现 fast forward。您也可以在终端里使用 `git config --global merge.ff false` 命令，将 --no-ff 设置成默认参数（设置后则不需要在每次使用 `merge` 命令的时候带上 `--no-ff` 参数）。
* 配合使用 `fetch` 与 `rebase` 命令更新本地分支，以获取远端上游（upstream）分支中的代码更新，不应使用 `pull` 命令（加 `--rebase` 参数除外）。
* 每一次的 commit 都应足够小，以确保一句话 commit message 能将所做的修改描述清楚。

如遇任何问题，或有好的建议，请在 Campfire 上讨论。有价值的部分，整理后添加到 Wiki。

## 日常使用实例

### Fork 项目

第一次参与项目，请在 GitHub 项目页面点击 fork，您将会跳转到 fork 项目。找到项目 `clone` 地址， 如： `git@github.com:mobull/MDM.git`。

### 克隆仓库

打开你喜欢的终端程序（如：Mac 下的 [iTerm2](www.iterm2.com)），输入一下命令克隆远程仓库：

    $ cd ~/Projects                                                  # 进入你用来存放项目的路径
    $ git clone git@github.com:mobull/MDM.git
    Cloning into 'MDM'...
    remote: Counting objects: 521, done.
    remote: Compressing objects: 100% (243/243), done.
    remote: Total 521 (delta 245), reused 512 (delta 236)
    Receiving objects: 100% (521/521), 81.93 KiB | 40 KiB/s, done.
    Resolving deltas: 100% (245/245), done.

## 参考资料与延展阅读

* http://scottchacon.com/2011/08/31/github-flow.html
* http://nvie.com/posts/a-successful-git-branching-model/
* http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/
* http://www.eqqon.com/index.php/Collaborative_Github_Workflow