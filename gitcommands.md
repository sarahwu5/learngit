# 1
`pwd`  
print working directory
# 2
`git init`  
初始化仓库
# 3 git add & commit
`git add file2.txt file3.txt`  
`git commit -m "wrote a readme file"`  
git add是把文件放进工作区
# 4
`git status`  
查看当前工作区状态
>未跟踪的文件（Untracked files）：工作区中新建的文件，但还从未被添加到 Git 中（即没有被 git add 添加到暂存区）。  
已修改但未暂存的文件（Changes not staged for commit）：这些文件已经被修改，但还没有用 git add 命令将它们放入暂存区。  
已暂存的文件（Changes to be committed）：这些文件已经被 git add 命令放入了暂存区，准备通过 git commit 提交。 

已经被track的文件（即第一次git add）被修改后，如果本次修改被add，则为Changes not staged for commit；如果本次尚未被add，则为Changes to be committed。  
从未被git add的文件，为Untracked files。
# 5
`git diff`  
>git diff 比较的是工作区（Working Directory）和暂存区（Staging Area）之间的差异。
换句话说，当你修改了一个已经被 Git 跟踪的文件（tracked file），但还没有使用 git add 暂存这些修改时，git diff 会显示这些未暂存的变化。


