# 服务器部署---《nginx篇》
---
汇总篇：
[服务器配置篇汇总（linux）+（jdk）+（tomcat）+（mysql）+（nginx）+（redis）+（fastDFS）+（mycat）](https://blog.csdn.net/qq_39231769/article/details/102571074)
接上篇：
[服务器部署---《mysql篇》](https://blog.csdn.net/qq_39231769/article/details/102649910)

---
## 四、nginx(安全组开启所配置端口)
1. 创建：mkdir /opt/nginx
2. 进入：cd /opt/nginx/
3. 解压：tar -zxvf nginx-1.13.0.tar.gz 
4. 编译：
```javascript?linenums
cd nginx-1.13.0
//安装编译源码所需要的工具和库：
yum install gcc gcc-c++ ncurses-devel perl 
yum install pcre pcre-devel
yum  install zlib gzip zlib-devel
//编译
./configure 
```
5. 安装到默认位置/usr/local/nginx：`make & make install`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTc1NDQ3NjgucG5n?x-oss-process=image/format,png)

6. 启动
```javascript?linenums
cd /usr/local/nginx/sbin/
//启动
./nginx
//重启
./nginx -s reload
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NTc4ODkxMTUucG5n?x-oss-process=image/format,png)

7. 虚拟主机配置
```javascript?linenums
vi /usr/local/nginx/conf/nginx.conf
//在原主页server上写入：

# 虚拟主机的配置

#虚拟主机一（虚拟域名）：
server { 
	listen       8081;   #端口
	server_name  hhh.idse.top;	#域名，虚拟机需要在windows的C:\Windows\System32\drivers\etc的hosts里面配置
				#120.27.244.176 hhh.idse.top
	location / {  
		root  abc; #相当于ningx目录下的hbq目录，可以写成绝对路径  /zhiyou/java 
		index a.html;  #默认跳转页面
	} 
}
#虚拟主机一（真实域名）：
server { 
	listen       8082;   #端口
	server_name  www.idse.top;     #公网域名，配置域名解析到本机ip
       
	location / {  
		root  abc; #相当于ningx目录下的hbq目录，可以写成绝对路径  /zhiyou/java 
		index b.html;  #默认跳转页面
	} 
}
#虚拟主机三（ip）：
 server{ 
	listen	8083;  #端口
	server_name 120.27.244.176; #域名        
	location / {  
		root  abc; #相当于ningx目录下的hbq目录，可以写成绝对路径  /zhiyou/java 
		index c.html;  #默认跳转页面
	}        
}
//创建文件
mkdir -p /usr/local/nginx/abc
vi /usr/local/nginx/abc/a.html  //写入aaa
vi /usr/local/nginx/abc/b.html  //写入bbb
vi /usr/local/nginx/abc/c.html  //写入ccc
//重启nginx
cd /usr/local/nginx/sbin/
./nginx -s reload
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5Njk1Njc0MjMucG5n?x-oss-process=image/format,png)

8. 负载均衡多服务器配置
```javascript?linenums
upstream tomcatserver1 {   #后面的名字自己起的，与下面proxy_pass后面保持一致
        server 120.27.244.176:8080  weight=2; #ip或者主机名都可以
        #server 120.27.244.176:81;
}
server {
        listen       80;   #端口
        server_name  www.idse.top;     #域名，虚拟机需要在windows的hosts里面配置

        location / {
        proxy_pass   http://tomcatserver1;    #代理，会更具名字找到上面的
        }
}

```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzA5NzA1ODUzNDMucG5n?x-oss-process=image/format,png)---
接下篇：
[服务器部署---《redis篇》](https://blog.csdn.net/qq_39231769/article/details/102649996)

---
