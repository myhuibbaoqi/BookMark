# 服务器部署---《mysql篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)
接上篇：
[服务器部署---《tomcat篇》](https://blog.csdn.net/qq_39231769/article/details/102649832)

---
## 三、mysql（安全组开启3306端口）
<font color=red size=5>所有确认操作均为：y </font>
1. 安装 wget 下载器：`sudo yum install wget`
2. 创建：`mkdir /opt/mysql`
3. 进入：`cd /opt/mysql/`
4. 安装
```javascript?linenums
wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
//用 yum 安装MySQL Yum
yum localinstall mysql57-community-release-el7-8.noarch.rpm
安装 MySQL
yum install mysql-community-server
```
5. 启动
```javascript?linenums
//启动 MySQL
systemctl start mysqld
//设置开机启动 MySQL
systemctl enable mysqld
systemctl daemon-reload
```
6. 查看密码：`sudo grep 'temporary password' /var/log/mysqld.log`
密码：`qGOzkVMGZ0%A`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTM3NjYxOTUucG5n?x-oss-process=image/format,png)
7. 设置新密码
```javascript?linenums
sudo mysql_secure_installation
//输入临时密码
qGOzkVMGZ0%A
//输入新密码（大写+小写+数字+符号）
***********
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTQ1OTgwNzIucG5n?x-oss-process=image/format,png)

8. 开启端口3306
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTU5NTIwOTUucG5n?x-oss-process=image/format,png)

9.  改变策略让root远程连接，或者创建新用户去远程连接
```javascript?linenums
//1. 登录,-u账号 -p密码
 mysql -uroot -p521521
//2. 进入mysql:
 use mysql;
//3.更新user表数据，添加远程访问权限；
update user set Host='%' where User='root';
//4.刷新属性
flush privileges;
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTYyMTM0NDYucG5n?x-oss-process=image/format,png)

10. navicat远程连接
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTY0ODE1MjAucG5n?x-oss-process=image/format,png)

---
接下篇：
[服务器部署---《nginx篇》](https://blog.csdn.net/qq_39231769/article/details/102649976)

---
