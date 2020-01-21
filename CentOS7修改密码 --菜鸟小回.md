# CentOS7忘记密码,修改密码。
1. 开机选择你要修改密码的系统
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191021211751176.png)
2. 找到修改 `ro` 为 `rw` 
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NTkxNjY4MDQucG5n?x-oss-process=image/format,png)
3. 本行最后继续添加 `init=/sysroot/bin/sh` 
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NTk2MDg5MTgucG5n?x-oss-process=image/format,png)
4. ctrl+x 进入如下界面
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NTk2NDY5ODAucG5n?x-oss-process=image/format,png)
5.分别输入命令
```javascript?linenums
//进入系统环境里面
chroot /sysroot 
//进入系统环境里面
passwd root 
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NTk3NzQ5NzAucG5n?x-oss-process=image/format,png)

6. 出现方框说明乱码
```javascript?linenums
//退出输入
ctrl+c
//修改语言
LANG=en
//重新修改(root为你想修改的用户名)
passwd root 
//创建开机项
touch /.autorelabel 
```
[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-YhvrY0wi-1571663816403)(http://hbq.idse.top/blog/1571659959517.png)]

7. 重启
```javascript?linenums
//退出当前模式
exit
// 重启
reboot
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjA4MzQ1ODYucG5n?x-oss-process=image/format,png)
<font color=red size=5>博主测试两台虚拟主机，均用上述方式两次成功修改。原因未知；如有一次修改无效的情况建议也再重复一次。如有解决办法，烦请告知。。。</font>
