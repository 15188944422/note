# 1、什么是dubbo

## 1.1、什么是分布式

**分布式也就是微服务中的一种体系结构，那么提到分布式、就要先说说单机和集群**

### 1.1.1、单机结构

> ​	单机就是所有业务全部写在一个项目中，部署服务到一台服务器上，所有请求业务都由这台服务器处理，显示，当业务增长到一定程度的时候，服务器的硬件会无法满足业务需求，自然而然的想到一个程序步行就部署多个。

### 1.1.2、集群

#### ①概念

> ​	集群就是单机的多实例(多态服务器的集合),在多个服务器上部署多个服务，每个服务就是一个节点，部署N个节点，处理业务的能力就提升N倍，这些节点的结合就叫做集群。
>
> ​	简单地说，集群就是指一组（若干个）相互独立的计算机，利用高速通信网络组成的一个较大的计算机服务系统，每个集群节点（即集群中的每台计算机）都是运行各自服务的独立服务器。这些服务器之间可以彼此通信，协同向用户提供应用程序，系统资源和数据，并以单一系统的模式加以管理。当用户请求集群系统时，集群给用户的感觉就是一个单一独立的服务器，而实际上用户请求的是一组集群服务器。

#### ②负载均衡

> 负载均衡：协调群里的每个节点均衡地接收业务请求。通俗的讲就是服务A和服务B相同时间段内处理的同类业务请求数量是相似的

#### ③集群的特点

> - 扩展性好：集群只是单机的多个复制，没有改变单机的原有的代码结构，每次部署新节点只需要复制部署即可。
> - 单个节点业务耦合度高、资源浪费：节点是多个业务处理集合（耦合度高），每个具体业务的访问量可能差异很大，比如JD上账户管理模块的访问量肯定低于订单模块。
> - 然而账户管理模块和订单模块的部署数量是一样的（因为每个节点里独有这两个模块），相对于订单模块来说，部署同样多的账户管理模块就是浪费。
> - 那就把单机节点不同的业务处理模块拆开，这就是[分布式](https://so.csdn.net/so/search?q=分布式&spm=1001.2101.3001.7020)了。

### 1.1.3、什么是分布式

> 分布式系统一定是由多个节点组成的系统。
>
> 其中，节点指的是计算机服务器，而且这些节点一般不是孤立的，而是互通的。
>
> 这些连通的节点上部署了我们的节点，并且相互的操作会有协同。
>
> 分布式系统对于用户而言，他们面对的就是一个服务器，提供用户需要的服务而已，
>
> 而实际上这些服务是通过背后的众多服务器组成的一个分布式系统，因此分布式系统看起来像是一个超级计算机一样。

### 1.1.4 分布式与集群的区别 

#### ①集群

> 集群是指**在几个服务器上部署相同的应用程序来分担客户端的请求**。
>
> 它是**同一个系统**部署在不同的服务器上，比如一个登陆系统部署在不同的服务器上。
>
> 好比 多个人一起**做同样的事**。
>
> 集群主要的使用场景是为了分担请求的压力。
>
> 但是，当压力进一步增大的时候，可能在需要存储的部分，比如mysql无法面对大量的“写压力”。
>
> 因为在mysql做成集群之后，主要的写压力还是在master的机器上，其他slave机器无法分担写压力，这时，就引出了“分布式”。

#### ②分布式

> 分布式是指多个系统协同合作完成一个特定任务的系统。
>
> 它是不同的系统部署在不同的服务器上，服务器之间相互调用。
>
> 好比 多个人一起做不同的事。
>
> 分布式是解决中心化管理的问题，把所有的任务叠加到一个节点处理，太慢了。
>
> 所以把一个大问题拆分为多个小问题，并分别解决，最终协同合作。
>
> 分布式的主要工作是分解任务，把职能拆解。
>
> 分布式的主要应用场景是单台机器已经无法满足这种性能的要求，必须要融合多个节点，并且节点之间的相关部分是有交互的。
>
> 相当于在写mysql的时候，每个节点存储部分数据（分库分表），这就是分布式存储的由来。
>
> 存储一些非结构化数据：静态文件、图片、pdf、小视频 ... 这些也是分布式文件系统的由来。
> 

#### ③用生活中的例子，来说明集群和分布式及其区别：

> 小饭店原来只有一个厨师，切菜洗菜备料炒菜全干。
>
> 后来客人多了，厨房一个厨师忙不过来，又请了个厨师，两个厨师炒一样的菜，这两个厨师的关系是集群。
>
> 
>
> 为了让厨师专心炒菜，把菜做到极致，又请了个配菜师负责切菜，备菜，备料，厨师和配菜师的关系是分布式，
>
> 一个配菜师也忙不过来了，又请了个配菜师，两个配菜师关系是集群。

#### ④最后，再深入理解一下集群和分布式及其区别：

> **分布式：把一个大业务拆分成多个子业务，每个子业务都是一套独立的系统，子业务之间相互协作最终完成整体的大业务。** 
>
> **集群：把处理同一个业务的系统部署多个节点 。**
>
> **把一套系统拆分成不同的子系统部署在不同服务器上，这叫分布式**。
>
> **把多个相同的系统部署在不同的服务器上，这叫集群。部署在不同服务器上的相同系统必然要做“负载均衡”。** 
>
> 集群主要是简单**加机器解决问题，对于问题本身不做任何分解**。
>
> 分布式处理里必然涉及**任务分解与答案归并**。分布式中的某个子任务节点，可以是一个集群，该集群中的任一节点都作为一个完整的任务出现。
>
> 集群和分布式都是由多个节点组成，但**集群中各节点间基本不需要通信协调**，而**分布式中各个节点的通信协调是必不可少的**。

## 1.2、什么是dubbo

官网：https://dubbo.apache.org/

### 1.2.1、dubbo介绍

**一个高性能的，基于** **java** **的，开源** **RPC** 框架。

Dubbo 是一个分布式服务框架，致力于提供高性能和透明化的 **RPC** 远程服务调用方案、服务治理方案。

Dubbo 是阿里巴巴服务化治理方案的核心框架，每天为 2,000+ 个服务提供3,000,000,000+次访问量支持，并被广泛应用于阿里巴巴集团的各成员站点

> ​	PRC 是 Remote Procedure Call Protocol ，称为：远程过程调用协议。是一种通过网络从远程计算机程序上请求服务，而不需要了解底层网络技术的协议。该协议允许运行于一台计算机的程序调用另一台计算机的程序。程序员无需编为网络交互功能编码。
>
> 主要功能是让构建分布式计算（应用）更容易，在提供强大的远程调用能力时不损失本地调用的语义简洁性。在一台计算的程序使用其他计算机上的功能就是使用自己的功能一样。RPC 技术提供了透明的访问其他服务的底层实现细节。使用分布式系统中的服务更加方便

## 1.3 `Dubbo`作用

### 1.3.1 为什么使用`Dubbo`

因为是阿里开源项目，国内很多互联网公司都在用，已经经过很多线上考验。内部使用了`Netty、Zookeeper`，保证了高性能高可用性。

- **使用`Dubbo`可以将核心业务抽取出来，作为独立的服务**，逐渐形成稳定的服务中心，可用于提高业务复用灵活扩展，使前端应用能更快速的响应多变的市场需求。
- 分布式架构可以承受更大规模的并发流量。

### 1.3.2 `Dubbo`能做什么

1. **透明化的远程方法调用**，就像调用本地方法一样调用远程方法，只需简单配置，没有任何`API`侵入。
2. **软负载均衡及容错机制**，可在内网替代`F5`等硬件负载均衡器，降低成本，减少单点。
3. **服务自动注册与发现**，不再需要写死服务提供方地址，注册中心基于接口名查询服务提供者的`IP`地址，并且能够平滑添加或删除服务提供者

## 1.4 `Dubbo`技术架构

![](imgs\dubbo架构.png)

**节点角色说明**

| 节点      | 角色说明                               |
| --------- | -------------------------------------- |
| Provider  | 暴露服务的服务提供方                   |
| Consumer  | 调用远程服务的服务消费方               |
| Registry  | 服务注册与发现的注册中心               |
| Monitor   | 统计服务的调用次数和调用时间的监控中心 |
| Container | 服务运行容器                           |

看了这几个概念后似乎发现其实`Dubbo` 的架构也是很简单的(其实现细节是复杂)，为什么这么说呢，有没有发现，其实很像**生产者-消费者**模型。只是在这种模型上，加上了**注册中心和监控中心**，用于管理提供方提供的`url`，以及管理整个过程。

**调用关系说明**

1. 服务容器负责启动，加载，运行服务提供者。
2. 服务提供者在启动时，向注册中心注册自己提供的服务。
3. 服务消费者在启动时，向注册中心订阅自己所需的服务。
4. 注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者。
5. 服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。
6. 服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心。

那么，整个**发布-订阅**的过程就非常的简单了：

- 启动容器，加载，运行服务提供者。
- 服务提供者在启动时，在注册中心发布注册自己提供的服务。
- 服务消费者在启动时，在注册中心订阅自己所需的服务。

如果考虑**失败或变更**的情况，就需要考虑下面的过程：

- 注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者。
- 服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。
- 服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心。

# 2、入门案例

## 2.1、直连的方式(没有使用注册中心 两层)

### 1.新建一个空的项目

### 2.新建第一个空maven

#### ①在pom.xml添加依赖

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.song.dubbo</groupId>
    <artifactId>001-link-userservice-provider</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!--注意这里的打包方式位war-->
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--Spring依赖-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>

        <!--dubbo依赖-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo</artifactId>
            <version>2.6.2</version>
        </dependency>

    </dependencies>

</project>
```

#### ②添加完依赖以后刷新然后补全目录

![](D:\Power\Dubbo\imgs\1.1.png)

#### ③新建一个User的实体类在pojo下

```java
package com.song.dubbo.pojo;

import java.io.Serializable;

public class User implements Serializable {
    private Integer id;

    private String username;

    private Integer age;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }
}
```

#### ④新建一个UserService

UserService.java

```java
package com.song.dubbo.service;

import com.song.dubbo.pojo.User;

public interface UserService {
    /**
     * 根据用户标识获取用户信息
     * @param id
     * @return
     */
    User queryUserById(Integer id);
}

```

UserServiceImpl.java

```java
package com.song.dubbo.service.impl;

import com.song.dubbo.pojo.User;
import com.song.dubbo.service.UserService;

public class UserServiceImpl implements UserService {
    @Override
    public User queryUserById(Integer id) {
        User user = new User();
        user.setId(id);
        user.setUsername("lisi");
        user.setAge(23);

        return user;
    }
}

```

#### ⑤配置dubbo的配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">

    <!--服务提供者声明名称:必须保证服务名称的唯一性,它的名称是dubbo内部使用的唯一标识-->
    <dubbo:application name="001-link-userservice-provider"/>

    <!--访问服务协议的名称及端口号,dubbo官方推荐使用的是dubbo协议,端口号默认为20880-->
    <!--
        name:指定协议的名称
        port:指定协议的端口号(默认为20880)
    -->
    <dubbo:protocol name="dubbo" port="20880"/>

    <!--
        暴露服务接口->dubbo:service
        interface:暴露服务接口的全限定类名
        ref:接口引用的实现类在spring容器中的标识
        registry:如果不使用注册中心,则值为:N/A
    -->
    <dubbo:service interface="com.song.dubbo.service.UserService" ref="userService" registry="N/A"/>

    <!--将接口的实现类加载到spring容器中-->
    <bean id="userService" class="com.song.dubbo.service.impl.UserServiceImpl"/>

</beans>
```

#### ⑥配置web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <context-param>
        <!--自定义Spring配置文件的位置和名称-->
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:dubbo-userservice-provider.xml</param-value>
    </context-param>
    <listener>
            <!--
            配置Spring的监听器，在服务器启动时加载Spring的配置文件
            Spring配置文件默认位置和名称：/WEB-INF/applicationContext.xml
            可通过上下文参数自定义Spring配置文件的位置和名称
            -->
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>
</web-app>

```

#### ⑦编写dubbo的配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">

    <!--服务提供者声明名称:必须保证服务名称的唯一性,它的名称是dubbo内部使用的唯一标识-->
    <dubbo:application name="001-link-userservice-provider"/>

    <!--访问服务协议的名称及端口号,dubbo官方推荐使用的是dubbo协议,端口号默认为20880-->
    <!--
        name:指定协议的名称
        port:指定协议的端口号(默认为20880)
    -->
    <dubbo:protocol name="dubbo" port="20880"/>

    <!--
        暴露服务接口->dubbo:service
        interface:暴露服务接口的全限定类名
        ref:接口引用的实现类在spring容器中的标识
        registry:如果不使用注册中心,则值为:N/A
    -->
    <dubbo:service interface="com.song.dubbo.service.UserService" ref="userService" registry="N/A"/>

    <!--将接口的实现类加载到spring容器中-->
    <bean id="userService" class="com.song.dubbo.service.impl.UserServiceImpl"/>

</beans>

```

### 3.创建第二个maven 

#### ①编写pom.xml文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.song.dubbo</groupId>
    <artifactId>002-link-consumer</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--Spring依赖-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>

        <!--dubbo依赖-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo</artifactId>
            <version>2.6.2</version>
        </dependency>

    </dependencies>

</project>

```



#### ②将第一个maven工程进行打包

**因为在第二个maven工程中需要导入第一个的依赖(jar包)**

**也就是,消费者需要用到提供者**

修改第一个maven的pom.xml文件将打包方式改成jar

```xml
<packaging>jar</packaging>
```

打包完成后在改回来

#### ③补全消费者的pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.song.dubbo</groupId>
    <artifactId>002-link-consumer</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--Spring依赖-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>

        <!--dubbo依赖-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo</artifactId>
            <version>2.6.2</version>
        </dependency>

        <!--依赖服务提供者-->
        <dependency>
            <groupId>com.song.dubbo</groupId>
            <artifactId>001-link-userservice-provider</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

    </dependencies>

</project>

```

#### ④编写web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <servlet>
        <servlet-name>dispatcherServlet</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:application.xml,classpath:dubbo-consumer.xml</param-value>
        </init-param>
    </servlet>

    <servlet-mapping>
        <servlet-name>dispatcherServlet</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app>

```

#### ⑤编写spring的配置文件 application.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <!--扫描组件-->
    <context:component-scan base-package="com.song.dubbo.web"/>

    <!--配置注解驱动-->
    <mvc:annotation-driven/>

    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/"/>
        <property name="suffix" value=".jsp"/>
    </bean>

</beans>

```



#### ⑥编写dubbo的配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">

    <!--声明服务消费者的名称:保证唯一性-->
    <dubbo:application name="002-link-consumer"/>

    <!--
        引用远程服务接口:
        id:远程服务接口对象名称
        interface:调用远程接口的全限定类名
        url:访问服务接口的地址
        registry:不使用注册中心,值为:N/A
    -->
    <dubbo:reference id="userService"
                     interface="com.song.dubbo.service.UserService"
                     url="dubbo://localhost:20880"
                     registry="N/A"/>

</beans>

```

#### ⑦编写jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>用户详情</title>
</head>
<body>
<h1>用户详情</h1>
<div>用户标识:${user.id}</div>
<div>用户名称:${user.username}</div>
</body>
</html>

```



#### ⑧编写控制器

```java
package com.song.dubbo.web;

import com.song.dubbo.pojo.User;
import com.song.dubbo.service.UserService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class UserController {

    @Autowired
    private UserService userService;

    @RequestMapping(value = "/user")
    public String userDetail(Model model, Integer id) {

        User user = this.userService.queryUserById(id);
        model.addAttribute("user",user);
        return "userDetail";
    }
}
```

# 3、注册中心

## 3.1、什么是注册中心

​	对于服务提供方，它需要发布服务，而且由于应用系统的复杂性，服务的数量、类型也不断膨胀；对于服务消费方，它最关心如何获取到它所需要的服务，而面对复杂的应用系统，需要管理大量的服务调用。

​	而且，对于服务提供方和服务消费方来说，他们还有可能兼具这两种角色，即需要提供服务，有需要消费服务。通过将服务统一管理起来，可以有效地优化内部应用对服务发布/使用的流程和管理。服务注册中心可以通过特定协议来完成服务对外的统一。Dubbo 提供的注册中心有如下几种类型可供选

> Multicast 注册中心：组播方式
>
> Redis 注册中心：使用 Redis 作为注册中心
>
> Simple 注册中心：就是一个 dubbo 服务。作为注册中心。提供查找服务的功能。
>
> Zookeeper 注册中：使用 Zookeeper 作为注册中心

​	推荐使用 Zookeeper 注册中心。

​	Zookeeper 是 Apacahe Hadoop 的子项目，是一个树型的目录服务，支持变更推送，适合作为 Dubbo 服务的注册中心，工业强度较高，可用于生产环境，并推荐使用。

​	Zookeeper 就像是 windows 的资源管理器，包含了所有的文件。都可以在这里找到。服务提供者和服务消费者，都在注册中心登记。服务消费者使用的访问地址不用写死。而且注册中心使用“心跳”机制更新服务提供者的状态。不能使用的服务提供者会自动从注册中心删除。服务提供者不会调用不能使用的服务。

## 3.2注册中心是什么？

> ​	Zookeeper 是一个高性能的，分布式的，开放源码的分布式应用程序协调服务。简称 zk。Zookeeper 是翻译管理是动物管理员。可以理解为 windows 中的资源管理器或者注册表。他是一个树形结构。这种树形结构和标准文件系统相似。ZooKeeper 树中的每个节点被称为Znode。和文件系统的目录树一样，ZooKeeper 树中的每个节点可以拥有子节点。每个节点表示一个唯一服务资源。Zookeeper 运行需要 java 环境。

![](D:\Power\Dubbo\imgs\注册中心.png)

## 3.3注册中心Zookeeper 怎么用

### Zookeeper下载

官网下载地址: http://zookeeper.apache.org/

进入官网地址，首页找到下载地址，现在稳定版本是 3.4.10

![](D:\Power\Dubbo\imgs\Zk下载1.png)

选择最下面的

![](D:\Power\Dubbo\imgs\Zk下载3.png)

![](D:\Power\Dubbo\imgs\Zk下载4.png)

![](D:\Power\Dubbo\imgs\Zk下载5.png)

### win下面的配置

下载的文件 zookeeper-3.4.10.tar. 解压后到目录就可以了，例如 d:/servers/ zookeeper-3.4.10修改 zookeeper-3.4.10/conf/ 目录下配置文件

![](D:\Power\Dubbo\imgs\zk配置.png)

复制 zoo-sample.cfg 改名为 zoo.cfg

文件内容：

![](D:\Power\Dubbo\imgs\zk配置2.png)

> tickTime: 心跳的时间，单位毫秒. Zookeeper 服务器之间或客户端与服务器之间维持心跳的时间间隔，
>
> ​		也就是每个 tickTime 时间就会发送一个心跳。表明存活状态。
>
> 
>
> dataDir: 数据目录，可以是任意目录。存储 zookeeper 的快照文件、pid 文件，默认为
>
> ​		/tmp/zookeeper，建议在 zookeeper 安装目录下创建 data 目录，
>
> ​		将 dataDir 配置改为/usr/local/zookeeper-3.4.10/data
>
> 
>
> clientPort: 客户端连接 zookeeper 的端口，即 zookeeper 对外的服务端口，默认为 2181
>
> ​	在下面添加一个 admin.serverPort=8888

### Linux配置

#### ①上传压缩包

Linux命令：

> rz

#### ②解压文件

解压文件 zookeeper-3.4.10.tar.gz

执行命令：tar -zxvf zookeeper-3.4.10.tar.gz -C /usr/local/

![](D:\Power\Dubbo\imgs\l1.png)

查看已解压：

![](D:\Power\Dubbo\imgs\l2.png)

> 修改名称：
>
> mv apache-zookeeper-3.4.10-bin zookeeper-3.4.10

#### ④配置文件

> 进入 
>
> cd  zookeeper-3.4.10/
>
> cd conf/

在 zookeeper 的 conf 目录下，将 zoo_sample.cfg 改名为 zoo.cfg，cp zoo_sample.cfg zoo.cfg

zookeeper 启动时会读取该文件作为默认配置文件。

**复制一份zoo_sample.cfg**

> cp zoo_sample.cfg  zoo.cfg

**修改配置文件**

> vim zoo.cfg
>
> 在内部中往clientPort下面添加admin.serverPort=8888



## 3.4基于注册中心入门案例

### zk-interface(简单的java工程)

该模块主要是编写实体类和接口

实体类

```java
package com.song.dubbo.pojo;

import java.io.Serializable;

public class User implements Serializable {

    private Integer id;

    private String username;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }
}

```

接口

```java
package com.song.dubbo.service;

import com.song.dubbo.pojo.User;

public interface UserService {

    /**
     * 根据用户标识获取用户的信息
     * @param id
     * @param username
     * @return
     */
    User queryUserById(Integer id, String username);
}

```

打包成为jar包

### zk-userservice-provider(提供者 web工程)

**这个模块主要是对userService的重写,并将重写类暴露出去**

#### userServiceImpl

```java
package com.song.dubbo.service.impl;

import com.song.dubbo.pojo.User;
import com.song.dubbo.service.UserService;

public class UserServiceImpl implements UserService {

    @Override
    public User queryUserById(Integer id,String username) {
        User user = new User();
        user.setId(id);
        user.setUsername(username);
        return user;
    }
}

```

#### dubbo-zk-userservice-provider.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">
    <!--声明dubbo服务提供者的名称,保证唯一性-->
    <dubbo:application name="007-zk-userservice-provider"/>

    <!--声明dubbo使用的协议名称和端口好-->
    <dubbo:protocol name="dubbo" port="20880"/>

    <!--现在使用zookeeper注册中心-->
    <!--指定注册中心地址和端口号-->
    <dubbo:registry address="zookeeper://localhost:2181"></dubbo:registry>
    
    <!--暴露服务接口-->
    <dubbo:service interface="com.song.dubbo.service.UserService" ref="userServiceImpl"/>
    <!--加载接口是西安类-->
    <bean id="userServiceImpl" class="com.song.dubbo.service.impl.UserServiceImpl"></bean>
</beans>

```

#### web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:dubbo-zk-userservice-provider.xml</param-value>
    </context-param>
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>

</web-app>

```

#### pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>007-zk-userservice-provider</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--Spring依赖-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>

        <!--Dubbo依赖-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo</artifactId>
            <version>2.6.2</version>
        </dependency>

        <!--接口工程依赖-->
        <dependency>
            <groupId>com.song.dubbo</groupId>
            <artifactId>006-zk-interface</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

        <!--zookeeper依赖-->
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-framework</artifactId>
            <version>4.1.0</version>
        </dependency>
    </dependencies>

</project>

```

### zk-consumer(消费者 web工程)

**这个模块就是功能的调用**

#### pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.song.dubbo</groupId>
    <artifactId>008-zk-consumer</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--Spring依赖-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>

        <!--Dubbo依赖-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>dubbo</artifactId>
            <version>2.6.2</version>
        </dependency>

        <!--接口工程依赖-->
        <dependency>
            <groupId>com.song.dubbo</groupId>
            <artifactId>006-zk-interface</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

        <!--zookeeper依赖-->
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-framework</artifactId>
            <version>4.1.0</version>
        </dependency>
    </dependencies>

</project>

```

#### applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <!--扫描组件-->
    <context:component-scan base-package="com.song.dubbo.web"/>

    <!--配置注解驱动-->
    <mvc:annotation-driven/>

    <!--视图解析器-->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/"/>
        <property name="suffix" value=".jsp"/>
    </bean>
</beans>

```

#### dubbo-zk-consumer.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">

    <!--声明dubbo服务消费者名称:保证唯一性-->
    <dubbo:application name="008-zk-consumer"/>

    <!--指定注册中心-->
    <dubbo:registry address="zookeeper://localhost:2181"/>
    <!--使用linux系统中的zookeeper服务-->
<!--    <dubbo:registry address="zookeeper://192.168.153.100:2181"/>-->

    <!--引用远程接口服务-->
    <dubbo:reference id="userService" interface="com.song.dubbo.service.UserService"/>

</beans>

```

#### web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">


    <servlet>
        <servlet-name>dispatcherServlet</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:applicationContext.xml,classpath:dubbo-zk-consumer.xml</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>dispatcherServlet</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app>

```

#### UserContoller

```java
package com.song.dubbo.web;

import com.song.dubbo.pojo.User;
import com.song.dubbo.service.UserService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class UserController {

    @Autowired
    private UserService userService;

    @RequestMapping(value = "/userDetail")
    public String userDetail(Model model, Integer id, String username) {
        User user = userService.queryUserById(id, username);
        model.addAttribute("user",user);
        return "userDetail";
    }
}

```

#### jsp

```jsp
<html>
<head>
    <title>用户详情</title>
</head>
<body>
<div>用户编号:${user.id}</div>
<div>用户姓名:${user.username}</div>
</body>
</html>

```

## 3.5版本号



```xml
<!--不管是否一个接口有多个实现类,只要服务提供者服务接口服务的时候指定了版本号,那做为消费者引用远程接口服务的时候就必须指定版本号-->
<dubbo:service interface="com.bjpowernode.dubbo.service.UserService"ref="userServiceImpl" version="1.0.0" timeout="15000" />

<dubbo:service interface="com.bjpowernode.dubbo.service.UserService" ref="userServiceImpl2" version="2.0.0"/>

<!--注意这是两个不同的实现类-->
<bean id="userServiceImpl" class="com.bjpowernode.dubbo.service.impl.UserServiceImpl"/>
<bean id="userServiceImpl2"class="com.bjpowernode.dubbo.service.impl.UserServiceImpl2"/>
```

```java
    @Autowired
    private UserService userService;//UserServiceImpl

    @Autowired
    private UserService userService2;//UserServiceImpl2

    @RequestMapping(value = "/userDetail")
    public String userDetail(Model model,Integer id,String username) {

        User user = userService.queryUserById(id, username);

        User user2 = userService2.queryUserById(id,username);

        model.addAttribute("user",user);
        model.addAttribute("user2",user2);

        return "userDetail";
    }
```

