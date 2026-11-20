这是一个我学习的git的实例代码，是一个贪吃蛇小游戏程序
用来学习如何使用git来管理代码库

具体学习记录：
1.安装git
windows下直接安装：https://git-scm.com/install/windows
安装好后会有可执行程序：Git bash
配置：
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

2.创建一个版本库并初始化
版本库就是我们的代码仓库
创建好后cd到版本库目录下进行初始化：
        lei.lin@JM230601012273 MINGW64 /d/git_learn
        $ git init
        Initialized empty Git repository in D:/git_learn/.git/

3.添加一个文件到库里并提交
lei.lin@JM230601012273 MINGW64 /d/git_learn (master)
$ git add README.md
lei.lin@JM230601012273 MINGW64 /d/git_learn (master)
$ git commit -m "wrote a readme file"
[master (root-commit) ec7dfcb] wrote a readme file
 1 file changed, 19 insertions(+)
 create mode 100644 README.md

4.
查看当前仓库状态：git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/
        main.py
        snake.py

no changes added to commit (use "git add" and/or "git commit -a")
这里可以查看在那个分支上，跟踪了那些文件，有没有改动，有没有提交

查看具体改动了什么：git diff
diff --git a/README.md b/README.md
index 4abb690..0a31064 100644
--- a/README.md
+++ b/README.md
@@ -16,4 +16,14 @@ $ git config --global user.email "email@example.com"
         $ git init
         Initialized empty Git repository in D:/git_learn/.git/

-3.
+3.添加一个文件到库里并提交
+lei.lin@JM230601012273 MINGW64 /d/git_learn (master)
+$ git add README.md
+lei.lin@JM230601012273 MINGW64 /d/git_learn (master)
+$ git commit -m "wrote a readme file"
+[master (root-commit) ec7dfcb] wrote a readme file
+ 1 file changed, 19 insertions(+)
+ create mode 100644 README.md
+
+
+
这里可以看到具体删除-和添加的内容+

再次提交(git add README.md)后：git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/
        main.py
        snake.py
5.版本回溯
使用git log可以看版本信息
简洁可加参数 git log --pretty=oneline 有版本的id信息
回溯：git reset --hard HEAD^ ,HEAD^代表上一个版本，上上一个版本HEAD^^,很多版本就是HEAD~100，上一百个版本
--hard会回退到上个版本的已提交状态，而--soft会回退到上个版本的未提交状态，--mixed会回退到上个版本已添加但未提交的状态。现在，先放心使用--hard
也可以在返回到最新版本，指定版本id：git reset --hard id
Git提供了一个命令git reflog用来记录你的每一次命令

6.缓存区
git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。

7.管理修改
每次修改后都需要add，如 第一次修改->add->第二次修改->commit,实际上还是只有第一次修改
必须：第一次修改->add->第二次修改->add-->commit

8.撤销修改
git checkout -- file
一种是自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态。
一种是已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令，我们在后面的分支管理中会再次遇到git checkout命令。

9.删除文件
rm README.md

10.远程管理，上传github
ssh-keygen -t rsa -C "youremail@example.com" 生成你的ssh密钥，位置在user/.ssh/id_rsa.pub
将这个密钥配置在自己的github账号上
然后在github创建一个new repository, 填上repository name
git remote add origin git@github.com:michaelliao/learngit.git 将michaelliao换为自己的用户名
git push -u origin master
上传成功

11.分支管理
创建一个分支 git checkout -b dev  
-b参数表示创建并切换，相当于以下两条命令：
**
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
**
git branch查看当前在那个分支
比如我们修改了README后再提交add ,commit
提交就是正常提交
提交：git -u origin dev
目前HEAD指针在dev上，我们要合并master和dev分支
先切换到master分支，然后git merge dev合并指令
再删除dev分支 git branch -d dev,这里主要要先commit后才能切换分支
这样，dev分支上的改动也到了master上了
