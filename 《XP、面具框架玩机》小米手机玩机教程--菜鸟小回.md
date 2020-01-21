# <center>《框架玩机》小米手机玩机教程

---

<center><font color=red>注：刷机有风险，玩机需谨慎。
 操作不当所造成后果与菜鸟小回无关！！！

---

今天来分享小米手机玩机技巧，Magisk面具+Xp框架!
可能你多上面的名词还有些陌生。
但下面的手机功能你应该是听说过的，刷步数，虚拟定位，蚂蚁森林自动偷能量，QQ,微信自动抢红包，防撤回，防闪照......也是因为近期好多朋友问我如何实现一些特殊功能，才有我现在的分享！
看下部分功能：
**1.部分模块预览**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717212437872.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717212459469.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

---

**2.部分模块功能预览**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717212904854.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717213134384.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717213006449.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071721305823.gif)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717213224465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717213258129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

部分功能展示完毕，是不是有一丢丢心动呢？以上功能均为本人在用，再提醒一次，刷机过程可能存在数据清除，卡米，无限重启等等后果，虽均有处理方案，但还是**不建议玩机新手学习**。**后果自负！！！**


---
教程开始（小米9为例）：
**主分六步：**
 **1.刷开发版系统
 2.解BootLoader锁
 3.解锁手机root权限
 4.刷入面具并安装
 5.刷入Xposed框架
 6.刷入所需模块**
## 一、先给你的手机来一个开发版系统 
此处较为简单，但注意更换版本需要<font color=red>清理掉手机所有数据，请**及时备份**！！！</font>
[最新开发版包下载](http://www.miui.com/getrom-357.html?m=yes&mobile=2)
1.首先在官网下载最新卡刷包到手机（记住放的位置，无需解压）。

2.在系统更新界面点击中间10十下即可激活隐藏功能，右上角点击从本地选择安装包更新。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719180015729.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
3.选择刚才下载的zip文件就可以了。***注意备份一下数据哦！***

## 二、解BootLoader锁
1.在小米官方申请小米解锁        [解锁地址](http://www.miui.com/unlock/index.html)

2.填写申请解锁信息，然后会出现申请成功，然后就等待小米公司发来的解锁通过短信为基准
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717214550670.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)3.解锁申请通过后请到小米申请解锁链接中下载小米手机解锁工具。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717214643214.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)4.下载解压之后点击图片中的MiUsbDriver进行安装驱动，如果检测已安装可以忽视此过程。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717214702110.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)         5.安装成功后我们现在就可以打开miflash_unlock解锁软件了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071721473080.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)点击登录小米账号
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717214756804.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)6.接下来我们可以来绑定手机设备了。找到手机设备信息，连续点击MIUI系统版本号开启开发者模式。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717214830505.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)在设置—更多设置中找到开发者模式
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071721491542.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70) 7.在开发者模式里面找到设备就锁状态，小米账号绑定此设备。如图下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071721494427.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)8.绑定后我们再打开解锁工具。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717215002240.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
这时会显示当前未连接手机，我们需要关机手机，“音量键减+开机键同时按”，进入fastboot模式
此时会出现一只小兔子，解锁工具会显示已连接手机
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717215018579.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)    9.点击下面的解锁按键，出现正在解锁当中。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717215040348.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)如果出现解锁失败或者是请绑定设备开机后检查是否绑定
重启到fastboot模式重新解锁即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071721511224.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)开机后找到开发者模式，如果显示已解锁，说明你就成功了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190717215127684.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
**到此为止，你的手机已经解锁成功。**

---
## 三、解锁root权限
1.回到安全中心，**应用管理**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190718082633430.png)

2.点击 **权限**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190718082729355.png)



3.点击**root权限管理**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190718082417501.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)4.勾选同意服务，等待进度条走满手机自动重启

5.重启完成后再回到当前位置查看，可以看到已经可以管理root权限了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190718082937718.png)

---
## 四、刷入面具并安装

 - **工具：**

1.可手机百度 **酷安**并下载安装--->酷安app中搜索 **"Magisk "** 下载安装。
2.直链MD2版本（小米九直接刷正版会有BUG），[Magisk MD2](https://pan.baidu.com/s/1YOmSXFhsAqYwrMDZrUFoXQ)

---

 - **过程：**
1.打开Mgisk看到此页面。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719110319685.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
2.开启Maisk ROOT权限:
		返回桌面“**安全中心**”-->“**应用管理**”-->“**权限**”-->"**ROOT权限管理**"-->**选上Magisk**（多次警告全部同意）
3.(**清理后台或重启手机后**)重新进入Maisk-->点击左上角**菜单栏**看到如下菜单，点击“**设置**”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719120413214.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)4.找到“**更新通道**”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719120713394.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)5.选择“**测试版**”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719120932747.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)6.回到Magisk主页面安装Magisk
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719121057917.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)7.选择“直接安装”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719121421837.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
8.等待刷入，显示“All done”，安装成功（若出现安装进度条卡死，请更换网络重试，一般联通流量成功率高）；重启面具安装完成。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719121335842.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
---

9.装入所需模块：

 - 面具模块汇总链接:

 https://pan.baidu.com/s/1quxdJ7adXW0K_zGEdtpr5g 提取码: 2xc3 
 
 下载需要模块**记住所放位置**(无需解压)，
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071915394113.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)10.Magisk主页面左上方**菜单栏**-->“**模块**”（找不到说明前面步骤出了问题，解决问题后再试）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719154343656.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

11.“**选择下好的zip格式模块**”-->自动安装，成功后重启生效。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719154710604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
12.重启后再次来到 **“模块”** 这里，整个面具模块完成。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719155035825.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)



---
 ### 五、刷入Xposed框架
 - 工具：

 模块链接: https://pan.baidu.com/s/1uG20BzMt4sxS2jWy2dWJmw 提取码: b35f 
 
 XP框架链接: https://pan.baidu.com/s/1k-X82grYKILiZLi6b7O4xA 提取码: whxr 

 - 过程：
 
 1.下载第一个模块链接内两个zip文件
 2.进入magisk模块，刷magisk-riru-core模块，然后刷magisk-EdXposed模块。（方法见上方Magisk模块安装过程）
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719162943350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
 
 3.下载第二个链接内EdxposedInstaller.apk，安装EdxposedInstaller.apk，看到以下页面表示xp框架安装成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719163950216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
 
 ----
 ###  六.刷入XP模块

 - 工具：

XP模块汇总: https://pan.baidu.com/s/1J3hwznpkBn31m89Mrayw3A 提取码: titr 
文章头预览模块汇总： https://pan.baidu.com/s/1u-7EHtWwCfoLS9umWA6CuQ 提取码: c2yq 
（含QQ模块、微信模块、支付宝刷步模块、蚂蚁森林&庄园模块）

 - 过程：
 1.只需下载上方需要模块，APK格式，直接安装。
 2.安装成功后打开XP软件，左上角菜单栏点击选择“**模块**”
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190719171523374.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
 3.进入XP主页，找到菜单，选择“**模块**”，打上对勾**重启**即可。
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/2019071916562814.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
 <font color=red>注：如果打开支付宝森林模块和运动模块未生效，可更换支付宝版本。
 [支付宝10.1.38版本](https://pan.baidu.com/s/1WZDmRsMZEieeHTSFh1Hy6g)提取码:3m69
 ----
 
 

<center><font color=green size=6 face="楷体">完成了，飞奔吧！</font>
