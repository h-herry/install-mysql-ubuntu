# install-mysql-ubuntu

在Ubuntu上安装MySQL

sudo apt update -y

sudo apt install mysql-server -y

sudo systemctl status mysql

sudo mysql_secure_installation


登录mysql 回车

mysql -h localhost -u root -p

use mysql;

update user set host='%' where user ='root';

flush privileges;

alter user 'root'@'%' identified with mysql_native_password by 'mysql123456';

mysql> select user,host from mysql.user;

如果查看到的'user'和'host'都是'root'和'%'，说明我们已经成功地开启了MySQL的远程访问功能。

上面的步骤中，我们已经开启了MySQL的远程访问功能，但是，如果使用MySQL管理工具navicat连接MySQL服务端时，还是可能会出现连接失败的情况。这是因为MySQL默认只允许本地访问。

使用vi 命令打开my.conf文件：

vi /etc/mysql/my.conf

在my.conf文件中，我们需要找到bind-address=127.0.0.1这一行，并把它改为bind-address=0.0.0.0。然后，我们需要重启MySQL服务端：

service mysql restart

这样就可以实现外部IP地址对MySQL服务端的访问了。
