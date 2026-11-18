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


