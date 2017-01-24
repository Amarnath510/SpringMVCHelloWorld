# Spring-MVC HelloWorld

## Project Setup
  - Install Maven in Eclipse.
  - Set up Tomcat 7 in Eclipse.
  - Eclipse -> File -> New -> Maven -> Maven Project -> Select "maven webapp" -> Give group id as "com.amarnath" and artifact id as "springmvchelloworld".

## Project Structure
  
  ![Project Structure](https://github.com/Amarnath510/SpringMVCHelloWorld/blob/master/spring-mvc-helloworld.png)

## Update pom.xml with new dependencies
  
  ```xml
    <dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
		</dependency>

		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jstl</artifactId>
			<version>1.2</version>
		</dependency>

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context-support</artifactId>
			<version>4.2.6.RELEASE</version>
		</dependency>

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>4.2.6.RELEASE</version>
		</dependency>
  
  ```
  
## Add Spring Configuration file
   - Under WEB-INF directory add `spring-web-servlet.xml` file.
   - Add ViewResolver class and view page path as below,
    
   ```xml
   <context:component-scan base-package="com.amarnath" />
	 <mvc:annotation-driven />

	 <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
		<property name="prefix">
			<value>/WEB-INF/views/jsp/</value>
		</property>
		<property name="suffix">
			<value>.jsp</value>
		</property>
	 </bean>
   ```
   
## Update web.xml file
   - Add Dispatcher Servlet info here as,
   
   ```xml
   <servlet>
		<servlet-name>spring-web</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<load-on-startup>1</load-on-startup>
	</servlet>

	<servlet-mapping>
		<servlet-name>spring-web</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
   ```
   
## Time to add Controller
   - Under `src/main/java` add a package `com.amarnath.springmvchelloworld`.
   - Add HomeController class in the above package.
   - The class has only two method which refer two different pages as,
   
   ```Java
    @Controller
    public class HomeController {

      @RequestMapping(value="/", method=RequestMethod.GET)
      public String home() {
        return "index";
      }

      @RequestMapping("/next")
      public String next() {
        return "next";
      }
    }
   ```
   
## Running the server
   - Right Click on project, select Run as and choose tomcat server.
   
## Credits
   - [Spring MVC Hello World](http://www.mkyong.com/spring3/spring-3-mvc-hello-world-example/)
 
 
 
