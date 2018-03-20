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

- 如果无任何变动：nothing
- 有新文件:untracked（红色）
- 已添加追踪：new file(绿色)

```
git status
```

## 跟踪文件

```
git add 你要跟踪的文件
```

> 跟踪成功后，终端不会给你反馈。通过`status`查看状态。













