# java中使用redis（含json类型与java类型装换）
1. pom依赖
```javascript?linenums
<!-- https://mvnrepository.com/artifact/redis.clients/jedis -->
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>3.0.1</version>
</dependency>
<!-- https://mvnrepository.com/artifact/com.alibaba/fastjson -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.56</version>
</dependency>

```
2. 工具类，用于连接redis
```javascript?linenums
public class JedisConnect {
	public static Jedis Conn(){
		Jedis jedis=new Jedis("120.27.244.176");
		return jedis;
	}
}
```
3. 存放一个redis，此处模拟session共享
```javascript?linenums
//连接
Jedis jedis=JedisConnect.Conn();
//对象转json字符串
String json_user=JSONObject.toJSONString(user);
/*
集合转换成json集合
String JList=JSONArray.toJSONString(list); 
*/
//放入redis
jedis.set("user",json_user);
//设置存活时间
jedis.expire("user", 300);
```
4. 获取redis
```javascript?linenums
//连接
Jedis jedis=JedisConnect.Conn();
//获取redis中的user（json字符串形式）
String json_user=jedis.get("user");
//json字符串转对象
User user=JSONObject.parseObject(json_user, User.class);
```
5. 模拟数据库添加灵活使用
```javascript?linenums
//连接
Jedis jedis=JedisConnect.Conn();
//对象转json字符串
String reward_json=JSONObject.toJSONString(reward);
/*
字符串转json对象
JSONObject json_object=JSONObject.parseObject({"Message":"OK"});
json集合转java集合
List<Goods>	list2=	JSONArray.parseArray(JList, Goods.class);
*/
//存入的时候使用“表名:主键名:主键值”形式存储将自动生成分级目录
jedis.set("reward:r_id:"+reward.getR_id(), reward_json);
```
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NDkyMzA1OTEucG5n?x-oss-process=image/format,png)
