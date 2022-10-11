



[TOC]



# 第一章框架概述

## 1.软件开发常用的结果

### 1.三层框架

1. 在项目开发中,遵循的一种形式模式.分为三层.：

   - 界面层（User Interface layer）
   - 业务逻辑层（Business Logic Layer）
   - 数据访问层（Data access layer）

2. 各层的职责：

   - 界面层:用来接收客 户端的输入,调用业务逻辑层进行功能处理,返回结果给客户端.过去的servlet就是界面层的功能.
   - 业务逻辑层:用来进行整个项目的业务逻辑处理,向上为界面层提供处理结果,向下问数据访问层要数据.
   - 数据访问层:专门用来进行数据库的增删改查操作,向上为业务逻辑层提供数据.

3. 三层的处理请求的交互：

   - 客户端<--->界面层<--->业务逻辑层<--->数据访问层<--->数据库

   - ![](图\MyBatis\1--三层架构.png)
   - 各层之间的顺序是固定不变的,不允许跨层访问
     - 用户应该访问服务员 服务员访问厨师 厨师访问采购员 采购员去收集菜(数据)
     - 然后 采购员给厨师 厨师炒好了给到了服务员 服务员上菜给用户
     - 不可以用户直接访问厨师吧

4. 为什么要使用三层？

   -  结构清晰、耦合度低,  各层分工明确
   - 可维护性高,可扩展性高
   - 有利于标准化
   -  开发人员可以只关注整个结构中的其中某一层的功能实现
   - 有利于各层逻辑的复用

### 2.常用框架(SSM)

1. MyBatis 框架：
   - MyBatis是一个优秀的基于java的持久层框架,内部封装了JDBC,开发者只需要关注的是sql语句本身,而不需要处理加载驱动(Class.forName) 创建连接（Connection）创建Statement,释放连接等繁琐的过程
   - MyBatis 通过 XML 或注解两种方式将要执行的各种 sql 语句配置起来，并通过 Java 对象和 sql 的动态参数进行映射生成最终执行的 sql 语句，最后由 mybatis 框架执行 sql 并将结果映射为 Java 对象并返回。
2. Spring 框架:
   - Spring 框架为了解决软件开发的复杂性而创建的。Spring 使用的是基本的 Java Bean 来完成以前非常复杂的企业级开发。Spring 解决了业务对象，功能模块之间的耦合，不仅在 javase,web 中使用， 大部分 Java 应用都可以从 Spring 中受益。
   - Spring 是一个轻量级控制反转(IoC)和面向切面(AOP)的容器。
   - 它是整合其它框架的框架.它的核心是IOC和AOP.它由20多个模块构成.在很多领域都提供了很好的解决方案.是一个大佬级别的存在.
3. SpringMVC 框架：
   - Spring MVC 属于 SpringFrameWork 3.0 版本加入的一个模块，为 Spring 框架提供了构建 Web 应用程序的能力。现在可以 Spring 框架提供的 SpringMVC 模块实现 web 应用开发，在 web 项目中可以无缝使用 Spring 和 Spring MVC 框架。

## 2.框架是什么

- 它是一个半成品软件.将所有的公共的,重复的功能解决掉,帮助程序快速高效的进行开发.它是可复用,可扩展的.

## 3.JDBC编程

```java
public void findStudent() {
    Connection conn = null; 
    Statement stmt = null;
    ResultSet rs = null;
    try {
    //注册 mysql 驱动 
      Class.forName("com.mysql.jdbc.Driver");
    //连接数据的基本信息 url ，username，password
    String url = "jdbc:mysql://localhost:3306/springdb"; 
    String username = "root";
    String password = "123456";
    //创建连接对象 
    conn = DriverManager.getConnection(url, username, password);
    //保存查询结果 
    List<Student> stuList = new ArrayList<>();
    //创建 Statement, 用来执行 sql 语句 
    stmt = conn.createStatement();
    //执行查询，创建记录集， 
    rs = stmt.executeQuery("select * from student");
    while (rs.next()) {
    Student stu = new Student(); 
    stu.setId(rs.getInt("id"));
    stu.setName(rs.getString("name"));
    stu.setAge(rs.getInt("age"));
    //从数据库取出数据转为 Student 对象，封装到 List 集合 
    stuList.add(stu);}
      }catch(Exception e){
          e.printStackTrace();
    }finally{
       try{
    if(rs != null)
          rs.lose();
    if(pstm != null)
          pstm.close();
       if(con != null)
          con.close();

    }catch(Exception e){
      e.printStackTrace();
    }
}
```

- JDBC得缺陷：
  - 代码比较多，开发效率低
  - 需要关注 Connection ,Statement, ResultSet 对象创建和销毁
  -  对 ResultSet 查询的结果，需要自己封装为 List
  - 重复的代码比较多些

## 4.MyBatis框架的概述

### 1.什么是MyBatis框架

-  MyBatis 本是 apache 的一个开源项目iBatis, 2010 年这个项目由 apache software foundation 迁移到了 google code，并且改名为 MyBatis  。2013 年 11 月迁移到 Github,最新版本是 MyBatis 3.5.7 ，其发布时间是 2021 年 4月 7日。
-  MyBatis完成数据访问层的优化.它专注于sql语句.简化了过去JDBC繁琐的访问机制. 

### 2.MyBatis框架的结构

![](图\MyBatis\2.MyBatis框架结构.png)

1. mybatis配置：
   - SqlMapConfig.xml，此文件作为mybatis的全局配置文件，配置了mybatis的运行环境等信息。
   - mapper.xml文件即sql映射文件，文件中配置了操作数据库的sql语句。此文件需要在SqlMapConfig.xml中加载。
2.  通过mybatis环境等配置信息构造SqlSessionFactory即会话工厂
3. 由会话工厂创建sqlSession即会话，操作数据库需要通过sqlSession进行。
4. mybatis底层自定义了Executor执行器接口操作数据库，Executor接口有两个实现，一个是基本执行器、一个是缓存执行器。
5.  Mapped Statement也是mybatis一个底层封装对象，它包装了mybatis配置信息及sql映射信息等。mapper.xml文件中一个sql对应一个Mapped Statement对象，sql的id即是Mapped statement的id。
6. Mapped Statement对sql执行输入参数进行定义，包括HashMap、基本类型、pojo，Executor通过Mapped Statement在执行sql前将输入的java对象映射至sql中，输入参数映射就是jdbc编程中对preparedStatement设置参数。
7. Mapped Statement对sql执行输出结果进行定义，包括HashMap、基本类型、pojo，Executor通过Mapped Statement在执行sql后将输出结果映射至java对象中，输出结果映射过程相当于jdbc编程中对结果的解析处理过程。

# 第二章MyBatis框架入门

## 1.创建一个数据库表

```sql
CREATE DATABASE ssm DEFAULT CHARSET utf8;

#使用(打开)ssm数据库
use ssm;

#创建表student
CREATE TABLE `student` (
`id` int(11)  AUTO_INCREMENT primary key ,
`name` varchar(255) DEFAULT NULL,
`email` varchar(255) DEFAULT NULL,
`age` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

insert into student(name,email,age) values('张三','zhangsan@126.com',22);
insert into student(name,email,age) values('李四','lisi@126.com',21);
insert into student(name,email,age) values('王五','wangwu@163.com',22);
insert into student(name,email,age) values('赵六','zhaoliun@qq.com',24);
select * from student;
```

## 2.新建一个Maven项目并修改Pom.xml

### 1.新建一个Maven项目

新建一个空的项目

![](图\MyBatis\3.创建空的工程.png)

- 下一步下一步就行

新建一个Module选择Maven工程选择quickstart模块

- ![](图\MyBatis\4.新建一个Maven模块.png)
- ![](图\MyBatis\4.2新建一个Maven模块.png)

### 2.补全目录

- ![](图\MyBatis\补全.png)

### 3.修改Pom.xml

1. 添加MyBatis和MySql的依赖在Pom.xml文件中

   - ```xml
       <dependencies>
         <dependency>
           <groupId>junit</groupId>
           <artifactId>junit</artifactId>
           <version>4.11</version>
           <scope>test</scope>
         </dependency>
         <!--添加MyBatis框架的依赖-->
         <dependency>
           <groupId>org.mybatis</groupId>
           <artifactId>mybatis</artifactId>
           <version>3.5.6</version>
         </dependency>
         <!--添加Mysql依赖-->
         <dependency>
           <groupId>mysql</groupId>
           <artifactId>mysql-connector-java</artifactId>
           <version>8.0.28</version>
         </dependency>
       </dependencies>
     ```

   - 注意添加完依赖以后要记得刷新一下Maven

     - ![](图\MyBatis\4.3刷新Maven.png)

2. 修改pom.xml文件,添加资源文件指定

   - ```xml
     <!--添加资源文件的指定-->
       <build>
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
       </build>
     ```

## 3.在idea中添加数据库可视化

![](图\MyBatis\idea可视化.png)

![](图\MyBatis\配置.png)

## 4.编写一个Student的实体类

```java
package com.bjpowernode.pojo;
/*
这里规范是将实体类放在pojo这个包下
注意了 成员变量名和数据库当中的列名是一样的,并且数据类型是一致的
*/
public class Student {
    private Integer id;
    private String name;
    private String email;
    private Integer age;
    
    //添加构造方法 无参的 全参数的 不带主键的 并且创建setter和getter方法
}
```



## 5.在resources添加配置文件

### 1.添加 jdbc.properties属性文件(数据库的配置)

- ```properties
  jdbc.driverClassName=com.mysql.cj.jdbc.Driver
  jdbc.url=jdbc:mysql://localhost:3306/ssm?useUnicode=true&characterEncoding=utf8
  jdbc.username=root
  jdbc.password=root
  ```

### 2.添加MyBatis的核心配置文件SqlMapConfig.xml文件

- 右键新建SqlMapConfig.xml文件,从MyBatis-3-User-Guide-Simplified-Chinese.pdf中拷贝过来头参数.

  - ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
            "http://mybatis.org/dtd/mybatis-3-config.dtd">
    ```

- 配置SqlMapConfig.xml文件

  - ```xml
    <configuration>
        <!--
    	1.读取属性文件(jdbc.properties)
    	其中一共有两个属性:
    		resource：从当前resource目录下找指定名称的文件加载
    		url：使用绝对路径加载属性配置文件
    	-->
        <properties resource="jdbc.properties"></properties>
        <!--
    	2. environments:进行环境变量(连接数据库)的配置
    	注意：
     		可以进行多个数据库连接配置,可以上线一套,开发一套,可以mysql一套,oracle一套等
    	default:
    		本次配置中使用的环境变量的名称,多套配置,default决定哪套配置生效
    	-->
        <environments default="development">
            <environment id="development">
                <!--
    			transactionManager配置事务管理器
    			type:指定事务管理的方式
                    JDBC:事务的控制交给程序员控制
                    MANAGED:由容器(spring)来管理事务
    			-->
                <transactionManager type="JDBC"></transactionManager>
                <!--
    			dataSource配置数据源
    			type:指定不同的配置方式
    				JNDI:java命名目录接口,在服务器端进行数据库连接池的管理
    				POOLED:使用数据库连接池
    				UNPOOLED:不使用数据库连接池
    			property:
    			    driver:数据库驱动
                     url:数据库的路径
                     username:访问数据库的用户名
                     password:访问数据库的用户的密码
    			-->
                <dataSource type="POOLED">
                    <property name="driver" value="${jdbc.driverClassNmae}"></property>
                    <property name="url" value="${jdbc.url}"></property>
                    <property name="username" value="${jdbc.username}"></property>
                    <property name="password" value="${jdbc.password}"></property>
                </dataSource>
            </environment>
        </environments>
        <!--
    	3.注册mapper.xml文件
    		resource:从resource目录中指定名称的文件注册
    		url:使用绝对路径注册
    		class:动态代理方式下的注册
    	-->
        <mappers>
            <mapper resource="StudentMapper.xml"></mapper>
        </mappers>
    </configuration>
    ```

  - 就此说一下数据库连接池

    - ![](图\MyBatis\数据库连接池.png)

  - 也就是第一次客户端从数据库连接池中拿数据,数据库连接池从数据库中拿数据

  - 第二次的时候,客户端向数据库连接池中拿数据的时候,如果数据库连接池中有这个数据,就不在和数据库进行连接了

  - 这样减少了对数据库的访问次数

### 3.创建StudentMapper.xml文件

1. 右键新建StudentMapper.xml文件,从MyBatis-3-User-Guide-Simplified-Chinese.pdf中拷贝过来头参数.

2. 该文件完成数据库中student表的所有增删改查的操作.

3. 编写sql语句

   - ```xml
     <!--
     mapper 是整个文件的大标签,用来开始和结束的xml
     属性：
     	namespace:指定命名空间(相当于包名),用来区分不同mapper.xml文件中相同的id属性
     -->
     <mapper namespace="zar">
         <!--
         完成查询全部学生的功能
         List<Student> getAll();
             id:通过id来调用的
             resultType:指定查询返回的结果集的类型,如果是集合则必须是泛型的类型
             parameterType:如果有参数,则通过它来指定参数的类型
         -->
         <select id="getAll" resultType="com.bjpowernode.pojo.Student">
             select id,name,email,age from student;
         </select>
         <!--
     	按主键查询学生的信息:
     	Student getById(Integer id);
     	resultType 这里的返回值为Student 要带包名的
     	parameterType 参数为int类型 到下面会说数据类型的别名
     	-->
         <select id="getById" resultType="com.bjpowernode.pojo.Student" ></select>
         
         <!--
     	学生模糊查询：
     	List<Student> getByName(String name)
     	parameterType 参数类型 String
     	-->
        <select id="getByName" parameterType="string" resultType="com.bjpowernode.pojo.Student">
             select id,name,email,age from student
             where name like '%${name}%'
        </select>
     	<!--
     	增加学生：
     	int insert(Student student); 注意 增删改不用返回值
     	我们对比这实体类来写
     	private Integer id;
     	private String name;
     	private String email;
     	private Integer age;
     	-->    
         <insert id="insert" parameterType="com.bjpowernode.pojo.Student">
             insert into student(name,email,age) values(#{name},#{email},#{age})
         </insert>
         <!--
     	按主键删除学生
     	int delete(Integer id);
     	-->  
         <delete id="delete" parameterTpye="int">
              delete from student where id=#{id}
         </delete>
         
         <!--
     	更新学生：
     	int update(Student student);
     	-->
         <update id="update" parameterType="com.bjpowernode.pojo.Student">
             update student set name=#{name},email=#{email},age=#{age}
             where id=#{id}
         </update>
     </mapper>
     ```

   - 各个数据类型的别名

     - ```
       别名				映射的类型
       _byte 				byte
       _long 				long
       _short 				short
       _int 				int
       _integer 			int
       _double 			double
       _float 				float
       _boolean 			boolean
       string 				String
       byte 				Byte
       long 				Long
       short 				Short
       int 				Integer
       integer 			Integer
       double 				Double
       float 				Float
       boolean 			Boolean
       date 				Date
       decimal 			BigDecimal
       bigdecimal 			BigDecimal
       object 				Object
       map 				Map
       hashmap 			HashMap
       list 				List
       arraylist 			ArrayList
       collection 			Collection
       iterator 			Iterator
       ```

## 6.测试

```java
//这里就直接上代码了
public class MyTest{
	@Test//这里要导入juint的依赖
    public void testGetAll(){
        //使用文件流读取核心配置文件SqlMapConfig.xml
        InputStream in=Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建SqlSessionFactory工程
        SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
        //取出SqlSession的对象
        SqlSession sqlSession=factory.openSession();
        //完成查询操作
        // 这里的 zar.getAll 就是上面StudentMapper.xml文件中 namespace 和id名称
        List<Student> studentList=sqlSession.selectList("zar.getAll");
        studentList.forEach(student -> System.out.println(student));
        //关闭sqlSession
       	sqlSession.close();
    }
    
    @Test
    public void testGetByName() throws IOException{
        //读取核心配置文件
        IputStream in=Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建SqlSessionFactory工程
        SqlSessionFactory factory=new SqlSessionFactoryBuilder.bulid(in);
        //取出SqlSession
        SqlSession sqlSeesion=factory.openSession();
        //完成查询操作
        List<Student> students=sqlSession.selectList("zar.getByName","张");
        students.forEach(student -> System.out.println(student));
        //关闭sqlSession
        sqlSession.close();
    }
    
    @Test
    public void testInsert() throws IOException {
        //读取核心配置文件
        InputStream in=Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建SqlSessionFactory
        SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
        //取出SqlSession
        SqlSession sqlSession=factory.openSession();
        //插入数据
        int num=sqlSession.insert("zar.insert",new Student("jack","222@155156",28));
        //切记切记切记：在所有的增删改中必须手工提交事务！！！！！
        sqlSession.commit();
        //关闭SqlSession
        sqlSession.close();
    }
    @Test
    public void testDelete() throws IOException{
        //读取核心配置文件
        InputStream in=Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建SqlSessionFactory
        SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
        //取出SqlSession
        SqlSession sqlSession=factory.openSession();
        //删除
        int num=sqlSession.delete("zar.delete",5);
        //切记切记切记：在所有的增删改中必须手工提交事务！！！！！
        sqlSession.commit();
        //关闭
        sqlSession.close();
    }
    
    @Test
    public void testUpdate() throws IOException{
        //读取核心配置文件
        InputStream in=Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建工厂
        SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
        //取出SqlSession
        SqlSession sqlSession=factory.openSession();
        //更新
        int num=sqlSession.update("zar.update",new Student(3,"sdfsdf","151@zhang",22));
        System.out.println("更新的条数为" + num);
        //提交事务
        sqlSession.commit();
        //关闭
        sqlSession.close();
    }   
}
```

## 7.优化

### 1.优化SqlMapConfig.xml和StudentMapper.xml

1. SqlMapCongfig.xml 

   - 当我们在StudentMapper.xml文件中 返回值和形式参数 都需要写全类型(带包名的)所以我们要注册别名

     - ```xml
       <!--
       在SqlMapConfig.xml文件中 标签也是有上下顺序的
       properties
       settings
       typeAliases 
       typeHandlers 
       objectFactory 
       objectWrapperFactory 
       reflectorFactory 
       plugins 
       environments 
       databaseIdProvider 
       mappers
       -->    
       
       
       <typeAliases>
           <!--单个实体类别名注册-->
           <!--<typeAlias type="com.bjpowernode.pojo.Student" alias="student"></typeAlias>-->
           <!--批量注册-->
           <package name="com.bjpowernode.pojo"></package>
       </typeAliases>
       ```

   - 输出日志信息

     - ```xml
           <!--设置日志输出底层执行的代码-->
           <settings>
               <setting name="logImpl" value="STDOUT_LOGGING"/>
           </settings>
       ```

   - 最终的为

     - ```xml
       <configuration>
           <!--读取jdbc.properties属性-->
           <properties resource="jdbc.properties"></properties>
           <!--设置日志输出-->
           <settings>
               <setting name="logImpl" value="STDOUT_LOGGING"/>
           </settings>
          <!--注册实体类的别名-->
           <typeAliases>
               <package name="com.bjpowernode.pojo"></package>
           </typeAliases>
           <!--配置环境变量-->
           <environments default="development">
               <environment id="development">           
                   <transactionManager type="JDBC"></transactionManager>   
                   <dataSource type="POOLED">
                       <property name="driver" value="${jdbc.driverClassName}"></property>
                       <property name="url" value="${jdbc.url}"></property>
                       <property name="username" value="${jdbc.username}"></property>
                       <property name="password" value="${jdbc.password}"></property>
                   </dataSource>
               </environment>
           </environments>
           <!--注册mapper文件-->
           <mappers>
               <mapper resource="StudentMapper.xml"></mapper>
           </mappers>
       </configuration>
       ```

       

2. StudentMapper.xml

   - 既然在SqlMapConfig.xml中注册了别名 就不用使用全类名了

     - ```xml
       <mapper namespace="zar">
           <select id="getAll" resultType="student">
               select id,name,email,age from student;
           </select>
           
           <select id="getById" parameterType="int" resultType="student">
               select id,name,email,age from student
               where id=#{id}
           </select>
           
           <select id="getByName" parameterType="string" resultType="student">
               select id,name,email,age from student
               where name like '%${name}%'
           </select>
           
           <insert id="insert" parameterType="student">
               insert into student(name,email,age) values(#{name},#{email},#{age})
           </insert>
           
           <delete id="delete" parameterType="int">
               delete from student where id=#{id}
           </delete>
           
           <update id="update" parameterType="student">
               update student set name=#{name},email=#{email},age=#{age}
               where id=#{id}
           </update>
       ```

### 2.改善Test测试类

- 发现在测试类中好多代码都是重复的，想这样的代码我们每次都要写一遍 特别繁琐，在JDBC中我们可以包装一个工具类 

  - ```java
    //读取核心配置文件
    InputStream in=Resources.getRescourceAsStream("SqlMapConfig.xml");
    //创建sqlSessionFactory工厂
    SqlSessionFactory factory=new SqlSessionFactoryBuilder.bulid(in);
    //取出SqlSession
    SqlSession sqlSession=factory.openSession();
    //关闭
    sqlSession.close();
    ```

- 在Junit注解中有 @Before @After 这两个注解

  - ```java
    //@Before：在所有的@Test方法执行前 先执行的代码
    // @After：在所有的@Test方法执行之前 执行代码
    
    public class MyTest {
         SqlSession sqlSession=null;
        
         @Before 
         public void openSqlSession() throws IOException {
            InputStream inputStream=Resources.getResourceAsStream("SqlMapConfig.xml");
            SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(inputStream);
            sqlSession=factory.openSession();
         }
    
         @After
         public void closeSqlSession(){
             sqlSession.close();
         }
        
        @Test
        public void testGetAll() throws IOException {
            List<Student> studentList=sqlSession.selectList("zar.getAll");
            studentList.forEach(student -> System.out.println(student));
    
        }
    
        @Test
        public void testGetById() throws IOException {
            Student student=sqlSession.selectOne("zar.getById",1);
            System.out.println(student);
        }
    
        @Test
        public void testGetByName() throws IOException {
            List<Student> students=sqlSession.selectList("zar.getByName","张");
            students.forEach(student -> System.out.println(student));
        }
    
        @Test
        public void testInsert() throws IOException {
            //插入数据
            int num=sqlSession.insert("zar.insert",new Student("jack","222@155156",28));
            //切记切记切记：在所有的增删改中必须手工提交事务！！！！！
            sqlSession.commit();
        }
    
        @Test
        public void testDelete() throws IOException{
            //删除
            int num=sqlSession.delete("zar.delete",5);
            //切记切记切记：在所有的增删改中必须手工提交事务！！！！！
            sqlSession.commit();
        }
        @Test
        public void testUpdate() throws IOException{
            //更新
            int num=sqlSession.update("zar.update",new Student(3,"afsfs","151@zhang",22));
            System.out.println("更新的条数为" + num);
            //提交事务
            sqlSession.commit();
        }
    }
    ```

## 8.MyBatis对象分析

### 1.Resources类

Resources 类，顾名思义就是资源，用于读取资源文件。其有很多方法通过加载并解析资源文件，返回不同类型的 IO 流对象。

### 2.SqlSessionFactoryBuilder类

SqlSessionFactory 的 创 建 ， 需 要 使 用 SqlSessionFactoryBuilder 对 象 的 build() 方 法 。 由 于SqlSessionFactoryBuilder对象在创建完工厂对象后，就完成了其历史使命，即可被销毁。所以，一般会将该 对象创建为一个方法内的局部对象，方法结束，对象销毁。

### 3.SqlSessionFactory接口

SqlSessionFactory 接口对象是一个重量级对象（系统开销大的对象），是线程安全的，所以一个应用只需要一个该对象即可。创建 SqlSession 需要使用 SqlSessionFactory 接口的的 openSession()方法。

A. openSession(true)：创建一个有自动提交功能的 SqlSession

B. openSession(false)：创建一个非自动提交功能的 SqlSession，需手动提交

C. openSession()：同 openSession(false)

### 4.SqlSession接口

SqlSession  接口对象用于执行持久化操作。一个 SqlSession  对应着一次数据库会话，一次会话以SqlSession 对象的创建开始，以 SqlSession 对象的关闭结束。

SqlSession 接口对象是线程不安全的，所以每次数据库会话结束前，需要马上调用其 close()方法，将其关闭。再次需要会话，再次创建。 SqlSession 在方法内部创建，使用完毕后关闭。







# 第三章动态代理

## 1.动态代理存在的意义

![](图\MyBatis\动态代理存在的意义.png)

## 2.动态代理的实现规范

1. UsersMapper.xml文件与UsersMapper.java的接口必须同一个目录下.
2. UsersMapper.xml文件与UsersMapper.java的接口的文件名必须一致,后缀不管.
3. UserMapper.xml文件中标签的id值与与UserMapper.java的接口中方法的名称完全一致.
4. UserMapper.xml文件中标签的parameterType属性值与与UserMapper.java的接口中方法的参数类型完全一致.
5. UserMapper.xml文件中标签的resultType值与与UserMapper.java的接口中方法的返回值类型完全一致.
6. UserMapper.xml文件中namespace属性必须是接口的完全限定名称com.bjpowernode.m apper.UsersMapper
7. 在SqlMapConfig.xml文件中注册mapper文件时,使用class=接口的完全限定名称com.bjpowernode.mapper.UsersMapper.

## 3.开发步骤

### 1.新建一个users表

```sql
use ssm;
-- ----------------------------
-- Table structure for `users`
-- ----------------------------
DROP TABLE IF EXISTS `users`;
CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `username` varchar(32) COMMENT '用户名称',
  `birthday` date DEFAULT NULL COMMENT '生日',
  `sex` char(2) DEFAULT NULL COMMENT '性别',
  `address` varchar(256) DEFAULT NULL COMMENT '地址',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=27 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of user
-- ----------------------------
INSERT INTO `users` VALUES (1, '王五', '2000-09-10', '2', '安徽');
INSERT INTO `users` VALUES (2, '张三', '2001-07-12', '1', '北京市');
INSERT INTO `users` VALUES (3, '张小明', '1999-02-22', '1', '河南');
INSERT INTO `users` VALUES (4, '陈小亮', '2002-11-19', '1', '辽宁');
INSERT INTO `users` VALUES (5, '张三丰', '2001-03-10', '1', '上海市');
INSERT INTO `users` VALUES (6, '陈小明', '2002-01-19', '1', '重庆市');
INSERT INTO `users` VALUES (7, '王五四', '2001-05-13', '2', '天津市');
select * from users;
```

### 2.新建maven工程,刷新可视化(这里和静态代理一样)

### 3.修改目录(这里和静态代理一样)

### 4.修改pom.xml文件,添加依赖(这里和静态代理一样)

### 5.添加jdbc.propertis和SqlMapConfig.xml到resources目录下

- jdbc.properties

  - ```properties
    jdbc.driverClassName=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/ssm?useUnicode=true&characterEncoding=utf8
    jdbc.username=root
    jdbc.password=root
    ```

- SqlMapConfig.xml

  - ```xml
    <configuration>
        <!--读取jdbc.properties属性-->
        <properties resource="jdbc.properties"></properties>
        <!--设置日志输出-->
        <settings>
            <setting name="logImpl" value="STDOUT_LOGGING"/>
        </settings>
        <!--注册实体类的别名-->
        <typeAliases>
            <package name="com.bjpowernode.pojo"></package>
        </typeAliases>
        <!--配置环境变量-->
        <environments default="development">
            <environment id="development">
                <transactionManager type="JDBC"></transactionManager>
                <dataSource type="POOLED">
                    <property name="driver" value="${jdbc.driverClassName}"></property>
                    <property name="url" value="${jdbc.url}"></property>
                    <property name="username" value="${jdbc.username}"></property>
                    <property name="password" value="${jdbc.password}"></property>
                </dataSource>
            </environment>
        </environments>
        <!--注册mapper文件-->
        <mappers>
            <!--<mapper class="com.bjpowernode.mapper.UsersMapper"></mapper>-->
            <!--批量注册-->
            <package name="com.bjpowernode.mapper"/>
        </mappers>
    
    ```

### 6.添加实体类

```java
//规范 实体类在pojo的包下
package com.bjpowernode.pojo;

import java.util.Date;

public class Users {
    private Integer id;
    private String username;
    private Date birthday;
    private String sex;
    private String address;
    //提供set get 无参 有参的构造方法
}
```

### 7.添加mapper文件夹,新建UsersMapper接口

```java
public interface UsersMapper {
    //查询全部用户信息
    List<Users> getAll();
    //根据用户主键查用户
    Users getById(Integer id);
    //根据用户名模糊查询
    List<Users> getByName(String name);
    //优化后的模糊查询
    List<Users> getByNameNice(String name);
    //用户的更新
    int update(Users users);
    //增加用户
    int insert(Users users);
    //根据主键删除用户
    int delete(Integer id);
    //模糊用户名和地址查询
    List<Users> getByNameOrAddress(
        	//在下面的${}有讲解
            @Param("columnName")
            String columnName,
            @Param("columnValue")
            String columnValue);
}

```

### 8.在mapper文件夹下,新建UsersMapper.xml文件,完成增删改查功能

```xml
<mapper name="com.bjpowernode">
    <!--
   	查询全部用户信息
    List<Users> getAll();
	-->
    <select id="getAll" resultTpye="users">
        select id,username,birthday,sex,address 
        from users
    </select>
    
    <!--
	根据用户主键查用户
    Users getById(Integer id);
	-->
    <select id="getById" parameterTyee="int" resultType="users">
        select id,username,birthday,sex,address 
        from users
        where id=${id}
    </select>
    
    <!--
	根据用户名模糊查询
    List<Users> getByName(String name);

	这个存在sql注入的问题 
	-->
    <select id="getByName" parameterType="string" resultType="users">
        select  id,username,birthday,sex,address 
        from users
        where username like '%name%';
    </select>
    
    <!--
	优化后的模糊查询
    List<Users> getByNameNice(String name);
	-->
    <select id="getByNameNice" parameterType="string" resultType="users">
        select id,username,birthday,sex,address 
        from users
        where username like concat('%',#{name},'%')
    </select>
    
    <!--
	用户的更新
    int update(Users users);
	如果是增删改的话 不用写返回值
	-->
    <update id="update" parameterType="users">
        update users set username = #{username},birthday=#{birthday},sex=#{sex},address=#{address}
        where id=#{id}
    </update>
    
    <!--
	增加用户
    int insert(Users users);
	selectKey 是返回主键标签
	-->
    <insert id="insert" parameterType="users">
        insert into users(username,birthday,sex,address) 
        	values(#{username},#{birthday},#{sex},#{address})
    </insert>
    
    <!--
	根据主键删除用户
    int delete(Integer id);
	-->
    <delete id="delete" parameterType="int">
        delete from users
        where id=#{id}
    </delete>
    
    <!--
	模糊用户名和地址查询
    List<Users> getByNameOrAddress(
            @Param("columnName")  ===>为了在sql语句中使用的名称
            String columnName,
            @Param("columnValue")  ===>为了在sql语句中使用的名称
            String columnValue);

		这里要用${columnName} 这也是$最光辉的时刻
	-->
  <select id="getByNameOrAddress" resultType="users">
      select id,username,birthday,sex,address
      from users
      where ${columnName} like concat('%',#{columnValue},'%')  ==>此处使用的是@Param注解里的名称
  </select>
</mapper>
```

### 9.测试

```java
public class MyTest {
    SqlSession sqlSession=null;
    //动态代理对象
    UsersMapper uMapper=null;
    //日期格式化的刷子
    SimpleDateFormat sf=new SimpleDateFormat("yyyy-MM-dd");

    @Before
    public void openSqlSession() throws IOException {
        //读取核心配置文件
        InputStream in= Resources.getResourceAsStream("SqlMapConfig.xml");
        //创建工厂对象
        SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
        //取出sqlSession
        sqlSession = factory.openSession(true);//这个是自动提交
        //取出动态代理得对象,完成接口中方法得调用,实则是调用xml文件中相应得标签得功能
        yMapper=sqlSession.getMapper(UsersMapper.class);
    }
    @After
    public void closeSqlSession(){
        sqlSession.close();
    }

    //查询所有
    @Test
    public void testGetAll(){
        System.out.println(uMapper.getClass());
        //List<Users> users=sqlSession.selectList("");
        //就说在调用接口的方法,mybatis框架已经为我们把功能代理出来了
        List<Users>  usersList=uMapper.getAll();
        usersList.forEach(users-> System.out.println(users));
    }

    //更新
    @Test
    public void testUpdate() throws ParseException {
        Users users=new Users(7,"haha",sf.parse("2000-01-01"),"2","北京大兴庄");
        int num=uMapper.update(users);
        System.out.println(num);
        //切记切记切记 手动提交
        sqlSession.commit();
    }
	//根据主键查询用户
    @Test
    public void testGetById(){
        Users users=uMapper.getById(3);
        System.out.println(users);
    }
	//根据模糊查询用户
    @Test
    public void testGetByName(){
        List<Users> usersList=uMapper.getByName("小");
        usersList.forEach(users -> System.out.println(users));
    }
	//优化后的模糊查询
    @Test
    public void teatGetByNameNice(){
        List<Users> usersList=uMapper.getByNameNice("小");
        usersList.forEach(users -> System.out.println(users));
    }
	//模糊用户名和地址查询
    @Test
    public void getByNameOrAddress(){
        List<Users> usersList=uMapper.getByNameOrAddress("username","小");
        usersList.forEach(users -> System.out.println(users));
    }
	//插入
    @Test
    public void testInsert() throws Exception{
        Users u=new Users("lala",sf.parse("2001-1-1"),"2","张家口");
        int num=uMapper.insert(u);
        System.out.println("改变的条数为"+num);
        sqlSession.commit();
        System.out.println(u);
    }
	//删除
    @Test
    public void testDelete(){
        int num=uMapper.delete(28);
        System.out.println(num);
        sqlSession.commit();
    }
	//uuid
    @Test
    public void testUUID(){
        //  这是一个全球唯一随机字符串,由36个字母数字中划线组.
        UUID uuid=UUID.randomUUID();
        System.out.println(uuid.toString().replace("-","").substring(20));
    }

}

```



## 4. #{}和${}

### #{}占位符

1. 传参大部分使用#{}传参,它的底层使用的是PreparedStatement对象,是安全的数据库访问 ,防止sql注入.

2. #{}里如何写,看parameterType参数的类型

   - 如果parameterType的类型是简单类型(8种基本(封装)+String),则#{}里随便写.

     - ```xml
       <select id="getById" parameterType="int" resultType="users">  ===>入参类型是简单类型
               select id,username,birthday,sex,address
               from users
               where id=#{zar}  ===>随便写
        </select>  
       ```

   - parameterType的类型是实体类的类型,则#{}里只能是类中成员变量的名称,而且区分大小写. 

     - ```xml
       <insert id="insert" parameterType="users" >  ===>入参是实体类
       	insert into users (username, birthday, sex, address) values(#{userName},#{birthday},#{sex},#{address})  ==>成员变量名称
        </insert>
       ```

### ${}字符串拼接或字符串替换

1. 字符串拼接,一般用于模糊查询中.建议少用,因为有sql注入的风险. 

2. 也分两种情况,同样的看parameterType的类型

   - 如果parameterType的类型是简单类型,则${}里随便写,但是分版本,如果是3.5.1及以下的版本,只以写value.

     - ```xml
       <select id="getByName" parameterType="string" resultType="users">  ===>入参是简单类型
               select id,username,birthday,sex,address
               from users
               where username like '%${zar}%'   ===>随便写
        </select> 
       ```

   - 如果parameterType的类型是实体类的类型,则${}里只能是类中成员变量的名称.(现在已经少用)

   - 优化后的模糊查询(以后都要使用这种方式)

     - ```xml
           <select id="getByNameGood" parameterType="string" resultType="users">
               select id,username,birthday,sex,address
               from users
               where username like concat('%',#{name},'%')
           </select>
       ```

3. 字符串替换

   - 需求:模糊地址或用户名查询

     - ```xml
       select * from users where username like '%小%';
       select * from users where address like '%市%'
       
       <!--
         //模糊用户名和地址查询
         //如果参数超过一个,则parameterType不写
         List<Users> getByNameOrAddress(
                 @Param("columnName")  ===>为了在sql语句中使用的名称
                 String columnName,
                 @Param("columnValue")   ===>为了在sql语句中使用的名称
                 String columnValue);
         -->
         <select id="getByNameOrAddress" resultType="users">
             select id,username,birthday,sex,address
             from users
             where ${columnName} like concat('%',#{columnValue},'%')  ==>此处使用的是@Param注解里的名称
         </select>
       
       ```

       

## 5.返回主键标签

在插入语句结束后, 返回自增的主键值到入参的users对象的id属性中.

```xml
<insert id="insert" parameterType="users" >
<selectKey  keyProperty="id" resultType="int" order="AFTER">
	select last_insert_id()
</selectKey>
    insert into users (username, birthday, sex, address) values(#{userName},#{birthday},#{sex},#{address})
</insert>


<selectKey>标签的参数详解:
    keyProperty: users对象的哪个属性来接返回的主键值
    resultType:返回的主键的类型
    order:在插入语句执行前,还是执行后返回主键的值 AFTER后 BFORE前
```



# 第四章动态sql

## 1.各个标签的使用和详解(在测试类中,没有写@Before @After)

### 1.sql 和include

```
<sql>:
	用来定义代码片断,可以将所有的列名,或复杂的条件定义为代码片断,供使用时调用.
	当多种类型的查询语句的查询字段或者查询条件相同时，可以将其定义为常量，方便调用。
<include>:
	用来引用<sql>定义的代码片断.
	用来引用常量的
```

- ```xml
   <!--定义代码片断-->
      <sql id="allColumns">
          id,username,birthday,sex,address
      </sql>
     <!--引用定义好的代码片断-->
     <select id="getAll" resultType="users" >
          select <include refid="allColumns"></include>
          from users
  </select>
  ```

### 2.if 和where

```
<if>:
	进行条件判断
	test条件判断的取值可以是实体类的成员变量,可以是map的key,可以是@Param注解的名称.	
<where>:
	进行多条件拼接,在查询,删除,更新中使用.
```
- ```xml
  <!--
  按指定的条件进行多条件查询
  List<Users> getByCondition(Users users);
  如果我们在构建一个 users对象的时候 
  Users users=new Users();
  u.setSex("1"); 此时查询的是 性别为 1的
  u.setUsername("小"); 此时查询的是 姓名中有小的 ....
  只要 属性值不为空 就会条件拼接 这也要看你test中写的是什么了
      根据实体类得成员变量来决定是否添加条件
          private Integer id; null 默认值
          private String username; null
          private Date birthday; null
          private String sex; null
          private String address; null
  -->
  <select id="getByCondition" parameterType="users" resultType="users">
      select <include refid="allColumns"></include>
      from users
      <where>
          <if test="username !=null and username !=''">
              and username like concat('%',#{username},'%')
          </if>
          <if test="birthday !=null">
              and birthday=#{birthday}
          </if>
          <if test="sex !=null and sex!=''">
              and sex=#{sex}
          </if>
          <if test="address!=null and address!=''">
              and address like concat('%',#{address},'%')
          </if>
      </where>
  </select>
  ```

- 测试：

  - ```java
        @Test
        public void testGetByCondition() throws ParseException {
            Users u=new Users();
            //多条件查询
              u.setSex("1"); 此时查询的是 性别为1的用户
    		//u.setUsername("小");
    		//u.setAddress("市");
    		//u.setBirthday(sf.parse("2001-01-01"));
            List<Users> usersList=uMapper.getByCondition(u);
            usersList.forEach(users -> System.out.println(users));
    
        }
    ```

### 3.set

```
set:
	有选择的进行更新处理,至少更新一列.能够保证如果没有传值进来,则数据库中的数据保持不变.
```

- ```xml
  <!--
  有选择得更新:
      int updateBySet(Users users);
      update users
      set ....
      where id=id
  如果我们构建的 users对象 主键id=10 其他的为null 那么更新的时候 其他的就全为null了
  <set> 标签就是有选择的更新 不为null 或空的更新
  -->
  <update id="updateBySet" paratemerType="users">
      update users
      <set>
          <if test="username !=null and username !=''">
              username = #{username}, ===>注意这里结尾是  ","
          </if>
          <if test="birthday !=null">
              birthday=#{birthday},
          </if>
          <if test="sex !=null and sex!=''">
               sex=#{sex},
          </if>
          <if test="address!=null and address!=''">
              address=#{address}
          </if>
      </set>
      where id=#{id}
  </update>
  ```

- 测试:

  - ```java
        @Test
        public void testUpdateSet() throws ParseException {
            Users users=new Users();
            //这里如果不是有选择得更新得话 除了id 和 username 其他得就全部是默认null了
            users.setId(7);
            users.setUsername("星期二");
            int num=uMapper.updateBySet(users);
            System.out.println(num);
            //切记切记切记 手动提交
            sqlSession.commit();
        }
    ```

    

### 4.foreach

```
<foreach>:
	用来进行循环遍历,完成循环条件查询,批量删除,批量增加,批量更新.
参数详解：
	collection:用来指定入参的类型,如果是List集合,则为list,如果是Map集合,则为map,如果是数组,则为array.
    item:每次循环遍历出来的值或对象
    separator:多个值或对象或语句之间的分隔符
    open:整个循环外面的前括号 
    close:整个循环外面的后括号
    index ：在list和数组中,index是元素的序号，在map中，index是元素的key，该参数可选。
    separator ：表示元素之间的分隔符，例如在in()的时候，separator=","会自动在元素中间用“,“隔开，避免手动输入逗号导致sql错误，如in(1,2,)这样。该参数可选。
```

- ```xml
  <!--
  查询多个指定id得用户信息
  List<Users> getByIds(Integer[] arr);
      select id,username,birthday,sex,address
      from users
      where id in(2,4,6)
  -->
  <select id="getByIds" resultType="users">
      select <include refid="allColumns"></include>
      from users
      where id in
      	<foreach collection="array" item="id" separator="," open="(" close=")">
              #{id}
      	</foreach>
  </select>
  ```

  - 测试：
    - ```java
          @Test
          public void testGetByIds(){
              Integer[] array={2,4,6};
              List<Users> usersList=uMapper.getByIds(array);
              usersList.forEach(users -> System.out.println(users));
          }
      ```

- ```xml
  <!--
  批量删除
  int deleteBatch(Integer[] arr);
  delete from users where id in(2,4,6)
  入参超过一个就不写 返回值增删改不写
  -->
  <delete id="deleteBatch">
      delete from users
      where id in
      	<foreach collection="array" item="id" separator=","  open="(" close=")" >
              #{id}
      	</foreach>
  </delete>
  ```

  - 测试：

    - ```java
          @Test
          public void testDeleteBatch(){
              Integer[] array={2,4,6};
              int num=uMapper.deleteBatch(array);
              sqlSession.commit();
              System.out.println(num);
          }
      ```

- ```xml
  <!--
  批量插入
  int insertBatch(List<Users> users)
          private Integer id; null 默认值
          private String username; null
          private Date birthday; null
          private String sex; null
          private String address; null
  这里要注意要 u.username u.birthday u.sex u.address 用到的是u中的成员变量
  -->
  <insert id="insertBatch">
      insert into users(username,birthday,sex,address)
      values
      	<foreach collection="list" item="u" separator=",">
              (#{u.username},#{u.birthday},#{u.sex},#{u.address})
      	</foreach>
  </insert>
  ```

  - 测试：

    - ```xml
          @Test
          public void testInsertBatch() throws Exception{
              Users u1=new Users("aa",sf.parse("2002-05-09"),"1","朝阳区");
              Users u2=new Users("bb",sf.parse("2002-05-09"),"1","朝阳区");
              Users u3=new Users("cc",sf.parse("2002-05-09"),"1","朝阳区");
              Users u4=new Users("dd",sf.parse("2002-05-09"),"1","朝阳区");
              List<Users> usersList=new ArrayList<>();
              usersList.add(u1);
              usersList.add(u2);
              usersList.add(u3);
              usersList.add(u4);
              int num=uMapper.insertBatch(usersList);
              sqlSession.commit();
              System.out.println(num);
          }
      ```

- ```xml
  <!--
  批量更新
  int updateBatch(List<User> users);
          private Integer id; null 默认值
          private String username; null
          private Date birthday; null
          private String sex; null
          private String address; null
  -->
  <update id="updateBatch">
      <foreach collection="list" item="u" separator=",">
          update users
          <set>
              <if test="u.username !=null and u.username !=''">
                  username=#{u.username},
              </if>
              <if test="u.birthday !=null">
                  birthday=#{u.birthday},
              </if>
              <if test="u.sex !=null and u.sex!=''">
                  sex=#{u.sex},
              </if>
              <if test="u.address!=null and address!=''">
                  address=#{u.address}
              </if>
          </set>
          where id=#{u.id}
      </foreach>
  </update>
  要使用批量更新，必须在jdbc.properties属性文件中的url中添加&allowMultiQueries=true，允许多行操作。
  ```

  - 测试

    - ```java
      @test
      public void testUpdateBatch{
          Users u1=new Users(4,"aa",sf.parse("2002-05-09"),"1","朝阳区");
          Users u2=new Users(5,"aa",sf.parse("2002-05-09"),"1","朝阳区");
          Users u3=new Users(3,"aa",sf.parse("2002-05-09"),"1","朝阳区");
          Users u4=new Users(4,"aa",sf.parse("2002-05-09"),"1","朝阳区");
          List<Users> usersList=new ArrayList<>();
          usersList.add(u1);
          usersList.add(u2);
          usersList.add(u3);
          usersList.add(u4);
          int num=uMapper.updateBatch(usersList);
          sqlSession.commit();
      }
      ```

## 2.指定参数位置

可以不使用对象的属性名进行参数值绑定，使用下标值。 mybatis-3.3 版本和之前的版本使用#{0},#{1}方式， 从 mybatis3.4 开始使用#{arg0}方式。	

```xml
<!--
查询指定如期范围内的用户
List<Users> getByBirthday(Date begin,Date end);
-->
<select id="getByBirthday" resultType="users">
    select <include refid="allColumns"></include>
    from users
    where birthday between #{arg0} and #{arg1}
</select>
```

```java
    @Test
    public  void testGetBirthday() throws Exception{
        Date begin=sf.parse("1999-01-01");
        Date end=sf.parse("1999-12-31");
        List<Users> usersList=uMapper.getByBirthday(begin,end);
        usersList.forEach(users-> System.out.println(users));
    }
```



## 3.入参是map

入参是map,是因为当传递的数据有多个,不适合使用指定下标或指定名称的方式来进行传参,又加上参数不一定与对象的成员变量一致,考虑使用map集合来进行传递.map使用的是键值对的方式.当在sql语句中使用的时候#{键名},${键名},用的是键的名称.

```xml
<!--
入参是map
List<Users> getByMap(Map map);
#{birthdayBegin}  #{birthdayEnd}就是用的Map里面的Key
-->
<select id="getByMap" resultType="users">
    select <include refid="allColumns"></include>
    from users
    where birthday between #{birthdayBegin} and #{birthdayEnd}
</select>
```

```java
    @Test
    public void testGetByMap() throws ParseException {
        Date begin=sf.parse("1999-01-01");
        Date end=sf.parse("1999-12-31");
        Map map=new HashMap<>();
        map.put("birthdayBegin",begin);
        map.put("birthdayEnd",end);
        List<Users> usersList=uMapper.getByMap(map);
        usersList.forEach(users -> System.out.println(users));
    }
```



## 4.返回值是map

返回值是map的适用场景,如果的数据不能使用对象来进行封装,可能查询的数据来自多张表中的某些列,这种情况下,使用map,但是map的返回方式破坏了对象的封装,返回来的数据是一个一个单独的数据, 之间不相关.**map使用表中的列名或别名做为键名进行返回数据.**

- 返回一行的

  - ```xml
    <!--
    返回值是Map(一行)
    Map getReturnMap(Integer id);
    -->
    <select id="getReturnMap" parameterType="int" resultType="map">
         select username,address
       	 from users
         where id=#{id}
    </select>
    ```

  - ```java
        @Test
        public void testReturnMap(){
            Map map=uMapper.getReturnMap(3);
            System.out.println(map);
            //这里的get 中的key就是 列名 或者是别名
            System.out.println(map.get("username"));
            System.out.println(map.get("address"));
        }
    ```

- 返回多行的

  - ```xml
    <!--
    返回多行的Map
    List<Map> getMulMap();
    -->
    <select id="getMulMap" resultType="map">
        select username,address
        from users
    </select>
    ```

  - ```java
        @Test
        public void testMulMap(){
            List<Map> mapList=uMapper.getMulMap();
            mapList.forEach(map -> System.out.println(map));
        }
    ```

    

## 5.列名和实体类的成员变量名不一致

![](图\MyBatis\名称不一致.png)

```xml
    <!--
        使用resultMap手工完成映射
        property是实体类中的名称
        column是数据库当中的名称 进行关联
	resultMap和中的id 和select 中resultMap一致
    -->
    <resultMap id="bookmap" type="book">
        <!--主键绑定-->
        <id property="id" column="bookid"></id>
        <!--非主键绑定-->
        <result property="name" column="bookname"></result>
    </resultMap>
    <select id="getAll" resultMap="bookmap">
        select bookid,bookname
        from book
    </select>
```

```java
     @Test
    public void testGetAll(){
         List<Book> books=bookMapper.getAll();
         books.forEach(book -> System.out.println(book));
     }

```



# 第五章表的关联关系

## 表的结构

![](图\MyBatis\表的结构.png)

## 1.表的关联关系

1.  一对多关联:一个老师可以教多个学生,多个学生只有一个老师来教,站在老师方,就是一对多关联.
2.  多对一关联:一个老师可以教多个学生,多个学生只有一个老师来教,站在学生方,就是多对一关联.
3.  一对一关联:一个老师辅导一个学生,一个学生只请教一个老师.学生和老师是一对一.
4.  多对多关联:园区划线的车位和园区的每一辆车.任意一个车位可以停任意一辆车.任意一车辆车可以停在任意一个车位上.

## 2.一对多关联

```xml
<!--
根据客户的id查询客户所有信息 并同时查询该客户名下的所有订单
Customer getById(Integer id);
Customer实体类：
    customer 表中的三个列
    private Integer id;
    private String name;
    private Integer age;x`
    该客户名下的所有订单的集合 一方持有多方的集合
    private List<Orders> ordersList;
-->

<resultMap id="customermap" type="customer"> ===> customer就是Custormer是实体类的别名
    <!--主键绑定 注意这里的column是列名或者是别名-->
    <id property="id" column="cid"></id> ==>注意了这里要使用别名 根据在下面的sql语句决定是否使用别名
    <!--非主键绑定-->
    <result property="name" column="name"></result>
    <result property="age" column="age"></result>
    <!--
	ordersList绑定
     Orders实体类
        private Integer id;
        private String orderNumber;
        private Double orderPrice;
	 ofType这个是集合中泛型(Orders) 已经起了别名 
	 property 这个是集合的名称 ordersList
	-->
    <collection property="ordersList" ofType="orders">
        <!--Orders的主键绑定-->
        <id property="id" column="oid"></id>==>注意这里使用别名
        <!--非主键绑定-->
        <result property="orderNumber" column="orderNumber"></result>
        <result property="orderPrice" column="orderPrice"></result>
    </collection>
</resultMap>


<select id="getById" parameterType="int" resultMap="customermap">=>当用resultMap手工映射时用resultMap
     select c.id cid,name ,age,o.id oid,orderNumber,orderPrice,customer_id
   	 from customer c left  join orders o on c.id=o.customer_id  ===>这里要用左外连接,要显示客户的所有信息
     where c.id =#{id}
</select>
```

测试：

```java
     @Test
    public void testGetCustomerById(){
         //注意了 这里要用外连接 需要将主表也就是用户表Customer全部内容查询出来 即便没有订单
         Customer customer=customerMapper.getById(3);
         System.out.println(customer);
     }
```



## 3.多对一关联

```xml
<!--
根据主键查询订单,并同时查询下此订单的客户信息
Orders getById(Integer id);

     Orders实体类
        private Integer id;
        private String orderNumber;
        private Double orderPrice;
		关联下此订单的客户信息 多方持有一方的对象
        private Customer customer;
-->
<resultMap id="ordersmap" type="orders">
    <!--主键绑定-->
    <id property="id" column="oid"></id>
    <!--非主键绑定-->
    <result property="orderNumber" column="orderNumber"></result>
    <result property="orderPrice" column="orderPrice"></result>
    <!--
	private Integer id;
    private String name;
    private Integer age;
    private List<Orders> ordersList;这个不用管
	这里的property是成员变量  javaType这个是成员变量的类型
	-->
    <association property="customer" javaType="customer">
        <id property="id" column="cid"></id>
        <result property="name" column="name"></result>
        <result property="age" column="age"></result>
    </association>
</resultMap>

<select id="getById" parameterType="int" resultMap="ordersmap">
    select o.id oid,orderNumber,orderPrice,customer_id,c.id cid, name,age
    from orders o inner join customer c on o.customer_id=c.id
    where o.id=#{id}
</select>
```

## 4.总结

总结：无论是什么关联关系，如果某方持有另一方的集合，则使用<collection>标签完成映射，如果某方持有另一方的对象，则使用<association>标签完成映射。

# 第六章事务

多个操作同时完成,或同时失败称为事务处理.
  事务有四个特性:一致性,持久性,原子性,隔离性.

1. 下订单的业务:

   - 订单表中完成增加一条记录的操作
   - 订单明细表中完成N条记录的增加
   - 商品数据更新(减少)
   - 购物车中已支付商品删除
   - 用户积分更新(增加)

2. 在MyBatis框架中设置事务

   - ```xml
     <transactionManager type="JDBC"></transactionManager>  ===>程序员自己控制处理的提交和回滚
     ```

3. 可设置为自动提交

   - ```java
     sqlSession = factory.openSession();  ===>默认是手工提交事务,设置为false也是手工提交事务,如果设置为true,则为自动提交.
     sqlSession = factory.openSession(true);  ===>设置为自动提交,在增删改后不需要commit();
     ```

# 第七章缓存

1. MyBatis框架提供两级缓存,一级缓存和二级缓存.默认开启一级缓存.

2. 缓存就是为了提交查询效率.

3.   使用缓存后,查询的流程:
     -   查询时先到缓存里查,如果没有则查询数据库,放缓存一份,再返回客户端.下次再查询的时候直接从缓存返回,不再访问数据库.
     -   如果sqlSession去执行commit操作（执行插入、更新、删除），则清空SqlSession中的一级缓存，这样做的目的为了让缓存中存储的是最新的信息，避免脏读。
     -   一级缓存使用的是SqlSession的作用域,同一个sqlSession共享一级缓存的数据.
     -   二级缓存使用的是mapper的作用域,不同的sqlSession只要访问的同一个mapper.xml文件,则共享二级缓存作用域.
     
4. 测试：

   - ```java
         @Test
         //这个测试的功能是一级缓存  默认开启
         public void testCache(){
             //第一次取id=5的用户
             Users users1=uMapper.getById(5);
             System.out.println("第一次取出的用户"+users1);
             System.out.println("******************************");
             Users users2=uMapper.getById(5);
             System.out.println("第二次取出的用户"+users2);
             //true 表示 在内存中
             System.out.println(users1==users2);
     
         }
     ```

     

# 第八章什么是ORM

1.  ORM(Object Relational Mapping):对象关系映射
2.  MyBatis框架是ORM非常优秀的框架.
3.  java语言中以对象的方式操作数据,存到数据库中是以表的方式进行存储,对象中的成员变量与表中的列之间的数据互换称为映射.整个这套操作就是ORM.
4.  持久化的操作：将对象保存到关系型数据库中 ,将关系型数据库中的数据读取出来以对象的形式封装
5.  MyBatis是持久化层优秀的框架

