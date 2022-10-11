# 第一章代理模式

## 1.什么是代理模式

- 代理模式是指，为其他对象提供一种代理以控制对这个对象的访问。在某些情况下， 一个对象不适合或者不能直接引用另一个对象，而代理对象可以在客户和目标对象之间起到中介的作用。
- 换句话说，使用代理对象，是为了在不修改目标对象的基础上，增强主业务逻辑。客户类真正的想要访问的对象是目标对象，但客户类真正可以访问的对象是代理对象。
- 客户类对目标对象的访问是通过访问代理对象来实现的。当然，代理类与目标类要实现同一个接口。
- 例如：
  - 生活中：
    - 房东		=====>目标对象
      房屋中介 =====>代理对象
      你，我 	=====>客户端对象
    - 服务生产厂          ===>目标对象
      门店(旗舰店)        ===>代理对象
      你,我               ===>客户端
  - 开发中：
    - 运营商(电信,移动,联通)      ====>目标对象
      第三方公司                  	====>代理对象
      开发的应用程序需要发送短信的功能  ===>客户端
      开发的应用程序需要支付的功能
  - 图解：
    - ![](图\JDK代理\1.什么是代理模式.png)
    - Window 系统的快捷方式也是一种代理模式。快捷方式代理的是真实的程序，双击快捷方式是启动它代表的程序。

## 2.代理模式的作用

1. 控制目标对象的访问
2. 增强功能

## 3.代理模式的分类

1. 静态代理
2. 动态代理,
   - 又为JDK动态代理,
   - CGLib动态代理(子类代理)

## 4.代理的实现方法

1. 静态代理实现
2. 动态代理的实现又分为 JDK 动态代理和 CGLib 动态代理

# 第二章静态代理

## 1.静态代理的特点

- 目标对象和代理对象实现同一个业务接口
- 目标对象必须实现接口
- 代理对象在程序运行前就已经存在
- 能够灵感的进行目标对象的切换,却无法进行功能的灵活处理(使用动态代理解决此问题)
-  静态代理要求目标对象和代理对象实现同一个业务接口。代理对象中的核心功能是由目标对象来完成，代理对象负责增强功能。

## 2.静态代理的实现

### 业务需求：

- 业务功能:请明星进行节目表演.
  - 明星刘德华:目标对象(无法直接访问)
  - 刘德华助理:代理对象(我们可以访问,他还可以跟明星对接)
  - 我们 :客户端对象
- 图解：
  - ![](图\JDK代理\2.业务需求.png)

### 实现步骤：

#### 1.定义业务接口

- ```java
  public interface Service {
      //规定得唱歌得业务功能
      void sing();
  }
  ```

  

#### 2.目标类实现接口(明星刘德华)

- ```java
  /**
   * 目标对象:刘德华,实现业务接口中得功能,进行唱歌表演
   *	目标类和代理类应该实现同一个接口
   */
  public class SuperStarLiu  implements Service {
      @Override
      public void sing() {
          System.out.println("我是刘德华,我正在表演唱歌");
      }
  }
  
  ```

  

#### 3.代理类实现接口(代理对象)

- ```java
  public class Agent implements Service{
      @Override
      public void sing(){
          System.out.println("预定时间........");
          System.out.println("预定场地........");
          SuperStarZhou Zhou=new SuperStarZhou();
          Zhou.sing();
          System.out.println("结算费用........");
      }
  }
  ```

  

#### 4.测试

- ```java
  /*
  要导入junit包 这里用maven就行
  */
  public class MyTest {
      @Test
      public void testAgent1(){//方法名前加test这是规范
          //这里不能直接new SuperStarLiu的对象 要new 代理的对象
          //可以理解成 我们想让刘德华来唱歌 必须找他的代理 直接找刘德华基本不可能
          Agent agent=new Agent();
          agent.sing();    
      }
      
      //改造上面的testAgent1
      public void testAgent2(){
          //有接口和实现类,必须使用接口指向实现类(规范)多态
          Service agent=new Agent();
          agent.sing();
      }
  }
  ```

  

#### 5.代理功能改造(面向接口编程--重要)

- 类中的成员变量设计为接口,方法的形参设计为接口,方法的返回值设计为接口,调用时接口指向实现类.

  - 代理对象(助理)

    - ```java
      public class Agent implements Service {
          //类中的成员变量设计为接口
          public Service target;
          //传入目标对象,方法的参数设计为接口
          public Agent(Service target){
              /*
              这里如果传入的是一个 Liu:
              	对象为:Service target=Liu
              如果传入的是一个 Zhou:
              	对象为：Service target=Zhou
              这个时候调用方法sing()的时候 就是重写以后的方法
              */
              this.target=target;
          }
          @Override
          public void sing() {
              System.out.println("预定时间........");
              System.out.println("预定场地........");
              //切记切记：业务功能功能必须由目标对象亲自实现
              //面向接口编程,调用时 接口指向实现类
              target.sing();
              System.out.println("结算费用........");
          }
      }
      ```

  - 客户对象(测试类)

    - ```java
          public void testAgent1(){
              Service agent=new Agent(new SuperStarLiu());
              agent.sing();
          }
      ```

## 3.静态代理的缺陷

### 代理复杂，难于管理

代理类和目标类实现了相同的接口，每个代理都需要实现目标类的方法，这样就出现了大量的代码重复。如果接口增加一个方法，除了所有目标类需要实现这个方法外，所有代理类也需要实现此方法。增加了代码维护的复杂度

### 代理类依赖目标类，代理类过多

代理类只服务于一种类型的目标类，如果要服务多个类型。势必要为每一种目标类都进行代理， 静态代理在程序规模稍大时就无法胜任了，代理类数量过多

# 第三章动态代理

## 1.什么是动态代理

### 1.什么是动态代理

动态代理是指代理类对象在程序运行时由 JVM 根据反射机制动态生成的。动态代理不需要定义代理类的.java 源文件。动态代理其实就是 jdk 运行期间，动态创建 class 字节码并加载到 JVM。动态代理的实现方式常用的有两种：使用 JDK 动态代理和 CGLIB 动态代理。

### 2.动态代理的特点

1.  代理对象在程序运行的过程中动态在内存构建.可以灵活的进行业务功能的切换.
2.  目标对象必须实现业务接口
3.  JDK代理对象不需要实现业务接口
4.  JDK动态代理的对象在程序运行前不存在.在程序运行时动态的在内存中构建
5.  JDK动态代理灵活的进行业务功能的切换
6.  本类中的方法(非接口中的方法)不能被代理

## 2.JDK动态代理

### 1.什么是JDK动态代理

- JDK动态代理是基于 Java 的反射机制实现的。
- 使用 JDK中接口和类实现代理对象的动态创建。
- JDK的动态代理要求目标对象必须实现接口，而代理对象不必实现业务接口，这是 java 设计上的要求。
- 从 jdk1.3 以来，java 语言通过 java.lang.reflect 包提供三个类和接口支持代理模式，它们分别Proxy, Method和 InvocationHandler。

### 2.InvocationHandler接口

1. InvocationHandler 接口叫做调用处理器，负责完成调用目标方法，并增强功能。

2. 通过代理对象执行目标接口中的方法 ， 会把方法的调用分派给调用处理器(InvocationHandler)的实现类，执行实现类中的 invoke()方法，我们需要把功能代理写在 invoke（）方法中 。

3. 此接口中只有一个方法。在调用的时候我们采用匿名内部类的形式

   - ```java
     public interface InvocationHandler{
         public Object invoke(Object proxy,Method method,Object args) throws Throwable;
     }
     ```

   - 在 invoke 方法中可以截取对目标方法的调用。在这里进行功能增强。

   - Java 的动态代理是建立在反射机制之上的。实现了 InvocationHandler 接口的类用于加强目标类的主业务逻辑

   - 这个接口中有一个方法 invoke()，具体加强的代码逻辑就是定义在该方法中的。通过代理对象执行接口中的方法时，会自动调用 invoke()方法。

   - invoke()方法的介绍如下：

     - ```java
       public Object invoke ( Object proxy, Method method, Object[] args){
           //proxy:代表生成的代理对象
           //method:代表目标对象
           //args:代表目标方法的参数
           //第一个参数 proxy 是 jdk 在运行时赋值的，在方法中直接使用，第二个参数后面介绍，第三个参数是方法执行的参数， 这三个参数都是 jdk 运行时赋值的，无需程序员给出。
          
       }
       ```

       

### 3.Method类

1. invoke()方法的第二个参数为 Method 类对象，该类有一个方法也叫 invoke()，可以调用目标方法。这两个 invoke()方法，虽然同名，但无关。

2. ```
   public Object invoke ( Object obj, Object... args):
       obj：表示目标对象
       args：表示目标方法参数，就是其上一层 invoke 方法的第三个参数
   ```

3. 该方法的作用是：调用执行 obj 对象所属类的方法，这个方法由其调用者 Method 对象确定。也可以理解为：method==sing(),show()。

4. 在代码中，一般的写法为:method.invoke(target, args);==>手工调用目标方法  sing();   show();

### 4.Proxy类

1. 通过JDK的java.lang.reflect.Proxy类实现动态代理，会使用其静态方法newProxyInstance()，依据目标对象、业务接口及调用处理器三者，自动生成一个动态代理对象。

2. ```java
   public static Object newProxyInstance ( 
       ClassLoader loader,
       Class<?>[] interfaces,
   InvocationHandler handler
   ){
       .....
   }
   //loader：目标类的类加载器，通过目标对象的反射可获取
   //interfaces：目标类实现的接口数组，通过目标对象的反射可获取
   //handler：调用处理器。
   ```

   

### 5.实现代码

```java
public class ProxyFactory{
    //类中的成员变量设计为接口,目标对象
    Service target;
    //传入目标对象
    public ProxyFactory(Service target){
        this.target=target;
    }
    //返回动态代理对象
    public Object getAgent(){
        return Proxy.newProxyInstance(
            //ClassLoader loader, 类加载器,完成目标对象的加载
            target.getClass().getClassLoader(),
            //Class<?>[] interfaces,目标对象实现的所有接口
            target.getClass().getInterfaces(),
             //InvocationHandler h,实现代理功能的接口 ,我们传入的是匿名内部实现
          	new InvocationHandler() {
                public Object invoke(
                    //创建代理对象
                    Object proxy,
                    //method就是目标方法sing(),show()
                    Method method,
                    //目标方法的参数
                    Object[] args) throws Throwable{
                          //代理功能
                          System.out.println("预订时间........");
                          //代理功能
                          System.out.println("预订场地........");
                          //主业务功能实现
                          //target.sing();还是写死了方法的调用, 不成
                          //sing(),show(),one()
                          Object obj = method.invoke(target,args);
                          //代理功能
                          System.out.println("结算费用........");
                          return obj;  //切记:这个是目标方法的返回值
                }               
            }  
        );
    }
}
```

 注意：JDK动态代理中，代理对象不需要实现接口，但是目标对象一定要实现接口，否则不能用JDK动态代理。

## 3.CGLib动态代理

### 1.什么是CGLib动态代理

1. 又称为子类.通过动态的在内存中构建子类对象,重写父类的方法进行代理功能的增强.
2. 如果目标对象没有实现接口,则只能通过CGLib子类代理来进行功能增强. 

3. 子类代理是对象字节码框架ASM来实现的.

### 2.CGLib动态代理的代码实现

- 目标对象不使用接口

  - ```java
    public class SuperStarLiu {
        public void sing(){
            System.out.println("我是刘德华,我正在表演........");
        }
    }
    ```

- 子类:

  - ```java
    public class SubSuperStarLiu extends SuperStarLiu {
        //重写父类的方法,进行增强功能
        @Override
        public void sing() {
            //子类完成代理功能
            System.out.println("预订时间...........");
            //子类完成代理功能
            System.out.println("预订场地...........");
    
            //父类实现自己的业务功能
            super.sing();
    
            //子类完成代理功能
            System.out.println("结算费用...........");
        }
    }
    ```

- 测试类:

  - ```java
    public class MyTest {
        @Test
        public void testAgent(){
            SuperStarLiu liu = new SubSuperStarLiu();
            liu.sing();
        }
    }
    
    ```

    