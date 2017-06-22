## ubuntu安装
* 1、进入VMware，点击标红处，如下图所示

![](https://github.com/weikaiv/mysql/blob/master/img/1.png)

* 2、点击next，进入如下界面

![](https://github.com/weikaiv/mysql/blob/master/img/2.png)

* 3、在标红处选择已下载的Ubuntu镜像的路径（可在Ubuntu.com中的的desktop中下载），如下图所示

![](https://github.com/weikaiv/mysql/blob/master/img/3.png)

*  4、继续点击next

* 5、fullname设为：linux，密码设为1，如下图

![](https://github.com/weikaiv/mysql/blob/master/img/4.png)

* 6、继续点击next，选择好安装位置，如下图所示

![](https://github.com/weikaiv/mysql/blob/master/img/5.png)

* 7、继续next一直到finish，安装完成
## Linux环境下文件基本操作
> 新建文件：touch  file

将file复制到file1：cp file file1

将file复制到另外一个目录下的file1：cp file  /home/linux/file1

重命名：mv file file2

把file移动到另外一个目录中：mv file  /home/linux/

查看文件权限及类型等：ls -al 

查看文件内容：cat file
### Linux环境下目录基本操作
> mkdir dir

cp dir   dir1  -a

cp dir   /home/linux/dir2  -a

mv dir  dir2

mv dir  /home/linux/

rm  dir  -rf

find  ./dir  -name  "filename"
### 文件的归档和压缩
> tar:                打包压缩
     -c              归档文件
     -x              压缩文件
     -z              gzip压缩文件
     -j              bzip2压缩文件
     -v              显示压缩或解压缩过程 v(view)
     -f              使用档名
例：
tar -cvf /home/abc.tar /home/abc              只打包，不压缩
tar -zcvf /home/abc.tar.gz /home/abc        打包，并用gzip压缩
tar -jcvf /home/abc.tar.bz2 /home/abc      打包，并用bzip2压缩
### 系统管理命令
stat          显示指定文件的详细信息，比ls更详细
who         显示在线登陆用户
whoami      显示当前操作用户
hostname     显示主机名
uname       显示系统信息
top          动态显示当前耗费资源最多进程信息
ps           显示瞬间进程状态 ps -aux
du           查看目录大小 du -h /home带有单位显示目录信息
df           查看磁盘大小 df -h 带有单位显示磁盘信息
ifconfig      查看网络情况
ping         测试网络连通
man         命令不会用了 如：man ls
clear         清屏
kill          杀死进程，可以先用ps 或 top命令查看进程的id，然后再用kill命令杀死进程

