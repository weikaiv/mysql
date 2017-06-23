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
### 连接远程github仓库
1、如图所示，先在自己的github远程端新建一个仓库

![](https://github.com/weikaiv/mysql/blob/master/img/10.png)

2、在远程端建立仓库时，要注意两个地方，如图所示，首先要写上仓库名，有重名时系统会在后面提示一个×，此时要修改一个不与曾经建的仓库重名的仓库名，系统会在后面提示√。其次，注意要选择public类型，若为private是要交钱的。

![](https://github.com/weikaiv/mysql/blob/master/img/11.png)

3、创建好远程仓库后会跳转到如图所示界面，上面有此远程仓库的链接地址。

![](https://github.com/weikaiv/mysql/blob/master/img/12.png)

4、上传到github远程仓库上：
* 在命令行执行git remote add origin https://github.com/weikaiv/github.git
* 查看有哪些分支：git branch –av
* 把分支保存到上述github仓库：git push，如果出错的话，可能改成git push origin master就可以了，之后再输入用户名和密码
* 保存到git仓库后可以用git branch –av查看是否处于同一状态，如所示，是，则成功
 

5、从github远程仓库上拿下来：
* 建一个文件夹other文件夹
* 进入目录cd other
* git clone +远程仓库链接地址
* git pull 或git pull origin master
* 注：若第一次做，需要完成上述全部步骤，之后就直接做最后一步即可

