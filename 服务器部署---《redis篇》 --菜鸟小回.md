# 服务器部署---《redis篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)
接上篇：
[服务器部署---《nginx篇》](https://blog.csdn.net/qq_39231769/article/details/102649976)

---

## 五、redis(安全组开启6379)
1. 创建：`mkdir /opt/redis`
2. 进入：`cd /opt/redis`
3. 解压：`tar -zxvf redis-5.0.3.tar.gz`
4. 编译：
```javascript?linenums
cd redis-5.0.3
make
```
5. 安装：`make install`
6. 创建新目录方便管理：`mkdir -p /opt/redis/redis-5.0.3/bin`
7. 拷贝文件：
```javascript?linenums
cd src/
cp redis-server /opt/redis/redis-5.0.3/bin/
cp redis-benchmark /opt/redis/redis-5.0.3/bin/
cp redis-cli /opt/redis/redis-5.0.3/bin/
cp /opt/redis/redis-5.0.3/redis.conf  /opt/redis/redis-5.0.3/bin/
```
8. 修改配置文件
```javascript?linenums
//修改配置文件
vi redis.conf
//找到daemonize no改为：
daemonize yes
//找到bind 127.0.0.1改为
#bind 127.0.0.1
//找到protected-mode yes改为
protected-mode no

```
9. 启动：` ./redis-server redis.conf`
10. 测试：
```javascript?linenums
./redis-cli 
set key "hello world!"
get key
//得到hello world!成功
```
10. 远程连接，先创建安全组6379端口！

![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzIwMjEzMTgucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzIxMjcwNTAucG5n?x-oss-process=image/format,png)

---
接下篇：
[服务器部署---《fastDFS篇》](https://blog.csdn.net/qq_39231769/article/details/102650042)

---
