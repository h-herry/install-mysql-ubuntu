# install-mysql-ubuntu

在Ubuntu上安装MySQL

sudo apt update -y

sudo apt install mysql-server -y

sudo systemctl status mysql

sudo mysql_secure_installation


登录mysql 回车

mysql -h localhost -u root -p

修改密码by后是密码

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new_password';

ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';

开启远程登录

查看 user 数据表当前已有的数据

select * from user \G;


修改一条 root 数据，并刷新MySQL的系统权限相关表

update user set Host = '%' where Host = 'localhost' and User='root';

flush privileges;
