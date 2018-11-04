# linux


## mysql

1、官方安装文档

http://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/


2、下载 Mysql yum包

wget http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm


3、安转软件源

rpm -Uvh mysql57-community-release-el7-10.noarch.rpm


4、安装mysql服务端

yum install  -y  mysql-community-server


5、首先启动mysql

service mysqld start（重启是restart，完全弄好MySQL后最好添加lower_case_table_names=1到[mysqld]下面一行然后重启MySQL，这是为了和windows兼容，还有就是在[mysql]下面一行加入default-character-set=utf8）


6、接着检查mysql 的运行状态

service mysqld status


7、修改临时密码

Mysql5.7默认安装之后root是有密码的。


7.1 获取MySQL的临时密码

为了加强安全性，MySQL5.7为root用户随机生成了一个密码，在error log中，关于error log的位置，如果安装的是RPM包，则默认是/var/log/mysqld.log。
只有启动过一次mysql才可以查看临时密码

grep 'temporary password' /var/log/mysqld.log（如果之前安装过MySQL则这里可能会有多个密码，用最后一个，注意这个密码输入时是可以粘贴的）


7.2 登陆并修改密码

使用默认的密码登陆

mysql -uroot -p（这是一个MySQL的以密码登录root用户的命令）

用该密码登录到服务端后，必须马上修改密码再执行一些数据库操作，不然会报如下错误：

mysql> select @@log_error;

ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement.

修改密码（注意，登录后的操作后面都最好要有;结尾）

ALTER USER 'root'@'localhost' IDENTIFIED BY 'root123';

如果密码设置太简单出现以下的提示

如何解决ERROR 1819 (HY000): Your password does not satisfy the current policy requirements呢？ 这里直接提供解决方案文末有详细的说明

必须修改两个全局参数：

首先，修改validate_password_policy参数的值

mysql> set global validate_password_policy=0;

再修改密码的长度

set global validate_password_length=1;

再次执行修改密码就可以了

ALTER USER 'root'@'localhost' IDENTIFIED BY 'root123';（ALTER等可以写成小写）

8、授权其他机器登陆

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;

FLUSH  PRIVILEGES;


