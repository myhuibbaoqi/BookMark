# Eclipse修改maven仓库到自定义位置+添加阿里依赖秒下jar包
---

+ 大家在刚开始使用eclipse使用坐标下载maven的jar包时一定出现过下载过慢或者缺包错误等等问题。出现该问题一般是因为使用系统默认的maven仓库，也就是用户.m2下的仓库。解决思路就是自己创建一个新的本地仓库。并使用国内阿里镜像下载。完美解决！

+ maven3.6.2包
链接:
[maven3.6.1包](https://pan.baidu.com/s/1rB9nUDpUeH3jqkQswY4Wwg) 提取码: 363w 
 [maven3.6.2包](https://pan.baidu.com/s/1NKiPmVThKb1mUyVvKw9FHQ&shfl=shareset) 提取码: 4cks 


---
## 一、Eclipse
1. 解压我们的maven包。
2. 新建一个空文件夹作为你的maven仓库
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjI0NjgyMDMucG5n?x-oss-process=image/format,png)
3. 找到D:\maven\apache-maven-3.6.2\conf目录下setting.xml修改配置：
```javascript?linenums
//ctrl+f搜索“repository”在注视下方加入下边语句，路径改为你新建的仓库路径（注意不要加在注释代码内）
 <localRepository>D:\maven\repository</localRepository>
//Ctrl+f搜“mirrors”注释下方添加阿里镜像
<mirror>
      <id>alimaven</id>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>        
</mirror>
```
[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-qWX3iTvz-1571663972281)(http://hbq.idse.top/blog/1571662661666.png)]
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjI4MjUxODcucG5n?x-oss-process=image/format,png)

4. 进入eclipse配置新的maven
+ `Window -> preferences -> maven -> installations -> add`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjI5OTUzNjEucG5n?x-oss-process=image/format,png)
+ 选择刚配置的maven
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjMxNDUxOTMucG5n?x-oss-process=image/format,png)
+ 勾选，应用
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjMyNzI5MjMucG5n?x-oss-process=image/format,png)

5. 更换新的仓库
+ `Window -> preferences -> maven -> user sertting -> browse`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjMzNDg1MDMucG5n?x-oss-process=image/format,png)
+ 找到我们刚才修改的setting设置，选中。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjM0MzM1OTQucG5n?x-oss-process=image/format,png)
+ 可以看到仓库已经自动由默认仓库换为我们自定义的
+ `updata settings ->APPLY -> OK`
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE2NjM1NTY4MzIucG5n?x-oss-process=image/format,png)

6. 导入你的pom依赖飞速下载吧！！！

## 二、idea
1. 点击File-settings
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191116112136377.png)
2. 设置maven![在这里插入图片描述](https://img-blog.csdnimg.cn/20191116112240693.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
3. 设置setting.xml位置和仓库位置。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191116112640599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)<font color=red size=5> 注：请使用idea请使用maven3.6.1版本</font>
