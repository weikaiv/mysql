# 2017-06-15 记录文档
## ubuntu **安装** MySQL关系型数据库
> 1、回到用户主目录

> 2、sudo vim /etc/apt/sources.list

>3、粘贴源（若无法复制粘贴在vim .vimrc做修改:进入第三行，移动到18行删除）

deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
`##`测试版源
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
`#`源码
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
`##`测试版源
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
`#`Canonical 合作伙伴和附加
deb http://archive.canonical.com/ubuntu/ xenial partner
deb http://extras.ubuntu.com/ubuntu/ xenial main

>4、sudo apt-get update

>5、sudo apt-get install tasksel

>6、sudo tasksel

>7、选择LAMP server ->ok

>8、输入密码是123456

>9、mysql -h主机地址 -u 用户名 -p 用户密码

>10、show databases
## 新建数据库stu
>create database stu
## 设计三张表

