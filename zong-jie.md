# 总结
---

## 初始化信息

登录
```
git config --global user.name <name>
git config --global user.email <email>
```

查看
```
git config --global user.name
git config --global user.email
```

## 创建新仓库

- **本地直接创建仓库**
  0. GitHub或Bitbucket新建仓库；
  1. 本地文件夹目录下`git init`生成`.git`本地仓库。
  2. 放入需要提交的文件；
  3. `git add .`添加追踪文件；
  4. `git commit -m "first commit"`提交暂存和填写提交信息；
  5. `git remote add origin <git-http>`添加远程仓库别名为origin；
  6. `git push -u origin master`提交中央仓库并新建master作为默认，之后可以直接`git push`提交。
  
- **中央服务器获取（推荐）**
  0. GitHub或Bitbucket新建仓库；
  1. `git clone <git-http>`
  2. 放入需要提交的文件；
  3. `git add .`添加追踪文件；
  5. `git push`直接提交。
  

## 查看状态

文件有新建、更新、删除都可以监测到。 

`git status`

## clone

自定义clone下来的仓库文件名

`git clone <git-http> <file-name>`

## add

除了方便的`git add .`，也可以自定义需要提交的文件。

```
git add <file name> <file name>
```

## push

标准写法

```
git push origin <branch>
```

快捷写法

```
git push
```

`git push` 等于 `git push origin master`，因为通过`-u`设定了一个默认主机。

## branch

1. `git branch`查看本地所有分支
2. `git branch -r`查看远程所有分支
3. `git branch -a`查看本地和远程所有分支

新建并切换到新的branch

```
git checkout -b <branch>
```

提交到中央仓库

```
git push origin <branch>
```

切换当前barnch

```
git checkout <branch>
```

删除branch

```
git branch -d <branch>
```

在你创建仓库的时候，master被“默认”创建。
我就是叛逆不喜欢master这个名字，如何改名...

```
git branch -m <old name> <new name>
```
























