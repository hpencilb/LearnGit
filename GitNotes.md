# Git Notes

- 初始化一个Git仓库，使用`git init`命令。
- 添加文件到Git仓库，分两步：
  1. 使用命令`git add `，注意，可反复多次使用，添加多个文件；
  2. 使用命令`git commit -m `，完成。
- 要随时掌握工作区的状态，使用`git status`命令。
- 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。
- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。
- 每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中。
- 当你改乱了工作区某个文件的内容：
  1. 想直接丢弃工作区的修改时，用命令`git checkout -- file`。
  2. 当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD `，就回到了1，第二步按1操作。
  3. 已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退，不过前提是没有推送到远程库。
- 命令`git rm`用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**。
- 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`。
- 关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容。
- 此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改。
- 要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。
- Git支持多种协议，包括`https`，但通过`ssh`支持的原生`git`协议速度最快。
- Git鼓励大量使用分支：
  - 查看分支：`git branch`
  - 创建分支：`git branch `
  - 切换分支：`git checkout `或者`git switch `
  - 创建+切换分支：`git checkout -b `或者`git switch -c `
  - 合并某分支到当前分支：`git merge `
  - 删除分支：`git branch -d `
- 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
  解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。
  用`git log --graph`命令可以看到分支合并图。
- 合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。
- 修复bug时，通过创建新的bug分支进行修复，然后合并，最后删除；
  当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场；
  在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick `命令，把bug提交的修改“复制”到当前分支，避免重复劳动。
- 如果要丢弃一个没有被合并过的分支，可以通过`git branch -D `强行删除。
- 查看远程库信息，使用`git remote -v`；
  本地新建的分支如果不推送到远程，对其他人就是不可见的；
  从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
  在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
  建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
  从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。
- `git rebase`操作可以把本地未push的分叉提交历史整理成直线，目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。
- 命令`git tag `用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；
  命令`git tag -a  -m "blablabla..."`可以指定标签信息；
  命令`git tag`可以查看所有标签。
- 命令`git push origin `可以推送一个本地标签；
  命令`git push origin --tags`可以推送全部未推送过的本地标签；
  命令`git tag -d `可以删除一个本地标签；
  命令`git push origin :refs/tags/`可以删除一个远程标签。
- 忽略某些文件时，需要编写`.gitignore`；
- `.gitignore`文件本身要放到版本库里，并且可以对`.gitignore`做版本管理！

