## 创建版本库
### 版本库介绍
版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，
每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。
### 创建版本库
> 1、第一步, 先要创建一个目录, 这个目录就是用来存放仓库的：

   mkdir github
   
   cd github
> 2、使用git init命令, 将当前目录创建成git仓库：

   git init
> 3、la -a会发现有一个隐藏的.git目录

> 4、增加文件：

touch README

vim README
> 5、查看文件状态：

git status
> 6、把文件加到仓库中去, 只有加到仓库中了, 才可能看一下文件的变化:

git add README
> 7、配置用户名：

git config --global user.name
> 8、配置用户邮箱：

git config --global user.email
> 9、配置编辑器：

git config --global core.editor vim
> 10、提交：

git commit
> 11、查看提交信息：

git log
> 12、比较变化：

git diff
