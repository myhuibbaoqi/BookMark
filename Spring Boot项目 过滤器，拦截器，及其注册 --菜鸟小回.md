# Spring Boot项目 过滤器，拦截器，及其注册
---
## 一、过滤器
```javascript?linenums
package com.zhiyou.filter;

import org.springframework.stereotype.Component;

import javax.servlet.*;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@Component
public class UserFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
		HttpServletRequest request2=(HttpServletRequest) request;
		HttpServletResponse response2=(HttpServletResponse) response;
		
		String url=request2.getScheme()+"://"+request2.getServerName()+":"+request2.getServerPort()+request2.getSession().getServletContext().getContextPath()+"/";
		
		Object o=request2.getSession().getAttribute("user");

		System.out.println("进入过滤器！"+o);


        //得到当前页面所在目录下全名称
		String urlPattern=request2.getServletPath();
		
		//得到页面所在服务器的绝对路径
		String path = request2.getRequestURI();

	
		if(o==null){		
			System.out.println(2);
			response2.sendRedirect(url+"login.html");
		}else{
			System.out.println(3);
			chain.doFilter(request, response);
		}

	}

	@Override
	public void destroy() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void init(FilterConfig arg0) throws ServletException {
		// TODO Auto-generated method stub
		
	}
}


```
## 二、拦截器
```javascript?linenums
package com.zhiyou.filter;

import com.alibaba.fastjson.JSONObject;
import com.zhiyou.pojo.User;
import com.zhiyou.util.JedisConnect;
import org.springframework.stereotype.Component;
import org.springframework.web.servlet.HandlerInterceptor;
import org.springframework.web.servlet.ModelAndView;
import redis.clients.jedis.Jedis;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
/**
 * 拦截器
 * @author XiaoHui
 *
 */
@Component
public class UserInterceptor implements HandlerInterceptor{

	@Override
	public void afterCompletion(HttpServletRequest arg0, HttpServletResponse arg1, Object arg2, Exception arg3)
			throws Exception {
		
	}

	@Override
	public void postHandle(HttpServletRequest arg0, HttpServletResponse arg1, Object arg2, ModelAndView arg3)
			throws Exception {
		
	}

	@Override
	public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object arg2) throws Exception {
		//redis里获取缓存用户
		Jedis jedis= JedisConnect.Conn();
		String json_user=jedis.get("user");
		User user=JSONObject.parseObject(json_user, User.class);
		//session中获取缓存用户
		//Object o=request.getSession().getAttribute("user");
		
		System.out.println("进入拦截器");
		//不为空，已登录放行；
		if(user!=null){
			//放行
			System.out.println("放行");
			return true;
		}
		System.out.println("拦截");
		return false;
	}

}

```
3. 注册
```javascript?linenums
package com.zhiyou.filter;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.web.servlet.FilterRegistrationBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

import java.util.ArrayList;
import java.util.List;

@Configuration
public class Config {
    @Autowired
    private UserInterceptor userInterceptor;
    @Autowired
    private UserFilter userFilter;
    /**
     * 拦截器
     * */
    @Bean
    public WebMvcConfigurer WebMvcConfigurer() {
        return new WebMvcConfigurer() {
            public void addInterceptors(InterceptorRegistry registry) {
                //排除无需拦截路径
                List<String> l=new ArrayList<>();
                l.add("/userLogin.do");
                l.add("/sendMessage.do");
                l.add("/register.do");
                //配置需要拦截路径/*.do
                registry.addInterceptor(userInterceptor).addPathPatterns("/*.do").excludePathPatterns(l);
            }
        };
    }
    /**
     * 过滤器
     * */
    @Bean
    public FilterRegistrationBean testFilterRegistration() {
        FilterRegistrationBean registration = new FilterRegistrationBean(userFilter);
        //配置需要过滤路径
        registration.addUrlPatterns("/index/*");
        registration.addUrlPatterns("/hospital/*");
        registration.addUrlPatterns("/medicine/*");
        registration.addUrlPatterns("/registration/*");
        registration.addUrlPatterns("/Resource/*");
        registration.addUrlPatterns("/Role/*");
        registration.addUrlPatterns("/User/*");
        registration.addUrlPatterns("/index/*");

        registration.setName("userFilter");
        return registration;
    }
}
```
