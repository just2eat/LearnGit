# 保存变更

## 初始化仓库

当需要将一个目录进行版本管理时，在该目录下执行 `git init` 进行初始化。如下:

```shell
$ git init
Initialized empty Git repository in Users/moss/go/src/github.com/just2eat/test/.git/
```

由上边提示可以看到，要管理的目录中多了一个 `.git` 文件夹。这里存放了所有版本管理的信息。
如果删除 `.git` 文件夹，`test` 目录就不再有版本管理。

配置用户信息。当进行版本管理时需要记录变更的作者。用下面的命令配置当前仓库的用户。

```shell
$ git config user.name "Name" # 去掉后边的双引号部分，可以查看相应的设置。
$ git config user.email "Name@name.com"
```

## 第一个变更

新建一个文件并写入内容。以此作为第一个变更。

```shell
$ echo "first line" > test.md
$ cat test.md 
first line
```

接下来把这次变更记录到版本管理系统中。

```shell
$ git add test.md 
$ git commit -m "a message about this commit"
[master (root-commit) 616ec91] a message about this commit
 1 file changed, 1 insertion(+)
 create mode 100644 test.md
```

至此我们已经记录了一次变更。如果修改 `test.md` 或者新建别的文件，都可以通过 `git add`, `git commit` 命令将他们作为变更加入到版本库中。

那么如何查看，对比不同的变更？如何将目录，或者叫代码仓库，恢复到指定的状态呢。
请继续往下看。

## 变更记录

再加一条 commit :

```shell
$ echo "second line" >> test.md 
$ git add test.md 
$ git commit -m "secont commit"
[master 8c12139] secont commit
 1 file changed, 1 insertion(+)
```

我们往 `test.md` 文件中追加了一行文字 `second line` 。并以 `second commit` 作为此次变更的描述，进行提交。

在当前仓库，我们进行了两次提交(commit)。需要用某种方式看到这个记录。这个命令是 `git log`。这个命令展示 commit history。

```shell
$ git log
commit e3b0a284c0a46a77e0e4078fa8610e22dfb8fb87 (HEAD -> master)
Author: Name <name@name.com>
Date:   Fri Jul 20 09:42:07 2018 +0800

    secont commit

commit 616ec91f25e7b7abe83214480a07584a2d8779ad
Author: Name <name@name.com>
Date:   Fri Jul 20 09:25:49 2018 +0800

    a message about this commit
```

这个命令展示一组 commit 。每组 commit 展示了该 commit 的 ID，作者，时间和变更描述。

至此我们就可以在本地进行最基本的版本管理了。
下一节介绍如何进行最基本的远程版本管理。