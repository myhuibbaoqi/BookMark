# idea新建一个Spring Boot项目+项目目录简单介绍+项目打包运行+导入Module项目无法识别问题（全部报红或灰色）解决
---
@[toc]
+ 本文主要记录首次使用idea创建Spring Boot项目过程以及常见问题，适合初学者。在此之前使用eclipse，打包一般为war包，使用外部tomcat方式部署项目。
另外spring boot项目内置tomcat，可以将项目打成jar包直接部署。
+ 首先建议更改自己的maven仓库，更快下载所需jar包：[修改maven仓库秒下依赖](https://blog.csdn.net/qq_39231769/article/details/102672272)
---
## 一、新建Spring Boot jar包项目
1. ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzM2MDU2NjIucG5n?x-oss-process=image/format,png)
2. ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzM2Nzg1ODgucG5n?x-oss-process=image/format,png)
3. ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzM3MDczMjgucG5n?x-oss-process=image/format,png)

---

## 二、 新建Spring Boot war包项目
+ 新建项目选项不同处： ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzU5MTk0NDUucG5n?x-oss-process=image/format,png)
+ 添加外部tomcat的pom依赖
```javascript?linenums
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-tomcat</artifactId>
   <scope>provided</scope>
</dependency>
```

+ 新建web.xml
1. ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzY2MjQwNzAucG5n?x-oss-process=image/format,png)
2. 然后选择Modules，点击web（如果没有就点击左上角的加号新建一个），接着双击下方的Web Resource Directory中的第一项，这里是来设置webapp的路径，一般是自动设置好了的，直接点ok，然后点yes。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzY2OTgwNDIucG5n?x-oss-process=image/format,png)
3. 最后点击上面的加号新建web.xml
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzY3MjMxNTgucG5n?x-oss-process=image/format,png)
4. 这里要注意路径，要放到刚才创建的webapp文件夹内。点击ok，然后再点击ok，web.xml就创建好了。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzY3NTMxNDgucG5n?x-oss-process=image/format,png)

+ 到此war包项目创建完毕，war包项目可使用外部tomcat运行。
---

## 三、项目目录简单介绍
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzU3NDM5MTQucG5n?x-oss-process=image/format,png)

---
## 四、项目打包运行
1. 右侧maven，找到项目，install
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODYwMjI5MTEucG5n?x-oss-process=image/format,png)
2. jar包运行（主机有jdk）
```javascript?linenums
java -jar 包名
//Linux中后台运行
nohup java -jar 包名 &
```
3. war包运行（tomcat的webapps文件夹下）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODYzMTkyNjgucG5n?x-oss-process=image/format,png)

---

## 五、新手常见问题--module转移后项目全部变灰色或报错。
+ 现象如图
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODUyMDA2MjAucG5n?x-oss-process=image/format,png)
+ 解决
1. 在idea右侧找到maven
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODUyNDkwOTgucG5n?x-oss-process=image/format,png)
2. 发现此处没有该module
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODUzNTE1MjgucG5n?x-oss-process=image/format,png)
3. 添加该module的pom.xml
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODU0NDE3OTIucG5n?x-oss-process=image/format,png)
+ 问题解决
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODU1MTA4MjUucG5n?x-oss-process=image/format,png)
