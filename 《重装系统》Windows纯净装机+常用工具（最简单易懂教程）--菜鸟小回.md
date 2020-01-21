# <center>重装系统教程
---
+ 入门IT第一步，来一个干净的电脑系统吧？
@[toc]
***（装机需谨慎，系统盘必须格式化，其他风险自测。）***
本教程提供两种重装系统方式，两种均为纯净装机,均需要U盘。
1、PE 重装，此方式会为装机者提供更多工具，包括分区大师，电脑密码解除等等工具。
2、ISO重装，此方法傻瓜式操作，简单快捷，一键重装。

---
## <center>PE重装
---
+ **工具:**
		1、8G以上U盘
		2、微PE工具：
						连接：[PE工具](https://pan.baidu.com/s/1FU0OW49XkVvVaHi1tDuv3A)
						[提取码]：qmea
		3、操作系统（此处提供纯净win10）：
						链接: [win10](https://pan.baidu.com/s/1DKSGIZZkfAxcvZ59oEe-kQ)
						[提取码]：6666
---
+ **过程：**
### 一、制作PE U盘
1.下载微PE工具，win10系统：

2.格式化U盘：
鼠标右击插入的U盘，选择“格式化”，在文件系统处选择“NTFS”，点击“开始”（格式化时，文件系统选择NTFS是为了U盘能够存储单个内存大于4G的文件）。

3.点击“安装PE到U盘”。
![](https://img-blog.csdnimg.cn/20190716211237158.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
4.点击“立即安装进U盘”（U盘卷标显示的名称为自己插入U盘的名称）。

5.点击“开始制作”。

6.将下载好的win10系统复制入U盘中

### 二、系统BIOS选择（不同电脑不同）：
---
**1.进入BIOS设置，一般快捷键根据电脑有所不同；**
+ 普通电脑：度娘搜对应电脑开机快捷键，格式：*xxx型号电脑BIOS设置U盘为第一启动项*

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716211529128.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
+ 特殊电脑（联想系列部分新机）;

关机状态用卡针点击电脑上的小孔（类似手机装卡孔）

**2.BIOS设置（不同电脑设置难易程度不同）：**
（此处为联想笔记本）进入BIOS~——>按→光标移动到boot——>设置页面如下图一：——>按→光标到exit
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716211815515.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716211831718.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
***注：***

***此过程的目的就是在启动电脑选择系统时选择到你的U盘启动，而不是电脑自己的硬盘。
所以虽然有多种启动方式，其过程一般在BOOT设置栏，看到自己的U盘，将其优先级别提高。
如：***
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717133532308.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)***简单的电脑一般可以直接选择启动盘，直接点击即可。如：***
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717133712338.png)

---
### 三、PE系统重装Windows
---
 ~~如需重新分盘或者格式化全盘，获得一个新的电脑系统请继续阅读本段：
如需保留系统盘外磁盘内容，跳过本段，否则数据丢失不负责呦！
打开分区助手——>点击快速分区——>执行即可
快速分区弹窗出现提示，需要注意以下几点
1.磁盘类型选择【MBR】
2.分区数目选择：多少个取决需求和硬盘大小
3.分区大小选择：第一个为主分区（即系统安装的分区），
一般建议25-100G左右即可（取决需求和硬盘大小）~~  

----
1、进入“PE系统”后，双击“**CGI备份还原**”。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716212203554.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
2、选择“**还原分区**”，**选择分区盘符为“C盘”**，在“3.请选择镜像文件”处**右侧点击“三个点”**。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716212240586.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
3.选择拷贝到U盘里的“镜像文件”（iso格式），点击“**打开**”。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716212253915.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
4.选择自己所需要安装的版本（我这里选择Windows 7 旗舰版），点击“**确定**”。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190716212317910.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
5.点击“**执行**”。

6.勾选“重启”，点击“**确定**”。

7.正在还原分区。

8.显示“还原成功”，此时拔掉U盘，重启完成。



## <center> ISO重装
----
+ **工具:**
		1、8G以上U盘
		2、软碟通：[软碟通官网](https://cn.ultraiso.net/xiazai.html)（直接免费下载试用）
		3、操作系统（此处提供纯净win10）：
						链接: [win10](https://pan.baidu.com/s/1DKSGIZZkfAxcvZ59oEe-kQ)
						[提取码]：6666

---
+ **过程：**

### 一、制作U盘启动盘
1.首先下载“软碟通”软件，下载后安装，选项默认，***不要自己去勾选***；安装完成后，**不需要**运行此软件。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717105627909.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
2.下载一个win10操作系统，下载的操作系统不要下载在U盘里，电脑的任意一个盘都可以
3、下载好系统后，插好U盘，直接**双击下载好的iso文件**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717110105264.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
弹出以下界面：点击“**继续试用**”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717120317294.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
4、选择左侧“**本地目录**”的U盘盘符，***千万不要选错***，再选择工具拦的“启动”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717120552123.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
5、在选中“**写入硬盘映像**”，（启动项里的第4个），跳出一个对话框，默认设置，直接点“**格式化**”，格式化完成后点“**写入**”，等待**刻录成功**，完成制作。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717120747747.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

### 二、 BIOS设置（同上U盘重装）

### 三、启动电脑,选择系统，划分盘符。
1、U盘启动后你会看见电脑屏幕会变为蓝色装机页面，以下的操作按照提示下一步就可以。
+ 选择自定义：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019112911235216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
2、注意分区时注意事项如上U盘重装注意事项，这里没有分区工具，需要分区请删除原分区，并分配新的大小作为新分区。
+ 删除原有分区
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129112833282.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

+ 新建分区，最先创建出主分区，就是系统盘。或产生引导分区，无需理会。![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129113001692.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
3、新建所有分区后，一直下一步然后等待，就OK。
4、启动系统后，激活系统。链接: [系统+office激活](https://pan.baidu.com/s/1ZZbVCLQxLlZE6PLIrIMJ0g) 提取码: a8d1 
---
以上为两种纯净装机方式；所装的系统是2017年系统，仅存在回收站，可能无驱动。
提供常用装机后、升级 以及 无线网卡驱动：
+ **win10易升：** 链接: [win10易升](https://pan.baidu.com/s/1Tj0QEJuWbNjZzKjduslpFg) 提取码: eqg6 
+ **360驱动大师（无线网卡驱动版）**：链接: [驱动大师](https://pan.baidu.com/s/1ClBRp52xFHqCLxhC9lgrEg)提取码: tywt 
+ **虚拟机(害怕电脑难以恢复的小白可以利用虚拟机进行第一次模拟测试)**:
[虚拟机](https://pan.baidu.com/s/1bTFt1hhPHIZ5YFbatN95bw) 提取码: t4v3


---

