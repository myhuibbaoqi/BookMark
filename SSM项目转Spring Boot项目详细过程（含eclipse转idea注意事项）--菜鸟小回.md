# SSM项目转Spring Boot项目详细过程（含eclipse-->idea注意事项）

---
@[toc]
+ 本文主要记录SSM项目转移为Spring Boot项目中注意事项。包括SSM中主要配置文件的转移
相关博文：
+ Spring Boot常用pom依赖：[Spring Boot常用依赖汇总 ](https://blog.csdn.net/qq_39231769/article/details/103096352)
+ idea创建Spring Boot项目介绍：[idea新建一个Spring Boot项目+项目目录简单介绍+项目打包运行](https://blog.csdn.net/qq_39231769/article/details/103098524)
---
## 一、建立Spring Boot项目并导入依赖参考上方相关博文

## 二、静态页面转移
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzI3MjU3OTMucG5n?x-oss-process=image/format,png)

## 三、后台代码
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzI5MDY3NjEucG5n?x-oss-process=image/format,png)

## 四、分离mapper文件
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4NzMwMzM3OTYucG5n?x-oss-process=image/format,png)

## 五、运行方式的改（由于内置tomcat，直接运行main方法就可以运行项目）变和注解扫描的配置
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODczMzQ3OTIucG5n?x-oss-process=image/format,png)

## 六、mysql以及mybatis的配置
1. mysql
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODc1ODY0ODMucG5n?x-oss-process=image/format,png)
2. mybatis的mapper.xml文件位置更换并配置包路径。
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODc3MjMxMTgucG5n?x-oss-process=image/format,png)
3. mybatis别名设置（直接设置pojo包，之后mapper.xml中就可以省略包名直接用类名） 
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODgwMDQyMjIucG5n?x-oss-process=image/format,png)

## 七、拦截器和过滤器的配置（主要改变为其注册方式，从配置方式改为java类配置）
1. 拦截器
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODgzOTczMDMucG5n?x-oss-process=image/format,png)

2. 过滤器
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODg1ODgzMzkucG5n?x-oss-process=image/format,png)

3. 附带拦截器、过滤器、注册代码：
[Spring Boot项目 过滤器，拦截器，及其注册](https://blog.csdn.net/qq_39231769/article/details/103099355)

## 八、事务的配置（直接对ServiceImpl中所需类或方法使用@Transactional注解)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODkwMDc0NDIucG5n?x-oss-process=image/format,png)

## 九、项目默认跳转首页设置（新增Controller）
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzM4ODk1NzIwMjcucG5n?x-oss-process=image/format,png)
```javascript?linenums
/* **********************************直接访问首页************************************* */
@Configuration
public class WebConfigurer implements WebMvcConfigurer {
	@Override
	public void addViewControllers(ViewControllerRegistry registry) {
		registry.addViewController("/").setViewName("forward:/login.html");
		registry.setOrder(Ordered.HIGHEST_PRECEDENCE);
	}
}
```

## 十、其他
1. mapper自动注入报错可以忽略，或者在mapper接口上加@Component。
2. 图片验证码可能失效，参考博文第二种方法：[Java中使用图片验证码](https://blog.csdn.net/qq_39231769/article/details/102710427)
3. PageHelper分页需要更换spring boot类型pom依赖


