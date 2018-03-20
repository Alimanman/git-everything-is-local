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
- 已添加追踪：Changes to be committed(绿色)

```
git status
```

## 跟踪文件

跟踪成功后，终端不会给你反馈。通过`git status`查看状态。

```
git add 你要跟踪的指定文件
git add . //添加所有变化文件
```

添加的文件已被放入staging area（暂存区）后以待提交。

## 提交

```
git commit
```

- 按一下 "i"（小写）来切换到插入模式
- 按 ESC 键返回到命令模式，输入大写"Z"退出

完成后通过`git log`查看，已经被保存在本地的.git目录里了。































