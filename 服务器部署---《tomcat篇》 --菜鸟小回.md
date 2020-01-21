# 服务器部署---《tomcat篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)
接上篇：
[服务器部署---《jdk篇》](https://blog.csdn.net/qq_39231769/article/details/102649799)

---
## 二、tomcat（安全组开启80、8080端口）
1. 创建：`mkdir -p /opt/tomcat`
2. 进入：`cd /opt/tomcat`
3. 上传：![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTA1MDE3MTIucG5n?x-oss-process=image/format,png)
4. 解压：`tar -zxvf apache-tomcat-8.5.34.tar.gz`
5. 改名：`mv apache-tomcat-8.5.34 tomcat-8.5.34`
6. 启动：
```javascript?linenums
cd /opt/tomcat/tomcat-8.5.34/bin/
./startup.sh
```
7. 关防火墙
```javascript?linenums
systemctl stop firewalld.service
systemctl disable firewalld.service
```
8. 开安全组
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTA5ODA2MTYucG5n?x-oss-process=image/format,png)
9. 访问：`http://120.27.244.176:8080` 耐心等待......
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTEzNTA1NDUucG5n?x-oss-process=image/format,png)
10. 修改端口，配置默认访问项目名
```javascript?linenums
//编辑配置文件
vi ../conf/server.xml
//搜索端口
:/8080
改为80
//搜索Host
//添加;root可改为你的项目名
<Context path="/" docBase="root" />
//保存退出
:wq
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTE2NTM3MzAucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTIwMzY1OTkucG5n?x-oss-process=image/format,png)

11. 重启tomcat
```javascript?linenums
cd /opt/tomcat/tomcat-8.5.34/bin/
//关闭
./shutdown.sh
//查看关闭成功（一行输出为成功，多行未成功）
ps -ef|grep java
//未成功，杀死线程
kill -9 线程号
//启动
./startup.sh
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTIzMDY2OTAucG5n?x-oss-process=image/format,png)

12. 访问：`http://120.27.244.176` 等待......
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTI5MzU2MDIucG5n?x-oss-process=image/format,png)

---
接下篇：
[服务器部署---《mysql篇》](https://blog.csdn.net/qq_39231769/article/details/102649910)

---
