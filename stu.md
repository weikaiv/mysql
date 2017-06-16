## 学生信息管理系统
### 数据库设计方案
#### 学校信息表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 编号 | sid | int(4) | √ |  | 自动增加，要求(sid>0)
 校名 | sname | varchar(10) |  |  | not null
 院系 | sdept | varchar(10) |  |  | not null
 专业 | smajor | varchar(10) |  |  | not null
 班级 | sclass | varchar(6) |  |  | not null
#### 学生信息表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 学号 | id | int(4) | √ |  | check(id>0)
 姓名 | name | varchar(6) |  |  | not null
 性别 | sex | varchar(1) |  |  | not null check(sex in('男','女'))
 出生日期 | birthday | varchar(10) |   | default'1990-01-01' |
 院校编号 | sid | int(4) |  |  |**外键**
#### 课程表设计
 字段 | 英文 | 字段类型 | 主键 | 备注
------|-----|---------|-----|-----
 课程号 | cid | int(4) | √ | check(cid>0)
 课程名 | cname | varchar(10) | | not null
 学分 | credit | int(2) | | not null check(credit>0)
#### 学生成绩表设计
 字段 | 英文 | 字段类型 | 主键 | 默认值 | 备注
------|-----|---------|-----|--------|-----
 学号 | id | int(4) | √ |  | check(id>0),**外键**
 课程号 | cid | int(4) | √ |  | check(id>0)，**外键**
 成绩 | score| double(4,1) |  | default'0' | check(sid>=0 and sgrade<=100)
