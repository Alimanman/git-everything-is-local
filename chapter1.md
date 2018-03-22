# 上手篇
---

## 安装

- https://git-scm.com/

## 创建项目

- github
- bitbucket

## 克隆到本地

隐藏的`\.git`目录，就是本地仓库（Local Repository）。也称之为 Git 的工作目录（Working Directory）

```
git clone 你刚复制的地址
```

## 查看提交历史

按 q 键退出

```
git log
```

## 查看工作目录当前状态

- 如果无任何变动：nothing to commit
- 有新文件：Untracked files（红色）
- 更新文件：Changes not staged for commit（红色）
- 已添加追踪：Changes to be committed(绿色)

```
git status
```

## 跟踪文件

跟踪成功后，终端不会给你反馈。通过`git status`查看状态。

```
git add 你要跟踪的指定文件
git add . //添加全部暂存
```

> add 添加的是文件改动，而不是文件名自身。
所以如果再更新过文件的话，还需要再add一次。

添加的文件已被放入staging area（暂存区）后以待提交。

## 提交

```
git commit
```

- 按一下 "i"（小写）来切换到插入模式
- 按 ESC 键返回到命令模式，输入大写"Z"退出

完成后通过`git log`查看，已经被保存在本地的.git目录里了。

再次查看`git status`，发现**ahead of**。
这表示本地的版本，已领先于目前版本。

## 推送到中央仓库

```
git push
```

## 上手篇小结

1. 从 GitHub 把中央仓库 clone 到本地（使用命令： `git clone`）

2. 把写完的代码提交（先用 `git add` 文件名 把文件添加到暂存区，再用 `git commit` 提交）
 - 在这个过程中，可以使用 `git status` 来随时查看工作目录的状态

 - 每个文件有 "changed / unstaged"（已修改）, "staged"（已修改并暂存）, "commited"（已提交） 三种状态，以及一种特殊状态 "untracked"（未跟踪）

3. 提交一次或多次之后，把本地提交 push 到中央仓库（`git push`）































