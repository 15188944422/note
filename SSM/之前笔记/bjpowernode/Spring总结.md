# 第一章Spring概述

## 1.Spring框架是什么？

1. 它是一个容器.它是整合其它框架的框架
2. 它的核心就是 **控制反转(IOC)** 和**面向切面编程(AOP)**
3. 它由20多个模块构成.它在很多领域都提供优秀的解决方案.
4. Spring 的主要作用就是为代码“解耦”，降低代码间的耦合度。就是让对象和对象（模块和模块）之间关系不是使用代码关联，而是通过配置来说明。即在 Spring 中说明对象（模块）的关系。
5. Spring 根据代码的功能特点，使用 Ioc 降低业务对象之间耦合度。IoC 使得主业务在相互调用过程中，不用再自己维护关系了，即不用再自己创建要使用的对象了。而是由 Spring 容器统一管理，自动“注入”,注入即赋值。 而 AOP 使得系统级服务得到了最大复用，且不用再由程序员手工将系统级服务“混杂”到主业务逻辑中了，而是由 Spring 容器统一完成“织入”。

## 2.Spring官网

https://spring.io/

 Spring官网有Spring家族技术的介绍,有相应框架的jar 包和文档,还有源码文件,必要的时候可以参考。

## 3.Spring特点

Spring 是一个框架，是一个半成品的软件。有 20 个模块组成。它是一个容器管理对象， 容器是装东西的，Spring 容器不装文本，数字。装的是对象。Spring 是存储对象的容器。

1. 轻量级
   - Spring 框架使用的 jar 都比较小，一般在 1M 以下或者几百 kb。Spring 核心功能的所需的 jar 总共在 3M 左右。Spring 框架运行占用的资源少，运行效率高。不依赖其他 jar。
2. 面向接口编程
   - 使用接口,就是面向灵活,项目的可扩展性,可维护性都极高.接口不关心实现类的类型.使用时接口指向实现类,切换实现类即可切换整个功能.
3. AOP:面向切面编程
   - 就是将公共的,通用的,重复的代码单独开发,在需要的时候反织回去.底层的原理是动态代理.
4. 整合其它框架
   - 它整合后使其它框架更易用.

## 4.spring体系结构

![](图\Spring\spring体系结构.png)

Spring 由 20 多个模块组成，它们可以分为数据访问/集成（Data Access/Integration）、

Web、面向切面编程（AOP, Aspects）、提供JVM 的代理（Instrumentation）、消息发送（Messaging）、核心容器（Core Container）和测试（Test）。

# 第二章IOC控制反转

## 1.IOC概念

1. 控制反转IoC(Inversion of Control)是一个概念，是一种思想。由Spring容器进行对象的创建和依赖注入.程序员在使用时直接取出使用.

2. 正转:由程序员进行对象的创建和依赖注入称为正转.程序员说了算.

   - ```java
     Student stu = new Student();   ===>程序员创建对象
     stu.setName("张三");           ===>程序员进行赋值
     stu.setAge(22);
     ```

3. 反转:由Spring容器创建对象和依赖注入称为反转,将控制权从程序员手中夺走,由给Spring容器,称为反转. 容器说了算.

   - ```xml
     <bean id="stu" class="com.bjpowernode.pojo.Student">     ===>Spring容器负责对象的创建
       <property name="name" value="张三">                    ===>Spring容器依赖注入值
       <property name="age" value="22"> 
     </bean>
     ```

4. 切记:Spring容器在启动时,就创建所有的对象stu....

## 2.基于XML的IOC

### 1.创建一个空的项目之后创建一个Maven的模块

![](图\Spring\Spring创建模块.png)

### 2.修改目录和修改Pom.xml

1. 修改目录

   - ![](图\Spring\补全目录.png)

2. 修改pom.xml

   - 修改properties

     - ```xml
       之前是1.7 改成了 1.8
       <properties>
           <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
           <maven.compiler.source>1.8</maven.compiler.source>
           <maven.compiler.target>1.8</maven.compiler.target>
         </properties>
       ```

   - 在dependencies中添加spring的依赖

     - ```xml
       </dependency>
           <!--添加spring依赖-->
           <dependency>
             <groupId>org.springframework</groupId>
             <artifactId>spring-context</artifactId>
             <version>5.2.5.RELEASE</version>
       </dependency>
       ```

   - 修改 build 

     - ```xml
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

### 3.新建一个pojo的包新建一个实体类

```java
package com.bjpowernode.pojo;

public class Student {
    private String name;
    private int age;
    
    //注意了这里要提供无参的构造方法
}
```

### 4.创建一个spring的配置文件

在 src/main/resources/目录现创建一个xml 文件，文件名可以随意，但 Spring 建议的名称为 applicationContext.xml。

```xml
<!--
id:就是创建对象的名称
class:就是创建的对象的类型,底层通过反射构建对象
这个就等用于创建了 Student stu=new Student(); 
这个调用了无参数的构造方法,所有我们必须提供一个无参数的构造方法
-->
<bean id="stu" class="com.bjpowernode.pojo.Student">
</bean>
```

### 5.容器接口和实现类

1. ApplicationContext接口(容器)
   - ApplicationContext用于加载Spring的配置文件,在程序中充当"容器"的角色
   - 实现类有两个ClassPathXmlApplicationConext(常用的) 和FileSystemXmlApplicationContext
2. 配置文件在类路径下(src路径下)
   - 若 Spring 配置文件存放在项目的类路径下，则使用 ClassPathXmlApplicationContext 实现类进行加载。
3. ApplicationContext容器中对象的装配时机
   - ApplicationContext 容器，会在容器对象初始化时，将其中的所有对象一次性全部装配好
   - 以后代码中若要使用到这些对象，只需从内存中直接获取即可。
   - 执行效率较高。但占用内存。
   - Spring初始化对象时要使用无参的构造方法，切记保证类中有无参构造方法。

### 6.测试

```java
package com.bjpowernode.test;

public class MyTest01{
    @Test
    public void testStudentSpring(){
        //由Spring容器进行创建对象
        //如果想从spring容器中取出对象,要先创建容器对象,并启动才可以取对象
        // s01/applicationContext.xml 这个是在resources 下的路径
        Application application=new ClassPathXmlApplicationContext("s01/applicationContext.xml");
        // 转型是因为取出来的为Object类型的 所有要去转型为Student类型的
        Student student=(Student) application.getBean("stu"); ===>stu 就是配置文件中bean中的id名
        System.out.println(student);        
    }
}
```

## 3.注入的分类

bean 实例在调用无参构造器创建对象后，就要对 bean 对象的属性进行初始化。初始化是由容器自动完成的，称为注入。根据注入方式的不同，常用的有两类：set 注入、构造注入。

### 1.set注入(掌握)

set 注入也叫设值注入是指，通过 setter 方法传入被调用者的实例。这种注入方式简单、直观，因而在 Spring 的依赖注入中大量使用。

必须要注意:使用setter注入必须提供无参的构造方法,必须提供setXXX()方法.

#### 简单类型---简单类型注入值使用value属性

实体类：

- ```java
  //实体类必须必须必须有无参数的构造方法和setter方法
  public class Student {
      private String name;
      private int age;
      public Student(){
          System.out.println("学生的无参数构造方法执行了");
      }
      //setter方法.....
  }
  ```

applicationContext.xml

- ```xml
  <!--
  这里就等同于 Student stu=new Student("张三",18);
  -->
  <bean id="stu" class="com.bjpowernode.pojo.Student">
      <property name="name" value="张三"></property>
      <property name="age" value="18"></property>
  </bean>
  ```

测试：

- ```java
  public void test(){
      ApplicationContext ac=new ClassPathXmlApplicationContext("s02/applicationContext.xml");
      Student student=ac.getBean("stu");
      System.out.println(stu);
      
      //执行程序的结果就是
      /*
      学生的无参数构造方法执行了 ===>无参构造方法
      Student{name='张三'，age='18'} ===>toString
      */
  }
  ```



#### 引用类型 ---引用类型注入值使用ref属性

实体类:

- ```java
  public class Student {
      private String name;
      private int age;
  
      //引用类型的成员变量,学生所在学校
      private School school;
      
      //提供 无参数的构造方法 和 setter方法
  }
  
  public class School {
      private String name;
      private String address;
      
      //提供 无参数的构造方法 和 setter方法
  }
  ```

applicationContext.xml

- ```xml
  <!--创建学校对象-->
  <bean id="school" class="com.bjpowernode.pojo2.School">
      <property name="name" value="清华大学"></property>
      <property name="address" value="海淀区"></property>
  </bean>
  
  <!--
  创建学生对象
  <property name="school" ref="school"></property> 这里的school 就是上方创建的school
  -->
  <bean id="student" class="com.bjpowernode.pojo2.Student">
      <property name="name" value="张三"></property>===>简单类型注入
      <property name="age" value="18"></property>
      <property name="school" ref="school"></property>  ===>引用类型注入
  </bean>
  ```

测试：

- ```java
  @Test
  public void testStudent(){
      //创建容器对象
      ApplicationContext ac=new ClassPathXmlApplicationContext("s02/applicationContext.xml");
      //取出学校对象
      Student student=(Student) ac.getBean("student");
      System.out.println(student);
  }
  
  /*
  运行结果：
  School的无参数构造方法被调用 ===>会先创建一个School
  学生的无参数构造方法执行了
  Student{name='李四', age=22, school=School{name='清华大学', address='海淀区'}}
  */
  ```

### 2.构造方法注入

构造注入是指，在构造调用者实例的同时，完成被调用者的实例化。即，使用构造器设置依赖关系。在实体类中必须提供相应参数的构造方法。

```
<constructor-arg />标签中用于指定参数的属性有：
	name：指定参数名称。
	index：指明该参数对应着构造器的第几个参数，从 0 开始。
		不过，该属性不要也行， 但要注意，若参数类型相同，或之间有包含关系，
		则需要保证赋值顺序要与构造器中的参数顺序一致。
```

#### 实体类:

- ```java
  public class Student {
      private String name;
      private int age;
  
      //引用类型的成员变量
      private School school;
  
      public Student(String name, int age, School school) {
          this.name = name;
          this.age = age;
          this.school = school;
      }
  }
  
  public class School {
      private String name;
      private String address;
  
      //使用带参的构造方法注入值
      public School(String name, String address) {
          this.name = name;
          this.address = address;
      }
  
  
  ```

#### applicationContext.xml

- ```xml
  <!--创建学校对象,使用构造方法的参数名称并注入值-->
  <bean id="school" class="com.bjpowernode.pojo3.School">
      <constructor-arg name="name" value="清华大学"></constructor-arg>
      <constructor-arg name="address" value="海淀区"></constructor-arg>
  </bean>
  
  <!--创建学生对象,使用构造方法的参数下表注入值-->
  <bean id="stu" class="com.bjpowernode.pojo3.Student">
      <constructor-arg index="0" value="张三"></constructor-arg>
      <constructor-arg index="1" value="22"></constructor-arg>
      <constructor-arg index="2" ref="school"></constructor-arg>
  </bean>
  
  <!--创建学生对象,使用默认的构造方法的参数顺序注入值-->
  <bean id="stuSequence" class="com.bjpowernode.pojo3.Student">
      <constructor-arg value="赵六"></constructor-arg>
      <constructor-arg value="22"></constructor-arg>
      <constructor-arg ref="school"></constructor-arg>
  </bean>
  
  ```

#### 测试：

- ```java
  public class MyTest3 {
      ApplicationContext ac=null;
      @Before
      public void before(){
          ac=new ClassPathXmlApplicationContext("s03/applicationContext.xml");
      }
      @Test
      public void testSchool(){
          School school= (School) ac.getBean("school");
          System.out.println(school);
      }
      @Test
      public void testStudent(){
          Student student= (Student) ac.getBean("stu");
          System.out.println(student);
      }
      @Test
      public void testStudentSequence(){
          Student student= (Student) ac.getBean("stuSequence");
          System.out.println(student);
      }
  }
  ```

### 3.引用类型自动注入

对于引用类型属性的注入，也可不在配置文件中显示的注入。可以通过为<bean>标签设置 autowire 属性值，为引用类型属性进行隐式自动注入（默认是不自动注入引用类型属性）。根据自动注入判断标准的不同，可以分为两种：

#### byName：根据名称自动注入

当配置文件中被调用者 bean 的 id 值与代码中调用者 bean 类的属性名相同时，可使用byName 方式

- ```
  实体类中: private School school; ====>属性名称为 school 调用者
  在Xml文件中 <bean id="school" class="..."></bean> ===>id名称与实体类中的属性名称一样 被调用者
  ```

applicationContext.xml:

- ```xml
      <!--
      创建学校的对象
      -->
      <bean id="school" class="com.bjpowernode.pojo2.School"> ===>被调用者
          <property name="name" value="清华大学"></property>
          <property name="address" value="海淀区"></property>
      </bean>
  
      <!--创建学生对象
          <property name="school" ref="school"></property> 这个可以用上面创建的school对象
          autowire 自动连接 byType按类型 byName按名称
      -->
      <bean id="student" class="com.bjpowernode.pojo2.Student" autowire="byName"> ==>调用者
          <property name="name" value="李四"></property>
          <property name="age" value="22"></property>
          <!--<property name="school" ref="school"></property>-->
      </bean>
  ```



#### byType： 根据类型自动注入

配置文件中被调用者 bean 的 class 属性指定的类， 要与代码中调用者 bean 类的某引用类型属性类型同源。即要么相同，要么有 is-a 关系（子类，或是实现类）。但这样的同源的被调用 bean 只能有一个。多于一个，容器就不知该匹配哪一个了。

- ```
  实体类：private School school; ===>属性类型为School 调用者
  xml文件中<bean id="school" class="com.bjpowernode.pojo2.School"> ===>class类型为School 被调用者
  ```

applicationContext.xml:

- ```xml
      <!--
      创建学校的对象
      -->
      <bean id="school" class="com.bjpowernode.pojo2.School">===>被调用者
          <property name="name" value="清华大学"></property>
          <property name="address" value="海淀区"></property>
      </bean>
  
      <!--创建学生对象
          <property name="school" ref="school"></property> 这个可以用上面创建的school对象
          autowire 自动连接 byType按类型 byName按名称
      -->
      <bean id="student" class="com.bjpowernode.pojo2.Student" autowire="byType">==>调用者
          <property name="name" value="李四"></property>
          <property name="age" value="22"></property>
          <!--<property name="school" ref="school"></property>-->
      </bean>
  ```

## 4.项目案例(这个是基于三层架构的)

 使用三层架构进行用户的插入操作.
 界面层,业务逻辑层,数据访问层(模拟).

### 1.没有用到spring框架的

#### 实体类

- com.bjpowernode.pojo  Users

  - ```java
    public class Users{
        private int uid;
        private String uname;
        private int uage;
    }
    ```

#### 数据访问层

- com.bjpowernode.dao UsersMapper.java(接口)

  - UsersMapper.java(实现类)

    - ```java
      //UsersMapperImpl.java(实现类)
      public class UsersMapperImpl implements UsersMapper{
          public int insert(Users u) {
              System.out.println(u.getUname()+"用户增加成功！");
              return 1;
          }
      }
      ```

#### 业务逻辑层

- com.bjpowernode.service   UsersService.java(接口)

  - UsersServiceImpl.java(实现类 )

    - ```java
      package com.bjpowernode.service.impl;
      
      public class UsersServiceImpl implements UsersService {
          //切记切记:在所有的业务逻辑层中 都必定有数据访问层的对象
          private UsersMapper usersMapper=new UsersMapperImpl();
          public int insert(Users users) {
              return usersMapper.insert(users);
          }
      }
      ```

#### 界面层

- com.bjpowernode.controller  UsersController.java

  - ```java
    public class UsersController {
        //如何去访问业务逻辑层(UsersServiceImpl) 就是创建对象
        //切记切记:所有的界面层,都会有业务逻辑层的对象
        public UsersService usersService=new UsersServiceImpl();
    
        //界面层的功能实现,对外提供访问的功能
        public int insert(Users users){
            return usersService.insert(users);
        }
    }
    ```

#### 测试：

```java
    @Test
    public void testInsertUsers(){
        //创建界面层的对象
        UsersController usersController=new UsersController();
        int num= usersController.insert(new Users(100,"张三",22));
        System.out.println(num);
    }
```



### 2.使用Spring框架的(xml) 

#### 三层的改动

业务逻辑层：com.bjpowernode.service   UsersService.java(接口)

- ```java
  package com.bjpowernode.service.impl;
  public class UsersServiceImpl implements UsersService {
      //切记切记:在所有的业务逻辑层中 都必定有数据访问层的对象
      private UsersMapper usersMapper;//=new UsersMapperImpl();
      //交给Spring去依赖注入值,必须提供setXxx()
      public void setUsersMapper(UsersMapper usersMapper) {
          this.usersMapper = usersMapper;
      }
      @Override
      public int insert(Users users) {
          return usersMapper.insert(users);
      }
  }
  ```

界面层：

- ```java
  public class UsersController {
      //如何去访问业务逻辑层(UsersServiceImpl) 就是创建对象
      //切记切记:所有的界面层,都会有业务逻辑层的对象
      public UsersService usersService;//=new UsersServiceImpl();
  
      //交给Spring去注入值 必须提供settXxx()
      public void setUsersService(UsersService usersService) {
          this.usersService = usersService;
      }
      //界面层的功能实现,对外提供访问的功能
      public int insert(Users users){
          return usersService.insert(users);
      }
  }
  
  ```

  

#### 使用一个大的配置文件

```xml
    <!--创建数据访问层的对象 dao包下的 有成员变量就property 没有就不用了-->
    <bean id="uMapper" class="com.bjpowernode.dao.UsersMapperImpl">
    </bean>

    <!--创建业务逻辑层的对象 service包下的 实现类中有一个成员变量 是private UsersMapper usersMapper;
    用ref
    -->
    <bean id="uService" class="com.bjpowernode.service.impl.UsersServiceImpl">
        <property name="usersMapper" ref="uMapper"></property>
    </bean>

    <!--创建界面层对象-->
    <bean id="uController" class="com.bjpowernode.controller.UsersController">
        <property name="usersService" ref="uService"></property>
    </bean>
```

#### 指定多个spring配置文件

applicationContext_mapper.xml(数据访问层):

- ```xml
      <!--创建数据访问层的对象 dao包下的 有成员变量就property 没有就不用了-->
      <bean id="uMapper" class="com.bjpowernode.dao.UsersMapperImpl">
      </bean>
  ```

applicationContext_service.xml(业务逻辑层对象)：

- ```xml
      <!--创建业务逻辑层的对象 service包下的 实现类中有一个成员变量 是private UsersMapper usersMapper;
      用ref
      -->
      <bean id="uService" class="com.bjpowernode.service.impl.UsersServiceImpl">
          <property name="usersMapper" ref="uMapper"></property>
      </bean>
  ```

applicationContext_controller.xml(界面层):

- ```xml
      <!--创建界面层对象-->
      <bean id="uController" class="com.bjpowernode.controller.UsersController">
          <property name="usersService" ref="uService"></property>
      </bean>
  ```

整合: total.xml

- ```xml
      <!--单个导入 这样配置以后他们就相当一个文件 -->
      <!--在下面的三个配置文件中 ref="uService"  ref="uMapper" 还是会报错 不影响-->
  <!--    <import resource="applicationContext_mapper.xml"></import>-->
  <!--    <import resource="applicationContext_service.xml"></import>-->
  <!--    <import resource="applicationContext_controller.xml"></import>-->
  
      <!--批量导入-->
      <import resource="applicationContext_*.xml"></import>
  ```

#### 测试：

- ```java
      @Test
      public void testInsertUsers(){
          //创建容器并启动
          //这个是大的配置文件
          //ApplicationContext ac=new ClassPathXmlApplicationContext("applicationContext.xml");
          //这个是分开的
          ApplicationContext ac=new ClassPathXmlApplicationContext("total.xml");
          //取出对象
          UsersController usersController= (UsersController) ac.getBean("uController");
  
          //测试功能
          int num=usersController.insert(new Users(200,"lll",123));
          System.out.println(num);
      }
  ```

## 5.应用指定多个 Spring 配置文件

### 1.拆分

当项目越来越大,需要多人合作开发,一个配置就存在很大隐患.

1. 拆分配置文件的策略

   - 按层拆

     - ```xml
       applicationContext_controller.xml        
         <bean id="uController" class="com.bjpowernode.controller.UsersController">
         <bean id="bController" class="com.bjpowernode.controller.BookController">
       applicationContext_service.xml        
          <bean id="uService" class="com.bjpowernode.controller.UsersService">
          <bean id="bService" class="com.bjpowernode.controller.BookService">
       applicationContext_mapper.xml        
          <bean id="uMapper" class="com.bjpowernode.controller.UsersMapper">
          <bean id="bMapper" class="com.bjpowernode.controller.BookMapper">
       ```

   - 按功能拆

     - ```xml
          applicationContext_users.xml        
             <bean id="uController" class="com.bjpowernode.controller.UsersController">
             <bean id="uService" class="com.bjpowernode.controller.UsersService">
             <bean id="uMapper" class="com.bjpowernode.controller.UsersMapper">
           applicationContext_book.xml      
             <bean id="bController" class="com.bjpowernode.controller.BookController">
             <bean id="bService" class="com.bjpowernode.controller.BookService">
             <bean id="bMapper" class="com.bjpowernode.controller.BookMapper">
       ```

### 2.整合

1. 单个文件导入 

   - ```xml
         <import resource="applicatoinContext_mapper.xml"></import>
         <import resource="applicatoinContext_service.xml"></import>
         <import resource="applicatoinContext_controller.xml"></import>
     ```

2. 批量导入

   - ```xml
     <import resource="applicatoinContext_*.xml"></import>
     ```

## 6.基于注解的IOC

### 1.创建对象的注解(放在类上的)

1. @Component:可以创建任意对象.创建的对象的默认名称是类名的驼峰命名法.也可以指定对象的名称@Component("指定名称").
2. @Controller:专门用来创建控制器的对象(Servlet),这种对象可以接收用户的请求,可以返回处理结果给客户端.
3. @Service:专门用来创建业务逻辑层的对象,负责向下访问数据访问层,处理完毕后的结果返回给界面层.
4. @Repository:专门用来创建数据访问层的对象,负责数据库中的增删改查所有操作.

### 2.给对象赋值的注解(放在属性上面的)

#### 简单类型(8种基本类型+String)的注入

- @Value:用来给简单类型注入值
- @Value("张三");

#### 引用类型的注入

- @Autowired:使用类型注入值,从整个Bean工厂中搜索同源类型的对象进行注入.
  - ![](图\Spring\Spring注解byType.png)
  - 同源类型也可注入.什么是同源类型:
    - a.被注入的类型(Student中的school)与注入的类型是完全相同的类型 
    - b.被注入的类型(Student中的school父)与注入的类型(子)是父子类
    - c.被注入的类型(Student中的school接口)与注入的类型(实现类)是接口和实现类的类型
  - 注意:在有父子类的情况下,使用按类型注入,就意味着有多个可注入的对象.此时按照名称进行二次筛选,选中与被注入对象相同名称的对象进行注入.
  - @Autowired 还有一个属性 required，默认值为 true，表示当匹配失败后，会终止程序运行。若将其值设置为 false，则匹配失败，将被忽略，未匹配的属性值为 null。
  - 注意:如果可注入的类型多于一个,则按名称进行二次匹配.如果有匹配到则注入,如果没有匹配到,则报错。
- @Autowired
  @Qualifier("名称"):使用名称注入值,从整个Bean工厂中搜索相同名称的对象进行注入.\
  - ![](图\Spring\Spring注解ByName.png)
  - 如果可注入的类型多于一个,则按名称进行匹配.如果有匹配到则注入,如果没有匹配到,则报错。
- 注意:如果有父子类的情况下,直接按名称进行注入值.

### 3.添加包扫描

基于注解的IOC,必须要在Spring的核心配置文件中添加包扫描. 就是applicationContext.xml 是用来包扫描的

添加包扫描 如果扫描到类上有@Component 这个注解 就会立马创建对象

1. 单个包扫描(推荐使用)

   - ```xml
     <context:component-scan base-package="com.bjpowernode.controller"></context:component-scan><context:component-scan base-package="com.bjpowernode.service.impl"></context:component-scan><context:component-scan base-package="com.bjpowernode.dao"></context:component-scan>
     ```

2. 多个包扫描,多个包之间以逗号或空格或分号分隔

   - ```xml
     <context:component-scan base-package="com.bjpowernode.controller com.bjpowernode.service ,com.bjpowernode.dao"></context:component-scan>
     ```

3. 扫描根包(不推荐)

   - ```xml
         <context:component-scan base-package="com.bjpowernode"></context:component-scan>
         会降低容器启动的速度,导致多做无用功.
     ```

### 4.测试

#### 简单类型注入

applicationContext.xml

- ```xml
  <!-- 基于注解的IOC,必须要在Spring的核心配置文件中添加包扫描.-->
  <!--添加包扫描 如果扫描到类上有@Component 这个注解 就会立马创建对象-->
  <context:component-scan base-package="com.bjpowernode.s01"></context:component-scan>
  ```

实体类：Student

- ```java
  /*
  交给Spring去创建对象,就是在容器启动时创建
  */
  @Component("stu") ===>如果没有指定名称 会默认为驼峰命名法 就是student
  public class Student {
      @Value("张三") ===>简单类型注入
      private String name;
      @Value("22") ===>简单类型注入
      private int age;
  
      public Student() {
          System.out.println("学生对象的无参数构造方法执行了");
      }
  
  ```

测试类：

- ```java
  public class MyTest01 {
      @Test
      public void testStudent(){
          //创建容器对象并启动
          ApplicationContext ac=new ClassPathXmlApplicationContext("s01/applicationContext.xml");
          //取出对象
          Student student= (Student) ac.getBean("stu"); ===>这里是@Component("指定的名称")
          System.out.println(student);
      }
  }
  
  /*
  测试结果：
  学生对象的无参数构造方法执行了
  Student{name='张三', age=22}
  */
  ```

#### 引用类型注入

applicationContext.xml

- ```xml
      <!-- 基于注解的IOC,必须要在Spring的核心配置文件中添加包扫描.-->
      <!--添加包扫描 如果扫描到类上有@Component 这个注解 就会立马创建对象-->
      <context:component-scan base-package="com.bjpowernode.s02"></context:component-scan>
  ```

实体类：

- School:

  - ```java
    /*
    交给Spring去创建对象,就是在容器启动时创建
    */
    @Component ===>这里没有指定名称为 shcool
    public class School {
        @Value("唐山学院") ===>简单类型
        private String name;
        @Value("唐山市") ===>简单类型
        private String address;
    
        public School() {
            System.out.println("School的无参数构造方法执行了");
        }
    
    ```

- Student

  - ```java
    @Component
    public class Student {
        @Value("宋sir")
        private String name;
        @Value("23")
        private int age;
    
        //引用类型 按类型注入
        //@Autowired 会在Spring 的bean工程找School 有就注入 没有就报异常
        //private School school;
    
        //按名称注入 注意这两个名称是一套
        @Autowired
        @Qualifier("school")// 在bean工程里面找 @Component("school") 
        private School school;
    
    ```

测试:

- ```java
      @Test
      public void testStudent(){
          //创建容器对象并启动
          ApplicationContext ac=new ClassPathXmlApplicationContext("s02/applicationContext.xml");
          //取出student对象
          Student student= (Student) ac.getBean("student");
          System.out.println(student);
      }
  
  /*
  School的无参数构造方法执行了
  Student得无参数构造方法执行了
  Student{name='宋sir', age=23, school=School{name='唐山学院', address='唐山市'}}
  */
  ```

#### 带父子类得引用数据类型

applicationContext.xml

- ```xml
  <!-- 基于注解的IOC,必须要在Spring的核心配置文件中添加包扫描.-->
      <!--添加包扫描 如果扫描到类上有@Component 这个注解 就会立马创建对象-->
      <context:component-scan base-package="com.bjpowernode.s02"></context:component-scan>
  ```

实体类：

- School:

  - ```java
    @Component("schoolFu") //交给Spring去创建对象,就是在容器启动时创建
    public class School {//此时School的名称为 schoolFu
        @Value("唐山学院")
        private String name;
        @Value("唐山市")
        private String address;
    
        public School() {
            System.out.println("School的无参数构造方法执行了");
        }
    ```

- School子类 SubSchool

  - ```java
    @Component("schoolZi") ==>这里得名称为schoolZi
    public class SubSchool extends School {
        @Value("清华附小")
        private String name;
        @Value("海淀小区")
        private String address;
    
        public SubSchool() {
            //创建子类对象会固定的调用父类的无参数构造方法
            System.out.println("这是SubSchool子类的构造方法 ..");
        }
    
    ```

- Student

  - ```java
    @Component ===>这里默认为student
    public class Student {
        @Value("宋sir")
        private String name;
        @Value("23")
        private int age;
    
        //引用类型 按类型注入
        //@Autowired 这个会按照 默认的名称注入 选中与School 相同名称的注入
        //private School school;
    
        //  @Autowired
        // @Qualifier 如果是这样 就会选中固定名称的注入
    
        @Autowired
        @Qualifier("schoolZi")
        private School school;
    
    ```

测试:

- ```java
      @Test
      public void testStudent(){
          ApplicationContext ac=new ClassPathXmlApplicationContext("s03/applicationContext.xml");
          Student student= (Student) ac.getBean("student");
          System.out.println(student);
      }
  /*
  测试结果：
  School的无参数构造方法执行了
  School的无参数构造方法执行了
  这是SubSchool子类的构造方法 ..
  Student{name='宋sir', age=23, school=SubSchool{name='清华附小', address='海淀小区'}}
  经过测试,无论是创建 School或者SunSchool 都会创建这两者得对象
  创建子类时注意 会先调用父类得无参数构造方法
  */
  ```

## 7.基于注解得方式修改三层架构

实体类没有变动

### 实体类：

```java
public class Users {
    private int uid;
    private String uname;
    private int uage;

    public Users() {
    }

    public Users(int uid, String uname, int uage) {
        this.uid = uid;
        this.uname = uname;
        this.uage = uage;
    }

```



### 1.数据访问层

package com.bjpowernode.dao UsersMapper(接口)

- UsersMapperImpl(实现类)

  - ```java
    /**
     * 数据访问层的实现类(采购员) @Repository 表示数据访问层的注解
     */
    @Repository //就是交给Spring框架去创建数据访问层的对象
    public class UsersMapperImpl implements UsersMapper{
        @Override
        public int insert(Users u) {
            System.out.println(u.getUname()+"用户增加成功！");
            return 1;
        }
    }
    
    ```

- applicationContext_mapper.xml：添加包扫描

  - ```xml
    <!--只要是基于注解的的开发,必须添加包扫描-->
    <context:component-scan base-package="com.bjpowernode.dao"></context:component-scan>
    ```

### 2.业务逻辑层：

package com.bjpowernode.service UsersService(接口)

- UsersServiceImpl(实现类)：

  - ```java
    /**
     * 业务逻辑层的实现类(厨师) @Service 表示业务逻辑层的注解
     */
    @Service //交给Spring创建业务逻辑层的对象
    public class UsersServiceImpl implements UsersService {
    
        //切记切记:在所有的业务逻辑层中 都必定有数据访问层的对象
        @Autowired ===>根据类名去扫描 搜素UsersMapper(类/接口)
        private UsersMapper usersMapper=new UsersMapperImpl();
    
        @Override
        public int insert(Users users) {
            //添加更复杂的业务,但是我们没有更复杂的业务
            return usersMapper.insert(users);
        }
    }
    ```

- applicationContext_service.xml:业务逻辑层得包扫描:

  - ```xml
    <!--只要是基于注解的的开发,必须添加包扫描-->
    <context:component-scan base-package="com.bjpowernode.service"></context:component-scan>
    ```

### 3.界面层:

package com.bjpowernode.controller UsersController(类):

- ```java
  /**
   * 界面层 最上面的 (服务员)
   */
  @Controller //交给Spring去创建对象
  public class UsersController {
      //如何去访问业务逻辑层(UsersServiceImpl) 就是创建对象
      //切记切记:所有的界面层,都会有业务逻辑层的对象
      @Autowired ===>自动扫描 UsersService类型得类/接口
      public UsersService usersService=new UsersServiceImpl();
  
      //界面层的功能实现,对外提供访问的功能
      public int insert(Users users){
          return usersService.insert(users);
      }
  }
  
  ```

applicationContext_controller.xml:界面层得包扫描：

- ```xml
      <!--只要是基于注解的的开发,必须添加包扫描-->
      <context:component-scan base-package="com.bjpowernode.controller"></context:component-scan>
  ```

### 3.整个applicationContext_*.xml

```xml
    <!--批量导入其他配置文件-->
    <import resource="applicationContext_*.xml"></import>
```

### 4.测试：

```java
public class MyTest {
    @Test
    public void testInsertUsers(){
        //创建并启动容器
        ApplicationContext ac=new ClassPathXmlApplicationContext("total.xml");
        //取出UsersControl对象
        UsersController usersController= (UsersController) ac.getBean("usersController");
        usersController.insert(new Users(100,"haha",20));
    }
}

```

# 第三章AOP面向切面编程

## 1.什么是AOP

1. AOP（Aspect Orient Programming），面向切面编程。
2. 切面:公共的,通用的,重复的功能称为切面,面向切面编程就是将切面提取出来,单独开发,在需要调用的方法中通过动态代理的方式进行织入.
3. AOP 底层，就是采用动态代理模式实现的。采用了两种代理：JDK 的动态代理，与 CGLIB的动态代理。

## 2.AOP的好处

1.减少重复；

2.专注业务；

![](图\Spring\AOP的好处.png)

## 3.模拟Aop(模拟的是图书购买的功能)

### 第一个版本：业务和切面紧耦合在一起,没有拆分.

BookServiceImpl(图书购买系统):

- ```java
  package com.bjpowernode.proxy1;
  /**
   *  图书购买业务和业务切面耦合在一起 这个是第一个版本
   */
  public class BookServiceImpl {
      public void buy(){
          //快捷键 ctrl+alt+t
          try {
              System.out.println("事务开启..........");
              System.out.println("图书购买功能实现............");
              System.out.println("事务提交");
          } catch (Exception e) {
              System.out.println("事务回滚");
          }
      }
  }
  //这里就不测试了
  ```

### 第二个版本:使用子类代理的方式拆分业务和切面.

BookServiceImpl:父类就提供一个干干净净的业务

- ```java
  /**
   *  使用子类代理的方式进行图书业务和事务切面的拆分
   */
  public class BookServiceImpl {
      //在父类中只有干干净净的业务
      public void buy(){
          System.out.println("图书购买功能实现.......");
      }
  }
  ```

SubBookServiceImpl:继承BookServiceImpl重写buy()方法

- ```java
  /**
   *  子类就是代理类,将父类的图书购买功能添加事务切面
   */
  public class SubBookServiceImpl extends BookServiceImpl {
      @Override
      public void buy() {
          try {
              //事务切面
              System.out.println("事务开启.......");
              //主业务实现,由父类取实现
              super.buy();
              //业务切面
              System.out.println("事务提交.......");
          } catch (Exception e) {
              System.out.println("事务回滚.......");
          }
      }
  }
  ```

测试：

- ```java
  public class MyTest02 {
      @Test
      public void test02(){
          BookServiceImpl service=new SubBookServiceImpl();
          service.buy();
      }
  }
  ```



### 第三个版本:使用静态代理拆分业务和切面.业务和业务接口已拆分.此时切面紧耦合在业务中.

Service:业务接口

- ```java
  public interface Service {
      //规定业务功能
      void buy();
  }
  ```

两个实现类(为了就是体现出静态代理的优点)：

- BookServiceImpl:图书购买业务

  - ```java
    public class BookServiceImpl implements Service{
    
        @Override
        public void buy() {
            System.out.println("图书购买业务实现..............");
        }
    }
    ```

    

- ProductServiceImpl:商品购买业务

  - ```java
    public class ProductServiceImpl implements Service{
        @Override
        public void buy() {
            System.out.println("商品购买业务...............");
        }
    }
    ```

代理对象:

- ```java
  /**
   * 静态代理 已经实现了目标对象的灵活切换
   * 图书购买业务,商品购买业务
   */
  public class Agent implements Service{
      //设计成员变量的类型为接口,为了灵活切换目标对象
      public Service target;
      //使用构造方法传入目标对象
      public Agent(Service target){// Service target=BookServiceImpl/ProductServiceImpl
          this.target=target;
      }
  
      @Override
      public void buy() {
          try {
              //切面功能
              System.out.println("事务开启........");//日志 权限切换
              //业务功能
              target.buy();
              //切面功能
              System.out.println("事务提交");
          } catch (Exception e) {
              System.out.println("事务回滚...........");
          }
      }
  }
  ```

测试：

```java
public class MyTest03 {
    @Test
    public void test03(){
        Service agent1=new Agent(new BookServiceImpl());
        agent1.buy();
        Service agent2=new Agent(new ProductServiceImpl());
        agent2.buy();
    }
}
```



### 第四个版本:使用静态代理拆分业务和业务接口,切面和切面接口.

![](图\Spring\第四个版本.png)

业务接口：

- ```java
  public interface Service {
      //规定业务功能
      void buy();
  }
  ```

两个实现类：

- BookServiceImpl

  - ```java
    public class BookServiceImpl implements Service {
    
        @Override
        public void buy() {
            System.out.println("图书购买业务实现..............");
        }
    }
    ```

- ProductServiceImpl

  - ```java
    public class ProductServiceImpl implements Service {
        @Override
        public void buy() {
            System.out.println("商品购买业务...............");
        }
    }
    ```

AOP接口：

- ```java
  public interface AOP {
      //JDK8 以后 default 有默认空实现 也就是需要那个实现那个
      default void before(){}
      default void after(){}
      default void exception(){}
  }
  ```

两个AOP接口的实现类

- LogAop 日志输出

  - ```java
    public class LogAop implements AOP{
        @Override
        public void before() {
            System.out.println("前置日志输出......");
        }
    }
    ```

- TranAop事务

  - ```java
    public class TranAop implements AOP{
        @Override
        public void before() {
            System.out.println("事务开启");
        }
    
        @Override
        public void after() {
            System.out.println("事务提交");
        }
    
        @Override
        public void exception() {
            System.out.println("事务回滚......");
        }
    }
    ```

代理对象：

- ```java
  public class Agent implements Service{
      //传入目标(业务)对象,切面对象
      Service target;
      AOP aop;
      //使用构造方法初始化业务对象和切面对象
      public Agent(Service target,AOP aop){
          this.target=target;// Service target=BookServiceImpl/ProductServiceImpl
          this.aop=aop;  // Aop aop=LogAop/TranAop
      }
      @Override
      public void buy() {
          try {
              //切面
              aop.before();//事务或者日志
              //业务
              target.buy(); //图书 商品
              //切面
              aop.after();//事务
          } catch (Exception e) {
              //切面
              aop.exception();
          }
      }
  }
  ```

测试：

- ```java
  public class MyTest04 {
      @Test
      public void test04(){
          Service agent=new Agent(new BookServiceImpl(),new LogAop());
          /**
           * 在传参的过程中 也就是
           * Agent实现了Service 这个接口
           * Service target=new Agent(new BookServiceImpl(),new LogAop())
           * AOP aop=new LogAop()
           * 这个也就是嵌套了一下
           */
          Service agent1=new Agent(agent,new TranAop());
          agent1.buy();
          /**
           * 前置日志输出......
           * 前置日志输出......
           * 图书购买业务实现..............
           */
      }
  }
  
  ```



### 第五个版本:使用动态代理完成第四个版本的优化.

第五个版本没有Agent这个代理类了 其他都一样 

把Agent代理类换为ProxyFactory这个动态代理类

ProxyFactory：

- ```java
  public class ProxyFactory {
      //返回动态代理的功能
      public static Object getAgent(Service target,AOP aop){
          //生成的动态代理对象
          return Proxy.newProxyInstance(
                  //类加载器
                  target.getClass().getClassLoader(),
                  //目标对象实现的所有接口
                  target.getClass().getInterfaces(),
                  //动态代理实现
                  new InvocationHandler() {
                      @Override
                      public Object invoke(
                              //生成的代理对象
                              Object proxy,
                              //正在被调用的目标方法
                              Method method,
                              //目标方法的参数
                              Object[] args) throws Throwable {
                          Object o= null;
                          try {
                              //切面
                              aop.before();//可能是事务,可能是日志
                              //业务 传进来那个实现类 就调用相应的方法
                              o = method.invoke(target,args);
                              //切面
                              aop.after();
                          } catch (Exception e) {
                              aop.exception();
                          }
                          //切面
                          return o;//目标方法的返回值
                      }
                  }
          );
      }
  }
  ```

测试：

- ```java
  public class MyTest05 {
      @Test
      public void MyTest05(){
          //得到动态代理对象
          Service agent= (Service) ProxyFactory.getAgent(new BookServiceImpl(),new TranAop());
          agent.buy();
      }
  }
  ```

## 4.Spring的AOP的通知类型(了解)

Spring支持AOP的编程，常用的有以下几种：

- Before通知：在目标方法被调用前调用，涉及接口org.springframework.aop.MethodBeforeAdvice; 
- After通知：在目标方法被调用后调用，涉及接口为org.springframework.aop.AfterReturningAdvice; 
- Throws通知：目标方法抛出异常时调用，涉及接口org.springframework.aop.ThrowsAdvice; 
- Around通知：拦截对目标对象方法调用，涉及接口为org.aopalliance.intercept.MethodInterceptor。

## 5.AOP编程术语

### 1.切面(Aspect)

切面:就是那些重复的,公共的,通用的功能称为切面,例如:日志,事务,权限.

### 2.连接点(JoinPoint)

连接点指可以被切面织入的具体方法。通常业务接口中的方法均为连接点。

### 3.切入点(PointCut)

指定切入的位置,多个连接点构成切入点.切入点可以是一个目标方法,可以是一个类中的所有方法,可以是某个包下的所有类中的方法.

### 4.目标对象(Target)

操作谁,谁就是目标对象.

### 5.通知(Advice)

来指定切入的时机.是在目标方法执行前还是执行后还是出错时,还是环绕目标方法切入切面功能.

## 6.Aspectj对AOP的实现(掌握)

### 1.什么是Aspectj

 AspectJ 是一个优秀面向切面的框架，它扩展了 Java 语言，提供了强大的切面实现。它因为是基于java语言开发的,所以无缝扩展.easy to learn and use（易学易用）.

### 2.  AspectJ 中常用的通知类型

  AspectJ 中常用的通知有四种类型：

- 前置通知@Before 
- 后置通知@AfterReturning
- 环绕通知@Around
- 最终通知@After
- 定义切入点@Pointcut(了解)

### 3.AspectJ 的切入点表达式(掌握)

1. 规范的公式:

   - execution(访问权限 方法返回值 方法声明(参数) 异常类型)

2. 简化后的公式:

   - execution( 方法返回值 方法声明(参数) )

3. 用到的符号:

   - *：代码任意个任意的字符(通配符)
   - ..： 如果出现在方法的参数中,则代表任意参数
         如果出现在路径中,则代表本路径及其所有的子路径

4. 示例:

   - ```
     execution(public * *(..)) :任意的公共方法
     	public---访问权限
     	* ---方法返回值
     	* ---方法声明
     	(..) ---参数
     	
     execution(* set*(..)):任何一个以“set”开始的方法
     	* ---返回值类型
     	set* ---以set打头的方法
     	(..) --参数
     	
     execution(* com.xyz.service.impl.*.*(..)):任意的返回值类型,在com.xyz.service.impl包下的任意类的任意方法的任意参数
     	* ---任意返回值类型
     	com.xyz.service.impl.* ---这个包下所有的类
     	*(..) ---任意方法(任意参数)
     	
     execution(* com.xyz.service..*.*(..)):任意的返回值类型 ,在com.xyz.service及其子包下的任意类的任意方法的任意参数  
     	例如：com.xyz.service.a.b.*.*(..)  
     
     execution(* *..service.*.*(..)):service之前可以有任意的子包
     execution(* *.service.*.*(..)):service之前只有一个包
     ```

### 4.AspectJ的开发环境(掌握)

添加依赖：

```xml
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.11</version>
    <scope>test</scope>
</dependency>
<!--spring依赖-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.2.5.RELEASE</version>
</dependency>
<!--aspects依赖-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-aspects</artifactId>
    <version>5.2.5.RELEASE</version>
</dependency>
```

### 5.AspectJ框架切换JDK动态代理和CGLib动态代理

```xml
<aop:aspectj-autoproxy ></aop:aspectj-autoproxy>  ===>默认是JDK动态代理,取时必须使用接口类型
<aop:aspectj-autoproxy proxy-target-class="true"></aop:aspectj-autoproxy>  ==>设置为CGLib子类代理,可以使用接口和实现类接
记住:使用接口来接,永远不出错.
```

### 6.AspectJ基于注解得Aop实现(掌握)

#### @Before前置通知实现

![](图\Spring\前置通知.png)

1. 添加依赖

2. 在applicationContext.xml文件中进行切面绑定

   - ```xml
         <!--基于注解的访问要添加包扫描-->
         <context:component-scan base-package="com.bjpowernode.s01"></context:component-scan>
         <!--绑定-->
         <aop:aspectj-autoproxy proxy-target-class="true"></aop:aspectj-autoproxy>
     ```

3. 创建业务接口

   - ```java
     public interface SomeService {
         String doSome(String name,int age);
         void show();
     }
     ```

4. 创建业务实现

   - ```java
     @Service
     public class SomeServiceImpl  implements SomeService{
         @Override
         public String doSome(String name, int age) {
             System.out.println("doSome的业务功能实现..............");
             return "abcd";
         }
         @Override
         public void show() {
             System.out.println("show()的业务方法被执行...........");
         }
     }
     ```

5. 创建切面类实现切面方法

   - ```java
     /**
      * 此类为切面类,包含各种切面方法
      */
     @Aspect //交给AspectJ的框架去识别切面类
     @Component
     public class MyAspect {
         /**
          * 所有切面的功能都是由切面方法来实现的
          * 可以讲各种切面都在此类进行开发
          *
          * 前置通知的切面方法的规范
          * 1.访问权限是public
          * 2.方法的返回值是void
          * 3.方法名称自定义
          * 4.方法没有参数,如果由也是JoinPoint类型
          * 5.必须使用@Before注解声明切入的时机是前切功能和切入点
          *    参数:value 指定切入点表达式
          *
          *
          *  业务方法:
          *      public String doSome(String name, int age)
          */
         //常用的写法
         @Before(value = "execution( * com.bjpowernode.s01.*.*(..))") //s0包下得所有类和方法
         public void myBefore(JoinPoint jp){
             System.out.println("切面方法中的前置通知功能实现............");
             System.out.println("目标方法的签名"+jp.getSignature());//这个就是详细得方法 带包名得
             System.out.println("目标方法的参数"+ Arrays.toString(jp.getArgs()));
         }
     }
     
     ```

6. 测试：

   - ```java
     @Test
     public void test01(){
         ApplicationContext ac=new ClassPathXmlApplicationContext("s01/applicationContext.xml");
         SomeService service= (SomeService) ac.getBean("someServiceImpl");//注意这里是驼峰命名法
         System.out.println(service.getClass());
         String s=service.doSome("张三",18);
         System.out.println(s);
         
         /*
         class com.bjpowernode.s01.SomeServiceImpl$$EnhancerBySpringCGLIB$$16b5aab6
         执行结果
         切面方法中的前置通知功能实现............
         目标方法的签名String com.bjpowernode.s01.SomeServiceImpl.doSome(String,int)
         目标方法的参数[张三, 18]
         doSome的业务功能实现..............
         abcd
         */
     }
     ```

#### @AfterReturing后置通知

后置通知是在目标方法执行后切入切面功能,可以得到目标方法的返回值.如果目标方法的返回值是简单类型(8种基本类型+String)则不可改变.如果目标方法的返回值是引用类型则可以改变.

![](图\Spring\后置通知.png)

1. 业务接口:

   - ```java
     public interface SomeService {
         String doSome(String name,int age);
     
         Student change();
     }
     ```

2. 业务接口实现类:

   - ```java
     @Service
     public class SomeServiceImpl implements SomeService{
         @Override
         public String doSome(String name, int age) {
             System.out.println("doSome()业务方法被执行");
             return "abcd";
         }
     
         @Override
         public Student change() {
             System.out.println("change方法被执行....");
             return new Student("张三");
         }
     }
     ```

3. 定义一个实体类：

   - ```java
     public class Student {
         private String name;
     }
     ```

4. 切面类：

   - ```java
     @Aspect
     @Component
     public class MyAspect {
         /**
          * 后置通知得方法得规范
          * 1.访问权限是public
          * 2.方法没有返回值 void
          * 3.方法名称自定义
          * 4.方法有参数,
          	也可以没有参数,如果目标方法没有返回值，则可以写无参得方法,
          	但一般会写有参,这里可以处理无参，可以处理有参,这个切面方法得参数 就是目标方法得返回
          * 5.使用@AfterReturning注解,表明是后置通知
          *  参数：
          *      value:指定切入点表达式
          *      returning:指定目标方法得返回值得名称,此名称必须与切面方法得参数名称一致
          *
          *      *  com.bjpowernode.s02.*.*(..) 任意访问权限 com.bjpowernode.so2包下得任意方法 参数类型任意
          */
         @AfterReturning(value = "execution(* com.bjpowernode.s02.*.*(..))",returning = "obj")
         public void myAfterReturning(Object obj){//这个是接收 目标方法得返回值
             System.out.println("后置通知功能实现.........");
             if (obj!=null){
                 if(obj instanceof String){
                     obj=obj.toString().toUpperCase();
                     //如果是8种基本数据类型 数据就是不可变 在测试方法中还是返回的目标方法的返回值 并不会在后切中改变
                     System.out.println("在切面方法中目标方法得返回执值"+obj);
                 }
                 if(obj instanceof Student){
                     Student student= (Student) obj;
                     //如果是引用数据类型就是可变的 在测试方法中也会变成李四
                     student.setName("李四");
                     System.out.println("在切面方法中目标方法的返回值"+student);
                 }
             }
         }
     }
     
     ```

5. applicationContext.xml

   - ```xml
         <!--基于注解的访问要添加包扫描-->
         <context:component-scan base-package="com.bjpowernode.s02"></context:component-scan>
     
         <!--绑定-->
         <aop:aspectj-autoproxy proxy-target-class="true"></aop:aspectj-autoproxy>
     ```

6. 测试：

   - ```java
     
     @Test
     public void test01(){
     	ApplicationContext ac=new ClassPathXmlApplicationContext("s02/applicationContext.xml");
     	SomeService service= (SomeService) ac.getBean("someServiceImpl");
     	String s=service.doSome("z22",18);
     	System.out.println("在测试方法中返回值为"+s); 
             /*
             返回值
             doSome()业务方法被执行
             后置通知功能实现.........
             在切面方法中目标方法得返回执值ABCD
             在测试方法中返回值为abcd
             
             如果是8种基本数据类型 数据就是不可变 在测试方法中还是返回的目标方法的返回值 并不会在后切中改变
             
             */
         }
         @Test
     public void test02(){
     	ApplicationContext ac=new ClassPathXmlApplicationContext("s02/applicationContext.xml");
     	SomeService service= (SomeService) ac.getBean("someServiceImpl");
     	Student student= service.change();
     	System.out.println("在测试方法中目标方法的返回值为"+student);
             /*
             返回值
             change方法被执行....
             后置通知功能实现.........
             在切面方法中目标方法的返回值Student{name='李四'}
             在测试方法中目标方法的返回值为Student{name='李四'}
             
             如果是引用数据类型就是可变的 在测试方法中也会变成李四
             */
     }
     
     ```

     

#### @Around环绕通知

  它是通过拦截目标方法的方式 ,在目标方法前后增强功能的通知.它是功能最强大的通知,一般事务使用此通知.它可以轻易的改变目标方法的返回值.

![](图\Spring\环绕通知.png)

1. 业务接口实现类:

   - ```java
     @Service
     public class SomeServiceImpl implements SomeService{
         @Override
         public String doSome(String name, int age) {
             System.out.println("s03的SomeServiceImpl中的doSome方法执行了......"+name);
             return "abcd";
         }
     }
     
     ```

2. 切面类

   - ```java
     @Aspect
     @Component
     public class MyAspect {
         /**
          * 环绕通知方法的规范:
          *  1.访问权限是public
          *  2.切面方法有返回值,此返回值就是目标方法的返回值
          *  3.方法名称自定义
          *  4.方法有参数,此参数就是目标方法
          *  5.回避异常
          *  6.使用@Around注解声明是环绕通知
          *      参数:
          *          value：指定切入点表达式
          */
     
         @Around(value = "execution(* com.bjpowernode.s03.*.*(..))")
         public Object myAround(ProceedingJoinPoint pjp) throws Throwable {
             //前切功能实现
             System.out.println("环绕通知中的前置功能实现");
             //目标方法调用 通过切面方法的参数调用 这个Obj就是目标方法的返回值
             Object obj=pjp.proceed(pjp.getArgs());
             //后切功能实现
             System.out.println("环绕通知中的后置功能实现");
             // 无论是什么类型 都会改变目标方法的返回值
             return obj.toString().toUpperCase(); //改变了目标方法的返回值
         }
     }
     ```

3. 测试:

   - ```java
      @Test
     public void test01(){
     	ApplicationContext ac=new ClassPathXmlApplicationContext("s03/applicationContext.xml");
     	SomeService service= (SomeService) ac.getBean("someServiceImpl");
     	String s=service.doSome("张三",123);
     	System.out.println(s);
     	/*
     	环绕通知中的前置功能实现
         s03的SomeServiceImpl中的doSome方法执行了......张三
         环绕通知中的后置功能实现
         ABCD ====>返回值改变了
     	*/
     }
     ```

     

#### @After最终通知  给切入点表达式起别名@Pointcut

无论目标方法是否正常执行,最终通知的代码都会被执行.

```java
@Aspect
@Component
public class MyAspect {
    /**
     * 最终通知方法的规范:
     *  1.访问权限是public
     *  2.方法没有返回值
     *  3.方法名称自定义
     *  4.方法没有参数,如果有也只能是JoinPoint
     *  5.使用@After注解表名最终通知
     *      参数:
     *          value：指定切入点表达式
     *  6.最终通知不管目标方法是否出现异常 都会执行完程序
     */
    @After(value = "mycut()")
    public void myAfter(){
        System.out.println("最终通知的功能.............");
    }

    @Before(value = "mycut()")
    public void myBefore(){
        System.out.println("前置通知的功能.............");
    }


    @AfterReturning(value = "mycut()",returning = "obj")
    public void myAfterReturning(Object obj){
        System.out.println("后置通知的功能.............");
    }

    @Around(value = "mycut()")
    public Object myAround(ProceedingJoinPoint point) throws Throwable {
        System.out.println("环绕通知中的前置通知的功能.............");
        Object obj=point.proceed(point.getArgs());
        System.out.println("环绕通知中的后置通知的功能.............");
        return obj;

    }

    //起别名
    //如果多个切面切入到同一个切入点,可以使用别名简化开发.使用@Pointcut注解,创建一个空方法,此方法的名称就是别名.
    @Pointcut(value = "execution(* com.bjpowernode.s04.*.*(..))")
    public void mycut(){}

}


/*
测试结果:
	环绕通知中的前置通知的功能.............
    前置通知的功能.............
    s04的SomeServiceImpl中的doSome方法执行了......13
    环绕通知中的后置通知的功能.............
    最终通知的功能.............
    后置通知的功能.............
    abcd

*/
```



# 第四章Spring集成MyBatis

## 1.SM开发步骤：

### 1.创建数据库表

```sql
use ssm;

create table springusers(
  userid int primary key,
  uname varchar(20),
  upass varchar(20)
);

create table accounts(
 aid  int primary key,
 aname varchar(20),
 acontent varchar(50)
);

select userid,uname,upass from users;
select aid,aname,acontent from accounts;
```



### 2.新建项目,选择quickstart模板(这个和之前的一样)

### 3.修改目录(就是补全 resuorces)

### 4.修改pom.xml文件,添加相关的依赖(使用老师提供)

```xml
 <groupId>com.bjpowernode</groupId>
  <artifactId>spring_008_sm</artifactId>
  <version>1.0-SNAPSHOT</version>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>

  <dependencies>
    <!--单元测试-->
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <!--aspectj依赖-->
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aspects</artifactId>
      <version>5.2.5.RELEASE</version>
    </dependency>
    <!--spring核心ioc-->
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-context</artifactId>
      <version>5.2.5.RELEASE</version>
    </dependency>
    <!--做spring事务用到的-->
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-tx</artifactId>
      <version>5.2.5.RELEASE</version>
    </dependency>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-jdbc</artifactId>
      <version>5.2.5.RELEASE</version>
    </dependency>
    <!--mybatis依赖-->
    <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis</artifactId>
      <version>3.5.1</version>
    </dependency>
    <!--mybatis和spring集成的依赖-->
    <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis-spring</artifactId>
      <version>1.3.1</version>
    </dependency>
    <!--mysql驱动-->
    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.28</version>
    </dependency>
    <!--阿里公司的数据库连接池-->
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>druid</artifactId>
      <version>1.1.12</version>
    </dependency>
  </dependencies>

  <build>
    <!--目的是把src/main/java目录中的xml文件包含到输出结果中。输出到classes目录中-->
    <resources>
      <resource>
        <directory>src/main/java</directory><!--所在的目录-->
        <includes><!--包括目录下的.properties,.xml 文件都会扫描到-->
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
      <resource>
        <directory>src/main/resources</directory><!--所在的目录-->
        <includes><!--包括目录下的.properties,.xml 文件都会扫描到-->
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
    </resources>
  </build>
```

### 5.添加MyBatis相应的模板(SqlMapConfig.xml和XXXMapper.xml文件)

Setting-->Editor-->File and code Templates-->点击"+"号添加

SqlMapConfig.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>

    <!--读取属性文件中数据库的配置-->
    <properties resource="db.properties"></properties>
    <!--设置日志输出语句,显示相应操作的sql语名-->
    <settings>
        <setting name="logImpl" value="STDOUT_LOGGING"/>
    </settings>
    <typeAliases>
        <package name="com.bjpowernode.pojo"></package>
    </typeAliases>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.cj.jdbc.Driver"/>
                <property name="url"
                          value="jdbc:mysql://localhost:3306/ssm?useSSL=false&amp;serverTimezone=UTC&amp;allowPublicKeyRetrieval=true"/>
                <property name="username" value="root"/>
                <property name="password" value="123456"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <package name="mapper文件所在的包名"></package>
    </mappers>
</configuration>
```

XXXMapper.xml文件

```xml
<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="接口的完全限定名称">

</mapper>
```



### 6.添加SqlMapConfig.xml文件(MyBatis核心配置文件),并拷贝jdbc.propertiest属性文件到resources目录下

jdbc.propertiest

- ```properties
  jdbc.driverClassName=com.mysql.cj.jdbc.Driver
  jdbc.url=jdbc:mysql://localhost:3306/ssm?useUnicode=true&characterEncoding=utf8
  jdbc.username=root
  jdbc.password=root
  ```

SqlMapConfig.xml

- ```xml
  <configuration>
      <!--设置日志输出语句,显示相应操作的sql语名-->
      <settings>
          <setting name="logImpl" value="STDOUT_LOGGING"/>
      </settings>
  </configuration>
  ```

  

### 7.添加applicationContext_mapper.xml (数据访问层Spring的核心配置文件)

这里是固定的写法记住就好

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">
    <!--读取属性文件 jdbc.properties-->
    <context:property-placeholder location="jdbc.properties"></context:property-placeholder>
    <!--创建数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${jdbc.driverClassName}"></property>
        <property name="url" value="${jdbc.url}"></property>
        <property name="username" value="${jdbc.username}"></property>
        <property name="password" value="${jdbc.password}"></property>
    </bean>
    <!--配置SqlSessionFactoryBean类-->
    <bean class="org.mybatis.spring.SqlSessionFactoryBean">
        <!--配置数据源 这里引用的是 上面的id="dataSource"-->
        <property name="dataSource" ref="dataSource"></property>
        <!--配置MyBatis的核心配置文件-->
        <property name="configLocation" value="SqlMapConfig.xml"></property>
        <!--注册实体类的别名-->
        <property name="typeAliasesPackage" value="com.bjpowernode.pojo"></property>
    </bean>
    <!--注册mapper.xml 这里面已经注册好了-->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="com.bjpowernode.mapper"></property>
    </bean>
</beans>
```



### 8.添加applicationContext_service.xml(这个是业务逻辑层的Spring配置)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context" xmlns:tx="http://www.springframework.org/schema/tx"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd">
    <!--导入applicationContext_mapper.xml-->
    <import resource="applicationContext_mapper.xml"></import>
    <!--SM是基于注解的开发 所以添加包扫描-->
    <context:component-scan base-package="com.bjpowernode.service.impl"></context:component-scan>

</beans>
```



### 9.添加Users实体类,Accounts实体类

Users

- ```java
  public class Users {
      private Integer userid;
      private String username;
      private String upass;
  
      public Users() {
      }
  }
  ```



### 10.添加mapper包,添加UsersMapper接口和UsersMapper.xml文件并开发

UserMapper.java(接口)：

- ```java
  public interface AccountsMapper {
      //增加账号
      int save(Accounts accounts);
  }
  ```

- UserMapper.xml

  - ```xml
    <mapper namespace="com.bjpowernode.mapper.AccountsMapper">
        <!--
            //增加账号
        int save(Accounts accounts);
        实体类：
            private Integer aid;
            private String ;
            private String  acontent;
        -->
        <insert id="save" parameterType="accounts">
            insert into accounts values (#{aid},#{aname},#{acontent})
        </insert >
    </mapper>
    ```

### 11.添加service包,添加UsersService接口和UsersServiceImpl实现类

UserService.java(接口)：

- ```java
  public interface UsersService {
      //增加用户
      int insert(Users users);
  }
  
  ```

- UserServiceImpi(实现类)

  - ```java
    @Service //业务逻辑层 用Service注解交给Spring创建对象
    //@Transactional(propagation = Propagation.REQUIRED)
    public class UsersServiceImpl implements UsersService {
        //切记切记:在所有的业务逻辑层中一定会有数据访问层的对象
        /**	过去的方式:
         *   读取核心配置文件
         *   InputStream in= Resources.getResourceAsStream("SqlMapConfig.xml");
         *   创建工厂对象
         *   SqlSessionFactory factory=new SqlSessionFactoryBuilder().build(in);
         *   取出sqlSession
         *   sqlSession = factory.openSession(true);//这个是自动提交
         *   取出动态代理得对象,完成接口中方法得调用,实则是调用xml文件中相应得标签得功能
         *   uMapper=sqlSession.getMapper(UsersMapper.class);
         *
         */
    
        //现在就直接用注解创建就可以了
        @Autowired //引用类型的注入
        UsersMapper usersMapper;
        
        @Override
        public int insert(Users users) {
            int num=usersMapper.insert(users);
            System.out.println("用户增加成功num="+num);
        }
    }
    
    ```

    

### 12.添加测试类进行功能测试

```java
     @Test
    public void testUsers(){
        ApplicationContext ac=new ClassPathXmlApplicationContext("applicationContext_service.xml");
        //取出UsersServiceImpl
        UsersService uService= (UsersService) ac.getBean("usersServiceImpl");
        int num= uService.insert(new Users(100,"张三","123"));
        System.out.println(num);
    }
```

## 2.事务

### 1.账户增加一套

1. 要演示事务需要两个实体类,所以要添加一个Account的实体类和数据库表

   - ```java
     public class Accounts {
         private Integer aid;
         private String aname;
         private String  acontent;
     
         public Accounts() {
        }
     ```

2. AccountsMapper.java(接口) ---->数据访问层

   - ```java
     public interface AccountsMapper {
         //增加账号
         int save(Accounts accounts);
     }
     ```

   - AccountsMapper.xml

     - ```xml
       <mapper namespace="com.bjpowernode.mapper.AccountsMapper">
           <!--
           增加账号
           int save(Accounts accounts);
           实体类：
               private Integer aid;
               private String ;
               private String  acontent;
           -->
           <insert id="save" parameterType="accounts">
               insert into accounts values (#{aid},#{aname},#{acontent})
           </insert>
       </mapper>
       ```

3. AccountsService.java(接口)----业务逻辑层

   - ```java
     public interface AccountsService {
         int save(Accounts accounts);
     }
     ```

   - AccountsServiceImpl(实现类)：

     - ```java
       @Service
       public class AccountsServiceImpl implements AccountsService {
           //一定会有数据访问的对象
           @Autowired
           AccountsMapper accountsMapper;
       
           @Override
           public int save(Accounts accounts) {
               int num=0;
               num=accountsMapper.save(accounts);
               System.out.println("增加账户成功 num="+num);
               //手工抛出异常
               System.out.println(1/0);
               return num;
           }
       }
       ```

4. 测试：

   - ```java
     @Test
     public void testAccounts(){
     	ApplicationContext ac=new ClassPathXmlApplicationContext("applicationContext_service.xml");
         
     	AccountsService accountsService= (AccountsService) ac.getBean("accountsServiceImpl");
     	System.out.println(accountsService.getClass());
     	accountsService.save(new Accounts(202,"李四2","账号安全2"));
     }
     ```

### 2.Spring添加事务的两种方法

1. 注解式的事务
   - 使用@Transactional注解完成事务控制,此注解可添加到类上,则对类中所有方法执行事务的设定.此注解可添加到方法上,只是对此方法执行事务的处理.
2. 声明式事务(必须掌握),在配置文件中添加一次,整个项目遵循事务的设定.

### 3.添加注解事务的步骤

1. 在applicationContext_service.xml文件中添加事务管理器

   - ```Xml
         <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
             <!--因为事务必须关联数据库处理,所以要配置数据源-->
             <!--ref 中的dataSource 是applicationContext_mapper.xml-->
             <property name="dataSource" ref="dataSource"></property>
          </bean>
     ```

2. 在applicationContext_service.xml文件中添加事务的注解驱动

   - ```xml
     <tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>
     ```

3. 在业务逻辑的实现类上添加注解@Transactional(propagation = Propagation.REQUIRED)

   - REQUIRED表示增删改操作时必须添加的事务传播特性

   - ```java
     @Service
     @Transactional(propagation = Propagation.REQUIRED)
     public class AccountsServiceImpl implements AccountsService {
         //一定会有数据访问的对象
         @Autowired
         AccountsMapper accountsMapper;
     
         @Override
         public int save(Accounts accounts) {
             int num=0;
             num=accountsMapper.save(accounts);
             System.out.println("增加账户成功 num="+num);
             //手工抛出异常
             System.out.println(1/0);
             return num;
         }
     }
     ```

     

### 4.@Transactional注解参数详解

```java
@Transactional(propagation = Propagation.REQUIRED,//事务的传播特性
	        noRollbackForClassName = "ArithmeticException", //指定发生什么异常不回滚,使用的是异常的名称
	        noRollbackFor = ArithmeticException.class,//指定发生什么异常不回滚,使用的是异常的类型
	        rollbackForClassName = "",//指定发生什么异常必须回滚
	        rollbackFor = ArithmeticException.class,//指定发生什么异常必须回滚
	        timeout = -1, //连接超时设置,默认值是-1,表示永不超时
	        readOnly = false, //默认是false,如果是查询操作,必须设置为true.
	        isolation = Isolation.DEFAULT//使用数据库自已的隔离级别        
	)
```

### 5.Spring中事务的五大隔离级别

1. 未提交读(Read Uncommitted)：允许脏读，也就是可能读取到其他会话中未提交事务修改的数据
2. 提交读(Read Committed)：只能读取到已经提交的数据。Oracle等多数数据库默认都是该级别 (不重复读)
3. 可重复读(Repeated Read)：可重复读。在同一个事务内的查询都是事务开始时刻一致的，InnoDB默认级别。在SQL标准中，该隔离级别消除了不可重复读，但是还存在幻象读，但是innoDB解决了幻读
4. 串行读(Serializable)：完全串行化的读，每次读都需要获得表级共享锁，读写相互都会阻塞
5. 使用数据库默认的隔离级别isolation = Isolation.DEFAULT
6. **MySQL：mysql默认的事务处理级别是'REPEATABLE-READ',也就是可重复读**
7. **Oracle：oracle数据库支持READ COMMITTED 和 SERIALIZABLE这两种事务隔离级别。默认系统事务隔离级别是READ COMMITTED,也就是读已提交**

### 6.添加事务管理器

- JDBC:  Connection   con.commit();   con.rollback();

- MyBatis:  SqlSession   sqlSession.commit();  sqlSession.rollback();

- Hibernate:  Session    session.commit();   session.rollback();

- 事务管理器用来生成相应技术的连接+执行语句的对象.

  - 如果使用MyBatis框架,必须使用DataSourceTransactionManager类完成处理

    - ```xml
          <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
             <!--因为事务必须关联数据库处理,所以要配置数据源-->
             <property name="dataSource" ref="dataSource"></property>
          </bean>
      ```

- 项目中的所有事务,必须添加到业务逻辑层上

### 7.Spring事务的传播特性

- 多个事务之间的合并,互斥等都可以通过设置事务的传播特性来解决.

  - 常用

    - ```
      PROPAGATION_REQUIRED：必被包含事务(增删改必用)
      PROPAGATION_REQUIRES_NEW：自己新开事务，不管之前是否有事务
      PROPAGATION_SUPPORTS：支持事务，如果加入的方法有事务，则支持事务，如果没有，不单开事务
      PROPAGATION_NEVER：不能运行中事务中，如果包在事务中，抛异常
      PROPAGATION_NOT_SUPPORTED：不支持事务，运行在非事务的环境
      ```

  - 不常用

    - ```
      PROPAGATION_MANDATORY：必须包在事务中，没有事务则抛异常
      PROPAGATION_NESTED：嵌套事务
      ```

### 8.为了测试传播特性改造项目

```java
  @Service  //交给Spring去创建对象
	@Transactional(propagation = Propagation.REQUIRED)
	public class UsersServiceImpl implements UsersService {    
	    @Autowired
	    UsersMapper usersMapper;

	    @Autowired
	    AccountsService accountsService;

	    @Override
	    public int insert(Users users) {
	        int num = usersMapper.insert(users);
	        System.out.println("用户增加成功!num="+num);

	        //调用帐户的增加操作,调用的帐户的业务逻辑层的功能
	        num = accountsService.save(new Accounts(300,"王五","帐户好的呢!"));
	        return num;
	    }
	}
```

### 9.声明式事务

 Spring非常有名的事务处理方式.声明式事务.

要求项目中的方法命名有规范：

1. 完成增加操作包含    add  save  insert  set
2. 更新操作包含   update   change  modify  
3. 删除操作包含   delete   drop    remove  clear
4. 查询操作包含   select   find    search  get 

配置事务切面时可以使用通配符*来匹配所有方法：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context" xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd http://www.springframework.org/schema/aop https://www.springframework.org/schema/aop/spring-aop.xsd">
    <!--此配置文件与applicationContext_service.xml的功能一样,只是事务配置不一样-->

    <!--导入applicationContext_mapper.xml-->
    <import resource="applicationContext_mapper.xml"></import>
    <!--添加包扫描-->
    <context:component-scan base-package="com.bjpowernode.service"></context:component-scan>
    <!--添加事务管理器-->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"></property>
    </bean>

    <!--添加注解事务-->
    <tx:annotation-driven order="100"></tx:annotation-driven>

    <!--配置事务切面-->
    <tx:advice id="myadivce" transaction-manager="transactionManager">
        <tx:attributes>
            <tx:method name="*select*" read-only="true"/>
            <tx:method name="*find*" read-only="true"/>
            <tx:method name="*search*" read-only="true"/>
            <tx:method name="*get*" read-only="true"/>
            <tx:method name="*insert*" propagation="REQUIRED" no-rollback-for="ArithmeticException"/>
            <tx:method name="*add*" propagation="REQUIRED"/>
            <tx:method name="*save*" propagation="REQUIRED" no-rollback-for="ArithmeticException"/>
            <tx:method name="*set*" propagation="REQUIRED"/>
            <tx:method name="*update*" propagation="REQUIRED"/>
            <tx:method name="*change*" propagation="REQUIRED"/>
            <tx:method name="*modify*" propagation="REQUIRED"/>
            <tx:method name="*delete*" propagation="REQUIRED"/>
            <tx:method name="*remove*" propagation="REQUIRED"/>
            <tx:method name="*drop*" propagation="REQUIRED"/>
            <tx:method name="*clear*" propagation="REQUIRED"/>
            <tx:method name="*" propagation="SUPPORTS"/>

        </tx:attributes>
    </tx:advice>
    <!--绑定切面和切入点-->
    <aop:config>
        <aop:pointcut id="mycut" expression="execution(* com.bjpowernode.service.impl.*.*(..))"></aop:pointcut>
        <aop:advisor advice-ref="myadivce" order="1" pointcut-ref="mycut"></aop:advisor>
    </aop:config>
</beans>

```

