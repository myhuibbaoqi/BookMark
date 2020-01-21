# Linuxs系统中修改配置文件使得访问java工程直接通过ip，除去端口号和项目名访问。
---
接上篇:[《阿里云服务器配置 + Linuxs系统安装 jdk、tomcat、MySQL汇总详细教程 + 项目上线发布中的部分小bug解决方案》](https://blog.csdn.net/qq_39231769/article/details/100587577)
方法很多，这里只写一种我成功的！

---

1. 删除/usr/tomcat/tomcat8/webapps下的ROOT文件夹
2. 将你的war包改名为ROOT.war
3. 上传ROOT.war
4. 进入你的conf->service.xml
4. 修改端口号为80
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL3B4ZXhjYjFsMi5ia3QuY2xvdWRkbi5jb20vYmxvZy8xNTY3ODQ4Njk5MjIzLnBuZw?x-oss-process=image/format,png)
5. 在下面<Host>  </Host>中添加下面语句，位置填你的项目位置；
`  <Context path="/" docBase="ss"/> `
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191009171005905.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)6.只输入ip访问下试试吧
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190907175234446.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
