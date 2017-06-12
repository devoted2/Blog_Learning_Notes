# Linux下MySQL数据库常用基本操作 

>1、显示数据库

	show databases;
		
> 2、选择数据库

	use 数据库名;
>3、显示数据库中的表
	
		 show tables;
> 4、显示数据表的结构 
		
		 describe 表名;
> 5、显示表中记录
		 
		 SELECT * FROM 表名 
>6、建库

	 create databse 库名; 
>7、建表
		
		 create table 表名 (字段设定列表)；

	mysql> create table name(
    -> id int auto_increment not null primary key ,
    -> uname char(8),
    -> gender char(2),
    -> birthday date );
	Query OK, 0 rows affected (0.03 sec)

	mysql> show tables;
	+------------------+
	| Tables_in_userdb |
	+------------------+
	| name             |
	+------------------+
	row in set (0.00 sec)

	mysql> describe name;
	+----------+---------+------+-----+---------+----------------+
	| Field    | Type    | Null | Key | Default | Extra          |
	+----------+---------+------+-----+---------+----------------+
	| id       | int(11) | NO   | PRI | NULL    | auto_increment |
	| uname    | char(8) | YES  |     | NULL    |                |
	| gender   | char(2) | YES  |     | NULL    |                |
	| birthday | date    | YES  |     | NULL    |                |
	+----------+---------+------+-----+---------+----------------+
	rows in set (0.00 sec)

	注： auto_increment 自增
     primary key    主键
>8、增加记录
		 
		 insert into name(uname,gender,birthday) values('张三','男','1971-10-01');
> 9、修改记录

update name set birthday='1971-01-10' where uname='张三';
>  10、删除记录
	
	delete from name where uname='张三';
>   11、删除表

	drop table 表名;
>    12、删除库
	
	 drop database 库名;
>13、备份数据库 

	mysqldump -u root -p --opt 数据库名>备份名; //进入到库目录
>14、恢复
	
	mysql -u root -p 数据库名<备份名; //恢复时数据库必须存在，可以为空数据库
> 15、数据库授权

	mysql> grant select,insert,update,delete on *.* to user001@"%" Identified by "123456";
例2、增加一个用户user002密码为123456,让此用户只可以在localhost上登录,也可以设置指定IP，并可以对数据库test进行查询、插入、修改、删除的操作 (localhost指本地主机，即MySQL数据库所在的那台主机）

//这样用户即使用知道user_2的密码，他也无法从网上直接访问数据库，只能通过MYSQL主机来操作test库。
 //首先用以root用户连入MySQL，然后键入以下命令：
	   
	   mysql>grant select,insert,update,delete on test.* to user002@localhost identified by "123456";
	   
注： 其次也可以采用修改表的方式，处理用户的登录方式：

数据库： Mysql
表:      User
修改：   User表中的Host列的值来现实登录入口
具休操作请参照：Centos 6.2 安装Mysql笔记
	 
 

     
     
