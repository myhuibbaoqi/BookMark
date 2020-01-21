# Spring boot与Spring clound 微服务项目搭建流程
---
@[toc]
+ 前言：此博文用于记录Spring boot与Spring clound 项目搭建过程，包含简单数据库查询，逆向工程，常用pom依赖。完整配置Spring clound 项目微服务项目。
<font color=red size=5>注：每次导入pom依赖后请install该module。</font>
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDEyNDczNDMucG5n?x-oss-process=image/format,png)

---

## 一、创建父级parent提供基础jar包
1. 创建maven的moudule
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ0OTkyMjQyNDEucG5n?x-oss-process=image/format,png)
2. 指定父类型都为pom类型，并添加相关依赖
[parent依赖一（1）](https://blog.csdn.net/qq_39231769/article/details/103216219)

---
## 二、创建common为项目提供公用jar包、实体类、工具类等
1. 创建maven类型module
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ0OTkyMjQyNDEucG5n?x-oss-process=image/format,png)
2. 添加父类依赖引用以及项目需要jar包
[common依赖一（2）](https://blog.csdn.net/qq_39231769/article/details/103216219)
3. 在resources下添加逆向工程配置文件generatorConfig.xml
[generatorConfig.xml 二（1）](https://blog.csdn.net/qq_39231769/article/details/103216219)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDA3Njk4MzIucG5n?x-oss-process=image/format,png)
4. 在resources下创建mappers目录用于存放mapper.xml。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDEzOTc0MTUucG5n?x-oss-process=image/format,png)

5. 如图位置运行逆向工程，得到mapper，pojo，mappers
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDEzNzMxMjAucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDE0ODI5NzIucG5n?x-oss-process=image/format,png)

6. 添加所需工具类，如
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDE1Nzk2MTQucG5n?x-oss-process=image/format,png)

---
## 三、创建server提供spring cloud服务
1. 创建spring boot的module
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDE2Nzk3MTgucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDE3NjE2ODMucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDE3NzY4MzEucG5n?x-oss-process=image/format,png)

2. 添加pom依赖引入父类包
[server依赖一（3）](https://blog.csdn.net/qq_39231769/article/details/103216219)

3. 运行主类添加@EnableEurekaServer 注解
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDIwMzk1ODAucG5n?x-oss-process=image/format,png)

4. 配置application.properties服务

```javascript?linenums
#端口
server.port=8000
#application.name
spring.application.name=ttl_server

#通过eureka.client.registerWithEureka：false和fetchRegistry：false来表明自己是一个eureka server.
eureka.instance.hostname=localhost
#registerWithEureka表示是否注册自身到eureka服务器
eureka.client.register-with-eureka=false
#fetchRegistry表示是否从eureka服务器获取注册信息。
eureka.client.fetch-registry=false
eureka.client.service-url.defaultZone=http://${eureka.instance.hostname}:${server.port}/eureka/

```
---
## 四、创建api编写项目源码
1. 创建spring boot的module（步骤同server创建）
2. 添加pom，将common作为jar包引入
[api依赖一（4）](https://blog.csdn.net/qq_39231769/article/details/103216219)

3. 运行主类添加client注解
```javascript?linenums
@EnableEurekaClient
@EnableFeignClients
@ComponentScan("com.zhiyou")
@MapperScan("com.zhiyou.mapper")
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDI3NTYwMzgucG5n?x-oss-process=image/format,png)

4. 配置application.properties客户端
```javascript?linenums
#设置客户端
server.port=8001
spring.application.name=ttl_api
eureka.client.service-url.defaultZone=http://localhost:8000/eureka/

#连接数据库
spring.datasource.url=jdbc:mysql://120.27.244.176:3306/hospital?useUnicode=true&characterEncoding=UTF-8&useSSL=false
spring.datasource.username=root
spring.datasource.password=HBQ521521cf*
spring.datasource.driver-class-name=com.mysql.jdbc.Driver

#设置mapper.xml文件扫描位置
mybatis.mapper-locations=classpath:/mappers/*.xml

#给实体类包起别名
mybatis.type-aliases-package=com.zhiyou.pojo

```
---
## 五、测试程序运行
1. 编写测试程序，查询表中内容
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDMwNjc4OTgucG5n?x-oss-process=image/format,png)
+ controller
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDMyNjc5NDIucG5n?x-oss-process=image/format,png)
+ serviceImpl
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDMyMTA3MzgucG5n?x-oss-process=image/format,png)

2. 先启动server，再启动api。
3. 浏览器输入"http://localhost:8001/found.action"测试
![enter description  here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzQ1MDMzNTM4MzUucG5n?x-oss-process=image/format,png)
