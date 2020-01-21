# java中阿里短信服务（短信验证码）
@[toc]
## 1. 创建签名
+ 如下位置创建签名，等待审核通过
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTAxMzI2MjkucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTAyMDA0NzMucG5n?x-oss-process=image/format,png)
## 2. 创建模板
+ 如下位置创建模板，等待审核通过
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTAzNjcyNjUucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTA1NDEwODMucG5n?x-oss-process=image/format,png)
## 3. 测试验证码功能
+ 填写相关信息，测试发送
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTA4MDM4ODAucG5n?x-oss-process=image/format,png)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTA4NTYyNDQucG5n?x-oss-process=image/format,png)
<font color=red size=5>注：发送失败可能因为你余额不足。可以选择购买套餐。新号可去尝试下图位置领取免费短信。</font>
+ 官网主页下拉最后
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTExNzEyMjAucG5n?x-oss-process=image/format,png)
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTExOTY4NjgucG5n?x-oss-process=image/format,png)
## 4. 查看Api Demo
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTEyMzUxNjUucG5n?x-oss-process=image/format,png)
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTE0Mjc5MzkucG5n?x-oss-process=image/format,png)
## 5. 获取AK信息
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTE1MDAyMjYucG5n?x-oss-process=image/format,png)
+ 创建AccessKey
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTE1NTQ4NTUucG5n?x-oss-process=image/format,png)
+ 保存一下AccessKeyId和AccessKeySecret
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTE2MDQ5NjIucG5n?x-oss-process=image/format,png)
+ 将其复制分别填到AccessKeyId和AccessKeySecret的位置
+ ![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTE5MjQ2NjcucG5n?x-oss-process=image/format,png)
## 6. 复制Api Demo到eclipse；复制依赖到pom.xml
![enter description here](https://imgconvert.csdnimg.cn/aHR0cDovL2hicS5pZHNlLnRvcC9ibG9nLzE1NzE3NTM2MDQ4OTgucG5n?x-oss-process=image/format,png)

## 7.自建工具类
```javascript?linenums
//六位随机密码生成
//传入手机号，成功返回后台随机验证码，失败返回null
public class ToolNote {
	
	public static String getNote(String tel){
		DefaultProfile profile = DefaultProfile.getProfile("cn-hangzhou", "你的accesskeyId", "你的secret");
        IAcsClient client = new DefaultAcsClient(profile);

        String[] codees={"0","1","2","3","4","5","6","7","8","9"};
        String code="";
        for(int i=0;i<6;i++){
        	int j=(int)(Math.random()*10);
        	code+=codees[j];
        }
        
        CommonRequest request = new CommonRequest();
        request.setMethod(MethodType.POST);
        request.setDomain("dysmsapi.aliyuncs.com");
        request.setVersion("2017-05-25");
        request.setAction("SendSms");
        request.putQueryParameter("RegionId", "cn-hangzhou");
        request.putQueryParameter("PhoneNumbers", tel);
        request.putQueryParameter("SignName", "IDSE");
        request.putQueryParameter("TemplateCode", "SMS_175540528");
        request.putQueryParameter("TemplateParam", "{\"code\":\""+code+"\"}");
        CommonResponse response=null;
        try {
        	response= client.getCommonResponse(request);
            System.out.println(response.getData());
            //获取当前返回字符串转换为json对象
            JSONObject json_object=JSONObject.parseObject(response.getData());
            //根据键获得值看是否为“OK”,是则发送成功，返回验证码
            String status=(String)json_object.get("Message");
            if(status.equals("OK")){
            	return code;
            }
        } catch (ServerException e) {
            e.printStackTrace();
        } catch (ClientException e) {
            e.printStackTrace();
        }
        
        return null;
	}
}
```

