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

# git log

```javascript
feat：新功能（feature）
fix：修补bug
docs：文档（documentation）
style： 格式（不影响代码运行的变动）
refactor：重构（即不是新增功能，也不是修改bug的代码变动）
test：增加测试
chore：构建过程或辅助工具的变动
```