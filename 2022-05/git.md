# 修改git url

- git remote set-url origin [url]
- git remote rm origin
  git remote add origin [url]

- 修改 config
  fatal: git pull origin master --allow-unrelated-histories

# 删除分支

- git push origin --delete b1 远程
- git branch -D b2 本地
- git remote prune origin 远程分支不存在