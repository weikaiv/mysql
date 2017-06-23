## CGI
CGI(Common Gateway Interface) 是WWW技术中最重要的技术之一，有着不可替代的重要地位。
CGI是外部应用程序（CGI程序）与WEB服务器之间的接口标准，是在CGI程序和Web服务器之间传递信息的过程。
CGI规范允许Web服务器执行外部程序，并将它们的输出发送给Web浏览器，CGI将Web的一组简单的静态超媒体文档变成一个完整的新的交互式媒体。
### Apache开启CGI
1、需要在apache中开启cgi支持：sudo ln -s /etc/apache2/mods-available/cgi.load /etc/apache2/mods-enabled/cgi.load
2、需要重启 apache 服务器：service apache2 restart
3、需要运行的cgi文件的存放路径为:/usr/lib/cgi-bin
4、改完目录的权限, 方便对目录下的文件写：sudo mkdir /usr/lib/cgi-bin/sx      sudo chmod 777 /usr/lib/cgi-bin/sx
### vim Makefile
1、install:
	cp *.cgi /usr/lib/cgi-bin/sx
### 安装mysql的C语言库
1、sudo apt-get install libmysqlclient-dev
### CCGI 基本使用
1、获取表单数据
cgiFormResultType   cgiFormString(char *name, char *result, int max);
参数：  name, 指定要获取的表单项的名字
  result,将获得的数据存储到result中
  max， 指定最多读取的字符个数
比如： cgiFormString("name", result,  16);可以获得最多16个字符并且保存于result中
2、输出函数fprintf
     int fprintf(FILE *stream, const char *format, ...);
功能： 将格式化的语句输出到指定的流
fprintf(stdin, "helloworld\n")  等价于 printf("helloworld\n);
3、字符串转换函数atoi
     int atoi(const char *nptr);
     参数：nptr为网页上输入的字符串数据名称
功能：将一个字符串转换成对应的数字，比如：“1234” ==》 1234
比如：sprintf(sql, "select * from information where id =%d", atoi(stuId));
4、初始化函数
     MYSQL *mysql_init(MYSQL *mysql)
参数：  定义的数据库指针
功能：初始化函数，参数为NULL即可，接收返回值
     失败，NULL
     比如：
     MYSQL *db;
	 db = mysql_init(NULL);
	 if (db == NULL)
	 {
		fprintf(cgiOut,"mysql_init fail:%s\n", mysql_error(db));
		return -1;
	  }
5、连接mysql服务器
   MYSQL *mysql_real_connect(MYSQL *mysql, const char *host, const char *user, const char *passwd, const char *db, unsigned int port, const char * unix_socket, unsigned long client_flag)
参数：  mysql，定义的数据库指针
        host，本地IP  
        user，用户名
        passwd，密码
        db，建立的数据库名
        port，端口号3306
        unix_socket，套接字，NULL
        flag ，标志位0
功能：连接mysql服务器
     失败，NULL
     比如：
MYSQL *db;
db = mysql_real_connect(db, "127.0.0.1", "root", "123456", "stu",  3306, NULL, 0);
if (db == NULL)
{
	fprintf(cgiOut,"mysql_real_connect fail:%s\n", mysql_error(db));
	mysql_close(db);
	return -1;
	  }
6、void mysql_close(MYSQL *mysql)
     参数：  mysql，定义的数据库指针
     功能：关闭服务器连接
     比如：mysql_close(db);
7、执行sql语句
 int mysql_real_query(MYSQL *mysql, const char *stmt_str, unsigned long length)
参数：  mysql，定义的数据库指针
        stmt_str,，Sql
        length ，Sql语句长度
功能：执行sql语句，sql语句不能以“；”结尾
 成功，0
     失败，非0
比如：
sprintf(sql, "delete from information where id = %d", atoi(stuId));
if ((ret = mysql_real_query(db, sql, strlen(sql) + 1)) != 0)
{
	fprintf(cgiOut,"mysql_real_query fail:%s\n", mysql_error(db));
	mysql_close(db);
	return -1;
}
8、存储mysql_query()
 MYSQL_RES *mysql_store_result(MYSQL *mysql)
参数：  mysql，定义的数据库指针
功能：存储mysql_query()或者mysql_read_query() 的数据
     失败，NULL
9、 const char *mysql_error(MYSQL *mysql)
参数：  mysql，定义的数据库指针
功能：返回出错提示
比如：fprintf(cgiOut,"mysql_real_query fail:%s\n", mysql_error(db));
10、访问表中每一条记录值
          MYSQL_ROW mysql_fetch_row(MYSQL_RES *result)
参数：  result ，MySQL_RES型结构体，存储mysql_query()
功能：返回集合中的一行， 结束或者错误返回NULL
比如：
MYSQL_ROW  row;
unsigned long  *len;
while ((row = mysql_fetch_row(res)) != NULL)
{
	  fprintf(cgiOut,"<tr>");
	  len = mysql_fetch_lengths(res);
	  for (i = 0; i < fields ; i++)
	  {
		fprintf(cgiOut,"<td>%.*s</td>", (int)len[i], row[i]);
	  }
	  fprintf(cgiOut,"</tr>");
}
11、返回集合中数组
  MYSQL_FIELD *mysql_fetch_fields(MYSQL_RES *result)
参数：  result ，MySQL_RES型结构体，存储mysql_query()
功能：返回集合中列的数组
比如：
unsigned int num_fields;
unsigned int i;
MYSQL_FIELD *fields;
num_fields = mysql_num_fields(result);
fields = mysql_fetch_fields(result);
for(i = 0; i < num_fields; i++)
{
    printf("Field %u is %s\n", i, fields[i].name);
}
12、返回当前行中每一个字段值的长度数组
  unsigned long *mysql_fetch_lengths(MYSQL_RES *result)
功能：返回当前行中每一个字段值的长度数组。


