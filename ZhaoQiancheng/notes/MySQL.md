系统：Ubuntu 版本号：Linux max-virtual-machine 5.4.0-29-generic

0.安装MySQL

sudo apt-get  install mysql-server

1.查看数据库

show databases;

2.选择数据库

use databaseName;

3.查看数据库中的表

show tables；

4.查询表中数据

select * from tableName；

5.退出数据库服务

exit；

6.创建数据库

create database databaseName

7.创建数据表

create TABLE pet(
​          name VARCHAR(20),
​          owner VARCHAR(20),
​          specise VARCHAR(20), 
​         sex CHAR(1),
​         brith DATAE，  
​        death DATE );

8.查看数据表的架构

describe tableName;

 说明:

+-------+-------------+------+-----+---------+-------+
\| Field | Type | Null | Key  | Default | Extra |
+-------+-------------+------+-----+---------+-------+

 Field   :   字段的名称
 Type   :   字段的类型,可以有int   var   varchar   
 Key    :   是否是关键字 如可以定义为:  primary key 或者 unique key  ...
 Default: :  若是该字段没有主动设置值的时候,该字段的默认值是什么?

9.插入数据

 INSERT INTO pet VALUES('kk','cc','dog','1','1998-8-2',null); 

+------+-------+---------+------+------------+-------+
| name | owner | specise | sex   | brith      | death |
+------+-------+---------+------+------------+-------+
| kk    | cc    | dog   | 1    | 1998-08-02 | NULL|
+------+-------+---------+------+------------+-------+
注意:
   NULL:代表的是空,表示该字段还没有数据.千万不要主动填写'NULL',这代表你的字段有一个值叫做'null'.
其实还有一种写法: 
   INSERT INTO pet(name,owner) VALUES ('xx','cc');代表我只在name和owner字段上面插入的一条,其他皆为NULL/默认值的数据

10.mysql 常用数据类型 

​    注意:金钱最好用int/bigint(整数,单位用分,拿出来进行*100换成元),千万不要直接用浮点,会有精度损失.

11.