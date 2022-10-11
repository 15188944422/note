# 第一章SpringMVC概述

## 1.SpringMVC简介

它是基于MVC开发模式的框架,用来优化控制器.它是Spring家族的一员.它也具备IOC和AOP.

什么是MVC?

- 它是一种开发模式,它是模型视图控制器的简称.所有的web应用都是基于MVC开发.
- M:模型层,包含实体类,业务逻辑层,数据访问层
- V:视图层,html,javaScript,vue等都是视图层,用来显现数据
- C:控制器,它是用来接收客户端的请求,并返回响应到客户端的组件,Servlet就是组件

## 2.SpringMVC优点

1. 轻量级,基于MVC的框架
2. 易于上手,容易理解,功能强大
3. 它具备IOC和AOP
4. 完全基于注解开发

## 3.SpringMVC的执行流程

![](图\SpringMvc\SpringMVC的执行流程.png)

执行流程说明：

1.  向服务器发送HTTP请求，请求被前端控制器 DispatcherServlet 捕获。
2. DispatcherServlet 根据`<servlet-name>`中的配置对请求的URL进行解析，得到请求资源标识符（URI）。然后根据该URI，调用 HandlerMapping 获得该Handler配置的所有相关的对象（包括Handler对象以及Handler对象对应的拦截器），最后以 HandlerExecutionChain 对象的形式返回。
3. DispatcherServlet 根据获得的Handler，选择一个合适的 HandlerAdapter。
4. 提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)。在填充Handler的入参过程中，根据你的配置，Spring将帮你做一些额外的工作：
   - HttpMessageConveter：将请求消息（如Json、xml等数据）转换成一个对象，将对象转换为指定的响应信息。
   - 数据转换：对请求消息进行数据转换。如String转换成Integer、Double等。
   - 数据格式化：对请求消息进行数据格式化。如将字符串转换成格式化数字或格式化日期等
   - 数据验证：验证数据的有效性（长度、格式等），验证结果存储到BindingResult或Error中。
5. Handler(Controller)执行完成后，向 DispatcherServlet 返回一个 ModelAndView 对象。
6. 根据返回的ModelAndView，选择一个适合的 ViewResolver（必须是已经注册到Spring容器中的ViewResolver)返回给DispatcherServlet。
7. ViewResolver 结合Model和View，来渲染视图。
8. 视图负责将渲染结果返回给客户端

# 第二章SpringMVC注解式开发

## 1.开发步骤

### 1.新建一个基于Maven的Web项目

![](图\SpringMvc\新建一个WEB项目.png)

### 2.补全相应的目标

一开始是：

- ![](图\SpringMvc\补全目录.png )

补全完：

- ![](图\SpringMvc\补全完目录.png)

### 3.修改pom.xml文件,添加SpringMVC的依赖,添加Servlet的依赖

```xml
<!--dependencies中-->
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <!--添加springmvc的依赖-->
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-webmvc</artifactId>
      <version>5.2.5.RELEASE</version>
    </dependency>
    <!--添加servlet的依赖-->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>3.1.0</version>
    </dependency>

<!--build中-->
    <resources>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.xml</include>
          <include>**/*.properties</include>
        </includes>
      </resource>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.xml</include>
          <include>**/*.properties</include>
        </includes>
      </resource>
    </resources>
```

### 4.添加springmvc.xml配置文件,指定包扫描,添加视图解析器.

在resources中新建一个springmvc.xml文件

```xml
<!--添加包扫描 基于spring去开发的 所以要添加包扫描-->
<context:component-scan base-package="com.bjpowernode.controller"></context:component-scan>
<!--添加视图解析器-->
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <!--配置前缀 这里要一定是 /admin/这样才能 /admin/..... -->
    <property name="prefix" value="/admin/"></property>
    <!--配置后缀  这样最终就是  /admin/***.jsp-->
    <property name="suffix" value=".jsp"></property>
</bean> 
```

### 5.删除web.xml文件(之前的版本太低了),新建web.xml

![](图\SpringMvc\修改webxml.png)

### 6.在web.xml文件中注册springMVC框架(所有的web请求都是基于servlet的)

```xml
    <!--注册springmvc的框架-->
    <servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <!--这里就是导入springmvc的核心配置文件-->
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:springmvc.xml</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <!--
            指定拦截什么样的请求：
            http://loaclhost:8080/demo.action
            <a href="${pageContext.request.contextPath}/demo.action">访问服务器</a>
		以 .action的请求才可以被触发
        -->
        <url-pattern>*.action</url-pattern>
    </servlet-mapping>
```

### 7.在webapp目录下新建admin目录,在admin目录下新建main.jsp页面,删除index.jsp页面,并新建index.jsp,发送请求给服务器

main.jsp:

- ```jsp
  <h2>main....................</h2>
  ```

index.jsp:

- ```jsp
      <a href="${pageContext.request.contextPath}/zar/demo.action">访问服务器zar</a>
      <a href="${pageContext.request.contextPath}/user/demo.action">访问服务器user</a>
  ```

### 8.开发控制器(Servlet),它是一个普通的类.

ZarDemoAction.java

- ```java
  /**
   * RequestMapping
   *  1.此注解就是用来映射服务器访问得路径
   *      此注解可加载方法上,是为此方法注册一个可以访问得名称(路径)
   *      此注解可以加载类上,相当于包名(虚拟路径),区分不同类中相同得action名称
   *      此注解可区分get请求和post请求
   *
   */
  
  @Controller //交给spring创建对象
  @RequestMapping("/zar")// 这个访问是类似于包名的这么一个东西 /zar下的请求
  public class DemoAction {
  
      /**
       * 以前的Servlet的规范
       * protected void doPost(HttpServletRequest request,HttpServletResponse response)
       *  throws ServletException,IOException{}
       *
       *
       * action中所有的功能实现都是由方法来完成的
       * action方法的规范:
       *  1.访问权限是public
       *  2.方法的返回值是任意
       *  3.方法名称任意
       *  4.方法可以没有参数,如果由可以是任意类型
       *  5.要是有@RequestMapping的注解来声明一个访问的路径(名称)
       */
      @RequestMapping("/demo") //	 /zar/demo.action
      public String demo(){
          System.out.println("zar服务器被访问到了..........");
          return "main"; //可以直接跳到/admin/mian.jsp页面上 在springMvc前后缀的拼接
      }
  }
  ```

UserDemoAction.java:

- ```java
  @Controller //交给spring创建对象
  @RequestMapping("/user")//加在类上区分不同类中相同的action的名称 这个访问是/user
  public class DemoAction1 {
  
      /**
       * 以前的Servlet的规范
       * protected void doPost(HttpServletRequest request,HttpServletResponse response)]
       *  throws ServletException,IOException{}
       *
       *
       * action中所有的功能实现都是由方法来完成的
       * action方法的规范:
       *  1.访问权限是public
       *  2.方法的返回值是任意
       *  3.方法名称任意
       *  4.方法可以没有参数,如果由可以是任意类型
       *  5.要是有@RequestMapping的注解来声明一个访问的路径(名称)
       */
      @RequestMapping("/demo")// /user/demo.action
      public String demo(){
          System.out.println("user服务器被访问到了..........");
          return "main"; //可以直接跳到/admin/mian.jsp页面上
      }
  }
  ```


## 2.分析web请求：

​	web请求的执行流程

- ```
    							    核心处理器
    index.jsp<--------------->DispatcherServlet<------------------->SpringMVC的处理器是一个普通的方法
    one.jsp  <--------------->DispatcherServlet<------------------->SpringMVC的处理器是一个普通的方法
  ```

- DispatcherServlet要在web.xml文件中注册才可用.

## 3.@RequestMapping注解详解

### 1.此注解可加在方法上,是为此方法注册一个可以访问的名称(路径)

```java
@RequestMapping("/demo")
public String demo(){
	System.out.println("服务器被访问到了.......");
	return "main";  //可以直接跳到/admin/main.jsp页面上   这里在前后缀拼接了 
}

/*
jsp:
    <a href="${pageContext.request.contextPath}/demo.action">访问服务器</a>
在web.xml 中配置了 url-pattern 为 *.action
*/
```

### 2.此注解可以加在类上,相当于是包名(虚拟路径),区分不同类中相同的action的名称

```java
@RequestMapping("/user")
public class DemoAction1 {
    @RequestMapping("/demo") //这里合起来就是 /user/demo.action
    public String demo(){....}
}
/*
jsp:
    <a href="${pageContext.request.contextPath}/user/demo.action">访问服务器</a>
*/
```

### 3.此注解可区分get请求和post请求

```java
    @RequestMapping(value = "/req",method = RequestMethod.GET)//最后会执行这个
    public String req(){
        System.out.println("我是处理get请求得");
        return "main";
    }

    @RequestMapping(value = "/req",method = RequestMethod.POST)
    public String req1(){
        System.out.println("我是处理post请求得");
        return "main";
    }

/*
jsp:
	<form action="${pageContext.request.contextPath}/req.action" method="get">
        <input type="submit" value="提交">
    </form>
这个根据 method谈话跳转到那个方法上 
*/
```

## 4.五种数据提交方式的优化

### 1.单个提交数据

- jsp

  - ```jsp
    <h2>1.单个数据提交</h2>
    <form action="${pageContext.request.contextPath}/one.action" method="post">
        姓名:<input name="myname"><br>
        年龄:<input name="age"><br>
        <input type="submit" value="提交">
    </form>
    ```

- 控制器controller: 

  - ```java
        /**
         * 姓名:<input name="myname"><br> name值和 形参名称一致
         * 年龄:<input name="age"><br>
         * 自动接受用户得数据
         */
        @RequestMapping("/one")
        public String one(String myname,int age ){ ===> 这里的名称和前端的 name名称是一致的
            System.out.println("myname="+myname+",age="+(age+100)); ===>自动注入,并且类型转换
            return "main";
        }
    ```

### 2.对象封装提交数据

在提交请求中,保证请求参数的名称与实体类中成员变量的名称一致,则可以自动创建对象,则可以自动提交数据,自动类型转换,自动封装数据到对象中.

- jsp:

  - ```jsp
    <%--
        private String name;
        private int age;
    	注意 类中的成员变量名称 需要和表单中的 name属性名称要完全一致
    --%>
    <h2>2.对象封装提交</h2>
    <form action="${pageContext.request.contextPath}/two.action" method="post">
        姓名:<input name="name"><br>
        年龄:<input name="age"><br>
        <input type="submit" value="提交">
    </form>
    ```

- 控制器controller: 

  - ```java
        /**
         *     private String name;
         *     private int age;
         *     姓名:<input name="name"><br>
         *     年龄:<input name="age"><br>
         *     自动封装对象
         */
        @RequestMapping("/two")
        public String two(Users users){ ===>注意 这里是SpringMVC通过的是Setter方法进行注入的
            System.out.println(users);
            return "main";
        }
    ```

### 3.动态占位符提交(仅适用于超链接)

仅限于超链接或地址拦提交数据.它是一杠一值,一杠一大括号,使用注解@PathVariable来解析.      

- jsp:

  - ```jsp
    <%--
        一个 / 一个值
    --%>
    <h2>3.动态占位符提交</h2>
        <a href="${pageContext.request.contextPath}/three/张三/22.action">动态提交</a>
    ```

- 控制器controller:

  - ```java
        /**
         *  <a href="${pageContext.request.contextPath}/three/张三/22.action">动态提交</a>
         *  /three/{uname}/{uage}
         *      张三-->占位符{uname}-->name参数      
         *      22-->占位符{uage}-->age属性
         *
         *  @PathVariable("uname") 用来解析路径中的请求参数
         *      {uname} 这里的名称和String name 这里的名称不一致,就需要加上这个注解
         *    	这个就是从路径中取变量 如果名称一样就不用加了 如果名称不一样需要加上("这里跟参数名称")
         *
         *  这个是占位符得 一杠一个值 用{} 来接
         */
        @RequestMapping("/three/{uname}/{uage}")
        public String three(
                @PathVariable("uname")//这里要和RequsetMapping的值是一样的
                String name,
                @PathVariable("uage")
                int age){
            System.out.println("name="+name+",age="+age);
            return "main";
        }
    ```

    



### 4.映射名称不一致 

提交请求参数与action方法的形参的名称不一致,使用注解@RequestParam来解析

- jsp:

  - ```jsp
    <h4>4.参数名称不一致解决方案</h4>
    <form action="${pageContext.request.contextPath}/four.action" method="post">
        姓名:<input name="name"><br>
        年龄:<input name="age"><br>
        <input type="submit" value="提交">
    </form>
    ```

- 控制器controller: 

  - ```java
        /**
         *     姓名:<input name="name"><br>
         *     年龄:<input name="age"><br>
         *
         *      @RequestParam("name") 解决名称不一致的问题是:
         *      	表单中的name属性值和形参的名称不一致
         *			<input name="name"><br> 这里的名称和String uname,参数不一致
         */
        @RequestMapping("/four")
        public String four(
                @RequestParam("name") ===>专门用来解决名称不一致的问题
                String uname,
                @RequestParam("age")
                int uage){
            System.out.println("uname="+uname+",uage="+uage);
            return "main";
        }
    ```

    

### 5.手工提取数据 使用HttpServletRequest提取

- jsp：

  - ```jsp
    <h4>5.手工提取数据</h4>
    <form action="${pageContext.request.contextPath}/five.action" method="post">
        姓名:<input name="name"><br>
        年龄:<input name="age"><br>
        <input type="submit" value="提交">
    </form>
    ```

- 控制器controller: 

  - ```java
        @RequestMapping("/five")
        public String five(HttpServletRequest request){
            String name=request.getParameter("name");
            int age=Integer.parseInt(request.getParameter("age"));
            System.out.println("name="+name+",age="+age);
            return "main";
        }
    ```

## 5.请求参数中文乱码问题

对于前面所接收的请求参数，若含有中文，则会出现中文乱码问题。Spring 对于请求参数中的中文乱码问题，给出了专门的字符集过滤器： spring-web-5.2.5.RELEASE.jar 的org.springframework.web.filter 包下的 CharacterEncodingFilter 类。

在web.xml文件中配置

```xml
    <!--中文编码过滤器配置-->
	<!--注册字符集过滤器:结果post请求乱码的问题-->
    <filter>
        <filter-name>encode</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <!--
            配置参数
                private String encoding;
                private boolean forceRequestEncoding;
                private boolean forceResponseEncoding;
        -->
        <!--指定字符集-->
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <!--强制request使用字符集encoding-->
        <init-param>
            <param-name>forceRequestEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
        <!--强制response使用字符集encoding-->
        <init-param>
            <param-name>forceResponseEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encode</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

## 6.处理器controller的返回值

1. String:客户端资源的地址,自动拼接前缀和后缀.还可以屏蔽自动拼接字符串,可以指定返回的路径.
2. Object:返回json格式的对象.自动将对象或集合转为json.使用的jackson工具进行转换,必须要添加jackson依赖.一般用于ajax请求.
3. void:无返回值,一般用于ajax请求.
4. 基本数据类型,用于ajax请求.
5. ModelAndView:返回数据和视图对象,现在用的很少.

## 7.完成ajax请求访问服务器,返回学生集合.

### 1.pom.xml

```xml
和之前得没区别 但要导入Jackson
    <dependency>
      <groupId>com.fasterxml.jackson.core</groupId>
      <artifactId>jackson-databind</artifactId>
      <version>2.9.8</version>
    </dependency>
```

### 2.springmvc.xml

```xml
    <!--添加包扫描-->
    <context:component-scan base-package="com.bjpowernode.controller"></context:component-scan>
    <!--不用添加视图解析器,因为处理的是ajax请求-->
<!--    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">-->
<!--        <property name="prefix" value="/admin/"></property>-->
<!--        <property name="suffix" value=".jsp"></property>-->
<!--    </bean>-->
    <!--必须要添加注解驱动,专门用来处理ajax请求的-->
    <mvc:annotation-driven></mvc:annotation-driven> ==>用来解析 @ResponseBody
```



### 3.web.xml

```xml
    <!--添加中文编码
        private String encoding;
        private boolean forceRequestEncoding;
        private boolean forceResponseEncoding;
    -->
    <filter>
        <filter-name>encode</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>forceRequestEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
        <init-param>
            <param-name>forceResponseEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encode</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    <!--注册springmvc-->
    <servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:springmvc.xml</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <url-pattern>*.action</url-pattern>
    </servlet-mapping>
```



### 4.导入jquery.js

### 5.index.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
  <%--导入JQuery的函数库 --%>
  <script src="js/jquery-3.3.1.js"></script>
</head>
<body>
<br><br><br>
<a href="javascript:showStu()">访问服务器返回学生集合</a><br>
<div id="mydiv">等待服务器返回数据</div>

<script type="text/javascript">
  function showStu(){
    //实验JQuery封装的ajax()方法发送请求
    $.ajax({
      url:"${pageContext.request.contextPath}/list.action",
      type:"get",
      dataType:"json",
        success:function (stuList){
            var s="";
            $.each(stuList,function (i,stu){
                //stu.name 调用的是实体类上的中的getName()
               s+=stu.name+"-----------"+stu.age+"<br>";
            });
            //回显数据
            $("#mydiv").html(s);
        }
    });
  }
</script>
</body>
</html>
```

### 6.pojo包下新建一个Student实体类

```java
public class Student {
    //这两个名字必须和页面的名称是一样的
    // s+=stu.name+"-----------"+stu.age+"<br>";
    private String name;
    private int age;
}
```



### 7.控制器编写

```java
public class StudentListAction {
    @RequestMapping("/list")
    @ResponseBody//用来解析ajax请求,必须要在springmvc.xml文件添加注解驱动 一定要加得
    public List<Student> list(){
        List<Student> list=new ArrayList<>();
        Student student1=new Student("张三",12);
        Student student2=new Student("张撕",13);
        Student student3=new Student("张五",14);
        list.add(student1);
        list.add(student2);
        list.add(student3);
		//调用json转换工具ObjectMapper进行转换
        return list;//SpringMvc框架负责将集合转为json数组
    }
}
```

## 8.四种跳转方式

在此之前,要明白转发和重定向得区别：

- 转发：无论是多少次跳转 都是一次请求

  - ```java
    request.getRequestDispatcher("/dept/list").forward(request, response);
    ```

- 重定向:

  - 重定向：这个是两次请求

    - ```java
      response.sendRedirect("/oa/dept/list");
      ```

      

### JSP：

```jsp
<a href="${pageContext.request.contextPath}/one.action">1.请求转发页面(默认)</a><br>
<a href="${pageContext.request.contextPath}/two.action">2.请求转发action</a><br>
<a href="${pageContext.request.contextPath}/three.action">3.请求转发重定向</a><br>
<a href="${pageContext.request.contextPath}/four.action">4.重定向action</a><br>
<a href="${pageContext.request.contextPath}/five.action">5.随便条页面</a><br>
```

### 另一个action:

```java
    @RequestMapping("/other")
    public String other(){
        System.out.println("这是other的action访问");
        return "main"; //这里默认得是转发页面
    }
```



### 1.请求转发页面(默认)

```java
    @RequestMapping("/one")
    public String one(){
        System.out.println("这是请求转发页面跳转");
        // 访问地址： http://localhost:8080/springmvc_004/one.action
        return "main";//默认是请求转发使用视图解析器拼接前缀后缀进行页面跳转
    }
```



### 2.请求转发action(forward 拼接前缀和后缀的拼接,实现请求转发)

跳转：

```java
    @RequestMapping("/two")
    public String two(){
        System.out.println("这是请求转发action跳转");
        //  前缀：/admin/   /other.action    后缀：.jsp
        //forward：这组字符串可以屏蔽前缀和后缀的拼接,实现请求转发
        //http://localhost:8080/springmvc_004/two.action
        return "forward:/other.action";//默认是请求转发使用视图解析器拼接前缀后缀进行页面跳转
    }
```



### 3.请求转发重定向(redirect)

```java
    @RequestMapping("/three")
    public String three(){
        System.out.println("这是重定向页面");
        //redirect:这组字符串可以屏蔽前缀和后缀的拼接,实现重定向
        //http://localhost:8080/springmvc_004/admin/main.jsp
        return "redirect:/admin/main.jsp";
    }
```



### 4.重定向action

```java
    @RequestMapping("/four")
    public String four(){
        System.out.println("这是重定向action");
        //redirect:这组字符串可以屏蔽前缀和后缀的拼接,实现重定向
        //http://localhost:8080/springmvc_004/other.action
        return "redirect:/other.action";
    }
```



### 5.随便转得

```java
    @RequestMapping("/five")
    public String five(){
        System.out.println("这是随便跳");
        // 加forward 就是随便跳
        return "forward:/fore/login.jsp";
    }
```

## 9.SpringMVC支持得默认参数类型

- HttpServletRequest
- HttpServletResponse
- HttpSession
- Model
- Map
- ModelMap

action:

```java
/*
jsp:
<a href="${pageContext.request.contextPath}/data.action?name=zar">访问服务器,进行暑假携带跳转</a>
*/

@Controller
public class DataAction {
    @RequestMapping("/data")
    public String data(HttpServletRequest request,
                       HttpServletResponse response,
                       HttpSession session,
                       Model model,
                       Map map,
                       ModelMap modelMap){

        //做一个数据,传达main.jsp页面上
        Users users=new Users("张三",22);

        //传递数据
        request.setAttribute("requestUsers",users);
        session.setAttribute("sessionUsers",users);
        model.addAttribute("modelUsers",users);
        map.put("mapUsers",users);
        modelMap.addAttribute("modelMapUsers",users);
        return "main";//请求转发方式跳转
        //return "redirect:/admin/main.jsp";转发跳只有session
    }
}

```

跳转得页面：

```jsp
<h2>main............显示数据</h2>
<%--
            request.setAttribute("requestUsers",users);
            session.setAttribute("sessionUsers",users);
            model.addAttribute("modelUsers",users);
            map.put("mapUsers",users);
            modelMap.addAttribute("modelMapUsers",users);
--%>
requestUsers:${requestUsers}<br>
sessionUsers:${sessionUsers}<br>
modelUsers:${modelUsers}<br>
mapUsers:${mapUsers}<br>
modelMapUsers:${modelMapUsers}<br>

从index.jsp页来得数据${param.name}
```

## 10.日期处理

### 日期的提交处理(前端提交得数据会进行处理)

#### 单个日期处理

要使用注解@DateTimeFormat,此注解必须搭配springmvc.xml文件中的<mvc:annotationdriven标签>

```java
@RequestMapping("/mydate")
public String mydate(
		@DateTimeFormat(pattern = "yyyy-MM-dd")
		Date mydate){
	System.out.println(mydate);
	System.out.println(sf.format(mydate));
	return "show";
    }
```

```xml
    添加注解驱动
    <mvc:annotation-driven></mvc:annotation-driven>
```



#### 类中全局日期处理

注册一个注解,用来解析本类中所有的日期类型,自动转换.

```java
    @InitBinder
    public void initBinder(WebDataBinder dataBinder){
	    SimpleDateFormat sf=new SimpleDateFormat("yyyy-MM-dd");
        dataBinder.registerCustomEditor(Date.class,new CustomDateEditor(sf,true));
    }
```



### 日期的显示处理

在页面上显示好看的日期,必须使用JSTL.

步骤:

1. 添加依赖jstl

   - ```xml
           <dependency>
           <groupId>jstl</groupId>
           <artifactId>jstl</artifactId>
           <version>1.2</version>
         </dependency>
     ```

2. 在页面上导入标签库 

   - ```jsp
         如果是单个日期对象,直接转为好看的格式化的字符串进行显示.
         如果是list中的实体类对象的成员变量是日期类型,则必须使用jstl进行显示.
         <%--导入jstl核心标签库--%>
     	<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
     	<%--导入jstl格式化标签库--%>
     	<%@taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
     ```

3. 使用标签显示数据    

   - ```jsp
     <table width="800px" border="1">
         <tr>
             <th>姓名</th>
             <th>生日</th>
         </tr>
         <c:forEach items="${studentList}" var="stu">
             <tr>
                 <td>${stu.name}</td>
                 <td>${stu.birthday}------- <fmt:formatDate value="${stu.birthday}" pattern="yyyy-MM-dd"></fmt:formatDate></td>
             </tr>
         </c:forEach>
     ```

## 11.<mvc:annotation-driven/>标签的使用

![](图\SpringMvc\1.png)

## 12.资源在WEB-INF目录下

此目录下的动态资源,不可直接访问,只能通过请求转发的方式进行访问 .

```java
@Controller
public class WebinfAction {
    @RequestMapping("/showIndex")
    public String showIndex(){
        System.out.println("访问index.jsp");
        return "index";
    }

    @RequestMapping("/showMain")
    public String showMain(){
        System.out.println("访问main.jsp");
        return "main";
    }

    @RequestMapping("/showLogin")
    public String showLogin(){
        System.out.println("访问login.jsp");
        return "login";
    }

    //登录的业务判断
    @RequestMapping("login")
    public String login(String name, String pwd , HttpServletRequest request) {
        if ("zar".equalsIgnoreCase(name) &&"123".equalsIgnoreCase(pwd)) {
            return "main";
        }else {
            return "login";
        }

    }

}
```



# 第三章SpringMVC拦截器

## 1.拦截器介绍

### 1.应用场景

1. 日志记录：记录请求信息的日志
2. 权限检查，如登录检查
3. 性能检测：检测方法的执行时间

### 2.执行原理

![](图\SpringMvc\2.png)

### 3.拦截执行时机

 1)preHandle():在请求被处理之前进行操作

 2)postHandle():在请求被处理之后,但结果还没有渲染前进行操作,可以改变响应结果

 3)afterCompletion:所有的请求响应结束后执行善后工作,清理对象,关闭资源

### 4.实现的两种方式

1)继承HandlerInterceptorAdapter的父类

 2)实现HandlerInterceptor接口,实现的接口,推荐使用实现接口的方式

### 5.实现步骤

1. 改造登录方法,在session中存储用户信息,用于进行权限验证

   - ```java
         //登录的业务判断
         @RequestMapping("login")
         public String login(String name, String pwd , HttpServletRequest request) {
             if ("zar".equalsIgnoreCase(name) &&"123".equalsIgnoreCase(pwd)) {
                 request.getSession().setAttribute("users",name);
                 return "main";
             }else {
                 request.setAttribute("msg","用户名或密码不正确");
                 return "login";
             }
     
         }
     ```

2. 开发拦截器的功能.实现HandlerInterceptor接口,重写preHandle()方法

   - ```java
     public class  LoginInterceptor implements HandlerInterceptor {
         @Override
         public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
             //是否登录过的判断
             if(request.getSession().getAttribute("users")==null){
                 //此时就是没有登录,打回到登录页面 并给出提示
                 request.setAttribute("msg","您还没有登录请先登录");
                 request.getRequestDispatcher("/WEB-INF/jsp/login.jsp").forward(request,response);
                 return false;
             }
             return true;//放行请求
         }
     }
     
     ```

3. 在springmvc.xml文件中注册拦截器

   - ```xml
         <!--注册拦截器-->
         <mvc:interceptors>
             <mvc:interceptor>
                 <!--映射要拦截的请求-->
                 <mvc:mapping path="/**"/>
                 <!--设置放行的请求-->
                 <mvc:exclude-mapping path="/showLogin"/>
                 <mvc:exclude-mapping path="/login"/>
                 <!--配置具体的拦截器实现功能的类-->
                 <bean class="com.bjpowernode.interceptor.LoginInterceptor"></bean>
             </mvc:interceptor>
         </mvc:interceptors>
     ```

     

# 第四章SSM整合