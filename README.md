# Linux-Mysql-Install
Linux安装Mysql5.6教程

### 1.下载安装包
wget http://cdn.mysql.com/archives/mysql-5.6/mysql-5.6.26-linux-glibc2.5-x86_64.tar.gz 
 
### 2.解压安装包
tar zxvf http://cdn.mysql.com/archives/mysql-5.6/mysql-5.6.26-linux-glibc2.5-x86_64.tar.gz 
 
### 3.进入文件夹
cd mysql-5.6.26-linux-glibc2.5-x86_64
 
### 4.创建用户组和用户
groupadd mysql
useradd -r -g mysql mysql
 
### 5.修改权限
chown -R mysql:mysql ./
 
### 6.安装数据库
./scripts/mysql_install_db --user=mysql
 
### 7.修改当前目录拥有者
chown -R root:root ./

chowd -R mysql:mysql data
 
### 8.添加mysql为系统服务
cp support-files/mysql.server 

/etc/init.d/mysql
 
### 9.修改mysql服务路径配置
vi /etc/init.d/mysql  

修改 basedir=mysql安装包路径、datadir=mysql数据存放目录(默认为mysql安装包路径/data)
 
### 10.复制配置mysql配置文件
先查看support-files目录下是否有mysql-medium.cnf文件，有的话直接复制就好了cp support-files/mysql-medium.cnf my.cnf 
如果没有就自己配置下
 
### 11.添加mysql系统变量
vi /etc/profile       //编辑该文件

修改PATH=$PATH:MYSQL安装包路径/bin   //按字母i进入编辑模式 esc退出编辑模式  :x保存并退出

source /etc/profile   //使文件生效

echo $PATH    //	查看是否加入成功
 
### 12.启动mysql
service mysql start  
 
### 13.命令行连接MYSQL
mysql -u root -p  //新安装默认没有密码，输入后直接回车即可
 
### 14.sql基本语句
SHOW DATABASES;  //查看当前所有数据库

CREATE DATABASE 数据库名;  //创建数据库

USE  数据库名; //选择数据库

SOURCE SQL文件路径; //导入数据

GRANT ALL PRIVILEGES ON 数据库名.* TO 用户名@"%" IDENTIFIED BY '密码' WITH GRANT OPTION; //创建一个远程用户使他有某个数据库的所有权限
