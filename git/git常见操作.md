##git常见场景操作

* 多个人对同一分支进行维护操作，提交自己代码要先更新同步后才能push成功
  ```bash
  git pull --rebase origin yourBranch
  # 肯能需要解决冲突后再push
  git push origin yourBranch
  ```

* git push冲突
  ```bash
  git fetch main
  git merge main/branch
  # 解决冲突
  git add .
  git merge --continue
  ```