# 阿里云服务器配置 + Linuxs系统安装 jdk、tomcat、MySQL汇总详细教程 + 项目上线发布中的部分小bug解决方案 --菜鸟小回
---
@[toc]
---
<font color=green size=5> 写在前面：
学了编程后就想知道自己写好的项目到底如何发布上线。却总停留在局域网访问范围...
Linuxs操作系统不会，网上教程太杂，云服务器还要钱，怕成功不了...还...屡次望而却步！
此次终于下定决心。问各路大神，跑各方博客，查各种百科，读各种开发文档...踩坑无数...然后...成功发布上线
。

[项目预览](http://www.idse.top)（比较low，勿喷哈...）
[项目下载](https://download.csdn.net/download/qq_39231769/11689461)(有需要的自行下载)
基础太差，编写不易，为编写此教程不缺失步骤，将辛苦配好的服务器初始化后重新配置，步步截图。甚至有少许啰嗦。望多多包涵！
</font>

---

所需软件打包：[Xshell+Xftp+navicat+tomcat+jdk]( https://pan.baidu.com/s/1BODnbuXlnNwre7OAO3CuSA ) 	提取码: bdqj （均可去官网自行下载，tomcat及jdk注意下载Linuxs系统下的！）

---
## 一、本机安装远程连接软件（远程软件用于简化操作，大神请忽略）
1. 自行下载安装Xshell（连接远程Linuxs系统）
2. 下载解压Xftp，解压后绿化再打开（配合Xshell与Linuxs进行文件传输）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MDkzLnBuZw?x-oss-process=image/format,png)
3. 下载安装Navicat，按照文档教程破解（连接远程MySQL数据库）

---

## 二、申请阿里云ECS
1. 注册阿里云账号：
[阿里云](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=e3v6m6yo)
3. 实名认证
4. 申请 云服务器ECS
+ 24岁以下可以去活动页买优惠的（位置如下；土豪跳过）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MjM3LnBuZw?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTU2LnBuZw?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTU0LnBuZw?x-oss-process=image/format,png)

---

## 三、 设置ECS远程控制
1. 找到你的ECS服务器
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTYxLnBuZw?x-oss-process=image/format,png)
2. 设置远程连接密码（首次使用默认分配密码登录，注意复制系统提示的默认密码）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTY5LnBuZw?x-oss-process=image/format,png)
3. 同样方法设置自己的实例密码（用于Linuxs系统启动）

4. 进入详细设置
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTcxLnBuZw?x-oss-process=image/format,png)
5. 点击远程连接
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTc3LnBuZw?x-oss-process=image/format,png)

6. 输入账号：“root” 密码：“实例密码” 进入系统（输入密码时无提示，直接输入就可以）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTc5LnBuZw?x-oss-process=image/format,png)

<font color=red size=5>致此处说明已经你的云服务器主机可以正常使用，但对于不会Linuxs系统的菜鸟来说，接下来可以使用远程连接工具操作了 </font>

## 四、使用Xshell连接远程Linuxs
1. 进入Xshell，新建连接
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTgyLnBuZw?x-oss-process=image/format,png)
2. 复制你的ECS公网ip到主机名点击“测试”
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTg2LnBuZw?x-oss-process=image/format,png)
3. 弹出提醒登录账号密码（就是你设置的实例 账号：root 密码：（实例密码））
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTg3LnBuZw?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTg5LnBuZw?x-oss-process=image/format,png)

4. 成功登录
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTkwLnBuZw?x-oss-process=image/format,png)
<font color=red size=5>注：出现下图情况可以忽略，强迫症可以去左上角 “文件”->“属性”->“隧道”->“勾去 转发X11连接到(X)”重新登录就正常啦！！ </font>
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTk1LnBuZw?x-oss-process=image/format,png)

---

## 五、配置Linuxs系统(重点到了)

<font color=red size=5>tips：粘贴代码使用“shift+insert” </font>
### 1. jdk安装与环境变量配置
1. 官网下载或使用我包中的压缩包（.tar.gz 文件）：
    ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTk2LnBuZw?x-oss-process=image/format,png)
2. 下载以后Xshell输入如下命令：
```javascript?linenums
//在usr文件夹下新建java目录
mkdir /usr/java
//进入java目录
cd /usr/java
//激活上传操作
yum -y install lrzsz
```
+ 激活成功
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MTk3LnBuZw?x-oss-process=image/format,png)

3. 进入xftp可视化工具，用于传输windows上下载好的jdk
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MjAyLnBuZw?x-oss-process=image/format,png)
+ 压缩包到Linuxs上（直接如图拖拽并等待上传）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MjAzLnBuZw?x-oss-process=image/format,png)

4. 上传完成后解压安装包：
```javascript?linenums
//在创建的/usr/java目录下执行ls，查看压缩包名
ls
//复制文件夹名填到下方压缩包名处，将压缩包解压
tar -zxvf 压缩包名

```
+ 解压完成（可以通过xftp查看）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5MjMxLnBuZw?x-oss-process=image/format,png)
5. 配置jdk环境变量
```javascript?linenums
//进入etc文件夹
cd /etc
//打开profile文件,按shift+i进入编辑模式
vi profile
//配置环境变量,在profile文件中添加如下内容,注意更换到你的版本
export JAVA_HOME=/usr/java/jdk1.8.0_221 
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib:$CLASSPATH
export JAVA_PATH=${JAVA_HOME}/bin:${JRE_HOME}/bin
export PATH=$PATH:${JAVA_PATH}
//按“esc”退出编辑模式,随后按“shift+：”进入命令模式，保存并退出
输入“wq” 回车
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDE4LnBuZw?x-oss-process=image/format,png)
+ 重启你的Linuxs输入"reboot"
`reboot`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDIxLnBuZw?x-oss-process=image/format,png)
6. 查看配置的环境变量
```javascript?linenums

javac 回车

java -version 回车

```
+ javac 配置成功
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDIyLnBuZw?x-oss-process=image/format,png)

+ java -version 配置成功
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDM5LnBuZw?x-oss-process=image/format,png)


### 2. tomcat安装与端口配置
1. 与解压tomcat方法相同，先创建一个tomcat文件夹
```javascript?linenums
//在usr文件夹下新建java目录
mkdir /usr/tomcat
//进入java目录
cd /usr/tomcat
//激活上传操作
yum -y install lrzsz
```
2. 进入xftp可视化工具，用于传输windows上下载好的tomcat
+ 压缩包到Linuxs上（直接如图拖拽并等待上传）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDQwLnBuZw?x-oss-process=image/format,png)

3. 上传完成后解压安装包：
```javascript?linenums
//在创建的/usr/java目录下执行ls，查看压缩包名
ls
//复制文件夹名填到下方压缩包名处，将压缩包解压
tar -zxvf 压缩包名
//修改文件夹名称（注意版本对应你下载的）
mv apache-tomcat-8.5.45 tomcat8
```

+ 解压完成
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDQxLnBuZw?x-oss-process=image/format,png)

<font color=red size=5>tips：tomcat端口号可使用xftp去“/usr/tomcat/tomcat8/conf”下的server.xml处修改，修改方法与Windows上相同 </font>
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDQ1LnBuZw?x-oss-process=image/format,png)

4. 启动tomcat
```javascript?linenums
//进入tomcat的bin目录
cd /usr/tomcat/tomcat8/bin
//启动tomcat,输入
./startup.sh 回车
```
5. 浏览器访问测试
```javascript?linenums
//ip和端口号换成你的
http://47.105.221.156:8080/
```
+ 成功访问：完成tomcat安装
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDQ4LnBuZw?x-oss-process=image/format,png)

<font color=red size=5>检查网址正确后仍然无法访问</font> 
+ 莫慌，回到阿里云控制台，找到“本实例安全组”->“配置规则”：
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDUyLnBuZw?x-oss-process=image/format,png)
+ 添加端口
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDUzLnBuZw?x-oss-process=image/format,png)
+ 端口范围按照你设置的端口来填，授权对象“0.0.0.0/0”
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDU1LnBuZw?x-oss-process=image/format,png)

+ 保存后重启你的Linuxs <font color=red size=5>重启后仍无法看到主页。请耐心等待20分钟，可以先继续其他步骤，因为开放端口过程需要给阿里一定时间去配置。只有第一次配置如此！</font>，重新访问tomcat首页，解决！

6. 使用eclipse把你的项目打为war包。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDU2LnBuZw?x-oss-process=image/format,png)

7. 上传到Linuxs的“/usr/tomcat/tomcat8/webapps”目录下；重启tomcat
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDU4LnBuZw?x-oss-process=image/format,png)
```javascript?linenums
//进入bin文件夹
cd /usr/tomcat/tomcat8/bin
//关闭tomcat
./shutdown.sh
//查看是否成功关闭
ps -ef|grep java
//如果出现以下信息，则表示Tomcat已经关闭
root 19955 19757 0 17:48 pts/0 00:00:00 grep java
//启动Tomcat
./startup.sh
```
+ 如果显示以下相似信息，说明Tomcat还没有关闭
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDYwLnBuZw?x-oss-process=image/format,png)
```javascript?linenums
//使用kill命令杀死tomcat
kill -9 12778 
//再次查看
ps -ef|grep java
//启动Tomcat
./startup.sh
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDYzLnBuZw?x-oss-process=image/format,png)
+ 发现我们的tomcat中已经有war包解压出的工程
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDY1LnBuZw?x-oss-process=image/format,png)
8. 访问你的项目，完成（无数据库工程）！
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDY2LnBuZw?x-oss-process=image/format,png)

<font color=red size=5>注：需要更换war包工程，先关tomcat；删除原来的war包和解压出的工程；在检查“/usr/tomcat/tomcat8/work/Catalina/localhost”路径下是否有部署的工程，有则删除。导入新包，重启tomcat！（载过坑...）</font>

---

### 3. MySQL安装与配置（非必须，无数据库用户忽略）
1. Xshell输入命令下载安装包
```javascript?linenums
//5.7版本
wget http://repo.mysql.com/mysql57-community-release-el7-8.noarch.rpm
//8.0版本
wget https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
//其他版本自己去官网下yum安装栏找下载路径
//未安装wget的同学执行以下命令安装
sudo yum install wget
```

2. 安装：
```javascript?linenums
//-ivh 后跟你装的对应版本mysql包
sudo rpm -ivh mysql57-community-release-el7-8.noarch.rpm
 
sudo yum install mysql-server
```
+ 输入“y” 确认安装，等待
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NDc1LnBuZw?x-oss-process=image/format,png)
+ 继续“y”，等待
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NTE2LnBuZw?x-oss-process=image/format,png)
+ 完成
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NjI2LnBuZw?x-oss-process=image/format,png)
3. 设置密码
```javascript?linenums
//当第一次启动MySQL服务器时，为MySQL根用户生成一个临时密码。 您可以通过运行以下命令找到密码：
sudo grep 'temporary password' /var/log/mysqld.log

```
4. 如果这个文件为空：
```javascript?linenums
//1.删除原来安装过的mysql残留的数据
rm -rf /var/lib/mysql
//2.重启mysqld服务
systemctl restart mysqld
//3.再去找临时密码
sudo grep 'temporary password' /var/log/mysqld.log
```
+ localhost：后面就是临时密码，复制 hr?=;FsST2fc
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NjI3LnBuZw?x-oss-process=image/format,png)

5. 配置安装项
`sudo mysql_secure_installation`

6. 粘贴你复制的密码，设置新密码（必须包含：密码：大写，小写，数字，字符）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NjI4LnBuZw?x-oss-process=image/format,png)
+ 选择项均为“Y”,确认。看到All done！完成配置。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NjM4LnBuZw?x-oss-process=image/format,png)
+ 尝试访问，成功
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3Nzc4ODk5NjM4LnBuZw?x-oss-process=image/format,png)

## 六、迁移数据库文件
1. 使用可视化软件navicat连接数据库
+ 新建连接
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQ1LnBuZw?x-oss-process=image/format,png)
+ 按照你的公网ip和设置的mysql密码进行连接
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQ1LnBuZw?x-oss-process=image/format,png)
2. 可能出现以下窗口（莫慌，这坑踩过了）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQ2LnBuZw?x-oss-process=image/format,png)
+ 两步走：
    + 第一步：老地方“安全组规则”->增加你的3306端口->重启。<font color=red size=5>重启后仍无法看到主页。请耐心等待20分钟，可以先继续其他步骤！部署项目到tomcat服务器需要一定等待时间，请等待。</font>
    ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDM5LnBuZw?x-oss-process=image/format,png)
    ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDMzLnBuZw?x-oss-process=image/format,png)
    + 第二步：Xhell中进入你的数据库
    ```javascript?linenums
    //1. 登录,-u账号 -p密码
     mysql -uroot -p521521
    //2. 查看数据库：
     show databases;
    //3. 进入mysql:
     use mysql;
    //4. 查看表：
    show tables;
    //5.更新user表数据，添加远程访问权限；
    update user set Host='%' where User='root';
    //重启mysql
    systemctl restart mysqld
    ```
    ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQwLnBuZw?x-oss-process=image/format,png)
+ 重新使用navicat工具连接数据库（踩坑完毕，全体鼓掌！）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQxLnBuZw?x-oss-process=image/format,png)
3. 转储你的项目数据库sql文件到阿里云服务器上的数据库中。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQzLnBuZw?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQyLnBuZw?x-oss-process=image/format,png)


4.  不要忘记修改你的代码，重新上传war包呦！！！
+ 项目上线发布成功，你的项目可以通过你的网址任意网络访问啦！（全体起立！）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODE1NTExNDQ1LnBuZw?x-oss-process=image/format,png)

<font color=red size=5>注：没有缺少任何步骤却无法访问项目的同学，注意：1.修改Linuxs端口后是否重启实例？ 2.修改war包后是否重启tomcat（必要时kill tomcat删除缓存项目重新加载，甚至删除tomcat重新解压。）3.再次检查过程是否缺失步骤！ </font>


<font color=green size=5>至此，项目上线成功。为整理出此教程加班三晚，若对大家有所帮助，请多多点赞转发。跪谢！如若还有问题未成功，私聊即可。</font>
   <font color=red size=5>注：转载请注明出处！！！ </font> 
   接下篇：[《Linuxs系统中修改配置文件使得访问java工程直接通过ip，除去端口号和项目名访问。》](https://blog.csdn.net/qq_39231769/article/details/100603219)
