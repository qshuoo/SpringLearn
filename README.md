# springMVC    
学习springMVC 搭建       
## 从maven仓库导入spring相关包
1、设置spring相关包版本

	<properties>
		<org.springframework.version>3.2.8.RELEASE</org.springframework.version>    
	</properties>

2、导入相关包

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${org.springframework.version}</version>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-web</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-test</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-orm</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-tx</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${org.springframework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context-support</artifactId>
			<version>3.2.4.RELEASE</version>
		</dependency>

## 编写springmvc核心配置文件（在[servlet-name]-servlet.xml中）  

编写springmvc-servlet.xml

	<beans xmlns="http://www.springframework.org/schema/beans"      
		xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"     		xmlns:mvc="http://www.springframework.org/schema/mvc"     
		xmlns:context="http://www.springframework.org/schema/context"     
		xsi:schemaLocation="http://www.springframework.org/schema/beans    
			http://www.springframework.org/schema/beans/spring-beans-3.2.xsd 
			http://www.springframework.org/schema/mvc 
			http://www.springframework.org/schema/mvc/spring-mvc-3.2.xsd 
			http://www.springframework.org/schema/context 
			http://www.springframework.org/schema/context/spring-context-3.2.xsd  ">
			
		<!-- Enables the Spring MVC @Controller programming model -->  
		<mvc:annotation-driven />  
		
		<context:component-scan base-package="com.qys" />  
			
		<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">  
			<property name="prefix" value="/" />  
			<property name="suffix" value=".jsp" />  
		</bean>  
	</beans>    
	

## 指定SpringMVC的入口程序（在web.xml中） 

编写web.xml

	<servlet>
		<servlet-name>springmvc</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<load-on-startup>1</load-on-startup>
	</servlet>
	
	<servlet-mapping>
		<servlet-name>springmvc</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
	
	
## 编写jsp与control类测试

编写jsp表单

	<form action="<%=request.getContextPath()%>/login">
		<table>
			<tr>
				<td>用户名</td>
				<td><input type="text"></td>
			</tr>
			<tr>
				<td>密码</td>
				<td><input type="text"></td>
			</tr>
			<tr>
				<td><input type = "submit" value = "submit"></td>
			</tr>
		</table>
	</form>
	
编写control类

	@Controller
	public class UserController {
		@RequestMapping("login")
		public String login() {
			return "index";
		}
	}

	
	

