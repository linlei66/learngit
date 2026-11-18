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



