# 服务器部署---《jdk篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)

---
## 一、jdk
1. 创建：`mkdir -p /opt/java`
2. 进入：`cd /opt/java`
3. 上传：![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NDkyMDU1MTkucG5n?x-oss-process=image/format,png)
4. 解压：`tar -zxvf jdk-8u141-linux-x64.tar.gz`
5. 编辑：`vi /etc/profile`
6. 配置环境变量：
```javascript?linenums
//进编辑模式
i 
//文档最后添加：
export JAVA_HOME=/opt/java/jdk1.8.0_141
export PATH=$PATH:$JAVA_HOME/bin
//保存退出
ESC
:wq
//更新配置
source /etc/profile
```
7. 验证：输出长内容
```javascript?linenums
java
javac
java -version
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTAyNzk2MTcucG5n?x-oss-process=image/format,png)

---
接下篇：
[服务器部署---《tomcat篇》 ](https://blog.csdn.net/qq_39231769/article/details/102649832)

---
