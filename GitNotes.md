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

