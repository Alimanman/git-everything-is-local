# 总结
---

## 创建新仓库

- 本地直接创建仓库
  1. `git init`生成`.git`本地仓库。
  2. 放入需要提交的文件。
  3. `git add .`添加追踪文件
  4. `git commit -m "first commit"`提交暂存和填写提交信息
  5. `git remote add origin <http>`添加远程仓库别名为origin
  6. `git push -u origin master`提交中央仓库并新建master作为默认，之后可以直接`git push`提交