# Fork代码到个人仓库及管理

## fork主仓库代码到个人代码

主仓库项目首页，点击右上fork，然后namespace选择个人仓库。等一段时间之后，fork完成，然后在自己的仓库里就可以看到项目了。

## 拉取个人仓库到本地

```bash
git clone git@xxxxxxxxxxxx.git
```

## 建立与主仓库的连接

查看当前仓库的remote关联：

```bash
git remote -v
```

若列表中没有主仓库地址，手动添加：

```bash
git remote add main git@main.git
```

其中main是自定义名称，添加后重新查看即可看到刚刚添加的远端仓库信息。

```bash
main    git@git.xxx.git (fetch)
main    git@git.xxx.git (push)
origin  git@git.xxxx.git (fetch)
origin  git@git.xxxx.git (push)
```

## 个人仓库同步主仓库代码

经过以上操作后，本地的分支代码对应的是个人仓库中的代码。
进行git操作的时候，如果不指定仓库名，默认（origin）的都是应用到个人仓库的。
如果主仓库代码有更新，按照以下方法同步到个人仓库。
假设需要把主仓库master分支的代码同步到个人仓库master分支：

```bash
git chekcout master (本地分支切换到master分支）
git fetch main (获取主仓库变更）
git merge main/master（和主仓库master分支内容到本地分支）
```

这个时候，如果没有冲突的话，完成合并后，本地分支的内容就和主仓库一致了。
如果有冲突话需要解决冲突后，然后以下命令完成合并：

```bash
git merge --continue
```

合并完成后，执行push命令就可以将最新代码同步到个人仓库了。

```bash
git push origin master:master
```

## 提交代码和MR

在本地分支开发完成后，push本地分支到个人仓库。比如：

```bash
git push origin dev:dev
```

注意一种场景，当主仓库master新增分支，fork的个人仓库没有新增的分支时候，此时把main仓库新分支同步到个人仓库使用一下方法:
```bash
# 本地创建新分支并将main仓库改分支代码pull到本地
git chekout -b newBranchName main/newBranchName
# 将新分支push到个人仓库
git push origin newBranchName
```

这样本地的代码就提交到个人仓库中了。
在个人仓库的对应的项目页面上，选择新建MR，然后在提交页面上：
Source Branch选个人仓库项目地址,Target Branch选主仓库项目地址
后面操作和同一仓库下，提MR一样，比较区别，然后提交MR。
