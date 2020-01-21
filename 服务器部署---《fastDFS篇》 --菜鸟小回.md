﻿# 服务器部署---《fastDFS篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)
接上篇：
[服务器部署---《redis篇》](https://blog.csdn.net/qq_39231769/article/details/102649996)

---

## 六、fastDFS（安全组开启22122、23000端口）
1. 创建：`mkdir /opt/fastDFS`
2. 进入：`cd /opt/fastDFS`
3. 下载libfastcommon：`wget https://github.com/happyfish100/libfastcommon/archive/V1.0.7.tar.gz`
4. 解压：`tar -zxvf V1.0.7.tar.gz`
5. 编译安装
```javascript?linenums
cd libfastcommon-1.0.7
./make.sh
./make.sh install
```
6. 创建软链接
```javascript?linenums
ln -s /usr/lib64/libfastcommon.so /usr/local/lib/libfastcommon.so
ln -s /usr/lib64/libfastcommon.so /usr/lib/libfastcommon.so
ln -s /usr/lib64/libfdfsclient.so /usr/local/lib/libfdfsclient.so
ln -s /usr/lib64/libfdfsclient.so /usr/lib/libfdfsclient.so 
```
7. 下载fastDFS: `wget https://github.com/happyfish100/fastdfs/archive/V5.05.tar.gz`
8. 解压：`tar -zxvf V5.05.tar.gz`
10. 编译安装
```javascript?linenums
cd fastdfs-5.05
./make.sh
./make.sh install
```

11. 建立软连接
```javascript?linenums
ln -s /usr/bin/fdfs_trackerd   /usr/local/bin
ln -s /usr/bin/fdfs_storaged   /usr/local/bin
ln -s /usr/bin/stop.sh         /usr/local/bin
ln -s /usr/bin/restart.sh      /usr/local/bin
```
12. 配置FastDFS跟踪器
```javascript?linenums
cd /etc/fdfs
cp tracker.conf.sample tracker.conf
vi tracker.conf
//查找修改如下内容
base_path=/home/idse/fastdfs/tracker
http.server_port=80
//创建上方修改后的目录
mkdir -p /home/idse/fastdfs/tracker
```
13. 启动tracker：
```javascript?linenums
/etc/init.d/fdfs_trackerd start
//查看启动成功
netstat -unltp|grep fdfs
//设置开机自启
chkconfig fdfs_trackerd on
```
14. 配置 FastDFS 存储
```javascript?linenums
cd /etc/fdfs
cp storage.conf.sample storage.conf
vi storage.conf
//查找修改如下内容
base_path=/home/idse/fastdfs/storage
store_path0=/home/idse/fastdfs/storage/file
tracker_server=www.idse.top:22122
http.server_port=80
//创建上方修改后的目录
mkdir -p /home/idse/fastdfs/storage
mkdir -p /home/idse/fastdfs/storage/file
```
15. 启动Storage
```javascript?linenums
/etc/init.d/fdfs_storaged start
//查看 Storage 是否成功启动
netstat -unltp|grep fdfs
//查看Storage和Tracker是否在通信：
/usr/bin/fdfs_monitor /etc/fdfs/storage.conf
//设置 Storage 开机启动
chkconfig fdfs_storaged on
```
16. 修改 Tracker 服务器中的客户端配置文件 
```javascript?linenums
cd /etc/fdfs
cp client.conf.sample client.conf
vi client.conf
//查找修改如下内容
base_path=/home/idse/fastdfs/client
tracker_server=www.idse.top:22122
//创建上方修改后的文件夹
mkdir -p /home/idse/fastdfs/client
```
17. 上传测试
```javascript?linenums
/usr/bin/fdfs_upload_file /etc/fdfs/client.conf /ti.jpg
//返回所传图片地址
group1/M00/00/00/rBDsh12jLdKAZCXFAAGTJAL2pIQ680.jpg
//查看该图片
cd /home/idse/fastdfs/storage/file/data/00/00
ls
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzUyMTQ2NzcucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzU1MTYxMjYucG5n?x-oss-process=image/format,png)

18. nginx中配置访问
```javascript?linenums
vi /usr/local/nginx/conf/nginx.conf
//插入如下代码到nginx.conf
//fastDFS图片上传配置
server {
        listen       80;
        server_name  120.27.244.176;

        location / {
                root   html;
                index  index.html index.htm;
        }
        location /group1/M00{
                alias /home/idse/fastdfs/storage/file/data;
        }
}
//重启nginx
cd /usr/local/nginx/sbin/
./nginx -s reload
```
19. 浏览器访问图片 `http://120.27.244.176/group1/M00/00/00/rBDsh12jLdKAZCXFAAGTJAL2pIQ680.jpg`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzY0MTA3MzYucG5n?x-oss-process=image/format,png)
---

接下篇：
[服务器部署---《mycat篇》](https://blog.csdn.net/qq_39231769/article/details/102650077)

附加篇：
[java中使用fastDFS上传图片(前端ajax+后端ssm)](https://blog.csdn.net/qq_39231769/article/details/102673170)

---
