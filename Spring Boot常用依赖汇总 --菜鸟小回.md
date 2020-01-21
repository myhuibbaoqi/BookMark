# Spring Boot常用依赖汇总 
---
```javascript?linenums

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.1.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.example</groupId>
    <artifactId>hospital</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>hospital</name>
    <description>Demo project for Spring Boot</description>

    <properties>
        <java.version>1.8</java.version>
        <servlet-api.version>3.1</servlet-api.version>
        <mysql.version>5.1.21</mysql.version>
        <fastjson.version>1.2.56</fastjson.version>

        <c3p0.version>0.9.1.2</c3p0.version>
        <jedis.version>3.0.1</jedis.version>
        <commons-fileupload.version>1.3.3</commons-fileupload.version>
        <log4j.version>1.2.12</log4j.version>
        <mybatis-spring.version>1.1.1</mybatis-spring.version>

        <jsqlparser>0.9.1</jsqlparser>
        <pagehelper.version>1.2.5</pagehelper.version>
        <validation-api.version>1.0.0.GA</validation-api.version>
        <tomcat-servlet-api.version>7.0.62</tomcat-servlet-api.version>
        <poi.version>3.17</poi.version>

        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>

        <!-- ******************************* 外部tomcat（部署war包使用） ********************** -->
        <!--<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            <scope>provided</scope>
        </dependency>-->
        <!-- ******************************* spring ********************** -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
            <version>2.1.6.RELEASE</version>
        </dependency>

        <!-- ******************************* 引入junit，做单元测试用，@Test注解需要它 ********************** -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
            <exclusions>
                <exclusion>
                    <groupId>org.junit.vintage</groupId>
                    <artifactId>junit-vintage-engine</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <!-- ******************************* 引入mybatis*********************************************** -->
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>${mybatis-spring.version}</version>
        </dependency>

        <!-- ******************************* 引入mysql *********************************************** -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>${mysql.version}</version>
        </dependency>

        <!-- ****************************************** 分页 ******************************************** -->
        <dependency>
            <groupId>com.github.pagehelper</groupId>
            <artifactId>pagehelper-spring-boot-starter</artifactId>
            <version>${pagehelper.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-lang3</artifactId>
            <version>3.7</version>
        </dependency>
        <!-- ******************************* c3p0连接池 *************************************************** -->
        <dependency>
            <groupId>c3p0</groupId>
            <artifactId>c3p0</artifactId>
            <!--suppress UnresolvedMavenProperty -->
            <version>${c3p0.version}</version>
        </dependency>

        <!-- ******************************** jedis，Jedis是Redis官方推荐的Java连接开发工具。*********************** -->
        <dependency>
            <groupId>redis.clients</groupId>
            <artifactId>jedis</artifactId>
            <version>${jedis.version}</version>
        </dependency>

        <!-- ******************************* fastjson，把对象和json格式互转换时需要用到 ****************************** -->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>${fastjson.version}</version>
        </dependency>

        <!-- ***************************************** commons ************************************* -->
        <dependency>
            <groupId>commons-fileupload</groupId>
            <artifactId>commons-fileupload</artifactId>
            <version>${commons-fileupload.version}</version>
        </dependency>
        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.4</version>
        </dependency>

        <!-- ***************************** 引入log4j，生成日志需要这个，log for java ，4是 for的近音  ************************ -->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>${log4j.version}</version>
        </dependency>

        <!-- ******************************* jsql ********************** -->
        <dependency>
            <groupId>com.github.jsqlparser</groupId>
            <artifactId>jsqlparser</artifactId>
            <version>${jsqlparser}</version>
        </dependency>

        <!-- ****************************************** poi导出excel ************************************ -->
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi</artifactId>
            <version>${poi.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-ooxml</artifactId>
            <version>${poi.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-ooxml-schemas</artifactId>
            <version>${poi.version}</version>
        </dependency>
        <!-- 防止 程序包javax.servlet.annotation不存在 -->
        <dependency>
            <groupId>org.apache.tomcat</groupId>
            <artifactId>tomcat-servlet-api</artifactId>
            <version>${tomcat-servlet-api.version}</version>
        </dependency>

        <!-- ******************************************* 校验器 ***************************************** -->
        <dependency>
            <groupId>javax.validation</groupId>
            <artifactId>validation-api</artifactId>
            <version>${validation-api.version}</version>
        </dependency>

        <!-- ******************************************* 文件服务器 ************************************** -->
        <dependency>
            <groupId>org.csource.fastdfs</groupId>
            <artifactId>fastdfs</artifactId>
            <version>1.2</version>
        </dependency>


        <!-- ********************************** 阿里短信依赖 ************************************** -->
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-core</artifactId>
            <version>3.7.0</version>
        </dependency>
        <dependency>
            <groupId>com.aliyun</groupId>
            <artifactId>aliyun-java-sdk-ecs</artifactId>
            <version>4.11.0</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>


```

