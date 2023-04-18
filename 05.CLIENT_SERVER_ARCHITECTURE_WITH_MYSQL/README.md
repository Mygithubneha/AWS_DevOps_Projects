# Implementing a Client Server Architecture Using MySQL server and MYSQL client
#

## Project Architecture
![project_architecture]![](1.project_architecture.jpg)

![]![](1.ec2-login.jpg)
![create_ec2]

To demonstrate Client-Server architecture we will be using two Ec2 instance with mysql-server and mysql-client respectively.
- Name one instance Mysql-server the other Mysql-client
  
![create_server_client]![](4.created_server&client.jpg)

Create and configure two Linux-based virtual servers (EC2 instances in AWS). <br/>
**Note**: <u>Make sure they are both in same subnet</u>

On mysql server Linux Server install MySQL Server software.
![](5.install_mysql_server.jpg)
![](6.mysql_server_running.jpg)


On mysql client Linux Server install MySQL Client software.
![](7.1.mysql-client.jpg)
![](7.install_mysql_client.jpg)

Open port 3306 on Mysql-server allow for connection. Both server can communicate using private IPs since they belong to the same subnet
![](8.server-SG.jpg)

Change bind-address on Mysql-server to allow for connection from any IP address. Set the bind-address to 0.0.0.0 using the command below:

sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
![](9.bind_port.jpg)

Configure MysQL server and create database and user
- Set up password with `sudo mysql_secure_installation` and create a user
- Create database
    
    ![](10.db-permission.jpg)
    

- grant all permission on database
    
    ![](10.db-permission.jpg)

From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH. You must use the mysql utility to perform this action.
    ![](12.db_connected.jpg)
   ![](11.db-connected-remotely.jpg)

Check that you have successfully connected to a remote MySQL server and can perform SQL queries. You should something similar to the screenshot below:

![](12.db_connected.jpg)