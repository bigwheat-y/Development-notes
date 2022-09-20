#### Git操作笔记

1、如果你是`git pull`或者`git push`报`fatal: refusing to merge unrelated histories`

```sh
git pull origin master --allow-unrelated-histories
```

2、更新GitHub项目出现`There is no tracking information for the current branch. Please specify which branch you want to merge with.` 怎么解决

```sh
git branch --set-upstream-to=origin/master master
```



