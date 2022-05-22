## 上传文件夹
* git bash here
* git init
* git status
* git add .
* git commit -m “备注”
* git remote add origin https://github.com/hanyuntao/text.git
* git push -u origin master

1.检查当前文件状态 --  `git status  git diff  git diff --staged` 

　　 `git status` :我们可以使用 `git status` 来查看文件所处的状态。当运行 `git status` 之后，出现类似下面输出：
```
$ git status
On branch master
nothing to commit, working directory clean
```
说明，现在的工作目录非常干净，换句话说，所有的已跟踪文件在上次提交之后都未被修改过。

　　 如果你想要知道具体修改了什么地方，可以使用 `git diff` 命令。

 1. git diff ：查看尚未暂存的文件更新了哪些部分。

 2. git diff --staged ：查看已暂存的文件更新了哪些部分。

2.跟踪新文件 --  `git add`

　　当在工作目录新建一个文件，运行 `git status` ，会显示这个文件是untracked状态。这时候需要使用 `git add`  将这个文件加入暂存区，也就是告诉Git需要去跟踪这个文件。

 git add 使用文件或者目录的路径作为参数；如果参数是目录的路径，那么将该目录下所有的文件加入暂存区，Git将会跟踪这个目录下面的所有文件。

3.暂存已修改文件 --  `git add`   --（可以将这个命令理解为：添加内容到下一次commit中）

　　当修改了Git追踪的一个文件之后，运行 git status 会看到 Changes not staged for commit ，说明已跟踪的文件发生了变化但是还没有被加入到暂存区，这时候需要运行 git add 将该文件放入暂存区。

　　 `git add` 是一个多功能命令：

1.使用它跟踪新文件；

2.将已跟踪的文件加入到暂存区；

3.还能用于合并时将有冲突的文件标记为已解决的状态。

注意： `git commit` 只会讲暂存区的文件提交到Git仓库中，不在暂存区中的文件是不会被提交的。比如：当你运行 git add README 之后，将README文件加入了暂存区，这时候你又修改了README文件，但是没有运行 `git add` ，这时候如果直接提交，那么只会讲暂存区中的README版本的文件提交到Git仓库。你对README新做的修改不会被提交到Git仓库。

4.忽略文件 -- `.gitignore`文件

　　一般我们总会有一些文件不想纳入Git进行管理，同时也不希望他们总出现在未跟踪文件列表。这时候只需要在`.gitignore`文件中指定这些你不想被Git进行管理的文件，这样一来当你在提交代码到远程仓库的时候也就不会将这些文件上传上去了。GitHub 有一个十分详细的针对数十种项目及语言的 `.gitignore` 文件列表，你可以在https://github.com/github/gitignore找到它.

5.提交更新 --  `git commit` 

 　　在暂存区准备完毕之后，就可以commit了。注意：在提交之前一定要确认还有什么没有修改过的活新建的文件还没有 git add 过，否则commit的时候不会记录这些还没暂存起来的变化，这些修改过的文件只会保留在本地磁盘（也就是工作区）。在每次提交之前，可以使用 git status 查看一下，文件是不是已经都暂存起来了。

1. `git commit` 如果不指定-m参数，那么git会打开一个编辑器，让你输入提交信息。

2. `git commit -m <info>`  指定-m参数，可以在后面直接指定提交信息。（推荐使用）

3. `git commit -a -m <info>`有时候，在修改某一个已经被track的文件之后，可以直接使用 `git commit -a -m "info"` 跳过add步骤而将这个文件提交。

注意：这条命令会将已经被track的文件加入到暂存区，然后进行提交；对于没有被track的文件（例如新添加的文件），在修改之后是不能使用这条命令直接进行提交的。

　　commit记录的是放在暂存区域的快照，每一次提交操作都是对项目做一次快照，以后可以回到这个状态，或者进行比较。

6.移除文件 --  `git rm` 

　　执行以下命令：删除一个文件。
```
$ git rm <filename>
$ git commit -m <info>
```
　　如果被删除的文件修改过，而且已经被放入了暂存区，那么需要加上 -f 参数，强制删除。这是一种安全特性，用于防止删除还没有被添加快照的数据，这种数据无法被Git恢复。

　　如果你只是想从暂存区删除文件，但是工作区的文件保持不变（将文件保存在磁盘），也就是说将文件保存在磁盘但是不想让Git进行跟踪，使用如下命令即可：
```
$ git rm --cached <filename>
```
7.移动文件 --  git mv 

　　可以使用 git mv 来讲文件重命名。命令格式如下：会将oldFile重新命名为newFile

`$ git mv <oldFile> <newFile>`
这条命令会：1.将文件改名；2.将改名之后的文件add进暂存区。等价于下面三条命令。
```
$ mv oldFile newFile
$ git rm oldFile
$ git add newFile
```
 