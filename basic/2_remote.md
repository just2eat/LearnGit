# 远程仓库

上一节讲了

1. 初始化仓库 `git init`
2. 提交变更
    1. `git add *.*`
    2. `git commit -m "xxx"`
3. 查看变更记录 `git log`

这里说如何跟远程仓库协作。

通常情况下，省略初始化仓库这一步，用 clone 仓库代替（有更灵活的用法，以后再讲）。
通常情况下我们选择在 github, gitlab, gogs 等产品上创建远程仓库。创建好之后，再 clone 回本地。
步骤如下:

1. 在网页上找到仓库的克隆地址。
    通常是一个 http 或 https 开头 .git 结尾的网页地址。
2. 在本地存放代码仓库的地方执行
    `git clone https://github.com/just2eat/LearnGit.git`

至此我们替换掉了初始化仓库这一步。提交变更记录的方式不变。

但是提交只保存在本地，并没有同步到远程仓库。这里介绍 git 的一个设计理念。
git 是分布式版本管理。本地的代码仓库和远程仓库是完全独立的，哪怕本地仓库是 clone 远程仓库得来的。离开远程仓库完全可以进行独立得版本管理。所以需要额外的同步步骤。

通常情况下同步用两个命令，`push` 和 `pull`。一个推送，一个拉取。

- `git push`
- `git pull`

推送时，对比本地和远程的 commit history 。如果本地比远程多了一个或多个 commit ，则会把这些 commit 推送到远程仓库。那么如果少 commit 呢？甚至 commit 顺序都不同呢？暂时不考虑，后边会讲。这里暂时只考虑最简单的用法。

所以现在所学到的一个工作流程就是

1. 克隆仓库 `git clone`
2. 拉取更新 `git pull`
3. 提交变更
    1. `git add xxx`
    2. `git commit -m "xxx"`
4. 推送更新 `git push`

2 ~ 4 不停循环