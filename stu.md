# 学生信息管理系统
## 数据库设计方案
#### 学校信息表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 编号 | sid | int(4) | √ |  | 自动增加，要求(sid>0)
 校名 | sname | varchar(20) |  |  | not null
 院系 | sdept | varchar(20) |  |  | not null
 专业 | smajor | varchar(20) |  |  | not null
 班级 | sclass | varchar(10) |  |  | not null
#### 学校信息表创建
```sql
create table school( 
   sid int(4) primary key auto_increment check(sid>0),
   sname varchar(20) not null, 
   sdept varchar(20) not null, 
   smajor varchar(20) not null, 
   sclass varchar(10) not null
)default charset=utf8;
```
#### 学生信息表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 学号 | id | int(4) | √ | check(id>0)
 姓名 | name | varchar(10) |  | not null
 性别 | sex | varchar(6) |  | not null check(sex in('男','女'))
 年龄 | age | int(4) |   |  | not null
 状态 | state | smallint |  |  default 0 |
 院校编号 | sid | int(4) |  |**外键**
 #### 学生信息表创建
 ```sql
create table information(
  id int(4) primary key check(id>0),
  name varchar(10) not null,
  sex varchar(6) not null check(sex in('男','女')),
  age int(4) not null, 
  sid int(4), 
  state smallint default 0,
  foreign key(sid) references school(sid)
)default charset=utf8;
 ```
#### 课程表设计
 字段 | 英文 | 字段类型 | 主键 | 备注
------|-----|---------|-----|-----
 课程号 | cid | int(4) | √ | check(cid>0)
 课程名 | cname | varchar(20) | | not null
 学分 | credit | int(2) | | not null check(credit>0)
 #### 课程表创建
 ```sql
 create table course( 
 cid int(4) primary key check(cid>0),
 cname varchar(20) not null,
 credit int(2) not null check(credit>0)
 )default charset=utf8;
 ```
#### 学生成绩表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 学号 | id | int(4) | √ |  | check(id>0),**外键**
 课程号 | cid | int(4) | √ |  | check(id>0)，**外键**
 成绩 | sgrade | double(4,1) |  | default'0' | check(sid>=0 and sgrade<=100)
 #### 学生成绩表创建
 ```sql
 create table score( 
  id int(4) check(id>0),
  cid int(4) check(id>0),
  sgrade double(4,1) default'0' check(sid>=0 and sgrade<=100),
  primary key(id,cid),
  foreign key(id) references information(id),
  foreign key(cid) references course(cid)
 )default charset=utf8;
 ```
 #### 教师信息表设计
  字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 教师编号 | tid | int(4) | √ |  | check(tid>0)
 教师姓名 | tname | varchar(20) |  |  | not null
 #### 教师信息表创建
 ```sql
 create table teacher(
   tid int(4) primary key check(tid>0),
   tname varchar(20) not null
 )default charset=utf8;
 ```
 ### 创建视图allinfo,连接school，information，score
```sql
 create view allinfo
 as
 select information.id,name,sex,age,state,sname,sdept,smajor,sclass,cname,sgrade from school,information,score,course
 where school.sid=information.sid and information.id=score.id and score.cid=course.cid;
```
 ### 创建视图ainfo,连接school，information
```sql
 create view ainfo
 as
 select distinct information.id,name,sex,age,state,sname,sdept,smajor,sclass from school,information,score,course
 where school.sid=information.sid ;
```
