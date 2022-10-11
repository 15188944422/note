# 第一章java概述

## 1.常用的DOS命令(Win+R输入cmd开打)

### 1.1什么是DOS命令

在DOS命令窗口中才可以输入并执行DOS命令。

在最初的windows计算机中没有图形界面的，只有DOS命令窗口。

也就是说通过执行DOS命令窗口可以完全完成文件的新建、编辑、保存、删除等一系列操作。

### 1.2新建文件夹

> mkdir **

### 1.3切换盘符或目录

> cmd 默认打开的是 C:\Users\用户名 这个目录

- 切换盘符
  - 直接进入盘符即可：例如:进入d盘 在cmd命令窗口上大 `d:`回车即可 
- 切换目录
  - 使用cd命令来完成目录的切换：cd是什么含义？change directory（改变目录）
  - cd命令怎么用，语法格式是什么？---`cd 路径`
  - cd .. 回到上一级
  - cd \ 直接回到根路径
  - . 一个点,代表当前路径
- 路径在windows上也分绝对路径和相对路径
  - 相对路径:相对路径一定是从当前位置作为起点开始找。
  - 绝对路径：在windows操作系统中凡是路径起点是盘符的都是绝对路径

### 1.4常用的DOS命令

- cls 清屏
- dir 查看当前目录下有什么
- exit 退出DOS命令窗口
- del 删除一个或者多个文件
  - 删除一个:`C:\Users\Administrator>del T1.class`
  - 删除多个:`C:\Users\Administrator>del *.class`
- 查看个人的IP地址
  - `ipconfig（ip地址的配置信息。）`
  - `ipconfig /all`该命令后面添加一个/all参数可以查看更详细的网络信息。
- 怎么查看两台计算机是否可以正常通信
  - ping命令:
  - 语法: ping IP地址

## 2java编程语言介绍

### 2.1什么是Java

Java是1995年美国的Sun公司（Stanford University Network/斯坦福大学网络公司）推出的一门面向对象的**高级编程语言**

> 那什么是面向对象呢？
>
> 是把构成问题事务分解成各个对象，建立对象的目的不是为了完成一个步骤，而是为了描述某事物在整个解决问题的步骤中的行为。

### 2.2Java的发展史

- 1995年Sun公司发布Java1.0版本
- 1997年发布Java 1.1版本
- 1998年发布Java 1.2版本
- 2000年发布Java 1.3版本
- 2002年发布Java 1.4版本
- **2004年发布Java 1.5版本**
- 2006年发布Java 1.6版本
- 2009年Oracle甲骨文公司收购Sun公司，并于2011发布Java 1.7版本
- **2014年发布Java 1.8版本**
- 2017年发布Java 9.0版本
- 2018年3月发布Java10.0版本
- **2018年9月发布Java11版本**
- 2019年3月发布Java12版本
- 2019年9月发布Java13版本
- 2020年7月发布Java14版本
- 2021年1月发布Java15版本

> 尽管出现了新版本，Java 8仍然是最受欢迎的。它被四分之三的Java开发人员使用。Java  11越来越流行。与去年相比，它的使用率增加了10个百分点。更新的Java 12和Java  13很快就找到了它们的受众。在我们调查的开发者中，有10%或更多的人经常使用它们。

### 2.3Java的平台

Java 平台有三个版本，这使软件开发人员、服务提供商和设备生产商可以针对特定的市场进行开发；

- Java SE（Java Platform，Standard Edition）：标准版（基础，要学java，必须先学习SE。基础语法+基础库）
- Java EE（Java Platform，Enterprise Edition）：企业版（专门为企业开发软件，为企业提供解决方案。例如：OA办公系统，保险行业的系统，金融行业的系统，医院系统....）
- Java ME（Java Platform，Micro Edition）：微型版（专门为微型设备做嵌入式开发的。）

## 3.Java语言的特性

1. 简单性
   -   Java语言的语法简单明了，容易掌握，而且是纯面向对象的语言。Javra 语言的简单性主要体现在以下几个方面:
   -   语法规则和 C++类似。从某种意义上讲，Java 语言是由C和C++语言转变而来的，所以C程序设计人员可以很容易地掌握Java语言的语法。
   -   Java语言对C++进行了简化和提高。例如，Java 使用接口取代了多重继承，并取消了指针，因为指针和多重继承通常使程序变得复杂。Java 语言还通过垃圾自动收集，大大简化了程序设计人员的资源释放管理工作。
   -   Java提供了丰富的类库、API 文档以及第三方开发包，另外还有大量基于Java的开源项目。JDK (Java开发者工具箱)已经开放源代码，读者可以通过分析项目的源代码，提高自己的编程水平。
2. 面向对象:
   - 面向对象是Java语言的基础，也是Java语言的重要特性，它本身就是一种纯面向对象的程序设计语言
   - Java提倡万物皆对象，语法中不能在类外面定义单独的数据和函数，也就是说，Java语言最外部的数据型是对象，所有的元素都要通过类和对象来访问。
3. 健壮性
   - 主要是因为Java中有一种机制：自动垃圾回收机制（GC机制）。
   - java语言是健壮的，相对于C语言来说，C语言没有Java健壮。
   - Java不容易导致内存的泄漏。C++或者C语言使用不当时很容易导致内存泄漏。
4. java完全/完美支持多线程并发。
5. 可移植性/跨平台
   - 只要Java语言编写了一次,就可以在各个系统上去运行(Windows、Linux、mac)

## 4.JVM，JDK，JRE三者的关系

- **JDK (Java Development Kit)**：是Java程序开发工具包，包含 JRE 和开发人员使用的工具；
- **JRE (Java Runtime Environment)** ：是Java程序的运行时环境，包含 JVM 和运行时所需的核心类库；
- **JVM（Java Virtual Machine ）**：是一款Java虚拟机，模拟Java运行时的一个平台，对内存分配，管理、线程调度等都有一定的管理；

> JDK包括JRE，JRE包括JVM。
>
> JVM是不能独立安装的。JRE和JDK都是可以独立安装的。
>
> 有单独的JDK安装包。也有单独的JRE安装包。
>
> 没有单独的JVM安装包。
>
> 安装JDK的时候：JRE就自动安装了，同时JRE内部的JVM也就自动安装了。
>
> 安装JRE的时候：JVM也就自动安装了。
>
> 问题：
> 假设你在软件公司开发了一个新的软件，现在要去客户那边给客户把
> 项目部署一下，把项目跑起来，你需要安装JDK吗？
>    只需要安装JRE就行了。
>    JRE体积很小，安装非常便捷快速



## 5.搭建开发环境并编写第一个java代码

### 5.1搭建开发环境

1. 下载JDK,[进入官网](https://www.oracle.com/java/)

   ![](https://foruda.gitee.com/images/1664252452469852555/f36d5128_10637153.png)

2. 下载JDK

   ![](https://foruda.gitee.com/images/1664253111009344508/0378ac84_10637153.png)

   ![](https://foruda.gitee.com/images/1664253059646469616/9eb8224d_10637153.png)

3. 下载的JDK找一个目录命名为java解压就可以(之前下载过了,所有就使用的 17.0.1的版本)

   ![](https://foruda.gitee.com/images/1664253089867736830/fa0540ca_10637153.png)

4. 之后我们需要配置环境变量,"我的电脑"打开属性选项,

   ![](https://foruda.gitee.com/images/1664253131411012363/82d035a0_10637153.png)

5. 之后点击高级系统设置

   ![](https://foruda.gitee.com/images/1664253139267119146/3df0e749_10637153.png)

6. 之后点击环境变量

   ![](https://foruda.gitee.com/images/1664253147725310375/dea27135_10637153.png)

7. 之后 我们要在"系统环境"中,配置java的环境

   - 配置 JAVA_HOME 这个要新建

     - 这个就是你解压JDK的目录 `C:\Program Files\java\jdk-17.0.1`
     - ![](https://foruda.gitee.com/images/1664253165744648515/466d434d_10637153.png)

   - 点击选中Path变量，之后点击编辑。配置Path环境变量 

     新建之后编写上 "%JAVA_HOME%\bin"

     ![](https://foruda.gitee.com/images/1664253184555171349/f2503dba_10637153.png)

8. 之后 打开cmd命令窗口 输入`java -version` 查看java的版本 保证配置成功

### 5.2编写Java代码

Java开发环境已经搭建完毕，可以开发我们第一个Java程序了。

新建一个HelloJava.java的文件,并且编写代码：

```java
public class HelloJava{
	public static void main(String[] args){
		System.out.println("2022-9-26：Hello Java！！！");
	}
}

```

<font color="#dd0000">注意:文件名要和类名(public class 后面的)保持一致！！</font>

### 5.3编译Java程序

在DOS命令行中，进入Java源文件的目录，使用`javac`命令进行编译。

格式如下：

​	`javac Java源文件名.后缀名`

示例：

​	`javac HelloWorld.java`



编译：

​	![](https://foruda.gitee.com/images/1664253100138104615/45316904_10637153.png)



运行:	

```cmd
2022-9-26：Hello Java！！！
```



### 5.4编译和运行

java程序非常重要的两个阶段：编译阶段和运行阶段

- **编译**：是指将我们编写的Java源文件翻译成JVM认识的class文件，在这个过程中， javac 编译器会检查我们

  所写的程序是否有错误，有错误就会提示出来，如果没有错误就会编译成功。

- **运行**：是指将 class文件 交给JVM去运行，此时JVM就会去执行我们编写的程序了

到这里第一章的java概述就结束啦

# 第二章java标识符和关键字

**标识符和关键字的定义：计算机处理的对象就是数据，而数据了解标识符和关键字。标识符就是用来标识实体的号，可以用来标识变量名，函数名和对象名等；关键字就是程序发明者规定的有特殊含义的单词，又叫保留字。**

## 标识符

1. 标识符是用来标识变量、函数、类、模块，或者任何其他用户自定义项 目的名称，用它来命名程序正文中的一些实体，比如函数名、变量名、类名、对象名等。

   ```java
   类名：public class biaoshifu{} //这里面的biaoshifu就是类名
   方法名：public static void main(String [] args) //这里面的main就是方法名
   变量名：int  a=100;//这里的a就是变量名
   ```

2. 命名规则(必须)：

   - 标识符只能由数字、字母、下划线、美元符号$组成
   - 标识符不能以数字开头
   - 关键字不能为标识符
   - 关键字是严格区分大小写的
   - 虽然java中的标识符严格区分大小写，但对于类名来说，如果一个java文件中同时出现了A类和a类那么在前就生成谁

3. 标识符的命名规范(非必须)

   - 规范一：见名之意
   - 规则二：遵循驼峰命名方式（一高一低）--BiaoShiFuTest
   - 规则三：类名、接口名有特殊要求--类名和接口名首字母大写，后面每个单词首字母大写
   - 规则四：变量名、方法名有特殊要求--变量名和方法首字母小写，后面的每个单词首字母小写
   - 规则五：所有常量名全部大写并且单词与单词之间采用下划线衔接

> 题目：
> 创建一个123.java文件可以嘛？---是可以的，因为123并不是标识符
>
> 在123.java文件中定义一个public类可以嘛？    
> 		不可以，因为在public类中，类名和文件名保持一致文件名为123 所以不行

## 关键字

1. 什么是关键字？
   - 在SUN公司开发Java语言的时候，提前定义好了一些具有特殊含义的单词，这些单词全部小写，具有特殊含义，不能用作标识符。

> 关键字都有那些呢(不需要花大量的时间去记)？
>
> public、static、void、class、byte......



# 第三章变量和数据类型

## 变量

1. 什么是变量呢？

   - 变量就是一个存数据盒子。（盒子大小谁来决定啊？数据类型。变量存储什么样的数据？数据类型决定）
     在内存中的最基本的存储单元。
     存数据用的，而且这个数据是可变的，所以叫做变量。

2. 变量的使用

   - 变量的三要素?  数据类型、变量名、值  （值就是数据，就是字面量。）

     ```java
     int i = 100;
     ```

   - java中的变量必须先声明，再赋值才能访问（必须手动赋值。）

     ```java
     int k; 
     System.out.println(k);// 这样是不行的。
     ```

   - 可以在一行上声明多个变量：

     ```java
     int a, b, c = 100;//c变量赋值100，a,b变量只声明了没有赋值。
     int a = 10, b = 20, c = 100;//可以这样每个都赋值。
     ```

   - 当然声明和赋值也可以分开做

     ```java
     int i;
     i=100;
     System.out.println(i);//100
     ```

   - 在"同一个域"中,变量名不可重复，

     - 但可以重新赋值

       ```java
       {
       	int i=100;
           double i=200.0;//重名了编译器会报错，不允许。
           i = 300; // 可以重新赋值。
       }
       ```

   - 那到底什么是一个域呢？

     - 目前解释不了,什么是一个域只需要记住一个大括号是一个域

       ```java
       {A域
       	{B域
       		{C域
       		}
       	}
       }
       A域包括B域，B域包括C域。
       ```

3. 变量的分类--根据位置进行分类：记住就行

   - 在方法体当中声明的变量叫做局部变量。

     ```java
     public static void m1(){
         //局部变量，方法执行结束之后内存释放。
         int k = 100;
     	int i = 200;
     }
     ```

   - 在方法体外以及类体内声明的变量叫做成员变量。

     ```java
     public class T{
         // 成员变量
     	int i = 200;
         
     	public static void x(){
     		//局部变量，方法执行结束之后内存释放。
         	int k = 100;
     	}
     	
     }
     ```

4. 变量的作用域--出了大括号就不认识了。别的先别管。
   <font color="red">java中有一个重要原则，那个变量离的近 就用那个</font>

   ```java
   {
   	int i = 100;
   	{
   		在这里可以访问i
   	}
   }
   
   {
   	在这里是无法访问i变量。
   }
   ```

## 数据类型

**数据类型分为基本数据类型和引用数据类型**

### 基本数据类型(包含类型转换)

| 数据类型     | 关键字         | 内存占用 | 取值范围               |
| ------------ | -------------- | -------- | ---------------------- |
| 字节型       | byte           | 1个字节  | -128~127               |
| 短整型       | short          | 2个字节  | -32768~32767           |
| 整型         | int（默认）    | 4个字节  | -2147483648~2147483647 |
| 长整型       | long           | 8个字节  | -2的63次方~2的63次方-1 |
| 单精度浮点数 | float          | 4个字节  | 1.4013E-45~3.4028E+38  |
| 双精度浮点数 | double（默认） | 8个字节  | 4.9E-324~1.7977E+308   |
| 字符型       | char           | 2个字节  | 0-65535                |
| 布尔类型     | boolean        | 1个字节  | true，false            |

> Java中的默认类型：整数类型是 int 、浮点类型是 double；
>
> ```java
> /*
> 在java中有一条重要的结论：在任何情况下，整数型的字面量/数据默认被当作int类型数据
> 如果字面量希望被当作long数据类型来处理，需要在字面量后面加上一个L
> */
> 
> public static void main(String[] args) {
>      //200这个字面量默认当作int类型来处理
>      //b变量是long类型，int类型占4个，long类型占8个
>      //小容量可以自动转化成大容量，这种操作被称为：自动类型转换
>      long b=200;
> 
>      System.out.println(b);
> 
>      long c=300L;
>      System.out.println(c);
>  	// int i=2147483648;
>      //在java中，整数型字面量一上来编译器就会将它看做int
>      //而2147483648超出了int范围，所以在没有编译之前就出错
>      //报错愿意 操作太大
>      //long d=2147483648;
>      //解决
>      long d=2147483648L;
>      System.out.println(d);
>  }
> ```
>
> 

对于这些基本数据类型有一些转换规则:

- 第一条：八种基本数据类型中，除 boolean 类型不能转换，剩下七种类型之间都可以进行转换

- 第二条：如果整数型字面量没有超出 byte,short,char 的取值范围，可以直接将其赋

- 第三条：小容量向大容量转换称为自动类型转换，容量从小到大的排序为：
  byte < short(char) < int < long < float < double，
  其中 short和 char都占用两个字节，但是char 可以表示更大的正整数；

- 第四条：大容量转换成小容量，称为强制类型转换，编写时必须添加“强制类型转换符”，
  但运行时可能出现精度损失，谨慎使用；
  强制类型转换规则:数据类型 变量名 = (数据类型)被转数据值;

- 第五条：byte,short,char 类型混合运算时，先各自转换成 int 类型再做运算；

- 第六条：多种数据类型混合运算，各自先转换成容量最大的那一种再做运算；

  

> 综合
>
> 8种数据类型boolean类型不能转换，其他七种类型之间都可以进行转换
>
> 如果整数型字面量没有超出byte short char的取值范围，可以之间将其赋值
>
> 小容量向大容量转换称为自动类型转换，容量从小到大的排序为：
>
> byte<short(char)<int<long<float<double其中short和char都占两个字节，但char可以表示更大的正整数。
> 大容量转小容量称为自动类型转换
>
> byte short char类型混合运算是，各自先转换成int类型
>
> 多种数据类型转换运算，各自转换成容量最大的哪一种运算

综合代码示例：

自动类型转换:将**取值范围小**的类型 自动提升为**取值范围大**的类型 

```java
//范围小的类型向范围大的类型提升，byte、short、char 运算时直接提升为 int ；
public class demo2 {
    public static void main(String[] args) {
        System.out.println("int类型和byte类型进运算");
        // 一个 int 类型和 byte类型 进行相加
        int a = 1;
        byte b = 2;
        //运算结果3，变量的类型将是 int 类型，这就是出现了数据类型的自动类型转换现象。
        System.out.println(a + b);
        //byte x=a+b;报错 int类型和byte类型运行,结果是int类型
        int y= a+b;
        System.out.println(y);

        System.out.println("==============================================");
        
        //当一个 int 类型变量和一个 double 变量运算时， int 类型将会自动提升为 double 类型进行运算
        System.out.println("int类型和double类型进运算");
        int p=1;
        double q=1.5;

        //int x=p+q;这样会报错 因为 自动类型转换 运算结果是向范围大的进行转换
        double z=p+q;


    }
}
```

强制类型转换:将 取值范围大的类型 强制转换成 取值范围小的类型；比较而言，自动转换是Java自动执行的，而制转换需要我们自己手动执行。





### 引用数据类型

> 字符串型String属于引用数据类型。
> String字符串不属于基本数据类型范畴。
> java中除了基本数据类型之外，剩下的都是引用数据类型。
> 引用数据类型后期面向对象的时候才会接触。

String类型使用：

```java
public class Demo3 {
    public static void main(String[] args) {

        String str1="hello~";

        String str2="你好啊~";

        String str3="嘿嘿~";

        System.out.println(str1);
        System.out.println(str2);
        System.out.println(str3);
    }
}

```

# IDEA工具的安装

**工欲善其事，必先利其器。要想快速的编写代码,必须有一个好的编译软件，idea[下载官网](https://www.jetbrains.com/idea/)**

IDEA 全称 IntelliJ IDEA，是java编程语言开发的集成环境。IntelliJ在业界被公认为最好的java开发工具之一，尤其在智能代码助手、代码自动提示、重构、J2EE支持、各类版本工具(git、svn等)、JUnit、CVS整合、代码分析、 创新的GUI设计等方面的功能可以说是超常的。IDEA是JetBrains公司的产品，这家公司总部位于捷克共和国的首都布拉格，开发人员以严谨著称的东欧程序员为主。它的旗舰版本还支持HTML，CSS，PHP，MySQL，Python等。免费版只支持Java，Kotlin等少数语言。

![](https://foruda.gitee.com/images/1664262069595803009/96e30eb0_10637153.png)

## 1.安装idea

我自己用的是idea2021的版本,可以参考IntellIJ IDEA安装和破解手册

## 2.创建项目和模块

### 2.1创建项目

1. 点击`Create New Project`：

   ![](https://foruda.gitee.com/images/1664262307293053229/9689bb5b_10637153.png)

2. 创建一个空的工程
   ![](https://foruda.gitee.com/images/1664262570716183508/aa191136_10637153.png)

### 2.2创建模块

- 在弹出的对话框中，点击"+"，然后点击`New Module`创建一个新的模块：
  ![](https://foruda.gitee.com/images/1664262956871713623/24e4612d_10637153.png)
- 创建一个Java模块
  ![](https://foruda.gitee.com/images/1664262966906553798/afe53d53_10637153.png)
- 选择模块的磁盘路径：
  ![](https://foruda.gitee.com/images/1664262977295717392/499a9a2b_10637153.png)
- 目录介绍
  ![](https://foruda.gitee.com/images/1664264817172073749/e5c0c04f_10637153.png)

### 2.3编写代码

```java
public class demo {
    public static void main(String[] args) { //主方法生成 psvm
        System.out.println("hello world");//输出语句 sout
    }
}
```

### 2.4运行代码

![](https://foruda.gitee.com/images/1664265168209076485/c57aee51_10637153.png)

### 2.5查看控制台

![](https://foruda.gitee.com/images/1664265201019184975/03feeb13_10637153.png)

### 2.6idea项目目录

- .idea：和我们开发无关，是IDEA工具自己使用的
- out：目录是存储编译后的.class文件
- Demo01：模块所在文件夹

![](https://foruda.gitee.com/images/1664265218596576706/da808fa0_10637153.png)

## 3.idea快捷键和设置

**这里只介绍一些常用的快捷键和通用的设置**

### 3.1字体设置

点击菜单栏上的 `File->Settings->Editor->Font` 修改字体

![](https://foruda.gitee.com/images/1664272317809517834/03ed90bb_10637153.png)

### 3.2idea常用快捷键

| 快捷键             | 功能                         |
| ------------------ | ---------------------------- |
| Alt+Enter          | 导入包，自动修正代码         |
| Ctrl+Y             | 删除一行                     |
| Ctrl+D             | 快速复制一行                 |
| Ctrl+Alt+L         | 格式化代码                   |
| Ctrl+/             | 单行注释                     |
| Ctrl++Shift+/      | 多行注释                     |
| Alt+Shift+上下箭头 | 移动当前代码行               |
| Ctrl+Shift+N       | 快速查询当前项目下的所有文件 |
| Ctrl+N             | 快速查询当前项目的所有类     |
| ctrl+alt+t         |                              |

> 有的时候我们要debug,
>
> Step  Over F8下一步
> Step Into F7 进入到某个方法中
> Force Step Into Alt+Shift+F7 强制进入
> Step Out Shift+F8 从某个方法中返回
> Drop Frame 返回上一个断点
> Run to Cursor Alt+F9 跳转到光标所在的这一行

# 第四章运算符

## 1.算术运算符

| 算术运算符 |                              |
| ---------- | ---------------------------- |
| `+`        | 加法运算，字符串连接运算     |
| `-`        | 减法运算                     |
| `*`        | 乘法运算                     |
| `/`        | 除法运算                     |
| `%`        | 取模运算，两个数字相除取余数 |
| `++、--`   | 自增自减运算                 |



## 2.赋值运算符

赋值运算符，就是将符号右边的值，赋给左边的变量。

| 赋值运算符 |            |
| ---------- | ---------- |
| `=`        | 赋值       |
| `+=`       | 加后赋值   |
| `-=`       | 减后赋值   |
| `*=`       | 减后赋值   |
| `/=`       | 除后赋值   |
| `%=`       | 取模后赋值 |

> 注意：`a=a+b和a+=b有什么区别`
>
> += 操作符会进行隐式自动类型转换,此处a+=b隐式的将加操作的结果类型强制转换为持有结果的类
>
> 型,而a=a+b则不会自动进行类型转换
>
> ```java
> byte a = 127;
> byte b = 127; 
> b = a + b; // 报编译错误:cannot convert from int to byte
> //正确写法
> b += a;
> 
> //有错误.short类型在进行运算时会自动提升为int类型,也就是说 s1+1 的运算结果是int类型,而s1是short类型,此时编译器会报错
> short s1= 1;
> s1 = s1 + 1;
> 
> //正确写法：
> short s1= 1;
> s1 += 1;
> ```
>
> 

## 3.比较运算符

| 比较运算符： |                                                              |
| ------------ | ------------------------------------------------------------ |
| `==`         | 比较符号两边数据是否相等，相等结果是true。                   |
| `<`          | 比较符号左边的数据是否小于右边的数据，如果小于结果是true。   |
| `>`          | 比较符号左边的数据是否大于右边的数据，如果大于结果是true。   |
| `<=`         | 比较符号左边的数据是否小于或者等于右边的数据，如果小于或等于结果是true。 |
| `>=`         | 比较符号左边的数据是否大于或者等于右边的数据，如果小于或等于结果是true。 |
| `!=`         | 不等于符号 ，如果符号两边的数据不相等，结果是true。          |

## 4.逻辑运算符

逻辑运算符，是用来对两个布尔类型进行运算的，运算结果都是布尔值 `true` 或者 `false`

| 运算符 | 运算规则                                                 | 示例           | 结果        |
| ------ | -------------------------------------------------------- | -------------- | ----------- |
| `&`    | 与（有假为假）                                           | false&true     | false       |
| `      | `                                                        | 或（有真为真） | false\|true |
| `^`    | 异或（相同为false，不同为true）                          | false^true     | true        |
| `!`    | 非（取反，true为false，false为trie）                     | !true          | false       |
| `&&`   | 短路与（和`&`一样，前面条件为false不执行后面的，效率高） | false&&true    | false       |

## 5.三元运算符

三元运算符格式：

```java
数据类型 变量名 = 布尔类型表达式 ? 结果1 : 结果2;
```

- 布尔类型表达式结果是true，三元运算符整体结果为结果1，赋值给变量。
- 布尔类型表达式结果是false，三元运算符整体结果为结果2，赋值给变量。

# 第五章控制语句

## 1.选择语句/分支语句

### 1.1.if

四种写法

1. ```java
   if(布尔表达式){
   }
   ```

2. ```java
   if(布尔表达式){
   }else{
   }
   ```

3. ```java
   if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }
   ```

4. ```java
   if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }else if(布尔表达式){
   }else{
   }
   ```

5. if语句嵌套：

   ```java
   if(布尔表达式){ //前提条件
      if(布尔表达式){
         if(布尔表达式){
   
         }else{
   
         }
      }
   }else{
   
   }
   ```

6. 执行原理

   ```
      对于一个if语句来说，只要有1个分支执行，整个if语句结束。
      当布尔表达式的结果为true时，分支才会执行。
      分支当中只有一条java语句，大括号可以省略。
      带有else的可以保证肯定会有一个分支执行。
   ```

### 1.2.switch

```java
完整语法结构：
	switch(值){ //值允许是String、int，（byte,short,char可以自动转换int）
	case 值1: case 值x:
		java语句;
		break;
	case 值2:
		java语句;
		break;
	case 值3:
		java语句;
		break;
	default:
		java语句;
	}
```

## 2.循环语句

### 2.1.for循环

```java
for循环语法机制：
	for(初始化表达式;条件表达式;更新表达式){
		循环体;
	}

	for(int i = 0; i < 10; i++){
		System.out.println(i);
	}
```

> for循环执行原理：
> 1、先执行初始化表达式，并且只执行1次。
> 2、然后判断条件表达式
> 3、如果为true，则执行循环体。
> 4、循环体结束之后，执行更新表达式。
> 5、继续判断条件，如果条件还是true，继续循环。
> 6、直到条件为false，循环结束。

### 2.2while循环

```java
while(布尔表达式){
	循环体;
}
执行次数：0~N次。
```

### 2.3.do..while

```java
do{
	循环体;
}while(布尔表达式);

执行次数：1~N次。
```

## 3.break

默认情况下，终止离它最近的循环。当然，也可以通过标识符的方式，终止指定的循环。

## 4.continue

终止当前“本次”循环，直接跳入下一次循环继续执行。

# 第六章方法

## 1.方法的概述

是可以完成某个特定功能的并且可以重复利用的代码片段。在C语言中，方法被称为函数。

你定义一个/抽取一个方法出来，而这个方法却无法完成某个特定功能，那么你抽取的这个方法毫无意义。一般一个方法就是一个“功能单元”。假设在以后的开发中，某个功能是可以独立抽取出来的，建议定义为方法，这样以后只需要这个功能，那么直接调用这个方法（函数）即可，而不需要重复编写业务代码。

**简单来说Java方法是语句的集合，它们在一起执行一个功能。**

**方法**：就是将一个**功能**抽取出来，把代码单独定义在一个大括号内，形成一个单独的功能。当我们需要这个功能的时候，就可以去调用。这样即实现了代码的复用性，也解决了代码冗余的现象。

## 2.方法的使用

### 2.1 方法的定义

定义格式

```java
[修饰符列表] 返回值类型 方法名（形式参数列表）{
    代码块;
    return 返回值;
}
```

定义格式名词解释:

- 修饰符： 目前固定写法 `public`、`static` 。
- 返回值类型： 方法运行结果的数据类型，如果该方法没有返回值，那么请声明为`void`
  - 返回值类型可以是任何类型，只要java中合法的数据类型就行，数据类型包括基本数据类型和引用数据类型。
  - 当一个方法执行结束不返回任何值得时候，返回值得类型也不能空白，必须写上void关键字，所以void表示该方法执行结束不返回任何结果
  - 第四如果返回值类型不是void，那么在方法体结束后，必须使用return返回来返回值,如果没有编译报错
  - 只要有return关键字执行，那么当前方法体结束，如果返回值类型为void 则方法体 中不能有 return 值,
    return; 代表整个方法体的结束.
- 方法名：满足标识符的规范，用来调用方法。
- 参数列表：参数像是一个占位符。当方法被调用时，传递值给参数。这个值被称为实参或变量。参数列表是指方法的参数类型、顺序和参数的个数。参数是可选的，方法可以不包含任何参数。

举例

```java
public static void methodName(){
    System.out.println("方法定义举例");
}
```

### 2.2方法的调用

方法在定义完毕后，方法不会自己运行，必须被调用才能执行，我们可以在主方法main中来调用我们自己定义好的方法。在主方法中，直接写要调用的方法名字就可以调用了

```java
//在方法调用的时候，在同一个类中，类名可以省略
//如果不在同一个类中，类名不能省略
public class MethodTest {
    public static void main(String[] args){

        //那么我们的类名可以省略吗
        daYin1();
        daYin2();
        daYin3();
        //像这种情况下“类名”就不能省略了
        Myclass.daYin1();
        Myclass.daYin2();
        Myclass.daYin3();

    }
    public static void daYin1(){
        System.out.println("hellp world");
    }
    public static void daYin2(){
        System.out.println("hellp world2");
    }
    public static void daYin3(){
        System.out.println("hellp world3");
    }
}

class MyClass{

    public static void daYin1(){
        System.out.println("1");
    }
    public static void daYin2(){
        System.out.println("2");
    }
    public static void daYin3(){
        System.out.println("3");
    }

}
```

### 2.3方法的调用的顺序

示例：

```java
public class MethodTest {
    public static void main(String[] args){
        System.out.println("This is main");
        m1();
        System.out.println("main over");
    }
    public static void m1(){
        System.out.println("This is m1");
        m2();
        System.out.println("m1 over");

    }
    public static void m2() {
        System.out.println("This is m2");
        m3();
        System.out.println("m2 over");
    }
    public static void m3(){
        System.out.println("This is m3");
        T.m4();
        System.out.println("m3 over");
}
    class T{
        public static void m4(){
            System.out.println("This is m4");
            System.out.println("m4 over");}

    }
}
/*
 以上代码会输出什么呢？
 	This is main
    This is m1
    This is m2
    This is m3
    This is m4
    m4 over
    m3 over
    m2 over
    m1 over
    main over
*/
```

JVM(虚拟机)的三大主要内存：栈内存，堆内存，方法区内存

- 方法区：我个人理解就是存放代码的(存放一些类的信息,静态变量,方法的信息,常量池等)
- 堆内存:到后面会有详细的解释
- 栈内存:方法执行的内存空间,以及局部变量
  - 方法调用的时候压栈(入push),方法结束的时候弹栈(出pop)
  - 采用的是先进先出,后进先出的原则

栈的数据结构,采用图的形式

![](https://foruda.gitee.com/images/1664332984610762990/658f9266_10637153.png)

对上方代码做出解释

- 程序加载,将一些class字节码文件、方法代码块进行加载

- 之后找到主程序入口也就是main方法,main方法输出

  ```java
   System.out.println("This is main");
  ```

- 之后调用m1方法,这里注意,调用m1()方法的时候,也就是将m1()方法压栈,main方法后面的代码就会停止运行，就行转到m1()方法执行代码 紧接着m1()方法调用m2()方法。m2()方法压栈,m1()方法后面的代码会停止运行转到m2()..... 以此类推,当最后一个方法执行完之后,就会出栈。就会转到之前调用这个方法的方法继续执行没有执行完的代码.。

### 2.4带参数的

其实在声明方法的时候我们要定义返回值类型和形式参数列表

```java
public class MethodTest {
    public static void main(String[] args) {

        int max = max(20, 18);

        System.out.println("最大值为: "+max);
    }

    public static int max(int num1, int num2) {
        return num1>num2?num1:num2;
    }
}

```

### 2.5方法的重载

方法重载的定义和使用

- **方法重载：指在同一个类中，允许存在一个以上的同名方法，只要它们的参数列表不同即可，与修饰符和返回值类型无关（即使修饰符和返回值列表不一样也属于重载）**
- 参数列表不同：个数不同，数据类型不同，顺序不同。

没有用方法重载的弊端

- ```java
  //三个方法功能不同，但是相似，分别起了不同的名字
  //第一：代码不够美观
  //第二：程序员需要记忆更多的方法名称，累！！
  public class overrideTest01 {
      public static void main(String[] args) {
          System.out.println(sumint(10,20));
          System.out.println(sumlong(10L,20L));
          System.out.println(sumdouble(10.0,20.0));
      }
      public static int sumint(int x,int y){
          return x+y;
      }
      public static long sumlong(long x,long y){
          return x+y;
      }
      public static double sumdouble(double x,double y){
          return x+y;
      }
  }
  ```

使用方法重载

- ```java
  public class overrideTest02 {
      public static void main(String[] args) {
          //对于程序员来说，只需要记忆一个方法名即可
          System.out.println(sum(10,20));
          System.out.println(sum(10L,20L));
          System.out.println(sum(10.0,20.0));
      }
      public static int sum(int x,int y){
          System.out.println("int的");
          return x+y;
      }
      public static long sum(long x,long y){
          System.out.println("long的");
          return x+y;
      }
      public static double sum(double x,double y){
          System.out.println("double的");
          return x+y;
      }
  }
  ```

# 第七章认识面向对象

## 1.什么是对象？

在Java中，对象（Object）是指一个具体事物的实例，任何事物都可以使用对象（类）来描述，如猫、狗、计算机、杯子、云、水、空气、叶子、灰尘等看得见的、看不见的、宏观的、微观的、具体的、抽象的都是对象，总之"万物皆对象"；

> 对象是实际存在的个体。（真实存在的个体）
>
> 宋小宝就是一个对象
> 姚明就是一个对象
> 刘德华就是一个对象
> ....
>
> 宋小宝、姚明、刘德华这3个对象都属于“明星”。

## 2.面向对象的程序设计

Java是一门面向对象的编程语言，面向对象是一种程序设计思想，与之对应的还有面向过程程序设计；面向对象是把一个对象的特征（属性）和行为单独封装到对象源代码中；这些属性和行为都被集中到一个地方，这样比把方法或者过程与数据分散开来更为方便和安全，含义更加明确；

## 3.面向对象和面向过程

举例子：开车去上班

- 面向过程：去车库提车、拿钥匙、打火、踩离合、挂挡、踩油门、刹车、加油、到公司、找车库停车
- 面向对象：打个滴滴（对象）、到公司

可以看得出来，面向过程关注的是步骤，将所有步骤连在一起"我就能到公司上班"，面向对象则关注的是"开车去上班"这个事物整体，完成这件事的步骤全部**封装**起来，交给指定的对象去做（司机）；

> tips:也是个人的理解
>
> 面向过程主要关注的是：实现步骤以及整个过程。过程A-B-C 这个三个过程都有因果关系.
> 										如果这三个过程中有一个过程发生错误,
> 										就如上述例子一样,如果去车库提车,如果车库钥匙丢了呢？那么整个过程无法进行
>
> 面向对象主要关注的是：对象A，对象B，对象C，然后对象ABC组合，或者CBA组合..... 
> 										这单个对象或者是对象的组合完成一个特定的功能
> 										如果这其中一个对象发生了错误,那么就可以修改发生错误的就可以了
> 										就如上述的例子,如果滴滴司机中途跟你说:实在不好意思,不能接单,那么就可以重新打

## 4.类和对象

在现实世界中，属于同一类的对象很多，**类是抽象的**，不是具体的，我们人习惯以对象的方式认识现实世界；

例如:学生这个类。如果单说这个学生的话,会觉得抽象，这个学生的学号呢？姓名呢？性别呢？等等

那么 这个学生就是一个模板(类),通过这个模板我们可以创建很多实体化的东西(实例化对象)。
比如：我创建了一个学生的模板(类) 学号：001，姓名：张三，性别：男

通过上述的例子就可以认识到 类和对象的关系了, 我们通过模板来创建一个实例。也就是通过类创建对象

> tips：**类是抽象的，对象是具体的，对象是类的实例化；**

类是一组相关属性和行为的集合。可以看成是一类事物的**模板**，使用事物的**属性特征**和**行为特征**来描述该类事物。

- 属性：该事物的状态信息；
- 行为：该事物的功能信息；

# 第八章创建对象和使用

## 1.Java类的定义

```java
public class 类名 {
	//成员变量
    //成员方法
}
```

- **定义类：** 就是定义类的成员，包括成员变量和成员方法。
- **成员变量：** 和以前定义变量几乎是一样的。只不过位置发生了改变。在类中，方法外。
- **成员方法：** 和以前定义方法几乎是一样的。只不过把static去掉，static的作用在面向对象后面再讲解。

类的定义格式举例：

```java
/*
注意:不需要写main方法,Student只是一个模板而已
*/
public class Student {
    //成员变量(属性) 描述事物的信息
    String name;        //姓名
    int age;            //年龄

    // 成员方法(行为) 描述事物的行为
    public void study(){
        System.out.println("学习");
    }

    public void eat(){
        System.out.println("吃饭");
    }
}

```

## 2.类的实例化(创建对象)

类是抽象的，不是具体的，类只是负责把事物描述起来，提供模板；对象是类的实例化，是具体的；我们定义好一个Java类后需要通过对象将类进行实例化；

创建对象的语法:`new`

```java
类名 对象名=new 类名()
```

使用对象访问类中的成员：`引用.`的方式(这里又称对象名为引用，意思就是只想堆内存的指针)

```java
对象名.成员变量;
对象名.成员方法();
```

类的实例化练习：

```java
public class Demo {
    public static void main(String[] args) {
        //创建对象格式： 类名 对象名 = new 类名();
        Student s = new Student();

        System.out.println("s: " + s); //s: com.song.Student@1540e19d 这里是为什么后面解释

        //直接输出成员变量的值
        System.out.println("姓名: " + s.name);      //null
        System.out.println("年龄" + s.age);         //0
        System.out.println("--------");

        //给成员变量赋值
        s.name = "张三";
        s.age = 21;

        //再次输出成员变量的值
        System.out.println("姓名： " + s.name);      //张三
        System.out.println("年龄： " + s.age);       //21
        System.out.println("---------");
        
        //调用成员方法
        s.study();          //学习
        s.eat();            //吃饭
    }
}

```

## 3.成员变量的默认值

在上方的案例当中,我们直接输出了成员变量的值 name(String类型) 为null ,age(int类型)为0

那么 就有了成员变量的默认值

### 基本类型：

| 数据类型                       | 默认值   |
| ------------------------------ | -------- |
| 整数（byte，short，int，long） | 0        |
| 浮点数（float，double）        | 0.0      |
| 字符（char）                   | ‘\u0000’ |
| 布尔（boolean）                | false    |

### 引用数据类型

| 数据类型           | 默认值 |
| ------------------ | ------ |
| 数组，对象，String | null   |

## 4.JVM内存

在上面"方法"一章说到了JVM有三大内存空间,只说到了方法区和栈区。接下载就说说堆内存

- **方法区**：类加载器classloader，将硬盘上的XXX.class字节文件码装载到jvm的时候，会将字节码文件放到方法区中。也就是方法区中存储的是代码片段，因为类需要加载，所以方法区中最先有数据
- **栈**：在方法被调用的时候，该方法需要的内存空间在栈中分配。
  栈式使用最频繁的，一直压栈和弹栈
  方法调用的时候压栈，栈中最主要的存储时局部变量，局部变量时在方法当中的。
  就比如，我们先执行main方法，压入栈中，我们称main方法栈帧
- **堆内存**：凡是用过，new运算符创建的对象，都在堆内存当中。new运算符的作用就是在堆内存中开辟一块空间。堆中存储“对象”，以及对象的实例变量

上图！

![](https://foruda.gitee.com/images/1664348991714815301/1bad8f36_10637153.png)

## 5.创建对象练习以及JVM内存图

Student类：

```java
public class Student {
    //属性（描述状态），在java程序中以“成员变量”的形式存在
    //学号
    int no;//这种变量又称为实例变量，一个对象一份
    //姓名
    String name;
    //年龄
    int age;
    //性别
    boolean sex;
    //住址
    String addr;
}
```

类的实例化:

```java
public class StudentTest02 {
    public static void main(String[] args) {
        /*
            访问学生姓名可以直接通过类名吗
            学生姓名是一个实例变量，实例变量是对象级别的变量
            是不是应该先有对象才能说姓名的事情
            不能通过”类名“来直接访问”实例变量“
            System.out.println(Student.name);
         */
        
        //应该注意，现有类才能创建对象，而有了对象，我们才能去对变量进行操作
        //创建对象一
        //s1这个局部变量叫做引用
        Student02 s1=new Student02();
        //创建对象二
        //s2这个局部变量也叫引用

        //怎么访问实例变量
        //语法： 引用（通过new出来的变量）.实例变量名
        System.out.println(s1.no);
        System.out.println(s1.name);
        System.out.println(s1.sex);
        System.out.println(s1.age);
        System.out.println(s1.addr);
        System.out.println("-------------------------");
        Student02 s2=new Student02();
        //这里的s1 s2都是属于局部变量
        System.out.println(s2.no);
        System.out.println(s2.name);
        System.out.println(s2.sex);
        System.out.println(s2.age);
        System.out.println(s2.addr);
        System.out.println("-------------------------");



        //代码到此处我可以修改学生s1的学生属性吗
        //通过”=“赋值的方式将内存中实例变量的值修改一下
        s1.no=110;
        s1.name="张三";
        s1.age=20;
        s1.sex=true;
        s1.addr="唐山学院";
        System.out.println(s1.no);
        System.out.println(s1.name);
        System.out.println(s1.sex);
        System.out.println(s1.age);
        System.out.println(s1.addr);
    }
}

```

JVM内存图:

![](https://foruda.gitee.com/images/1664349585560247395/4755859a_10637153.png)

## 6.成员变量和局部变量

根据声明的位置不同,变量也有不同的名称,当然存放的位置也可能不同,下面进行代码测试

```java
public class Student {
    int age;//成员变量 年龄

    String name;//成员变量 姓名

    //成员方法 学习方法
    public  void study(){
        int i = 10; //局部变量
        System.out.println("学生正在学习");
    }

    /**
     * 自我介绍的方法
     * @param name 姓名(局部变量)
     * @param age  年龄(局部变量)
     */
    public void intro(String name,int age){
        System.out.println("大家好我叫"+name+"我今年"+age+"岁了");
    }
}

```

![](https://foruda.gitee.com/images/1664358653461774723/5c149687_10637153.png)

成员变量和局部变量的区别：   

- 成员变量：     
  - 成员变量定义在类中，在整个类中都可以被访问。
  - 成员变量分为类成员变量和实例成员变量，实例变量存在于对象所在的堆内存中
  - 成员变量有默认初始化值。
  - 成员变量的权限修饰符可以根据需要，选择任意一个
- 局部变量:
  - 局部变量只定义在局部范围内，如：方法内，代码块内等。
  - 局部变量存在于栈内存中，当方法弹栈（执行完毕）后，局部变量销毁；
  - 局部变量没有默认初始化值，使用前必须手动赋值；
  - 局部变量声明时不指定权限修饰符；

> 就现在而言总体来说：在方法内部的就是局部变量存放的位置在栈区, 在方法外部的就是成员变量 存放的位置为堆区或者是方法区(这个到后面将static会解释)

## 7.方法调用传参问题

类：

```java
class ren{
    int age;
}
```

测试类：

```java
/*
java中关于方法调用时参数传递实际上只有一个规则
不管你是什么类型的数据，实际上传递的时候，都是将变量中保存的那个值复制一份传过去
*/
public class Test {
    public static void main(String[] args){
        ren r=new ren();
        r.age=10;
        add(p);
        /*
        这里是将一个对象的内存地址传到了add中，
        也就是add中的对象和main中的对象 保存的地址都指向了堆内存同一个类型的对象
        但是我们要注意 main中的p 和add中的p 是两个p
        */
        System.out.println("main--->"+p.age);//11

    }
    //方法中的参数可以是基本的也可以是引用的
    public static void add(ren r){
        //这里会让堆内存中age这个属性下存放的值发生改变
        p.age++;
        //理解为c语言的指针，形参和实现指向同一内存地址
        System.out.println("add--->"+p.age);//11
    }
}
/*
最后输出为
add--->11
main--->11
*/
```

在此需要明确什么是值传递和址传递

- 值传递：（参数类型是基本数据类型）：方法调用时，实参把它的值传递给对应的形参，形参只是用实参的值初始化自己的存储单元内容，**是两个不同的存储单元**，所以方法执行中形参值的改变不影响实参的值。
- 引用传递：(参数类型是引用数据类型参数)：也称为传地址。方法调用时，实参是对象（或数组），这时实参与形参指向同一个地址，在方法执行中，对形参的操作实际上就是对实参的操作，这个结果在方法结束后被保留了下来，所以方法执行中形参的改变将会影响实参。

> 在Java中，除了基本数据类型之外的数据类型都是引用数据类型，都是通过new在堆内存开辟空间；

对上方的代码,内存图解释

![](https://foruda.gitee.com/images/1664360660659307046/855491e0_10637153.png)

## 8.this关键字

1. this是一个关键字，是一个引用，保存内存地址指向自身

2. this可以使用在实例方法中，也可以使用在构造方法中

3. this出现在构造方法中其实代表的是当前对象

4. this不能使用在静态方法中

5. this大部分情况下是可以省略的，在区分局部变量和实例变量的时候不能省略

6. this（）这种语法只能出现在构造方法中的第一行，表示当前构造方法调用本类其他的构造方法

   ```java
   public class ThisTest(){
       int year;
       int month;
       int day;
       
       public date(){
           this(1970,1,1);
       }
       
       public date(int year,int month,int day){
           this.year=year;
           this.month=month;
           this.day=day;
       }
       public static void main(String[] a){
           date d1=new date();//1970,1,1
           date d2=new date(1999,2,1);//1999,2,1
       }
   }
   ```

this内存结构图

​	![](https://foruda.gitee.com/images/1664362582760000134/75b434ad_10637153.png)

通过图解可以看出,this的中保存的内存地址和引用是一样的

## 9.static关键字

### 9.1static概述

`static` 关键字它可以用来修饰的**成员变量**和**成员方法**，**被修饰的成员是属于类的**，而不是单单是属于某个对象的。被static修饰的成员由该类的所有实例（对象）共享；

static修饰的统一都是静态的，都是类相关的，不需要new对象，之间采用”类名.“访问当一个属性是类级别的属性，所有对象的这个属性的值都是一样的，建议定义为静态变量

### 9.2定义和使用格式

#### 9.2.1类变量

当 `static` 修饰成员变量时，该变量称为**类变量**。该类的每个对象都共享同一个类变量的值。任何对象都可以更改该类变量的值，但也可以在不创建该类的对象的情况下对类变量进行操作，因为该变量属于类，而不是某个对象。

**类变量：** 使用 static关键字修饰的成员变量。

定义格式:

```java
static 数据类型 变量名;
```

使用格式：

```java
类名.变量名
```

例如：

```java
static String name;
```

如果一个类当中,每个对象都有公共的字段呢?每次new都会实例化一个新的公共字段,那显然是浪费内存的，所以有没有一种方法可以把公共的属性提出来.就是static关键字(到下面会讲解静态原理图)

```java
public class StaticTest {
    public static void main(String[] args) {
        //访问中国人的国际
        //静态变量应该使用"类名."的方式访问
        System.out.println(Chinese.guoji);
        Chinese c1=new Chinese("123","张三");
        System.out.println(c1.name);
        System.out.println(c1.zheng);
        Chinese c2=new Chinese("456","李四");
        System.out.println(c2.name);
        System.out.println(c2.zheng);
    }
}
class Chinese{
    //身份证号
    //每个人的身份证号不同，所以身份证号都应该是实例变量，一个对象一个
    String zheng;
    //名字也是一个人一个
    String name;
    //对于zhongguo这个类来说，国际都是中国，不会随对象的改变而改变。
    //国籍属于整个类的特征
    //加static的变量叫静态变量
    //静态变量在类加载时初始化，不需要new对象，静态变量的空间就开出来了
    //静态变量存储在方法区
    static String guoji="中国";
    //无参数
    public Chinese(){

    }
    //有参数
    public Chinese(String zheng,String name){
        this.zheng=zheng;
        this.name=name;
    }
}
```

#### 9.2.2 静态方法

当 `static` 修饰成员方法时，该方法称为类方法。静态方法在声明中有 static ，建议使用类名来调用，而不需要创建类的对象。调用方式非常简单。

**类方法**：使用 static关键字修饰的成员方法，习惯称为**静态方法**。

定义格式：

```java
修饰符 static 返回值类型 方法名 (参数列表) { 
	// 执行语句
}

```

举例：在Student类中定义静态方法

```java
public static void showId(int id) {
    System.out.println("id:" + id);
}

```

静态方法调用的注意事项：   

- 静态方法可以直接访问类变量（被static修饰的变量）和静态方法。（静态方法能够访问静态资源）
- 静态方法不能直接访问普通成员变量或成员方法。反之，成员方法可以直接访问类变量或静态方法。
- 静态方法中，不能使用this关键字

> tips：静态方法只能访问静态成员。

#### 9.2.3调用格式

```java
// 访问类变量
类名.类变量名；

// 调用静态方法
类名.静态方法名(参数)；
```

> 总结：
>
> 成员变量和成员方法的访问：`引用.`的形式 
>
> - 引用.成员变量
> - 引用.成员方法
>
> **这里要注意,要先有对象(先new对象)才能去使用`引用.`的形式否则是无法访问**
>
> 静态变量和静态方法
>
> - 静态变量:类名.类变量名
> - 静态方法:类名.静态方法名(参数)

### 9.3静态原理图解

`static` 修饰的内容：

- 是随着类的加载而加载的，且只加载一次。
- 存储于一块固定的内存区域（静态区），所以，可以直接被类名调用。
- 它优先于对象存在，所以，可以被所有对象共享。

![](https://foruda.gitee.com/images/1664368391233672206/d40d69ea_10637153.png)

### 9.4静态代码块

1. 使用static关键字可以定义：静态代码块

2. 定义格式

   ```java
   static{
           java语句
       }
   ```

3. static静态代码块在什么时候执行的呢？

   - 类加载时执行，并且只执行一次,静态代码块由这样的特征

4. 静态代码块在类加载时执行，并且在main方法之前执行

5. 静态代码块是自上而下顺序执行

6. 静态代码块的作用

   - 第一：静态代码块不这么常用（不是每个类都要写的东西）
   - 第二：静态代码块这种语法机制实际上是sun公司给我们java程序员的一个特殊的实际这个时机叫类加载时机

### 9.5实例代码块

执行的时机:只有时构造方法，必然在构造方法之前，执行一次

语法:

```java
   {
       java语句；
   }
```



## 10.构造方法

### 10.1概念

什么是构造方法呢？

- 构造方法是一个特殊的方法，通过构造方法可以完成对象的创建，以及实例化变量的初始化。换句话说：构造方法是用来创建对象，并且同时给对象的属性赋值
  注意：实例变量没有手动赋值的时候，系统会赋默认值
- 也就是当我们new 的时候 就会调用构造方法

在类当中没有写构造方法为什么还能调用呢?

- 当一个类没有提供任何构造方法时，系统会默认提供一个无参数的构造方法（而这个构造方法叫做缺省构造器）

构造方法的语法？

- ```java
  [修饰符列表] 构造方法名 （形式参数列表）{
  				构造方法体；
  }
  ```

- 注意：

  - 第一:修饰符列表统一写public 不要写成public static
  - 第二：构造方法名必须和类名一样
  - 第三：构造方法不需要指定返回值类型，也不能写void，写上以后就是普通方法了

构造方法的特点

- 构造方法是支持方法重载
- 在一个类中构造方法可以有多个，并且所有的构造方法名字都是一样的
- 对于实例变量来说，只要你在构造方法中没有手动给他赋值，统一都会默认赋值，默认赋值系统值

> 实例变量是什么时候完成初始化的呢？
>
> ​	实例变量是在构造方法执行的过程中完成初始化的

### 9.2代码测试

vip类：

```java
/*
1.构造方法可以有多个.
2.如果我们没有写构造方法,那么系统会默认提供一个无参数的构造方法(缺省构造器)
3.构造方法支持方法的重载,可以写一个参数的构造方法,可以写连两个参数的构造方法.也可以写全参的构造方法
4.如果我们写了构造方法,那么无参的构造方法就不在提供,所以为了保险起见 我们要把无参数的构造方法手动写上
*/
public class Vip {
    long no;
    String name;
    String birth;
    boolean sex;
    
    public Vip(){

    }
    public Vip(long no,String name){
        //给实例变量赋初值【初始化实例变量，初始化属性】
        this.no=no;
        this.name=name;
        //这里实际上还有两行代码
        //this.birth=null
        //this.sex=false
    }
    public Vip(long no,String name,String birth){
        no=no;
        this.name=name;
        this.birth=birth;
        //这里实际上还有一行代码
        //this.sex=false
    }
    public Vip(long no,String name,String birth,boolean sex){
        this.no=no;
        this.name=name;
        this.birth=birth;
        this.sex=sex;
    }
}
```

代码测试：

```java
public class ConstructorVip {
    public static void main(String[] args) {

        //无参构造方法
        Vip u1=new Vip();
        System.out.println(u1.no);
        System.out.println(u1.name);
        System.out.println(u1.birth);
        System.out.println(u1.sex);
        
        //有参构造方法
        Vip u4=new Vip(3333L,"黑寡妇","2001-2-03",false);
        System.out.println(u4.no);
        System.out.println(u4.name);
        System.out.println(u4.birth);
        System.out.println(u4.sex);
      
    }

}

```

## 11.package和import

1. 为什么要用package

   - package是java中的包机制。包机制的作用是为了方便程序的管理
   - 不同功能的类分别存放在不同的包下。（按照功能划分的，不同的软件包具有不同的功能）

2. package怎么用？

   - package是一个关键字，后面加包名
   - 注意：package语句只运行出现在java源代码的第一行

3. 包名命名规范

   - 一般采用公司域名倒叙的方式（因为公司域名具有全球唯一性）
   - 公司域名倒叙名+项目名+模块名+功能名

4. 编译带有包的java程序

   - 编译

     ```java
     javac -d .  Ptest.java
     ```

   - 运行

     ```java
     java  packagetest.Ptest01// packagetest.Ptest这个是类名
     ```

     

## 12.访问权限

访问权限有那些呢？

- private私有的
- protected受保护的
- public公开的
- 默认的（什么也不写）

| 访问控制修饰符 | 本类访问 | 同包访问 | 子类访问 | 编写位置任意 |
| -------------- | -------- | -------- | -------- | ------------ |
| public         | 可以     | 可以     | 可以     | 可以         |
| protected      | 可以     | 可以     | 可以     | 不行         |
| 默认           | 可以     | 可以     | 不行     | 不行         |
| private        | 可以     | 不行     | 不行     | 不行         |

访问控制权限可以修饰什么？

- 属性（四个都可以）
- 方法（四个都可以）
- 类（public和默认可以）
- 接口（public和默认可以）

# 第九章面向对象的三大特征

## 1.封装

### 1.1封装概述

封装是面向对象的三大特征之一，面向对象编程语言是对客观世界的模拟，客观世界里成员变量都是隐藏在对象内部的，外界无法直接操作和修改。封装可以被认为是一个保护屏障，防止该类的代码和数据被其他类随意访问。要访问该类的数据，必须通过指定的方式。适当的封装可以让代码更容易理解与维护，也加强了代码的安全性

举例：

```java
public class Person { 
    int age;
}
```

这里我们先不封装来分析一下程序的缺点：

- 如果不去封装,那么这个属性就是对外暴露的，随便去访问都可以.这显然是不安全的。
  举个例子 如果我们给Person的age属性赋值为300呢？
  那显然是不合理的。人的年龄怎么会超过300岁呢？
  所以我们要对age属性进行封装。加强安全性！

### 1.2private关键字

1. private是一个权限修饰符，代表最小权限。
2. 可以修饰成员变量和成员方法。
3. **被private修饰后的成员变量和成员方法，只在本类中才能访问。**

封装的原则：将属性隐藏起来，若需要访问某个属性，提供公共方法对其访问(setter和getter方法)

使用`private` 修饰成员变量，代码如下：

```java
public class Person { 
    //年龄
    //private表示私有的，被这个关键字修饰之后，该数据只能在本类中访问
    //出了这个类，age属性就无法访问了
    private int age;
    
	//封装的第二步：对外提供的公开的set(写) get(读)方法作为操作入口（并且都不带static，都是实例方法）
    /*
    注意：
        在java开发中 get方法和set方法应该满足一下格式
        public 返回值类型 get+属性名首字母大写（无参）{}
        public void set+首字母大写（有一个参数）{xxx=参数;}
    */
    
     public int getAge(){
        return age;
    }
    public void setAge(int age){
        //能不能在这里设置关卡
        if (nianling>150 ||nianling<0) {
            System.out.println("对不起，您输入的年龄有问题");
            return;
        }
        //程序到了这里说明，年龄合法的了
        this.age = age;

    }
    
    
}
```

> 总结:
>
> 1.封装
>    第一点要记住：有个封装才能有继承，有了继承才能有多态
> 2.面向对象得首要特征：封装
>    作用：保证内部得安全性，屏蔽复杂，暴露简单
> 3.在代码级别上，封装有什么用？
>    一个类体当中得数据，假设封装之后，对于代码得调用人员来说，不需要关心代码得复杂实现，只需要通过一个简单得入口就可以访问了。
>    另外，类体中安全级别较高得数据封装起来，外部人员不能随意访问，来保证数据得安全性
> 4.封装的代码实现两步
>    第一步：属性的私有化
>    第二步：一个属性对外提供set和get方法。外部程序只能通过set方法修改，只能通过get方法读取，可以在set方法中设立关卡来保证数据的安全性
>    在强调一下：set和get方法都是实例方法，不能带有static
>    不带static的方法称为实例方法，实例方法的调用必须现有new对象
>    set方法：
>       public void set+属性名首字母大写(一个参数){xxx=一个参数}
>    get方法:
>       public  返回值类型 get+属性名首字母大写（无参）{return xxx; }

## 2.继承

### 2.1继承概述

1. 子类继承父类可以获得父类的功能，提高代码的复用性
2. 子类可以重写（覆盖）某些父类的功能，我们一般称为增强
3. 子类除了可以继承父类的功能之外，还可以额外添加子类独有的功能。
4. 继承的作用：
   - 基本作用：子类继承父类，代码可以得到复用
   - 主要作用：因为有了继承关系，才有后期的方法的覆盖和多态机制

> 那么在实际开发中,满足什么条件才使用继承呢？
>
> 凡是采用“is a”能描述的，都可以去继承
>
> 例如：cat is a Animal 猫是一个动物，dog is Animal 狗是一个动物
>
> 假设以后的开发中有一个A类，有一个B类，A类和B类确实有重复的代码，那么他们两个之间可以继承吗？
> 不一定，还要看他们之间是否可以用is a去描述

### 2.2继承语法

```java
class 父类
    
class 子类 extends 父类
```

注意点：

- B类继承A类，则称A类为超类(superclass)、父类、基类,B类称为子类(subclass)、派生类、扩展类
- java中的继承只支持单继承，不支持多继承
- 虽然java中不支持多继承，但有的时候会产生间接继承的效果

### 2.3案例

举例：

1. 老师
   - 属性(成员变量)：**姓名**，**年龄**，**性别**
   - 行为(成员方法)：**吃饭**，**睡觉**，**授课**
2. 学生
   - 属性(成员变量)：**姓名**，**年龄**，**性别**
   - 行为(成员方法)：**吃饭**，**睡觉**，**听课**

1)分析一下这两个对象有什么公共的部分,姓名、年龄、性别、吃饭、睡觉 都是公共的部分。只有授课和听课不同

定义父类,提取公共的部分

```java
//提取公共部分,封装到Person类中
public class Person{
    String name;//姓名
    int age;//年龄
    boolean sex;//性别
    
    //吃饭的行为
    public void eat(){
        System.out.println(name+"正在吃饭");
    }
    
    public void sleep(){
        System.out.println(name+"正在睡觉");
    }
}
```

2)定义一个老师的类,继承Person类,也就是将父类的属性和行为都继承过来.自己扩展一个授课的行为

```java
public class Teacher extends Person{
	public void teach(){
        System.out.println(name+"授课");
    }
}
```

3)定义一个老师的类,继承Person类,也就是将父类的属性和行为都继承过来.自己扩展一个上课的行为

```java
public class Student extends Person{
	public void study(){
        System.out.println(name+"学习");
    }
}
```

4)测试类

```java
public class Test{
    public static void main(String[] args){
        //创建教师对象
        Teacher t = new Teahcer();
        t.name="张三";
        t.age=38;
        t.sex=true;//true表示男人
        t.teach();
        t.eat();
        t.sleep();
        
        //创建学生对象
        Student t = new Student();
        t.name="李四";
        t.age=21;
        t.sex=false;//true表示男人
        t.study();
        t.eat();
        t.sleep();
    }
}
```

### 2.4父类不可继承的内容

父类中所有的内容,不是都可以让子类继承的,以下两个内容就不可以让子类继承

- 被private修饰的(这里访问要通过setter和getter方法)
- 构造方法不能被继承

### 2.5成员变量的继承

当继承父类之后,成员变量的方法名重名和不重名是否有冲突呢？

#### 2.5.1成员变量不重名

子类和父类不重名的情况下,直接继承过来没有任何的影响

```java
public class Demo {
    public static void main(String[] args) {
        Zi zi=new Zi();
        System.out.println("父类num:"+zi.num1);//父类继承下来的
        System.out.println("子类num:"+zi.num2);//这个是本身的
    }
}

class Fu{
    int num1=10;
}

class Zi extends Fu{
    int num2=20;
}

```

结果输出

```java
父类num:10
子类num:20
```

#### 2.5.2成员变量重名

当成员变量重名的时候呢？

```java
public class Test {
    public static void main(String[] args) {
        Zi zi=new Zi();
        System.out.println(zi.num);
        System.out.println(zi.num);
    }
}

class Fu{
    int num=10;
}

class Zi extends Fu{
    int num=20;
}

```

测试结果

```java
20
20
```

**经过测试可以得出,当子类和父类的成员变量名重名的时候,就会采用就近原则使用子类的成员变量**

### 2.6成员方法的继承(重写)

#### 2.6.1什么是方法的重写

如果子类和父类中出现**不重名**的成员方法，这时的调用是**没有影响**的。对象调用方法时，会先在子类中查找有没有对应的方法，若子类中存在就会执行子类中的方法，若子类中不存在就会执行父类中相应的方法；

但是如果是重名的时候呢?
和成员变量的继承是一样的,当成员方法重名的时候会调用子类的方法,**这么机制叫做方法的重写(Override)**

> 在此回顾以下方法的重载:
>
> 当一个类中，如果功能相似的话，建议将名字定义的一样，这样代码美观
>  条件一：在同一个类中
>  条件二：方法名相同
>  条件三：参数列表不同（个数、顺序、类型）

#### 2.6.2什么时候采用重写机制

子类继承父类之后，放继承过来的方法无法当前子类的业务需求时，子类有权力对这个方法进行重新编写.则有必要进行方法的覆盖(重写),

在前面就提到，成员方法描述的是，对象的行为。当子类和父类行为有一些差异的时候，但都属于一种同一种行为，只是行为方式不一样.就比如父类采用的学习方式是线下课(行为),而子类采用学习的方式是网课。显然这两种行为都是学习，但只是方式不同，所以我们要进行方法的重写。

**举例 :没有使用方法的重写**

```java
public class OverrideTest {
    public static void main(String[] args) {
        //创建鸟儿对象
        Bird b1=new Bird();
        //让鸟儿移动
        b1.move();//动物在移动
    }
}
//父类
class Animal{
    public void move(){
        System.out.println("动物在移动");
    }
}
//子类
class Bird extends Animal{
    //子类继承父类中，有一些“行为”可能不需要改进，有一些“行为”可能面临这必须改进
    //因为父类中继承过来的方法已经无法满足子类的需求

    //鸟儿在移动的时候希望输出鸟儿在飞翔

}

class Cat extends Animal{
    //猫在移动的时候，我希望输出：猫在走猫步
}
```

**上方案例的改进**

```java
public class OverrideTest {
    public static void main(String[] args) {
        bird b=new bird();//鸟儿在飞行
        b.move();
        Dog c=new Dog();//狗在走狗步
        c.move();

    }
}
class animal{
    public void move(){
        System.out.println("动物在移动");
    }
}
class bird extends animal{
    //对move方法进行方法的覆盖，方法的重写
    //最好将父类中的方法原封不动的复制过来
    //方法覆盖，就是将继承过来的那个方法覆盖掉了，继承过来的方法没了
    public void move(){
        System.out.println("鸟儿在飞行");
    }
}

class Dog extends animal{
    public void move(){
        System.out.println("狗在走狗步");
    }
}

```

> 结论：
>
> ​	当子类对父类继承过来的方法进行”方法覆盖“之后，
> ​	子类对象调用该方法的时候，一定执行覆盖之后的方法

#### 2.6.2重写的注意点

- 条件一:两个类必须要有继承关系
- 条件二:重写之后的方法和之前的方法具有：
  相同的返回值类型
  相同的方法名
  相同的形式参数列表
- 条件三:访问权限不能更低，可以更高(子类重写的方法,访问权限不能更低只能更改)关于访问权限后面会有讲解
- 条件四:重写之后的方法不能比之前的方法抛出更大的异常，可以更少(异常会到后期有讲解)

> 这里还有几个注意事项：
>
>    注意一：方法覆盖只是针对方法，和属性无关
>
>    注意二：私有方法无法覆盖
>
>    注意三：构造方法不能被继承，所有构造方法也不能被覆盖
>
>    注意四：方法覆盖只是针对于实例方法，静态方法覆盖没有意义

#### 2.6.3方法重载和方法覆盖有什么区别？

- 方法重载发生在同一个类当中。
- 方法覆盖是发生在具有继承关系的父子类之间。
- 方法重载是一个类中，方法名相同，参数列表不同。
- 方法覆盖是具有继承关系的父子类，并且重写之后的方法必须和之前的方法一致：
  方法名一致、参数列表一致、返回值类型一致。

### 2.7super关键字

写super关键字之前，思考两个问题

- 当子类的成员变量名称和父类的成员变量名称重名的时候,那么我们怎么访问父类的成员变量呢？
- 当子类的成员方法名称和父类的成员方法名称重名的时候,那么我们怎么访问父类的成员方法呢？

这个时候就体现了super的重要性了

`super`关键字：用于修饰父类成员变量，类似于之前学过的 `this` ；`this`代表的是本类对象，而`super`代表的是父类对象；使用`super`我们可以调用父类的成员（属性和行为），注意super关键字不能访问父类私有（private修饰）的成员

子父类中出现了同名的成员变量时，在子类中需要访问父类中**非私有**成员变量（不是private修饰的）时，需要使用 `super` 关键字，修饰父类成员变量，类似于之前学过的 `this` 。

super关键字的作用：

- 用于访问父类中定义的属性
- 用于调用父类中定义的成员方法
- 用于在子类构造方法中调用父类的构造器

#### 2.7.1.this和super的图解

先上示例

```java
public class SuperTest {
    public static void main(String[] args) {
        Zi zi = new Zi();
        System.out.println(zi.num);
        zi.method();
    }
}
class Fu{
	private int num=20;
    public void method(){
        System.out.println("父类的method");
    }
    
}
class Zi extends Fu{
	int num=10;
    public void method(){
        System.out.println("父类的method");
    }   
}

```

![](https://foruda.gitee.com/images/1664453027701358113/35adc4e6_10637153.png)

- main方法进栈执行；
- 执行new Zi()，首先现将Fu、Zi两个类加载到内存（方法区）
- 初始化Fu类，再初始化子类；子类中保留父类的引用super；可以通过super来获取父类的非私有内容；
- 子类调用method方法，调用的是this区中的方法，因此输出的是Zi method...

#### 2.7.2super()

super,是手动调用还是自动的去调用呢？

示例:

```java
public class SuperTest {
    public static void main(String[] args) {
        Zi zi1=new Zi();
        Zi zi2=new Zi(20);

    }
}
class Fu{
    String name;
    int age;

    public Fu() {
        System.out.println("Fu类的无参数构造方法执行了");
    }

    public Fu(String name, int age) {
        System.out.println("Fu类的全参构造方法执行了");
        this.name = name;
        this.age = age;
    }
}

class Zi extends Fu{
    int id;
    
    public Zi(){
        System.out.println("Zi类的无参数构造方法执行了");
    }

    public Zi(int id){
        System.out.println("Zi类的有参数构造方法执行了");
        this.id=id;
    }
}
```

测试内容

```
Fu类的无参数构造方法执行了
Zi类的无参数构造方法执行了
Fu类的无参数构造方法执行了
Zi类的有参数构造方法执行了
```

得出结论:

- 在初始化子类的时候(new),会先调用父类的无参数构造方法,来实例化父类(也就是先有父后有子)

- 所以在父类当中,**一定要手动写上无参数的构造方法.这样才能不会出错,确保父类一定会实例化**

- 我们没有手动写上super这个关键字,也会调用父类的无参数构造方法。那会是什么位置呢？

- 在测试结果上我们可以看出,"Fu类的无参数构造方法执行了"总是比"Zi类的无参数构造方法执行了"先执行，那么系统一定会在构造方法的首行写调用super这个关键字的,由于是调用的构造方法 
  所以在首行会默认的有一个`super()`(`this()`是调用本类的构造方法,`super()`是调用父类的构造方法)

  ```java
  class Zi extends Fu{
      int id;
      
      public Zi(){
          super();
          System.out.println("Zi类的无参数构造方法执行了");
      }
  }
  ```

<font color="red">注意:父类的无参数构造方法一定要手动写出来</font>

<font color="red">注意:在前面说到this()也是出现在构造方法的首行的,所以this()和super()不能共存</font>

#### 2.7.3.访问父类

在前面说到用`private`修饰的无法去访问,那么既然学了super 就可以调用父类的setter和getter方法去访问

如果成员变量和成员方法和父类的一样那么怎么去访问呢？

示例：

```java
 class Fu{
    private String name;

    public Fu() {
    }

    public Fu(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void method(){
        System.out.println("父类的方法");
    }
}

class Zi extends Fu{
    public void method() {
        System.out.println("子类的方法");
        //System.out.println(super.name);父类私有成员不可以通过super获取
        System.out.println(super.getName());// 获取父类的方法
        super.method();//执行父类的方法
    }
}
```

#### 2.7.4.this和super对比的去学

this关键字：

- this能出现在实例方法中和构造方法中
- this的语法是：”this.“ ”this（）“
- this不能使用在静态方法中。
- this. 大部分是可以省略的
- this. 在区分句部变量和实例变量时候不能省略
- this（）只能出现在构造方法第一行中，通过当前的构造方法去调用”本类“中
  其他的构造方法，目的是：代码复用

super关键字

- super能出现在实例方法中和构造方法中
- super的语法是：”super.“ ”super（）“
- super不能使用在静态方法中。
- super. 大部分是可以省略的
- super. 在什么时候不能省略呢？？
      父类和子类中有同名属性，或者说有同样的方法，
      想在子类中访问父类的 super.不能省略
- super（）只能出现在构造方法第一行中，通过当前的构造方法去调用”父类“中
  的构造方法，目的是：创建子类对象的时候，先初始化父类特征。

## 3.多态

### 3.1多态概述

面向对象的三大特性——封装、继承、多态；前两个我们都学习过了，多态也是面向对象中一项重大的特征，多态体现了程序的可扩展性、代码的复用性等；

> 多态：即事物（对象）存在的多种形态，简称多态；

在生活中，多态处处看见；如"我要吃水果"，这个水果有很多种形态，苹果、梨子、香蕉等都是水果；再比如说话，猫的叫声是喵喵，狗的叫声是汪汪，苍蝇的叫声蝇蝇等；同一行为，通过不同的事物，可以体现出来的不同的形态；

### 3.2多态案例

现有一家宠物店：宠物店有寄存宠物的功能，但是运营之初，只能寄存狗，针对狗这个类，有吃饭、睡觉的行为；

> 多态的用法,就是基于这个案例来实现的

#### 3.2.1不使用多态的写法

1）定义狗类:

```java
public class Dog {
    public void eat(){
        System.out.println("狗狗正在吃饭");
    }
    public void sleep(){
        System.out.println("狗狗正在睡觉");
    }
}
```

2) 定义一个宠物店

```java
public class PetShop {
    //存放狗
    public void DogShop(Dog dog){
        dog.eat();
        dog.sleep();
    }
}

```

但是运营一段时间以后,宠物店强大了起来，就可以寄存猫了

1)定义猫类

```java
public class Cat {
    public void eat(){
        System.out.println("小猫正在吃饭");
    }
    public void sleep(){
        System.out.println("小猫正在睡觉");
    }
}
```

2)扩展原来PetShop宠物店类

```java
public class PetShop {
    //存放狗
    public void DogShop(Dog dog){
        dog.eat();
        dog.sleep();
    }
    
    //存放猫
    public void DogShop(Cat cat){
        cat.eat();
        cat.sleep();
    }
}
```

**到这里需要注意了,如果宠物店又强大可以寄存鹦鹉呢？那是不是还要在之前的宠物店这个类继续扩展,如果扩展一个，两个觉得没啥,但是要扩展上百个上千个呢。还总是要修改一些重复的代码**

#### 3.2.2多态的写法

1)定义所有宠物的父类

```java
public class Animal {
    public void eat(){
        System.out.println("动物正在吃饭");
    }
    public void sleep(){
        System.out.println("动物正在睡觉");
    }
}

```

2)修改上方的狗类去继承宠物类

```java
public class Dog extends Animal {
    public void eat(){
        System.out.println("狗狗正在吃饭");
    }
    public void sleep(){
        System.out.println("狗狗正在睡觉");
    }
}

```

3)修改上方的猫类去继承宠物类

```java
public class Cat extends Animal{

    public void eat(){
        System.out.println("猫猫正在吃饭");
    }
    public void sleep(){
        System.out.println("猫猫正在睡觉");
    }
}
```

4)修改上方的宠物店类

```java
public class PetShop {
    //存放所有的动物
    public void AnimalShop(Animal animal){// Animal animal=new Dog();
        animal.eat();
        animal.sleep();
    }
}
```

可能在这里还是不知道 这哪里是多态了呢？最后寄存宠物的时候,存放的是所有宠物的父类而不是存放的各个宠物啊。

下面进行一个测试代码：

```java
public class Test {
    public static void main(String[] args) {
        //先创建一个宠物店类
        PetShop petShop=new PetShop();
        //创建狗狗类
        Dog dog=new Dog();
        //寄存动物
        petShop.AnimalShop(dog);
    }
}

```

测试结果:

```java
狗狗正在吃饭
狗狗正在睡觉
```

根据测试结果,在宠物店寄存方法中,参数是所有宠物的父类

```java
public void AnimalShop(Animal animal){
        animal.eat();
        animal.sleep();
}
```

那为什么输出的狗狗在吃饭和睡觉呢？

我们new的是狗狗的对象,是宠物类的子类,在寄存方法中接收到的参数为

```java
Animal animal=new Dog();
```

这就引出了多态的用法，**向上转型和向下转型** 下面详细讲解

### 3.3多态用法

多态的前提

1. 继承或者实现(实现到后面来讲)
2. 方法的重写(子类方法的重写)
3. 父类引用指向子类对象

一句话概括多态就是**父类引用指向子类对象**，在上一章案例中就是父类引用（Animal）指向了子类对象（Dog、Cat），多态一般伴随着重写的出现，调用者是父类，具体执行的方法则是子类（子类重写了父类的方法运行的是子类），因为只有子类的功能才能凸显多态性，不同的子类具备的功能是不一样的，那么有重写肯定就会有继承或者实现；

多态的格式

```java
父类类型 变量名 = new 子类对象;
变量名.方法名();
```

> **当使用多态方式调用方法时，首先检查父类中是否有该方法，如果没有，则编译错误；如果有，执行的是子类重写方法。**

### 3.4多态的转型

转型分为:

- 向上转型:自动类型提升；多态本身是子类类型向父类类型向上转换的过程，这个过程是**默认**的。当父类引用指向一个子类对象时，便是向上转型。**子类型重写的方法**
  子----->父（自动类型转化）----> 父类 引用名 = new 子类（）；
- 向下转型:父类类型向子类类型向下转换的过程，这个过程是强制的。一个已经向上转型的子类对象，将父类引用转为子类引用，可以使用强制类型转换的格式，便是向下转型。**子类型特有的方法**
  父----->子（强制类型转换，需要加强制类型转换符） 子类 引用名 = (子类)父类引用;

> tips：
>
> 向上转型和向下转型可以理解为自动类型转换和强制类型转换
>
> 自动类型转换：小范围(子类)--->大范围(父类)
>
> 强制类型转换：大范围(父类)--->小范围(子类)

#### 3.4.1向上类型转换

子类重写父类的方法,在调用方法的时候 会指向子类的方法

示例：水果摊

1. 定义水果的父类

   ```java
   public class Fruit {
   
       public void buy(){
           System.out.println("客户买了水果");
       }
   }
   
   ```

2. 定义苹果类

   ```java
   public class Apple extends Fruit{
       public void buy() {
           System.out.println("客户买了苹果");
       }
   }
   
   ```

3. 定义香蕉类

   ```java
   public class Banana extends Fruit{
       public void buy() {
           System.out.println("客户买了香蕉");
       }
   }
   
   ```

4. 定义客户类

   ```java
   public class Customer {
    
       //这里Fruit fruit=new Apple()
   	//Fruit fruit=new Banana()
       public void buyFruit(Fruit fruit){
           fruit.buy();
       }
   }
   
   ```

5. 测试类

   ```java
   public class Test {
       public static void main(String[] args) {
           //创建用户类
           Customer customer=new Customer();
           //这个就是两行代码的合并 Apple apple =new Apple(); customer.buyFruit(apple);
           //用户购买苹果
           customer.buyFruit(new Apple()); 
           //用户购买香蕉
           customer.buyFruit(new Banana());
       }
   }
   ```

6. 测试结果

   ```
   客户买了苹果
   客户买了香蕉
   ```

> 在客户类当中
>
>  fruit.buy();
>
> java程序分为编译阶段和运行阶段
>
> 先来分析编辑阶段
>     对于编译器来说，编译器只知道fruit的类型是Fruit
>     所以编译器在检测语法的时候，会去 Fruit.class字节码文件找到buy()方法
>     找到了，绑定上buy()方法，编译通过，静态绑定成功。（编译阶段属于静态绑定）
> 再来分析运行阶段：
>     运行阶段的时候，实际上在堆内存中创建的java对象是Apple/Banana对象
>     所以buy()的时候，真正参与buy()的对象是Apple/Banana，所以
>     运行阶段会动态指向Apple/Banana对象的buy()方法
>     这个过程属于运行阶段的绑定（运行阶段绑定属于动态绑定）
> 多态表示多种形态
>     编译的时候一种形态(编译的时候是水果)
>     运行的时候一种形态(运行的时候是一只苹果)

#### 3.4.2向下类型转换

父类要用子类特有的方法

示例:

1. 定义动物类

   ```java
   public class Animal {
       public void move(){
           System.out.println("动物在移动");
       }
   }
   
   ```

2. 定义猫类

   ```java
   public class Cat extends Animal {
       //Cat子类 对父类进行重写
       public void move(){
           System.out.println("cat在走猫步");
       }
       //猫除了move之外,应该有自己特有的行为(动作、方法)
       //例如：抓老鼠
       public void zha(){
           System.out.println("抓老鼠");
       }
   }
   ```

3. 测试类

   ```java
   public class Test01{
    	public static void main(String[] args) {
           //new 一个Animal对象
           Animal animal = new Animal();
           //这样就是 向上转型，子类重写父类的方法 也就是父子共有的方法
           animal.move();
           //如果我们访问子类特有的方法呢 zha
           //animal.zha(); 这样编译就有错误
           //大范围(父类)--访问子类特有的方法-->小范围(子类)需要转型
           Cat cat = (Cat)animal;
           //这样就可以
           cat.zha();
       }
   }
   ```

> 解释：为什么`animal.zha()`为什么会编译会报错
>
> 对于编译器来说，编译器只知道animal的类型是Animal
> 所以编译器在检测语法的时候，会去 Animal.class字节码文件找到zha()方法
> 没有找到zha()方法，编译不通过，静态绑定失败。

### 3.5instanceof关键字

我们需要知道只要强制类型转换就会有风险，基本类型的强制类型转换会有损失精度的风险。

那么引用类型的强制类型转换也会有风险

举例：

1. 定义动物类

   ```java
   public class Animal {
       public void run(){
           System.out.println("动物在跑");
       }
   }
   
   ```

2. 定义狗类

   ```java
   public class Dog extends Animal {
       public void run(){
           System.out.println("狗狗在跑步");
       }
   }
   ```

3. 定义猫类

   ```java
   public class Cat extends Animal{
       public void run(){
           System.out.println("猫猫在跑步");
       }
   }
   ```

4. 测试：

   ```java
   public class Test {
       public static void main(String[] args) {
           Animal animal=new Dog();
           Cat cat=(Cat)animal;
           cat.run();
       }
   }
   ```
   
5. 根据测试结果:控制台输出了`java.lang.ClassCastException`类型转换异常，

   - 在编译的时候,我们new的是一个Animal 对象 编译通过
   - 在运行的时候,Animal这个对象 底层是一个Dog类型的对象
   - 在进行强制类型转换的时候 Dog和Cat没有继承关系,所以转换失败

那么我们怎么去解决呢？

**instanceof关键字：**

instanceof 是 Java 的一个二元操作符，类似于 ==，>，< 等操作符，它的作用是测试它左边的对象是否是它右边的类的实例，返回 boolean 的数据类型。

语法：

```java
boolean result = 变量名 instanceof 数据类型;
```

意思就是 判断,这个变量是否是这个数据类型

对上方测试进行修改，也就是 判断 animal是否是一个猫 如果是一个猫 才去转型

```java
public class Test {
    public static void main(String[] args) {
        Animal animal=new Dog();
        if(animal instanceof Cat){
            Cat cat=(Cat)animal;
        }else{
            System.out.println("不是该类型！");
        }

    }
}
```

# 第十章 final关键字

- final是java语言的一个关键字
- final表示最终的，不可变的
- final可以修饰变量以及方法，还有类等
- final修饰的局部变量，一旦赋值，不能重新赋值，final只能赋值一次
- final修饰的方法无法被覆盖（重写）
- final修饰的类无法被继承
- final修饰的实例变量必须手动赋值，也就是必须赶到系统赋默认值之前赋值
- static final联合修饰的变量为常量。常量名建议全部大写，每个单词用下划线
      public static final double PI=3.1415926;

修饰类：

- final修饰的类不能被继承。提高安全性，提高程序的可读性；

  ```java
  final class A{
  }
  class B extends A{     // 错误,被final修饰的类不能被继承。
  }
  
  ```

修饰方法：

- final修饰的方法不能被子类重写；

  ```java
  class A{
      public final void method(){
          System.out.println("hello");
      }
  }
  class B extends A{
      public void method(){   // 错误,被final修饰的方法不能被重写
          System.out.println("Hi");
      }
  }
  
  ```

修饰变量：

- final修饰的变量（成员变量或局部变量）只能被赋值一次；因此被final修饰的变量我们称为常量，**通常全大写命名；**

  ```java
  class  A{
      private final double PI = 3.14;     //  声明常量
      public void print(){
          PI = 3.15;          // 错误,被final修饰的变量是常量(不可更改值)
      }
  }
  
  ```

# 第十一章抽象类

## 1.抽象类概述

在继承体系中，由于父类的设计应该保证继承体系中所有子类的共性，子类往往比父类要描述的更加清晰、具体；因此我们有时需要将父类设计的抽象化；即方法只声明方法体，而没有方法具体功能，我们把没有方法主体的方法称为**抽象方法**。**包含抽象方法的类就是抽象类**。

### 1.1举例

```java
1. 厨师    成员变量:工号,姓名,工资    成员方法:工作(炒菜)
2. 保安    成员变量:工号,姓名,工资    成员方法:工作(检查外来人员)
3. 保洁    成员变量:工号,姓名,工资    成员方法:工作(负责公司的清洁)
```

图解：

![](https://foruda.gitee.com/images/1664541636157272774/c87d3575_10637153.png)

### 1.2定义

- 抽象方法 ：没有方法体的方法。
- 抽象类：包含抽象方法的类。

## 2.抽象语法

使用 `abstract` 关键字修饰方法，该方法就成了抽象方法，抽象方法只包含一个方法名，而没有方法体。

### 2.1抽象类的定义

语法：

```java
[修饰符列表] abstract class 类名{
    类体;
}
```

代码示例：

```java
public  abstract class Animal {
 	....   
}
```

### 2.2抽象方法的定义

语法：

```java
修饰符 abstract 返回值类型 方法名 (参数列表);
```

代码示例：

```java
public abstract void work()；
```

### 2.3抽象的使用

- 继承抽象类的子类**必须重写父类所有的抽象方法**。否则，该子类也必须声明为抽象类。
- 必须有子类实现该父类的抽象方法，否则，从最初的父类到最终的子类都不能创建对象，失去意义。

> 抽象类是不可以进行实例化的，抽象类本就是包含有无法实例化的抽象方法，或者说这个方法是没有任何意义的，他存在的意义就是让子类去实现它；因此抽象类是不可以实例化的，也就是不能创建对象；

代码示例:

```java
public class Demo01 {
    public static void main(String[] args) {
        Employee employee=new Cook("123","张三",28.5);
        employee.work();
    }
}

/**
 * 员工类(抽象)
 */
abstract class Employee {

    private String id;
    private String name;
    private Double salary;

    public Employee() {
    }

    public Employee(String id, String name, Double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    //注意这里要提供getter和setter方法
    

    // 抽象方法不能有方法体
    // 表示员工本就有工作,但是每个员工的工作内容是不一样的(由具体的子类来实现)
    public abstract void work();
}

/**
 * 厨师类
 */
class Cook extends Employee {
    public Cook() {
        super();
    }

    public Cook(String id, String name, Double salary) {
        super(id, name, salary);
    }

    // 必须重写父类的抽象方法
    public void work() {
        System.out.println("炒菜");

    }
}


/**
 * 保洁类
 */
class Cleaner extends Employee {
    public Cleaner() {
        super();
    }

    public Cleaner(String id, String name, Double salary) {
        super(id, name, salary);
    }

    // 必须重写父类的抽象方法
    public void work() {
        System.out.println("检查外来人员");
    }
}

/**
 * 保安类
 */
class Security extends Employee {
    public Security() {
        super();
    }

    public Security(String id, String name, Double salary) {
        super(id, name, salary);
    }

    // 必须重写父类的抽象方法
    public void work() {
        System.out.println("负责公司清洁");
    }
}
```

> 此时的方法重写，是子类对父类抽象方法的完成实现，我们将这种方法重写的操作，也叫做**实现方法**。

## 3.抽象类注意点

- 抽象类是无法实例化的，无法创建对象的，所以抽象类是用来被子类继承的。
- final和abstract不能联合使用，是对立的
- 抽象类的子类可以是抽象类。也可以是非抽象类。
- 抽象类中，可以有构造方法，是供子类创建对象时，初始化父类成员使用的。
- 抽象类中不一定有抽象方法,抽象方法必须出现在抽象类中！！！！
- 一个非抽象的类继承抽象类，必须将抽象类中的抽象方法实现(覆盖)了，这里的覆盖或者重写，就叫做实现(对抽象的实现)

> java语言中凡是没有方法体的方法都是抽象方法？
> 不对！！
> 	object类中就有很多方法都有方法体，public native int hashCode();都是以;结尾的，但他们不是抽象方法
> 	他们是调用C++的

# 第十二章接口

## 1.接口概述

### 1.1接口引入

继承抽取了类的共性，使得其子类都具备了父类的功能，提高了代码的复用性，但是有些情况下，并不是所有的子类都应该具备父类的全部功能，有些功能只是当做与"扩展功能"，并不是与生俱备的；

例如：吃饭、睡觉、上课等都是学生具有的共同的功能，我们就可以将其定义在学生类当中。但是，学生之间也是有差异的，比如课外扩展这一方面有的人喜欢学习俄语，有的人喜欢编程等等，如果讲学俄语，打代码都写到学生类当中显然是不符合逻辑的，不是每个学生都有这样的课外扩展。

像这样的独特的功能，不是每个人都具有的。可以作为"扩展功能",并不是所有都会，而是部分人会；在Java中，我们可以将扩展功能定义在接口中；

### 1.2接口的定义

接口（英文：Interface），在Java编程语言中是一个抽象类型，接口中定义的全都是抽象方法，使用Interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

一个类继承接口则需要实现该接口的所有的抽象方法，除非继承接口的类是抽象类，因此一个类继承接口我们往往称为某个类实现了（`implements`）某个接口，关键字从`extends`更换为`implements`；

### 1.3接口的特点

Java中定义接口采用`interface`关键字，关于接口有如下特点：

1. 接口也是一种引用数据类型,编译之后也是.class字节码文件

2. 接口是完全抽象的。(抽象类是半抽象的)或者说接口是特殊的抽象类

3. 接口支持多继承，一个接口可以继承多个接口

4. 接口中只包含两部分内容：一部分是：常量，一部分是：抽象方法,接口中没有其他内容了

   接口中的所有成员变量都默认是由public static final修饰的；

   接口中的所有方法都默认是由public abstract修饰的；

5. 接口没有构造方法（不能实例化对象）；

6. 类继承（实现）接口时，必须重写接口中的所有抽象方法，否则该类是抽象类；

7. 接口中没有静态代码块。

8. 接口的静态方法不能被继承下来；

## 2.接口语法

```java
public interface 接口名称{        
}
```

示例：

1. 接口

   ```java
   public interface InterfaceTest {
   
       //public static final String Guo_ji="中国"; 和下面的写法是等价的
   
       String Guo_ji="中国";
   
       //public abstract void method(); 和下面的是等价的
   
       void method();
   
       int sum(int a,int b);
       
       static  void method2(){
           System.out.println("静态方法执行了");
       }
   }
   
   ```

2. 实现类

   ```java
   public class ImplementsTest implements InterfaceTest{
   
       public void method() {
           String guo_ji = InterfaceTest.Guo_ji;
           System.out.println(guo_ji);//这里可以直接调用常量
           System.out.println("实现了接口中method的方法");
       }
   
   
       public int sum(int a, int b) {
           //两数之和的功能
           return a+b;
       }
   }
   
   ```

3. 测试类

   ```java
   public class Test {
       public static void main(String[] args) {
           //可以采用多态的形式
           InterfaceTest interfaceTest=new ImplementsTest();
           interfaceTest.method();
           InterfaceTest.method2();
   
           //调用 sum方法
           ImplementsTest implementsTest=new ImplementsTest();
           int sum = implementsTest.sum(3, 5);
           System.out.println("求和结果为"+sum);
       }
   }
   
   ```



## 3.JDK1.8新特性

### 3.1语法

在JDK7及以前，接口中只允许存在抽象方法，在JDK8中，接口允许存在**默认方法**和**静态方法**，两种方法可以为接口提供一些功能性的代码，也可以让子类选择性的重写方法，而不是强制性重写接口中的所有方法；

> 默认方法的出现可以让子类实现接口时选择性的重写方法，而不是强制性重写所有的方法；

- 默认方法：使用 `default` 修饰，**不可省略**，供子类调用或者子类重写。
- 静态方法：使用 `static` 修饰，供接口直接调用（接口中，被static修饰的方法不能被继承到子类）。

> tips：接口中默认方法的`default`修饰符不可省略，这点和我们之前学习的权限修饰符不一样；

### 3.2示例代码

- 接口

  ```java
  public interface Interface {
  
      default void method() {
          System.out.println("默认的方法");
      }
  
      default int sum(int a,int b){
          return a+b;
      }
  
      void a();
  
  }
  
  
  ```

- 实现类

  ```java
  public class Implements implements Interface{
      public void a() {
          System.out.println("这个就需要重写");
      }
  }
  
  ```

- 测试

  ```java
  public class Demo {
      public static void main(String[] args) {
          Interface in=new Implements();
          in.method();
          int sum = in.sum(1, 2);
          System.out.println(sum);
  
      }
  }
  
  ```

> tips：
>
> 默认方法可以重写也可以不重写，不重写默认被继承下来；
>
> 在接口中，静态方法不会被继承下来；

## 4.JDK1.9新特性

### 4.1语法

在JDK9中，接口除了运行存在默认方法、静态方法之外（JDK8新特性），还允许存在**私有方法**，让接口本身可以封装某段逻辑但又不想被子类继承的方法；

示例代码:

```java
public interface InterFaceName {
    private void method(){

    }
    
    private static void method2(){

    }
}

```

### 4.2示例

1. 定义接口：

   ```java
   public interface A {
   
       default void method3(){
           System.out.println("A 的默认方法~");
   
           // 调用a的私有方法
           method();
       }
   
       private void method() {
           System.out.println("A 的私有方法~");
       }
   
       private static void method2() {
           System.out.println("A 的静态私有方法~");
       }
   }
   ```

2. 定义实现类

   ```java
   public class B implements A{
   
   }
   ```

3. 测试：

   ```java
   public class Demo {
       public static void main(String[] args) {
           B b=new B();
           b.method3();
       }
   }
   
   ```

## 5.接口案例

案例：现有一家饭店，有两个厨师 一个是中国厨师，另一个是西方厨师。 这两个厨师都会西红柿炒鸡蛋和鱼香肉丝。

图解：

![](https://foruda.gitee.com/images/1664605012755348655/5501eb17_10637153.png)

代码：

1. 定义员工类

   ```java
   public class Employee {
   
       private int empId;
       private String empName;
       private double sal;
   
       public Employee() {
       }
   
       public Employee(int empId, String empName, double sal) {
           this.empId = empId;
           this.empName = empName;
           this.sal = sal;
       }
   
       public int getEmpId() {
           return empId;
       }
   
       public void setEmpId(int empId) {
           this.empId = empId;
       }
   
       public String getEmpName() {
           return empName;
       }
   
       public void setEmpName(String empName) {
           this.empName = empName;
       }
   
       public double getSal() {
           return sal;
       }
   
       public void setSal(double sal) {
           this.sal = sal;
       }
   }
   ```

2. 定义做菜的接口

   ```java
   //做菜的接口
   public interface Menu {
       void ScrambledEWT();//西红柿炒鸡蛋
       void ShreddedPork();//鱼香肉丝
   }
   
   ```

3. 定义中国厨师

   ```java
   public class ChineseChef extends Chef{
   
       public ChineseChef() {
           super();
       }
   
       public ChineseChef(int empId, String empName, double sal) {
           super(empId, empName, sal);
       }
   
       public void ScrambledEWT(){
           System.out.println("员工："+super.getEmpName());
           System.out.println("中国厨师做的西红柿炒鸡蛋真好吃！！！！！！！！！！！！！");
       }
       public void ShreddedPork(){
           System.out.println("员工："+super.getEmpName());
           System.out.println("中国厨师做的鱼香肉丝真好吃！！！！！！！！！！！！！");
       }
   }
   
   ```

4. 定义外国厨师

   ```java
   public class WesternChef extends Chef{
   
   
       public WesternChef() {
           super();
       }
   
       public WesternChef(int empId, String empName, double sal) {
           super(empId, empName, sal);
       }
   
       public void ScrambledEWT(){
           System.out.println("员工："+super.getEmpName());
           System.out.println("西方厨师做的西红柿炒鸡蛋真好吃");
       }
       public void ShreddedPork(){
           System.out.println("员工："+super.getEmpName());
           System.out.println("西方厨师做的鱼香肉丝真好吃");
       }
   
   }
   
   ```

5. 定义顾客类

   ```java
   public class Customer {
       private Chef chef;
   
       public Customer() {
       }
   
       public Customer(Chef chef) {
           this.chef = chef;
       }
   
       public Chef getEmployee() {
           return chef;
       }
   
       public void setEmployee(Chef chef) {
           this.chef = chef;
       }
   
       //提供点餐的功能
       public void order(){
           chef.ScrambledEWT();
           chef.ShreddedPork();
       }
   }
   
   ```

6. 定义测试类

   ```java
   public class TestProcedure {
       public static void main(String[] args) {
           // 先new 一个客户
           Customer customer1=new Customer();
   
           // 点中国厨师做的饭
   
           //先 new 一个中国厨师
           ChineseChef chineseChef=new ChineseChef(111,"张三",8000.00);
   
           customer1.setEmployee(chineseChef);
   
           //点菜
           customer1.order();
   
           // 上面代码的合并 (西方厨师)
           Customer customer2=new Customer(new WesternChef(222,"jack",6000.00));
           customer2.order();
   
       }
   }
   ```

> 这里感觉博主，写的有问题的话，麻烦私信指出一下 谢谢各位大佬

# 第十三章Object祖类

`java.lang.Object`类是Java语言中的根类，即所有类的父类。它中描述的所有方法子类都可以使用。在对象实例化的时候，最终找的父类就是Object。

在Object类中有一段描述

```java
Class Object is the root of the class hierarchy. Every class has Object as a superclass. All objects, including arrays, implement the methods of this class.
```

大致意思就是：
类对象是类层次结构的根。每个类都有Object作为超类。所有对象（包括数组）都实现此类的方法。 

| 方法名                         | 介绍                               |
| ------------------------------ | ---------------------------------- |
| `public String toString()`     | 返回该对象的字符串表示。           |
| `boolean equals(Object obj)`   | 指示其他某个对象是否与此对象“相等” |
| `public native int hashCode()` | 对象的内存地址                     |
| `finalize()`                   | 垃圾回收之前执行的代码             |

接下来对Object这个祖类中的方法进行讲解

## 1.toString方法

### 1.1方法摘要

| 方法名                     | 介绍                                                         |
| -------------------------- | ------------------------------------------------------------ |
| `public String toString()` | 返回该对象的字符串表示。**我们在输出对象时，默认会调用该对象的toString()方法；** |

toString方法返回该对象的字符串表示，其实该字符串内容就是对象的类型+@+内存地址值。由于toString方法返回的结果是内存地址，而在开发中，经常需要按照对象的属性得到相应的字符串表现形式，因此也需要重写它。

举例：

```java
public class ToStringDemo {
    public static void main(String[] args) {
        Person person=new Person(21,"张三");
        System.out.println(person);

    }

}

class Person{
    private int age;
    private String name;

    public Person() {
    }

    public Person(int age, String name) {
        this.age = age;
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

输出结果：

```java
toString.Person@4eec7777
包名@内存地址    
```

### 1.2.2 覆盖重写

如果不希望使用toString方法的默认行为，则可以对它进行覆盖重写。

```java
public class ToStringDemo {
    public static void main(String[] args) {
        Person person=new Person(21,"张三");
        System.out.println(person);

    }

}

class Person{
    private int age;
    private String name;

    public Person() {
    }

    public Person(int age, String name) {
        this.age = age;
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
    
    
    public String toString() {
        return "Person{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}

```

测试结果：

```java
Person{age=21, name='张三'}
```

> 重写的规则 自己说了算
>
> 上方toString方法就是idea快捷生成的 alt+insert 选择toString即可

## 2.equals方法

### 2.1 方法摘要

| 方法名                              | 作用                                 |
| ----------------------------------- | ------------------------------------ |
| `public boolean equals(Object obj)` | 指示其他某个对象是否与此对象“相等”。 |

调用成员方法equals并指定参数为另一个对象，则可以判断这两个对象是否是相同的。这里的“相同”有默认和自定义两种方式。

### 2.2 默认地址比较

如果没有覆盖重写equals方法，那么Object类中默认进行`==`运算符的对象地址比较，只要不是同一个对象，结果必然为false。

源码：

```java
public boolean equals(Object obj) {
        return (this == obj);
}
```

我们知道，引用存储的是对象的内存地址。所以这里比较的就是两个引用的内存地址

### 2.3对象内容比较

```java
public class equalsTest01 {
    public static void main(String[] args) {
		MyTime m1=new Mytime(2000,2,18);
		MyTime m2=new Mytime(2000,2,18);
        System.out.println(m1.equals(m2));//true
    }
}

class MyTime {
    int year;
    int month;
    int day;

    public Mytime() {
    }

    public Mytime(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }


    /*
    public boolean equals(Object obj){
        //如果obj是空就返回null
        if (obj==null){
            return false;
        }
        //如果obj不是Mytime 就返回false
        if (!(obj instanceof  Mytime)){
            return false;
        }
        //如果obj和this保存的内存地址相等，没必要比较了，直接返回true
        //内存相等的情况下，堆内存的对象肯定是同一个
        if(this==obj){
            return true;
        }
        //程序到此处说明了什么
        //说明obj不是null obj是mmm类型
        Mytime t=(Mytime) obj;
        if (this.year==t.year &&this.month==t.month&&this.day==t.day){
            return true;
        }
        //程序能到这里返回false
        return false;
    }
    */

    //直接生成的 alt+insert
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Mytime mytime = (Mytime) o;
        return year == mytime.year && month == mytime.month && day == mytime.day;
    }

    @Override
    public String toString() {
        return "Mytime{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }
}
```

<font color="red">注意:只要不是基本数据类型我们就要用equals来比较</font>

## 3.hashCode()方法

代码示例：

```java
/*
hashCode方法：
        在Object中的hashCode方法是怎样的？
public native int hashCode();
        这个方法不是抽象的，带有native关键字，底层调用c++程序
        hashCode()返回的是哈希码
        实际上就是一个java对象的内存地址，经过哈希算法，得出的一个值
        所以hashCode()方法的执行结果可以等同看作一个java对象的内存地址
*/
public class hashCodeTest {
    public static void main(String[] args) {
        Object o=new Object();
        int hashCodeValue=o.hashCode();
        System.out.println(hashCodeValue);
    }
}
```

## 4.finalize()方法

代码示例：

```java
/*
非重点
关于Object类中的finalize()方法
    1.在Object类中的源代码是什么？
         protected void finalize() throws Throwable { }
         GC来负责调用finalize()方法。
    2.finalize()方法只有一个方法体，里面没有代码，而且这个方法是protected修饰的
    3.这个方法不需要程序员手动调用，JVM的垃圾回收器负责调用这个方法。
    4.finalize()方法执行的时机
        当一个java对象即将被垃圾回收器回收的时候，垃圾回收器负责调用finalize()方法
    5.finalize()方法实际上是sun公司为java程序员准备的一个时机，垃圾销毁时机。
    如果希望在对象销毁时机执行一段代码的话，这段代码要写到finalize()方法中
    6.java中的垃圾回收器不是轻易启动的，垃圾太少，或者时间不到，种种条件下

 */
public class finalizeTest01 {
    public static void main(String[] args) {
        Person p=new Person();
        //怎么把person对象变为垃圾
        p=null;
        //有一段代码是建议垃圾回收器启动
        System.gc();//建议启动！！！ 不一定启动
    }
}
//业务需求：所有对象在JVM中被释放的时候，请记录一下时间
//记录对象被释放的时间点，这个负责记录的代码放在那里？finalize()
class Person{
    //重写finalize()方法
    //person类型的对象被垃圾回收器回收的时候，垃圾回收器负责调用p.finalize();
    protected void finalize() throws Throwable {
        System.out.println("即将被销毁");
    }
}
```



# 第十四章Array数组

## 1.数组概述

### 1.1什么是数组

数组是编程语言中非常常见的一种**数据结构**，是一种容器，用于存储**多个相同类型**的数据（元素）。在数组中，会为每一个元素分配一个下标（也叫索引），该下标默认从0开始，一直自增累加，我们可以通过下标来访问数组中的任意元素；

> 总结：数组就是一个容器，能够帮我们存储很多**相同类型**的数据；

### 2.2数组的特点

前面提到过，数组就是一个容器，可以存储很多相同类型的数据；此外，**数字的长度是固定的**，最大下标默认为长度-1

![](https://foruda.gitee.com/images/1664613021590084509/c699ee5a_10637153.png)



- java语言中的数组是一种引用数据类型，父类是Object类
  数组是一个容器可以容纳多个元素
  数组字面意思就一组数据的集合
- 数组当中可以存储基本数据类型和引用数据类型
- 数组因为是引用数据类型，所以数组对象是堆内存当中（数组存放在堆内存当中）
- 数组中如果存储的是”java对象“，实际上存储的是对象的引用（内存地址），数组中不能直接存储java对象
- 数组一旦创建，长度不可变
  所有的数组对象都有length属性(java自带的)来获取数组中元素的个数
- java中的数据要求存储的数据类型是一样的，int类型数组只能存储int类型，Person类型数组只能存储Person类型的数据
- 数组中每一个元素都是有下标的，下标从0开始，以1递增。最后一个元素的下标是：length-1
  下标非常重要，因为我们对数组元素进行“存取”的时候，都需要通过下标进行

## 2.数组的定义

### 2.1方式一动态

动态初始化，只指定数组的长度，由系统为数组的每个元素分配初始值；

```java
数组存储的数据类型[] 数组名字=new 数组存储的数据类型[长度];
int[] arr=new int[3];
```

> tips：数组的长度一旦指定，不能更改

### 2.2方式二静态

静态初始化，创建数组时，显式的指定数组元素的初始值，数组的长度由系统根据元素的格式来决定；

```java
数据类型[] 数组名称=new 数据类型[]{元素1,元素2,元素3....};
int[] arr=new int[]{3,5,6};
int[] arr={1,2,3,4}//正常的写法
int arr[]={1,2,3}//c的写法
```

> tips：数组已经给定了元素，就不能再指定长度了

## 3.数组的访问

**索引**：前面提到过，数组会为其中每个元素分配一个下标，这个下标我们称之为索引，索引在数组中都是从0开始，我们可以通过数组的索引来获取数组中的任意元素

访问格式

```java
数组名[索引];
```

通过索引访问数组中的元素

- 数组名[索引]：取出数组中指定索引位置上的元素
- 数组名[索引]=数值：给数值中指定索引位置上的元素赋值

示例：

```java
public class ArrayTest {
    public static void main(String[] args) {
        //静态定义
        int[] arr={1,2,3,4};
        /**
         * [I@776ec8df
         *  [: 表示数组
         *  I: 表示int类型数组, D表示double类型数组
         *  @: 没有什么用(分割作用)
         *  1540e19d: 数组在内存中的地址
         */
        System.out.println(arr);

        //下标是从0开始的
        //访问第一个数组
        System.out.println(arr[0]);//1
        //访问第二个元素
        System.out.println(arr[1]);//2

        //改变数组的值
        arr[0]=20;
        System.out.println(arr[0]);//20
    }
}

```

## 4.数组长度属性

**数组的长度属性：** 每一个数组都具有一个`length`属性，该属性的值为当前数组的元素个数，也就是数组的长度，通过`数组名.length`，可获取当前数组的长度值，返回的是一个int数，由此可以推断出，数组的最大索引值为`length-1`；

```java
public class ArrayTest02 {
    public static void main(String[] args) {

        //动态指定
        int[] arr=new int[3];

        //数组的长度
        System.out.println(arr.length);

    }
}
```



## 5.数组遍历

遍历数组的意思就是对数组整个数据的一个搜索，通过数组的长度属性我们可以知道数组里面到底有多少个元素，使用循环语句便可以逐个取出

### 方式一逐个取出

```java
public class ArrayTest03 {
    public static void main(String[] args) {
        int[] arr={1,2,3};
        System.out.println(arr[0]);
        System.out.println(arr[1]);
        System.out.println(arr[2]);
    }
}
```

### 方式二循环取出

对于上面的案例,数据不多的,可以使用逐个取出的形式,但是如果数据很多呢?我们学过循环呀

#### for循环

```java
public class ArrayTest04 {
    public static void main(String[] args) {
        int[] arr={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}

```

#### while循环

```java
public class ArrayTest04 {
    public static void main(String[] args) {
        int[] arr={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};
        int i=0;
        while (i<arr.length){
            System.out.println(arr[i]);
            i++;
        }
    }
}
```

####  do..while循环

```java
public class ArrayTest04 {
    public static void main(String[] args) {
        int[] arr={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};
        int i=0;
        do {
            System.out.println(arr[i]);
        }while (++i< arr.length);
    }
}

```

## 6.数组越界异常

测试代码如下:

```java
public class ArrayTest05 {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        System.out.println(arr[3]);
    }
}
```

创建数组，赋值3个元素，数组的索引就是0，1，2，没有3索引，因此我们不能访问数组中不存在的索引，程序运行后，将会抛出 `ArrayIndexOutOfBoundsException` 数组越界异常。



## 7.空指针异常

测试代码如下：

```java
public class ArrayTest06 {
    public static void main(String[] args) {
        int[] arr = {1, 4, 7};

        arr=null;

        System.out.println(arr[1]);
    }
}

```



## 8.数组内存图

代码：

```java
public class ArrayTest07 {
    public static void main(String[] args) {
        int[] arr={1,2,3};
        System.out.println(arr[0]);
		arr[0]=15;
        System.out.println(arr[0]);
    }
}

```

![](https://foruda.gitee.com/images/1664677963117215313/0421c0f5_10637153.png)

## 9.数组作为方法的参数和返回值

```java
public class ArrayTest06 {
    public static void main(String[] args) {
        int[] arr={1,2,3};
        print(arr);
    }

    public static void print(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}

```

输出结果：

```java
[I@776ec8df
[I@776ec8df
```

这就说明 数组也是一个引用类型，在作为方法的参数是址传递

## 10.二维数组

二维数组其实是一个特殊的一维数组，特殊在这个一维数组当中的每一个元素是一维数组

### 10.1定义

#### 静态

```java
数组数据类型[][] 变量名 = {{},{},{}....}
int[][] array={{1,1,1},{2,2},{3,3,3}};
```

#### 动态

```
数组数据类型[][] 变量名 = new 数组数据类型[][];
int[3][2] array=new int[3][2];
```

### 10.2遍历

```java
public class ArrayTest07 {
    public static void main(String[] args) {
        //动态初始化一个二维数组
        int[][] array=new int[3][3];
        //遍历
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                System.out.println(array[i][j]);
            }
        }

        //静态
        int[][] array2={{1,231,21,65},{154,654,65,4,654},{51,6,51,6}};
        printlnArray(array2);
        printlnArray(new int[][]{{5125,16,5},{51,1,65,16,5}});

    }
    //静态方法
    public static void printlnArray(int[][] array){
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                System.out.println(array[i][j]);
            }

        }

    }
}

```



# 第十五章核心API

## 1.API概述

### 1.1API概述

API（Application Programming Interface，应用程序接口）是一些预先定义的接口（功能），提供给开发人员使用，开发人员无需访问源码，或理解内部工作机制的细节；在JDK中提供了非常丰富的API接口，这些类将底层代码封装起来对外提供非常丰富而又强大的功能；我们这一章节主要来学习JDK给我提供的那些类的使用方法；

> 简单来说API就是提供的一些方法给我们开发时使用，不使用这些API也能开发，只不过API中封装的功能就得我们自己编写了；

### 1.2 Java常用包介绍

JDK中为开发开发人员提供了大量可使用的Java类库，类库是以包的形式提供的，这些包统称为API（应用程序接口），下列表格是常用包的功能介绍：

| 包名        | 简介                                                         |
| ----------- | ------------------------------------------------------------ |
| java.applet | 创建applet小程序所需的类                                     |
| java.awt    | 创建图形化界面和绘制图形图形所属的类                         |
| java.io     | 包含能提供多种输入/输出功能的类。                            |
| java.util   | 包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日期日历相关的函数。 |
| java.text   | 包含了一些java格式化相关的类                                 |
| java.sql    | 包含了java进行JDBC数据库编程的相关类/接口                    |
| java.lang   | 包含一些Java语言的核心类，如String、Math、Integer、System和Thread，提供常用功能。 |
| java.nio    | 为输入/输出操作提供缓存的类                                  |
| java.net    | 提供用于网络应用程序相关的类                                 |
| javax.sql   | 对于java.sql包进行扩展，提供了一些扩展类，如数据源、XA协议等； |
| javax.swing | 针对于AWT功能的升级、加强，提供更多、更丰富的UI组件类；      |
| javax.net   | 对于java.net包的扩展，提供了许多网络应用扩展类；             |

> java包和javax包的区别：javax的x是extension的意思，也就是扩展包，一般是对原有的包进行扩展、增强，在原有的基础上增加了许多功能类；

### 1.3 java.lang包

java.lang包是所有类库的基础，为Java应用程序的运行做支持，java.lang包已经被嵌入到JVM虚拟机中并创建为对象，因此java.lang包下的类不需要使用import语句导入；

### 1.4 Java开发手册

Java官方提供了开发手册，JDK中所有的类都可以在这个手册中查询到他的使用方法、功能、介绍等；

官方在线手册：https://docs.oracle.com/javase/8/docs/api/

我们打开查看：

![](https://foruda.gitee.com/images/1664680440257080071/3f339f25_10637153.png)

> 在线地址（中文版）：https://www.matools.com/api/java8
>
> 官方版（英文版）：https://docs.oracle.com/javase/8/docs/api/
>

## 2.Scanner类

### 2.1Scanner简介

Java 5 中添加了`java.util.Scanner`类，这是一个用于扫描输入文本的新的实用程序，可以解析基本类型和字符串的简单文本扫描器；

用法：

```java
Scanner in=new Scanner(System.in);
```

> tips：System.in 系统输入指的是通过键盘录入数据；

### 2.2 Scanner类的使用

#### 2.2.1导包

Scanner类在`java.util`包下，需要我们手动导入：

```java
import 包名.类名;
```

#### 2.2.2 创建对象

使用该类的构造方法，创建一个该类的对象

格式：

```java
数据类型  变量名  =  new 数据类型(参数列表);
```

示例：

```java
Scanner in=new Scanner(System.in);
```

> Scanner的构造方法传递的是一个输入流类型，System.in返回的是键盘输入流；关于流的知识我们到后面章节再学习；

#### 2.2.3常用方法

| 返回值    | 方法名                | 作用                                         |
| :-------- | --------------------- | -------------------------------------------- |
| `boolean` | `nextBoolean()`       | 将输入的下一个标记扫描为布尔值，并返回该值。 |
| `byte`    | `nextByte()`          | 将输入的下一个标记扫描为 `byte` 。           |
| `byte`    | `nextByte(int radix)` | 将输入的下一个标记扫描为 `byte` 。           |
| `double ` | `nextDouble()`        | 将输入的下一个标记扫描为 `double` 。         |
| `float`   | `nextFloat()`         | 将输入的下一个标记扫描为 `float` 。          |
| `int`     | `nextInt()`           | 将输入的下一个标记扫描为 `int` 。            |
| `int`     | `nextInt(int radix)`  | 将输入的下一个标记扫描为 `int` 。            |
| `String`  | `next()`              | 获取输入的一行字符串                         |
| `long`    | `nextLong()`          | 将输入的下一个标记扫描为 `long` 。           |
| `short`   | `nextShort()`         | 将输入的下一个标记扫描为 `short` 。          |

#### 2.2.4示例

```java
import java.util.Scanner;

public class ScannerTest {
    public static void main(String[] args) {
        // 创建一个Scanner扫描器
        Scanner in=new Scanner(System.in);

        System.out.println("请输入一个布尔值类型");
        boolean nextBoolean = in.nextBoolean();
        System.out.println("您输入的布尔值为"+nextBoolean);

        System.out.println("请输入一个double类型");
        double nextDouble = in.nextDouble();
        System.out.println("您输入的double为"+nextDouble);

        System.out.println("请输入一个int类型");
        int nextInt = in.nextInt();
        System.out.println("您输入的int为"+nextInt);

        System.out.println("请输入一个字符串");
        String next = in.next();
        System.out.println("您输入的字符串为"+next);



    }
}

```

运行结果

![](https://foruda.gitee.com/images/1664682239805964405/9c834eb3_10637153.png)

#### 2.2.5 next与nextLine方法

- `public String next()`：获取输入的一行字符串（该方法不会获取回车符）
- `public String nextLine()`：获取输入的一行字符串（该方法会获取回车符）

next()方法与nextLine()方法有些许类似，都是获取Scanner扫描的一行字符串，唯一不同的点在于next()方法并不会接收回车符号，而nextLine()方法则会接收回车符号，而Scanner扫描的结束信号恰好就是输入回车键；

这样一来如果使用next()方法来接收键盘输入的值时，单单输入回车并不会使得这一次扫描结束；而如果使用nextLine()则会结束本次扫描，并将接收到的回车符返回给nextLine()方法的调用者；

> Tips：不仅是next()方法不会接收回车符，nextInt()、nextDouble()等方法都不会接收回车符；因此我们在使用Scanner时，需要注意next()不要与nextLine()方法混用；

## 3.Random类

### 3.1 Random类简介

就是生成随机数的

### 3.2 Random的类使用

#### 3.2.1构造方法

| 构造方法            | 介绍                                   |
| ------------------- | -------------------------------------- |
| `Random()`          | 创建一个新的随机数生成器。             |
| `Random(long seed)` | 根据seed种子创建一个新的随机数生成器。 |

#### 3.2.2常用方法

| 返回值 | 方法名               | 作用                                 |
| ------ | -------------------- | ------------------------------------ |
| int    | `nextBoolean()`      | 随机生成一个布尔值                   |
| double | `nextDouble()`       | 随机生成一个`[0~1)`之间的double值    |
| int    | `nextInt()`          | 在int的存储范围内随机生成一个int值   |
| int    | `nextInt(int bound)` | 随机生成一个`[0~bound)`之间的int数   |
| float  | `nextFloat()`        | 随机生成一个`[0~1)`之间的float值     |
| long   | `nextLong()`         | 在long的存储方位内随机生成一个long值 |

> `[`：代表包含
>
> `)`：代表不包含

#### 3.2.3使用

```java
public class RandomTest01 {
    public static void main(String[] args) {
        //创建随机数对象
        Random random=new Random();

        //随机产生一个int类型取值范围内的数字
        int num1=random.nextInt();
        System.out.println(num1);

        //产生0-100之间的随机数。不能产生101
        //nexInt翻译为：下一个int类型的数据是101,表示只能取到100
        int num2=random.nextInt(101);//不包括101
        System.out.println(num2);
    }
}
```

#### 3.3.4练习 猜拳小游戏

```java
import java.util.Random;
import java.util.Scanner;

public class RandomTest03 {
    public static void main(String[] args) {
        Scanner in =new Scanner(System.in);
        Random random =new Random();


        while (true){
            //玩家输入 石头、剪刀、布
            System.out.println("请输入猜拳:0代表石头，1代表剪刀，2代表布");
            int nextInt = in.nextInt();
            if (nextInt>2){
                System.out.println("您输入的有错误请重新输入");
                continue;
            }
            //电脑随机生成
            int anInt = random.nextInt(3);
            if (nextInt==anInt){
                System.out.println("平局");
            }else if((nextInt==0&&nextInt==1)||(nextInt==2&&anInt==0)||(nextInt==1&&anInt==2)){
                System.out.println("玩家获胜");
                break;
            }else {
                System.out.println("电脑获胜");
            }

        }

    }
}
```



## 4.Runtime类

### 4.1 Runtime简介

在`java.lang`包中定义的Runtime类封装了与虚拟机相关的一些方法，在每一个Java进程之中都会存在有一个Runtime类的对象。Runtime类可以获取当前程序运行信息、退出程序、关闭虚拟机等操作；

### 4.2 Runtime类的使用

#### 4.2.1 获取Runtime类

Runtime的创建是由Java虚拟机来完成的，Java程序是不能自己来创建Runtime对象的；

源码：

```java
public class Runtime {
    private static final Runtime currentRuntime = new Runtime();

    private static Version version;

    /**
     * Returns the runtime object associated with the current Java application.
     * Most of the methods of class {@code Runtime} are instance
     * methods and must be invoked with respect to the current runtime object.
     *
     * @return  the {@code Runtime} object associated with the current
     *          Java application.
     */
    public static Runtime getRuntime() {
        return currentRuntime;
    }

    /** Don't let anyone else instantiate this class */
    private Runtime() {}
    
    ......
}

```

> Runtime的构造方法被私有，外界不能通过构造方法来创建Runtime类；

#### 4.2.2 常用方法

| 返回值  | 方法名                     | 作用                            |
| ------- | -------------------------- | ------------------------------- |
| Runtime | public static getRuntime() | 获取当前进程的Runtime实例       |
| long    | totalMemory()              | 获取JVM总的内存量（字节）       |
| long    | maxMemory()                | 获取JVM使用的最大内存量（字节） |
| long    | freeMemory()               | 获取JVM中的空闲内存量（字节）   |
| void    | gc()                       | 运行垃圾回收器                  |
| Process | exec(String command)       | 以单独的经常执行其他应用程序    |

#### 4.2.3 使用示例

```java
package com.dfbz.demo01;

public class Demo01 {
    public static void main(String[] args) throws Exception{
        Runtime runtime = Runtime.getRuntime();

        long totalMemory = runtime.totalMemory();
        long maxMemory = runtime.maxMemory();
        long freeMemory = runtime.freeMemory();

        System.out.println("所有可用内存空间: " + totalMemory);
        System.out.println("最大可用内存空间: " + maxMemory);
        System.out.println("空余内存空间: " + freeMemory);

        // 执行哔哩哔哩应用程序
        runtime.exec("D:\Program Files\bilibili\哔哩哔哩.exe");
   
    }
}

```

## 5.Math类

### 5.1 Math类简介

`java.lang.Math`类包含执行基本数字运算的方法。为了使用简单，其方法大都是静态方法；

### 5.2 Math类的使用

#### 5.2.1 常用方法

| 返回值 | 方法名                   | 作用                |
| ------ | ------------------------ | ------------------- |
| int    | `static abs(int a)`      | 获取绝对值          |
| double | `static ceil(doublea)`   | 向上取整            |
| double | `static floor(double a)` | 向下取整            |
| long   | `static round(double a)` | 四舍五入            |
| double | `static random()`        | 返回`[0~1)`的随机数 |

#### 5.2.2代码示例

```JAVA
package com.dfbz.demo01;

/**
 * @author lscl
 * @version 1.0
 * @intro:
 */
public class MathTest {
    public static void main(String[] args) {

        // 绝对值
        int abs = Math.abs(-20);
        System.out.println(abs);//20

        // 向上取整
        double ceil = Math.ceil(30.2);
        System.out.println(ceil);//31.0

        // 向下取整
        double floor = Math.floor(28.9);
        System.out.println(floor);//28.0

        // 四舍五入
        long r1 = Math.round(20.3);
        System.out.println(r1);//20

        // 四舍五入
        long r2 = Math.round(20.5);
        System.out.println(r2);//21

        // 生成0~1的随机数
        for (int i = 0; i < 20; i++) {
            System.out.println(Math.random());
        }
    }
}

```

## 6.String类

### 6.1String简介

`java.lang.String`类是用于创建字符串的，**创建后不可变**，其值在创建之后将被视为**常量**。String类封装了字符串类型的相关操作方法；

1.String字符串，属于引用数据类型
2.在java中随便使用""括起来的都属于String对象
3.java规定双引号括起来的字符串，是不可变的。

### 6.2 String 类的使用

#### 6.2.1构造方法

- String s = "abc";

- String s=new String();创建一个空的字符串

  String s = new String("abc");根据字符串来创建字符串对象

- String s = new String(byte数组);

- String s = new String(byte数组, 起始下标, 长度);

- String s = new String(char数组);

- String s = new String(char数组, 起始下标, 长度);

代码示例：

```java
public class StringDemo1 {
    public static void main(String[] args) {
        //第一种方式直接写
        String str1="123";
        
        //第二种方式 创建一个空的字符串对象
        String str2=new String();

        //第三种方式根据字符串来创建一个字符串对象
        String str3=new String("456");

        //第四种方式根据char数组来创建
        char[] chars={'a','b','c'};
        String str4=new String(chars);
        
        //第五种方式 根据byte数组来创建
        byte[] bytes={99,100,101};
        String str5=new String(bytes);
    }
}
```

#### 6.2.2常用的方法

| 方法名                                                       | 介绍                                                         |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| `char charAt(int index)`                                     | 返回char指定索引处                                           |
| `int compareTo(String anotherString)`                        | 比较字符串大小                                               |
| `boolean contains(CharSquence c)`                            | 判断前面的字符串是否包含后面的字符串子串                     |
| `boolean endsWith(String suffix)`                            | 测试此字符串是否以指定的后缀                                 |
| `public boolean equals(Object object)`                       | 比较两个字符串的大小必须使用equals方法                       |
| `boolean equalsIgnoreCase(String anotherString)`             | 如果两个字符串的长度相同，并且两个字符串中的相应字符等于忽略大小写，则两个字符串被认为是相等的。 |
| `public int indexOf(String str)`                             | 判断某个字符串在当前字符串中,第一次出现处的索引(下标)        |
| `pubkic byte[] getBytes()`                                   | 将字符串转成成字节数组                                       |
| `boolean isEmpty()`                                          | 判断某个字符是否为空                                         |
| `int  length()`                                              | 字符串的长度                                                 |
| `int lastIndexOf(String str)`                                | 返回指定子字符串最后一次出现的字符串中索引下标               |
| `String replace(CharSequence target,CharSequence replacement)` | 替换                                                         |
| `String[] split(String regex)`                               | 拆分字符串:以regex进行拆分 返回一个String数组                |
| `boolean startsWith(String prefix)`                          | 测试此字符串是否以指定的子字符串开头                         |
| `String substring(int beginIndex)`                           | 截取字符串,beginIndex表示参数的起始下标 到字符串最大长度     |
| `String substring(int beginIndex,int endIndex)`              | 截取字符串,beginIndex表示起始下标，endIndex表示结束下标      |
| `char[] toCharArray()`                                       | 将此字符串转换为新的字符数组。                               |
| `String toLowerCase()`                                       | 转大写                                                       |
| `String toUpperCase()`                                       | 转小写                                                       |
| `String trim()`                                              | 去除前后空白                                                 |
| `String valueOf()`                                           | 静态方法 可以将非字符串的数据转换成字符串                    |
| `String concat (String str)`                                 | 将指定的字符串连接到该字符串的末尾。                         |

#### 6.2.3比较功能方法

| 方法名                                            | 介绍                                         |
| ------------------------------------------------- | -------------------------------------------- |
| `boolean equals (Object anObject)`                | 将字符串与指定的字符串进行比较               |
| `boolean equalsIgnoreCase (String anotherString)` | 将字符串与指定的字符串进行比较，忽略大小写。 |
| `int compareTo(String anotherString)`             | 比较字符串大小                               |

代码:

```java
public class StringDemo2 {
    public static void main(String[] args) {
        String str1="hello";
        String str2="hello";
        String str3="Hello";

        //boolean equals(Object anObject) 将此字符串与指定对象进行比较。
        System.out.println(str1==str2);//这里也是true 这里是为什么后面会将
        System.out.println(str1.equals(str2));//true
        System.out.println(str1.equals(str3));//false

        //boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
        System.out.println(str1.equalsIgnoreCase(str2));//true
        System.out.println(str1.equalsIgnoreCase(str3));//true
        
		/*
        public int compareTo(String anotherString)
            比较字符串的大小
            相等为0
            前小后大 返回-1 前大后小 返回1
            在比较过程中 以第一个不相等的字符为准
         */
        System.out.println("abc".compareTo("abc"));
    }
}

```

#### 6.2.4获取方法

| 方法名                    | 介绍                   |
| ------------------------- | ---------------------- |
| `int length ()`           | 返回此字符串的长度。   |
| `char charAt (int index)` | 返回指定索引处的字符。 |

代码：

```java
public class StringDemo3 {
    public static void main(String[] args) {
        String str1="HelloWorld";

        //public int length(String str)
        System.out.println("字符串的长度"+str1.length());

        //public String concat (String str) 将指定字符添加到字符串末尾
        String str2=str1.concat("Song");
        System.out.println(str2);

        //  public char charAt (int index) ：返回指定索引处的 char值.
        char c1 = str1.charAt(0);
        char c2 = str2.charAt(1);
        System.out.println(c1);//H
        System.out.println(c2);//e

    }
}

```

#### 6.2.5转换功能方法

| 方法名                         | 介绍                                          |
| ------------------------------ | --------------------------------------------- |
| `char[] toCharArray ()`        | 返回字符串的字符表示形式                      |
| `byte[] getBytes ()`           | 返回字符串的字节表示形式                      |
| `String toLowerCase()`         | 将字符串转换为小写                            |
| `String toUpperCase()`         | 将字符串转换为大写                            |
| `String[] split(String regex)` | 拆分字符串:以regex进行拆分 返回一个String数组 |

代码：

```java
public class StringDemo04{
    public static void main(String[] args){
		/*
        public char[] toCharArray()
            将此字符串转换为新的字符数组。
         */
        char[] chars="我是中国人".toCharArray();
        for (int i = 0; i <chars.length ; i++) {
            System.out.println(chars[i]);
        }
        
        
		/*
        public byte[] getBytes()
            将字符串对象转换成字节数组
         */
        byte[] bytes="abcdef".getBytes();
        for (int i = 0; i < bytes.length; i++) {
            System.out.println(bytes[i]);
        }
        
		/*
        public String toLowerCase()
            转小写
         */
        System.out.println("ABDcsadADAS".toLowerCase());//abdcsadadas
        
        /*
        public String toUpperCase()
        	转大写
        */
        System.out.println("sadasdasd".toUpperCase());//SADASDASD
        
        /*
        public String[] split(String regex)
        	拆分字符串:以regex进行拆分,返回一个String数组
        */
        String[] ymd="1980-7-2".split("-");
        for (int i = 0; i < ymd.length; i++) {
            System.out.println(ymd[i]);
        }
        
        
            
    }
}
```

#### 6.2.6判断方法

| 方法名                              | 介绍                                                  |
| ----------------------------------- | ----------------------------------------------------- |
| `boolean contains(CharSquence c)`   | 判断前面的字符串是否包含后面的字符串子串              |
| `boolean endsWith(String suffix)`   | 测试此字符串是否以指定的后缀                          |
| `public int indexOf(String str)`    | 判断某个字符串在当前字符串中,第一次出现处的索引(下标) |
| `int lastIndexOf(String str)`       | 返回指定子字符串最后一次出现的字符串中索引下标        |
| `boolean isEmpty()`                 | 判断某个字符是否为空                                  |
| `boolean startsWith(String prefix)` | 测试此字符串是否以指定的子字符串开头                  |

代码：

```java
public class StringDemo5 {
    public static void main(String[] args) {
		/*
        public boolean contains(CharSequence s)
            判断前面字符串是否包含后面字符串
         */
        System.out.println("StringTest.java".contains("java"));
        
		/*
        public boolean endsWith(String suffix)
            判断此字符串是否以指定的后缀结尾
        */
        System.out.println("text.java".endsWith("java"));
        
		/*
        public int indexOf(String str)
            判断某个子字符串在当前字符串中第一次出现处的索引(下标)
            如果没有找到返回-1
         */
        System.out.println("jklasdhkjahakjhabcasda".indexOf("abc"));//15
        
        /*
        public int lastIndexOf(String str)
            返回指定子字符串最后一次出现的字符串中的索引(下标)
            如果找不到返回-1
         */
        System.out.println("sad21as32d1as21".lastIndexOf("2"));//13
        
		/*
        public boolean isEmpty()
            判断某个字符串是否为空,底层源码应该是调用了length()方法
         */
        String s1="";
        System.out.println(s1.isEmpty());//ture
        
		/*
        public boolean starsWith(String prefix)
            测试此字符串是否以指定的子字符串开头。
         */
        System.out.println("http://www.baidu.com".startsWith("http"));//true
        
    }
}
```

#### 6.2.7截取替换方法

| 方法                                                         | 介绍                                                     |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| `String substring(int beginIndex)`                           | 截取字符串,beginIndex表示参数的起始下标 到字符串最大长度 |
| `String substring(int beginIndex,int endIndex)`              | 截取字符串,beginIndex表示起始下标，endIndex表示结束下标  |
| `String replace(CharSequence target,CharSequence replacement)` | 替换                                                     |

代码:

```java
public class StringDemo{
    public static  void main(String[] args){
        /*
        public String substring(int beginIndex)
            beginIndex表示参数的起始下标
            截取字符串
         */
        System.out.println("http://www.baidu.com".substring(7));//www.baidu.com
        
        /*
        public String substring(int beginIndex,int endIndex)
            beginIndex表示起始下标，endIndex表示结束下标
            子串开始于指定beginIndex,并延伸到字符索引endIndex-1
         */
        System.out.println("http://www.baidu.com".substring(7,9));//ww
        
        /*
        public String replace(CharSequence target,CharSequence replacement)--掌握
            String的父接口就是CharSequence
            将与字面目标序列匹配的字符串的每个子字符串替换为指定的字面替换序列。
            替换从字符串开始到结束，例如，在字符串“aaa”中用“b”替换“aa”将导致“ba”而不是“ab”。
         */
        String newString="http://www.baidu.com".replace("http://","https://");
        System.out.println(newString);//https://www.baidu.com
    }
}
```

#### 6.2.8其他方法

| 方法                         | 介绍                                      |
| ---------------------------- | ----------------------------------------- |
| `String trim()`              | 去除前后空白                              |
| `String valueOf()`           | 静态方法 可以将非字符串的数据转换成字符串 |
| `String concat (String str)` | 将指定的字符串连接到该字符串的末尾。      |

代码：

```java
public class StringDemo{
    public static void main(String[] args){
		/*
        public String中只要一个方法是静态的，不需要new对象
            这个方法就是valueOf
            将非字符串的东西转换成字符串
            这个静态的valueOf()方法，参数是一个对象的时候，会调用toString方法

             public static String valueOf(Object obj) {
                return (obj == null) ? "null" : obj.toString();
            }

            这里运用到多态Object obj=new Customer();
         */
        String s7=String.valueOf(1516);
        System.out.println(s7);//1516
        
        /*
        public String trim()
         去除前后空白
        */
        String s8="   123     ";
        System.out.println(s8);//      123   
		String s9=s8.trim();
        System.out.println(s9);//123
        
        /*
        String concat (String str)
        	将指定的字符串连接到该字符串的末尾。
        */
        String s10="Learn";
		String s11=s10.concat("Java");
        System.out.println(s11)//LearnJava
        
    }
}
```

### 6.3常量池

常量池也是JVM中的一块内存区域，在JDK1.6及以前，常量池是存储在方法区的，在JDK1.7之后，常量池被划分到了堆内存。常量池存储的是普通字面量的常量，其存储的东西只会**保存一份**；

#### 6.3.1 String字符串的比较

创建字符串的方式有很多种，不同的方式创建的字符串在内存中的表现形式是不一样的；因此我们在使用字符串做`==`比较时需要格外注意；因为`==`比较的是两个对象的内存地址值；

```java
package com.dfbz.demo01;

/**
 * @author lscl
 * @version 1.0
 * @intro:
 */
public class Demo06 {
    public static void main(String[] args) {

        // 存储在常量池
        String s1 = "abc";
        
        String s2="abc"

        // new的东西都存储在堆内存
        String s3 = new String("abc");

        // new的东西都存储在堆内存
        String s4 = new String("abc");

        System.out.println(s1);     // abc
        System.out.println(s2);     // abc
        System.out.println(s3);     // abc
		System.out.println(s4);     // abc
        System.out.println(s1 == s2);     // true
        System.out.println(s2 == s3);     // false
		System.out.println(s1 == s3);     // false
    }
}

```

内存图解：

![](https://foruda.gitee.com/images/1664775854145074082/5c045bef_10637153.png)

#### 6.3.2 字符串的创建

我们之前就介绍过，String是一个不可变的字符序列，即字符串一旦创建就是不可变的；但我们在操作字符串时，字符串好像是可以拼接改变的，这究竟是怎么回事呢？

下列代码产生了几个字符串？

```java
String s1="1";
s1="2";
```

这个会产生两个字符串,一开始s1指向的"1"这个字符串,经过`s1="2"`之后s1就指向了"2"这个字符串串,
而"1"这个字符串没有了指向

所以会产生两个字符串，并且都在常量池当中

例二:

```java
String s1 = "10" + "1";
```

前面我们说过只要是""双引号引起来的就是一个字符串,并且在常量池当中

所以在字符串常量池当中 会有 "10" "1" "101"这三个

例三:

```java
String str=new String("abc")
```

图解：

![](https://foruda.gitee.com/images/1664776220790172773/47561d45_10637153.png)

例四:

```java
String s1 = "10";
s1 += "1";			// s1=s1+"1";
```

3个，“10”、"1"存储在常量池，"101"存储在堆内存，s1保存着堆内存中"101"的引用；

> **任何与变量相加的字符串都会产生一个新字符串**，存储在堆内存；

### 6.3.4 intern方法

`public String intern()`：当调用intern方法时，如果常量池已经包含与equals()方法确定相当的字符串时（比较的是字符串内容而不是地址值），则返回来自常量池的字符串，否则将此字符串添加到常量池中并返回；

```java
public class StringDemo {

    public static void main(String[] args) {
        String s1 = "1" + new String("1");

        // 查看常量池是否有"11"这个字符串,如果没有,则将"11"存入常量池,并返回常量池的地址
        String s2 = s1.intern();

        String s3 = "11";
        System.out.println(s2 == s3);			// true
    }
}

```

## 7.Arrays类

### 7.1 Arrays类简介

`java.util.Arrays`类是一个有关于数组操作的工具类，比如数组排序，搜索，拷贝，字符打印，数组转集合等操作。Arrays工具类中的方法均为静态方法，使用起来非常方便；

### 7.2常用方法

- `public static String toString(int[] a)`：返回该数组的字符串表示形式
- `public static void sort(int[] a) `：对a数组进行升序排序
- `public static void sort(int[] a, int fromIndex, int toIndex) `：对a数组指定范围内的元素进行排序   
  - 排序 索引fromIndex(含)~toIndex(不含)
- `public static int binarySearch(int[] a, int key)`：使用搜索前必须使用sort方法进行排序，在a数组中搜索是否存在key这个元素   
  - 如果搜索到：返回元素的索引
  - 如果没有搜索到：按顺序计算到key元素应该插入的位置index，最终返回`(-index-1)`的值
- `public static int[] copyOf(int[] original, int newLength)`：从original数组拷贝的0下标拷贝到newLength下标到新数组，并将新数组返回；其中0（含），newLength（不含）
- `public static int[] copyOfRange(int[] original, int from, int to) `：从original数组拷贝的from下标拷贝到to下标到新数组，并将新数组返回；其中from（含），to（不含）
- `public static boolean equals(int[] a, int[] a2)`：比较两个数组中的元素是否相同；

### 7.3代码示例

```java
import java.util.Arrays;
public class ArraysDemo {
    public static void main(String[] args) {

        int[] arr1 = {32, 132, 19, 28, 17, 54};
        int[] arr2 = {32, 132, 19, 28, 17, 54};

        // 比较两个数组里面的元素是否相同
        System.out.println(Arrays.equals(arr1, arr2));           // true
    }

    public static void test6() {
        int[] arr = {32, 132, 19, 28, 17, 54};

        // 从0(包含)下标开始拷贝到4下标(不包含),将中间的元素放入新数组,并将新的数组返回
        int[] newArr_1 = Arrays.copyOfRange(arr, 0, 4);

        // 从2(包含)下标开始拷贝到4下标(不包含),将中间的元素放入新数组,并将新的数组返回
        int[] newArr_2 = Arrays.copyOfRange(arr, 2, 4);

        System.out.println(Arrays.toString(arr));           // [32, 132, 19, 28, 17, 54]
        System.out.println(Arrays.toString(newArr_1));      // [32, 132, 19, 28]
        System.out.println(Arrays.toString(newArr_2));      // [19, 28]
    }

    public static void test5() {
        int[] arr = {32, 132, 19};

        // 拷贝arr数组的0下标开始拷贝2个元素到新的数组,并将新数组返回
        int[] newArr = Arrays.copyOf(arr, 2);

        System.out.println(Arrays.toString(newArr));            // [32, 132]
    }

    /**
     * binarySearch()方法
     */
    public static void test4() {
        int[] arr = {32, 132, 19, 28, 17, 54};

        // 搜索前必须先排序
        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));           // [17, 19, 28, 32, 54, 132]

        // 在数组中搜索54
        int index = Arrays.binarySearch(arr, 54);       // 4
        System.out.println(index);

        int index2 = Arrays.binarySearch(arr, 35); // 35插入的索引是:4, 最终查询到的索引位置是: (-4-1)=-5
        System.out.println(index2);                         // -5

        int index3 = Arrays.binarySearch(arr, 18);      // 18插入的索引是:1, 最终查询到的索引位置是: (-1-1)=-2
        System.out.println(index3);                         // -2
    }


    /**
     * sort()方法的其他使用
     */
    public static void test3() {
        int[] arr = {32, 132, 19, 28, 17, 54};
        System.out.println(Arrays.toString(arr));           // [32, 132, 19, 28, 17, 54]

        // 数组排序,排序0~3(不含)索引的元素
        Arrays.sort(arr, 0, 3);
        System.out.println(Arrays.toString(arr));           // [19, 32, 132, 28, 17, 54]
    }

    /**
     * sort()方法
     */
    public static void test2() {
        int[] arr = {32, 132, 19, 28, 17, 54};
        System.out.println(Arrays.toString(arr));           // [32, 132, 19, 28, 17, 54]

        // 数组排序(默认为升序排序)
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));           // [17, 19, 28, 32, 54, 132]
    }


    /**
     * toString()方法
     */
    public static void test1() {
        int[] arr = {32, 132, 19, 28, 17, 54};

        String arrStr = Arrays.toString(arr);

        System.out.println(arrStr);    // [32, 132, 19, 28, 17, 54]
    }
}

```



## 8.Date类

### 8.1Date类的概述

java.util.Date是java对日期的处理,精确到毫秒。

### 8.2Date类的构造方法

| 构造方法               | 介绍                                                         |
| ---------------------- | ------------------------------------------------------------ |
| public Date()          | 分配Date对象并初始化此对象，以表示分配它的时间（精确到毫秒）。 |
| public Date(long date) | 分配Date对象并初始化此对象，以表示自从标准基准时间（称为“历元（epoch）”，即1970年1月1日00:00:00 GMT）以来的指定毫秒数。 |

示例代码:

```java
public class DateDemo1 {
    public static void main(String[] args) {
        Date date1=new Date();
        System.out.println(date1);//Mon Oct 03 14:52:45 CST 2022

        Date date2=new Date(1L);
        System.out.println(date2);//Thu Jan 01 08:00:00 CST 1970
    }
}

```

### 8.3常用方法

#### 8.3.1 获取相关

`int getDate()`：获取一个月中的日期；

`int getDay()`：获取一个星期中的星期几，取值范围：0-6；0代表星期天、1代表星期1、2代表星期2；

`int getHours()`：获取小时；

`int getMinutes()`：获取分钟；

`int getMonth()`：获取0-11的月份，0代表1月，1代表2月以此类推；因此我们获取月份一般使用：`getMonth()+1`

`int getSeconds()`：获取秒；

`long getTime()`：返回自1970年1月1日以来到当前日期的毫秒数；

`int getYear()`：获取1900年到当前年的年份，如121代表2021年，120代表2020年以此类推…

#### 8.3.2 设置相关

`void setYear(int year)` 设置年，从1900为0年，设置1为1901年，设置20为1920年，设置120为2020年…

`void setMonth(int month)`：设置月，范围0-11，0为1月，1为2月，11为12月…

`void setDate(int date)`：设置一个月的某天；

`void setHours(int hours)`：设置小时

`void setMinutes(int minutes)`：设置分钟；

`void setSeconds(int seconds)` ：设置秒；

`void setTime(long time)`：设置1970年1月1日到现在的毫秒值；

### 8.4DateFormat类

`java.text.DateFormat` 是日期/时间格式化子类的抽象类，我们通过这个类可以帮我们完成日期和文本之间的转换,也就是可以在Date对象与String对象之间进行来回转换。

- **格式化**：按照指定的格式，从Date对象转换为String对象。
- **解析**：按照指定的格式，从String对象转换为Date对象。

#### 8.4.1 构造方法

由于DateFormat为抽象类，不能直接使用，所以需要常用的子类`java.text.SimpleDateFormat`。这个类需要一个模式（格式）来指定格式化或解析的标准。构造方法为：

`public SimpleDateFormat(String pattern)`：用给定的模式和默认语言环境的日期格式符号构造SimpleDateFormat。

参数pattern是一个字符串，代表日期时间的自定义格式。

#### 8.4.2格式规则

| 标识字母（区分大小写） | 含义 |
| ---------------------- | ---- |
| y                      | 年   |
| M                      | 月   |
| d                      | 日   |
| H                      | 时   |
| m                      | 分   |
| s                      | 秒   |

例如：

```java
public class Demo01 {
    public static void main(String[] args) {
        // 对应的日期格式如：2022-10-3 15：03：99
        DateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
    }
}
```



#### 8.4.3常用方法

DateFormat类的常用方法有：

- `public String format(Date date)`：将Date对象格式化为字符串。
- `public Date parse(String source)`：将字符串解析为Date对象。

代码示例：

```java
public class Demo2 {
    public static void main(String[] args)  throws Exception{
        //获取系统当前时间(精确到毫秒的系统当前时间)
        //直接调用无参数构造方法就行
        Date nowTime=new Date();
        System.out.println(nowTime);

        SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH-mm-ss SSS");
        String noTimeStr=sdf.format(nowTime);
        System.out.println(noTimeStr);//2022-03-29 16-54-33 994


        /*
        SimpleDateFormat sdf=new SimpleDateFormat("格式不能随便写，要和日期字符串格式相同")
        若格式不相同会出现异常java.text.ParseException throws ParseException
        字符串转换成日期类型
         */
        String time="2008-08-08 08:08:08 888";
        SimpleDateFormat sdf2=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        Date dateTime=sdf2.parse(time);
        System.out.println(dateTime);//Fri Aug 08 08:08:08 CST 2008

    }
}

```



## 9.Calendar类

### 9.1Calendar类概述

`java.util.Calendar`是日历类，在Date后出现，替换掉了许多Date的方法。该类将所有可能用到的时间信息封装为静态成员变量，方便获取。日历类就是方便获取各个时间属性的。

### 9.2获取方式

Calendar为抽象类，Calendar类在创建对象时并非直接创建，而是通过静态方法创建，返回子类对象，如下：

`public static Calendar getInstance()`：使用默认时区和语言环境获得一个日历

```java
import java.util.Calendar;

public class Demo01 {
    public static void main(String[] args) {

        // 获取日历对象
        Calendar cal = Calendar.getInstance();
    }
}

```



### 9.3常用方法

根据Calendar类的API文档，常用方法有：

`public int get(int field)`：返回给定日历字段的值。

`public void set(int field, int value)`：将给定的日历字段设置为给定值。

`public abstract void add(int field, int amount)`：根据日历的规则，为给定的日历字段添加或减去指定的时间量。

`public Date getTime()`：返回一个表示此Calendar时间值（从历元到现在的毫秒偏移量）的Date对象。

`public long getTimeInMillis()`：获取1970年到当前时间的毫秒值；

Calendar类中提供很多成员常量，代表给定的日历字段：

| 字段值             | 含义                                                   |
| ------------------ | ------------------------------------------------------ |
| YEAR               | 年                                                     |
| MONTH              | 月（从0开始，可以+1使用）                              |
| DATE、DAY_OF_MONTH | 月中的天（几号）                                       |
| HOUR               | 时（12小时制）                                         |
| HOUR_OF_DAY        | 时（24小时制）                                         |
| MINUTE             | 分                                                     |
| SECOND             | 秒                                                     |
| DAY_OF_WEEK        | 周中的天（周几，0为星期6,1为星期天,2为星期1,3为星期2） |
| WEEK_OF_MONTH      | 一个月的第几周                                         |

#### 9.3.1get方法

```java
package com.dfbz.demo01;

import java.util.Calendar;


public class Demo02 {
    public static void main(String[] args) {
        Calendar calendar = Calendar.getInstance();

        System.out.println("年： " + calendar.get(Calendar.YEAR));
        System.out.println("月： " + calendar.get(Calendar.MONTH));    
        System.out.println("日： " + calendar.get(Calendar.DAY_OF_MONTH));  
        System.out.println("星期几： " + calendar.get(Calendar.DAY_OF_WEEK));
        System.out.println("一个月第几周： " + calendar.get(Calendar.WEEK_OF_MONTH));
        System.out.println("时： " + calendar.get(Calendar.HOUR));
        System.out.println("分： " + calendar.get(Calendar.MINUTE));
        System.out.println("秒： " + calendar.get(Calendar.SECOND));
    }
}

```

>  0-11,4代表5月,5代表6月
>  0-6,0代表星期六,1代表星期天

#### 9.3.2set方法

```java
package com.dfbz.demo01;

import java.util.Calendar;


public class Demo03 {
    public static void main(String[] args) {
        Calendar calendar = Calendar.getInstance();

        calendar.set(Calendar.YEAR, 2020);
        calendar.set(Calendar.MONTH, 10);            
        calendar.set(Calendar.DAY_OF_MONTH, 8);        
        calendar.set(Calendar.HOUR, 10);
        calendar.set(Calendar.MINUTE, 18);
        calendar.set(Calendar.SECOND, 50);

        System.out.println("年： " + calendar.get(Calendar.YEAR));
        System.out.println("月： " + calendar.get(Calendar.MONTH));      
        System.out.println("日： " + calendar.get(Calendar.DAY_OF_MONTH));
        System.out.println("星期几： " + calendar.get(Calendar.DAY_OF_WEEK));      
        System.out.println("时： " + calendar.get(Calendar.HOUR));
        System.out.println("分： " + calendar.get(Calendar.MINUTE));
        System.out.println("秒： " + calendar.get(Calendar.SECOND));

    }
}

```



#### 9.3.3add方法

```java
import java.util.Calendar;
public class Demo04 {
    public static void main(String[] args) {
        Calendar cal = Calendar.getInstance();

        
        System.out.println(cal.get(Calendar.YEAR) + "年" + (cal.get(Calendar.MONTH) + 1) + "月" + cal.get(Calendar.DAY_OF_MONTH) + "日");

        // 使用add方法
        cal.add(Calendar.DAY_OF_MONTH, 2); 

        cal.add(Calendar.YEAR, -3); 

        System.out.println(cal.get(Calendar.YEAR) + "年" + (cal.get(Calendar.MONTH) + 1) + "月" + cal.get(Calendar.DAY_OF_MONTH) + "日");
    }
}

```

#### 9.3.4getTime方法

```java
import java.util.Calendar;
import java.util.Date;

public class Demo05 {
    public static void main(String[] args) {
        Calendar cal = Calendar.getInstance();
        Date date = cal.getTime();
        System.out.println(date);          
    }
}

```

## 10.StringBuilder类

### 10.1StringBuilder简介

java中的字符串是不可变的，每一次拼接都会产生新的字符串这样会占用大量的方法区内存。造成内存空间的浪费

```java
 String s=”abc“;
    s+="hello";
```

 就以上两行代码，就导致在方法区字符串常量池中创建了3个对象

```java
 "abc","abchello","hello"
```

  java.lang.StringBuilder又称为可变字符序列，是个字符串的缓冲区，即它是一个容器，容器中可以装很多字符串。并且能够对其中的字符串进行各种操作。它的内部拥有一个数组用来存放字符串内容，进行字符串拼接时，直接在数组中加入新内容。StringBuilder会自动维护数组的扩容。(默认16字符空间，超过自动扩充)

```java
public StringBuilder() {
        super(16);
}
```



### 10.2构造方法

- `public StringBuilder()`：构造一个空的StringBuilder容器。
- `public StringBuilder(String str)`：构造一个StringBuilder容器，并将字符串添加进去。

示例代码：

```java

public class Demo01 {
    public static void main(String[] args) {
        StringBuilder sb1 = new StringBuilder();
        System.out.println(sb1); // (空白)
        
        // 使用带参构造
        StringBuilder sb2 = new StringBuilder("abc");
        System.out.println(sb2); // abc
    }
}

```

​    就以上两行代码，就导致在方法区字符串常量池中创建了3个对象
​    "abc","abchello","hello"

### 10.3常用方法

- `public StringBuilder append(...)`：添加任意类型数据的字符串形式，并返回当前对象自身。
- `public String reverse()`：将当前对象的字符串反转，并返回当前对象自身。
- `public String toString()`：将当前StringBuilder对象转换为String对象。

示例代码：

```java
public class StringBuilderDemo {
    public static void main(String[] args) {
        StringBuilder stringBuilder=new StringBuilder();
        stringBuilder.append("hello");
        stringBuilder.append("123");
        System.out.println(stringBuilder);//hello123

        stringBuilder.reverse();
        System.out.println(stringBuilder);//321olleh

        String s = stringBuilder.toString();
        System.out.println(s);//321olleh
    }
}

```

### 10.4StringBuilder和String

```java
public class StringBuliderTest01 {
    public static void main(String[] args) {
        String s="";
        //这样做会给java的方法区字符串常量池带来很大压力
        for (int i = 0; i < 10; i++) {
            s+=i;
            System.out.println(s);
        }
        //这两行的代码区别就是
        /*
        String 每次连接的时候，他都会产生一个新的字符串，然后s指向没有都发生改变
        0------------第一次 s指向
        01----------第二次 s指向 之后字符串“0”就会没有指向
        012---------第三次 s指向 之后字符串”01“没有指向
        0123    .
        01234   .
        012345  .
        0123456 .
        01234567.
        012345678
        0123456789
        依次类推 会产生大量的空间浪费
        这样会产生"0","01","012","0123","01234" .....”012345678“这么多字符串 导致空间浪费
        最后只有“0123456789”s是指向的
         */


        /*
        StringBuffer：
        0
        01
        012
        0123
        01234
        012345
        0123456
        01234567
        012345678
        0123456789
        最后只是产生了一个字符串“0123456789”，就是因为append 字符串的拼接
         */
        StringBulider s1=new StringBulider(100);
        for (int i = 0; i < 10; i++) {
            s1.append(i);
            System.out.println(s1);
        }
    }
}
```

> 注意：String和StringBufilder 底层都是一个byte[]数组

### 10.5 StringBuilder和StringBuffer

其实这两个类方法名都是一样的,但是我们看底层的源码可以知道 StringBuffer比StringBulider方法上多一个synchronized这样的一个修饰符

后面在多线程中会讲解synchronized这个修饰词 ,现在就给一个结论 StringBuffer是线程安全的,StringBuilder是非线程安全的

既然有得就有失,所以在效率方面 StringBuilder的效率要比StringBuffer要高

### 10.6总结

- StringBuffer/StringBuilder可以看做可变长度字符串。
- StringBuffer/StringBuilder初始化容量16.
- StringBuffer/StringBuilder是完成字符串拼接操作的，方法名：append
- StringBuffer是线程安全的。StringBuilder是非线程安全的。
- 频繁进行字符串拼接不建议使用“+”



> 两个面试题:
>
> String为什么是不可变的？
>
> ​	我看过源代码，String类中一个byte[]数组，这个byte[]数组采用了final修饰，private final byte[] value;
> 因为数组一旦创建长度不可变。并且被final修饰的引用一旦指向了某个对象之后，不可以
> 再指向其他对象，所以String是不可变的！
> ”abc“无法变成”abcd“
>
> StringBuilder/StringBuffer为什么是可变的？
>
> 我看过源代码，StringBuffer/StringBuilder内部实际上是一个byte[]数组，
> 这个byte[]数组没有被final修饰，StringBuffer/StringBuilder的初始化
> 容量我记得是16.当存满之后会进行扩容，底层调用了数组拷贝的方法
> System.arraycopy()...是这样扩容的。所以StringBuffer/StringBuilder
> 适合于使用字符串的频繁拼接操作
>
> 



## 11.System类

### 11.1 常用方法

`java.lang.System`是Java中的系统类，主要用于获取系统的属性数据，没有构造方法。类中提供了大量的静态方法，可以获取与系统相关的信息或系统级操作，在System类的API文档中，常用的方法有：

- `public static long currentTimeMillis()`：返回以毫秒为单位的当前时间。
- `public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`：将数组中指定的数据拷贝到另一个数组中。
- `public static exit(int status)`：该方法用于退出jvm，如果参数是0表示正常退出jvm，非0表示异常退出jvm。
- `public static getProperties()`：该方法用于获取系统的所有属性。属性分为键和值两部分，它的返回值是Properties。
- `public static gc()`：该方法用来建议jvm赶快启动垃圾回收器回收垃圾。只是建议启动，但是Jvm是否启动又是另外一回事。

### 11.2System类的使用

#### 11.2.1currentTimeMillis

通过System的currentTimeMillis()方法我们可以获取当前时间的毫秒值，有了毫秒值我们可以将其转换为Date对象、Calendar对象等进行日期的运算；

```java
public class SystemDemo {
    public static void main(String[] args) {
        long currentTimeMillis = System.currentTimeMillis();
        System.out.println(currentTimeMillis);

        Date date=new Date(currentTimeMillis);
        System.out.println(date);

        SimpleDateFormat simpleDateFormat=new SimpleDateFormat("yyyy-MM-dd");
        String format = simpleDateFormat.format(date);
        System.out.println(format);

        Calendar calendar=Calendar.getInstance();

        calendar.setTimeInMillis(currentTimeMillis);
        System.out.println(calendar.get(Calendar.YEAR));
        System.out.println(calendar.get(Calendar.MONDAY)+1);
        System.out.println(calendar.get(Calendar.DAY_OF_MONTH));


    }
}

```

#### 11.2.2 arraycopy

`public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`：将数组中指定的数据拷贝到另一个数组中。

数组的拷贝动作是系统级的，性能很高。System.arraycopy方法具有5个参数，含义分别为：

| 参数序号 | 参数名称 | 参数类型 | 参数含义             |
| -------- | -------- | -------- | -------------------- |
| 1        | src      | Object   | 源数组               |
| 2        | srcPos   | int      | 源数组索引起始位置   |
| 3        | dest     | Object   | 目标数组             |
| 4        | destPos  | int      | 目标数组索引起始位置 |
| 5        | length   | int      | 复制元素个数         |

```java
public class SystemDemo2 {
    public static void main(String[] args) {
        int[] oldArr={1,2,3,4};
        int[] newArr={5,6,7,8};
        System.arraycopy(oldArr,0,newArr,0,4);
        System.out.println(Arrays.toString(oldArr));//[1, 2, 3, 4]
        System.out.println(Arrays.toString(newArr));//[1, 2, 3, 4]


    }
}

```

#### 11.2.3 exit

exit用于退出Jvm，需要注意的是：0或者非0的数据都可以退出Jvm,对于用户而言没有任何区别，对于windows是有作用的，因为如果传非0对于windows而言是异常终止的，如果是正版的操作系统，对于异常退出的软件，需要把这些异常退出的软件信息做成报告发送给微软，微软就可以针对这些问题对系统做出一些修改。

```java
public class Demo03 {
    public static void main(String[] args) {

        for (int i = 0; i < 10; i++) {
            System.out.println(i);
            if (i == 5) {
                System.exit(0);         // 程序退出
            }
        }
    }
}
```



#### 11.2.4 gc

在Java程序运行时，如果一个对象没有再被引用，或者被指向为null，那么这个对象就应该被标记为"垃圾"，Jvm会根据某种算法来定时清除这些对象来释放内存；我们也可以通过System.gc()方法告诉Jvm垃圾回收器，叫他来清除一下垃圾；但gc方法只是建议Jvm赶快启动垃圾回收器回收垃圾。Jvm是否启动又是另外一回事。

```java
package com.dfbz.demo01;

import java.util.Properties;

public class Demo04 {
    public static void main(String[] args) {

        for (int i = 0; i < 10; i++) {
            // 使用匿名对象(没有对象保存返回值)
            new Student();

            // 触发垃圾回收器
            System.gc();
        }
    }
}

class Student {
    @Override
    protected void finalize() throws Throwable {
        System.out.println("垃圾回收器执行了");
    }
}

```

> finalize()：是Object类的一个方法，如果一个对象被垃圾回收 器回收的时候，会先调用对象的finalize()方法。

## 12.包装类

### 12.1包装类概述

Java提供了两个类型系统，基本类型与引用类型，使用基本类型在于效率，然而很多情况，会创建对象使用，因为对象可以做更多的功能，如果想要我们的基本类型像对象一样操作，就可以使用基本类型对应的包装类，如下：

| 基本类型 | 对应的包装类（位于java.lang包中） |
| -------- | --------------------------------- |
| byte     | Byte                              |
| short    | Short                             |
| int      | **Integer**                       |
| long     | Long                              |
| float    | Float                             |
| double   | Double                            |
| char     | **Character**                     |
| boolean  | Boolean                           |

### 12.2拆箱与装箱

基本类型与对应的包装类对象之间，来回转换的过程称为”装箱“与”拆箱“：

**装箱**：从基本类型转换为对应的包装类对象。

**拆箱**：从包装类对象转换为对应的基本类型

用Integer与 int为例：（了解即可）

基本数值---->包装对象

```java
Integer i = new Integer(4);//使用构造函数函数
Integer ii = Integer.valueOf(4);//使用包装类中的valueOf方法
```

包装对象---->基本数值

```java
int num = i.intValue();
```

### 12.3 自动装箱与自动拆箱

由于我们经常要做基本类型与包装类之间的转换，从Java 5（JDK 1.5）开始，基本类型与包装类的装箱、拆箱动作可以自动完成。例如：

```java
Integer i = 4;		// 自动装箱。相当于Integer i = Integer.valueOf(4);
i = i + 5;			// 等号右边：将i对象转成基本数值(自动拆箱) i.intValue() + 5;
					// 加法运算完成后，再次装箱，把基本数值转成对象。

```

### 12.4 基本类型与字符串之间的转换

#### 12.4.1  基本类型转换为String

这里以int类型为讲解

```java
String s=String.valueOf(int i)
String s=""+i;
```

#### 12.4.2 String转换成对应的基本类型

除了Character类之外，其他所有包装类都具有parseXxx静态方法可以将字符串参数转换为对应的基本类型：

`public static byte parseByte(String s)`：将字符串参数转换为对应的byte基本类型。

`public static short parseShort(String s)`：将字符串参数转换为对应的short基本类型。

`public static int parseInt(String s)`：将字符串参数转换为对应的int基本类型。

`public static long parseLong(String s)`：将字符串参数转换为对应的long基本类型。

`public static float parseFloat(String s)`：将字符串参数转换为对应的float基本类型。

`public static double parseDouble(String s)`：将字符串参数转换为对应的double基本类型。

`public static boolean parseBoolean(String s)`：将字符串参数转换为对应的boolean基本类型。

```java
public class Demo01 {
    public static void main(String[] args) {

        // 字符串转byte
        byte b = Byte.parseByte("100");

        // 字符串转short
        short s = Short.parseShort("100");

        // 字符串转num
        int num = Integer.parseInt("100");
        
        // 字符串转long
        long l = Long.parseLong("100");

        // 字符串转float
        float f = Float.parseFloat("100.0");
        
        // 字符串转double
        double d = Double.parseDouble("100.0");
        
        // 字符串转boolean
        boolean boo = Boolean.parseBoolean("true");

        // 字符串转char
        char c = "a".charAt(0);
    }
}

```

### 12.5 其他方法(以Integer)

```java
public class IntegerTest08 {
    public static void main(String[] args) {
        /*
        重点方法:
            static int parseInt(String s)
            静态方法 传参String  返回int
         */
        int value=Integer.parseInt("123");
        System.out.println(value);

        //照葫芦画瓢
        double c=Double.parseDouble("21.056");
        System.out.println(c+1);

        float d=Float.parseFloat("13.01");
        System.out.println(d+1);

        //static Integer valueOf(int i)
        //静态的:将int--->Integer
        Integer integer1=Integer.valueOf(100);
        System.out.println(integer1);

        //static Integer valueOf(String i)
        //静态的:将String-->Integer
        Integer integer2=Integer.valueOf("100");
        System.out.println(integer2);

        //static String toBinaryString(int i)
        //静态的：将十进制转换成二进制字符串.
        String binaryString=Integer.toBinaryString(3);
        System.out.println(binaryString);//"11"二进制字符串

        //static String toHexString(int i)
        //静态的：将十进制转换成十六进制字符串.
        String hexString=Integer.toHexString(16);
        System.out.println(hexString);//"10"

        //static String toOctalString(int i)
        //静态的：将十进制转换成八进制字符串.
        String octalString=Integer.toOctalString(8);
        System.out.println(octalString);//"10"

        /*
        扩展
         public String toString() {
                return getClass().getName() + "@" + Integer.toHexString(hashCode());
            }
        getClass().getName()对应java.lang.Object
        Integer.toHexString(hashCode());对应3b07d329

         */
        System.out.println(new Object());//java.lang.Object@3b07d329

    }
}

```

### 12.6 String int Integer之间的转换

```JAVA
public class IntegerTest09 {
    public static void main(String[] args) {
        //String-->int
        String string1="110";
        int valInt1=Integer.parseInt(string1);
        System.out.println(valInt1);//110

        //int-->String
        String string2=String.valueOf(valInt1);
        String string3=""+valInt1;
        System.out.println(string2);//110
        System.out.println(string3);//110

        //int-->Integer 自动装箱
        Integer integer1=1000;
        System.out.println(integer1);

        //Integer-->int自动拆箱
        int valInt2=integer1;
        System.out.println(valInt2);


        //String-->Integer
        Integer valString=Integer.valueOf("123");

        //Integer-->String
        String string4=String.valueOf(valString);
    }
}
```

> String---int：
> 	int i=Integer.parseInt(String str)
>
> int---String:
> 	String s=""+String类型的数据
>
> int---Integer:自动装箱
>
> Integer---int:自动拆箱
>
> String---Integer:
> 	Integer i=Integer.valueOf(String str);
>
> Integer-->String:
> 	String str=String.valueOf(Integer i);

### 12.7 缓存问题

为了提高的程序提高效率，将-128到127之间所有的包装对象，提前创建好
放到了一个方法区的”整数型常量池“当中了，目的是只要用这个区间的数据不需要再new了
直接从整数型常量池当中取出来

```java
cache，就是缓存机制
优点：效率高
缺点：消耗内存

缓存机制要重视,大型项目中的重要优化手段就是:cache缓存机制
 */
public class IntegerTest06 {
    public static void main(String[] args) {
        Integer a=128;
        Integer b=128;
        System.out.println(a==b);//false

        /*

        原理：x保存的内存地址和y保存的内存地址是一样的
         */
        Integer x=127;
        Integer y=127;
        System.out.println(x==y);//true
    }
}
```



## 13.数值类

8个基本数据类型都是有大小的，例如一个byte类型变量只能存储-128~127之间的数字，多了就存不下，这样在面对大数据量的计算时（如科学计算）基本数据类型会出现很大的问题（存不下）；

如果基本的整数和浮点数精度不能够满足需求，那么可以使用java.math包中两个很有用的类：BigInteger、BigDecimal。这两个类可以处理包含任意长度数字序列的数值；BigInteger类实现任意精度的整数运算，BigDecimal实现任意精度的浮点数运算；

### 13.1BigInteger

可以通过一个字符串来构建一个BigInteger类，BigInteger类封装了大量对数字的加减乘除等操作的方法，而字符串可以任意长度，也就是说BigInteger支持任意长度的数字进行加减乘除等运算；

#### 13.1.1 获取BigInteger对象

构造方法：   

- `public BigInteger(String val)`：通过一个字符串来构建BigInteger对象；

普通方法：   

- `public static BigInteger valueOf(long val)`：通过一个Long数值来构建一个BigInteger对象，由于BigInteger对象都是针对于非常庞大的数据（远远超过了Long的取值范围）进行运算，因此很少使用这个方法来构建BigInteger对象；

代码:

```java
import java.math.BigInteger;

public class Demo01_BigInteger的获取 {
    public static void main(String[] args) {
        // 基于一个Long数值来创建一个BigInteger对象
        BigInteger big1 = BigInteger.valueOf(1230020200L);

        // 基于一个字符串来创建一个BigInteger对象
        BigInteger big2 = new BigInteger("234234234231213123123123123213");
    }
}

```

#### 13.1.2BigInteger的常用方法

`public BigInteger add(BigInteger val)`：返回值为 (this + val)

`public BigInteger subtract(BigInteger val)`：返回值为 (this - val)

`public BigInteger multiply(BigInteger val)`：返回值为 (this * val)

`public BigInteger divide(BigInteger val)`：返回值为 (this / val)

`public BigInteger mod(BigInteger m)`：返回值为(this % m)

`public int compareTo(BigInteger val)`：如果this的数值比val的大，返回1，否则返回-1，如果相等则返回0

代码：

```java
import java.math.BigInteger;


public class Demo02_BigInteger的常用方法 {
    public static void main(String[] args) {
        BigInteger num1 = new BigInteger("100");
        BigInteger num2 = new BigInteger("10");

        System.out.println(num1.add(num2));                 // 110
        System.out.println(num1.subtract(num2));            // 90
        System.out.println(num1.multiply(num2));            // 1000
        System.out.println(num1.divide(num2));              // 10
        System.out.println(num1.mod(num2));                 // 0
        System.out.println(num1.compareTo(num2));           // 1
    }
}

```

#### 13.1.3BigInteger转换为基本数据类型

```java
import java.math.BigInteger;

public class Demo0 {
    public static void main(String[] args) {
        BigInteger num = new BigInteger("10");

        // BigInteger转换为对应的基本数据类型
        byte b = num.byteValue();
        short s = num.shortValue();
        int i = num.intValue();
        long l = num.longValue();
        float f = num.floatValue();
        double d = num.doubleValue();

        // BigInteger转换为字符串
        String str = num.toString();
    }
}

```

#### 13.1.4 BigInteger注意事项

BigInteger只能构建整数，不能构建小数，否则会出现程序异常现象；另外，**如果两个BigInteger计算的值出现小数时则会出现丢失精度现象；**

```java

import java.math.BigInteger;
public class Demo04_浮点数运算 {
    public static void main(String[] args) {
        BigInteger num1 = new BigInteger("10");
        BigInteger num2 = new BigInteger("3");

        System.out.println(num1.divide(num2));          // 结果为: 3; 出现丢失精度现象
    }
    
    public static void test(){
        
        // Exception in thread "main" java.lang.NumberFormatException: For input string: "9.3"
        BigInteger num1 = new BigInteger("9.3");
        BigInteger num2 = new BigInteger("2.5");

        // 程序异常: Exception in thread "main" java.lang.NumberFormatException: For input string: "9.3"
        System.out.println(num1.multiply(num2));
    }
}

```

### 13.2BigDecimal

BigInteger是针对大整数的运算，BigDecimal则是针对大型浮点数的运算。值得注意的是，BigDecimal也可以针对大型整数进行运算，也就是包含了BigInteger的绝大部分功能，在大部分场景下我们使用BigDecimal会比较多，他与BigInteger其他特性几乎一样；

#### 13.2.1获取BigDecimal对象

静态方法：   

`public static BigDecimal valueOf(long val)`：基于一个Long类型的数值来构建BigDecimal对象

`public static BigDecimal valueOf(double val) `：基于一个Double类型的数值来构建BigDecimal对象

构造方法：   

`public BigDecimal(String val)`：基于一个字符串来构建BigDecimal对象

```java
import java.math.BigDecimal;

public class Demo01_BigDecimal的获取 {
    public static void main(String[] args) {

        // 基于一个Long类型的数值来构建BigDecimal对象
        BigDecimal big1 = BigDecimal.valueOf(1000);

        // 基于一个Double类型的数值来构建BigDecimal对象
        BigDecimal big2 = BigDecimal.valueOf(399.38);

        // 基于一个字符串来构建BigDecimal对象
        BigDecimal big3 = new BigDecimal("99999");

        // 基于一个字符串来构建BigDecimal对象
        BigDecimal big4 = new BigDecimal("99999.99");
    }
}

```

#### 13.2.2BigDecimal的常用方法

BigDecimal的常用方法和BigInteger基本一致；不过**BigDecimal对除法(divide)进行了优化；**

- `public BigDecimal divide(BigDecimal divisor, int roundingMode)`：除法运算，默认情况下不允许出现无限循环小数；
  - BigDecimal.ROUND_UP：最后一位如果大于0，则向前进一位，**如果是正数则向上取整，如果是负数则向下取整。**
    - 例如：3.3->4；-3.3->-4
  - BigDecimal.ROUND_DOWN：**最后一位不管是什么都会被舍弃。**
    - 例如：3.3->3；-3.3->-3
  - BigDecimal.ROUND_CEILING：**向上取整。**
    - 例如：3.3->4；-3.3->-3。
  - BigDecimal.ROUND_FLOOR：**向下取整。**
    - 例如：3.3->3；-3.3->-4。

# 第十六章内部类

## 1. 内部类概述

以前我们定义的类都是一个独立的整体，内部类即在一个类中又定义一个类；

我们知道类是用于描述事物的，比如人、电脑、汽车等；但是有些情况下一个事物中还包含有另一个独立的事物，如一台电脑有价格、颜色、品牌等属性，可其内部也有CPU、内存等独立的事物存在，CPU有价格、核心数、线程数、缓存大小等属性也需要描述；再比如一辆汽车有颜色、价格，其内部还有发动机，发动机又有转数、气缸数等属性；这个时候就需要采用内部类在一个类中再描述一件事物了；

## 2. 内部类的分类

内部类按照定义的位置来分类

- 实例(成员)内部类:定义在成员变量的位置上
- 局部内部类:类定义在方法中

## 3.内部类的使用

### 3.1 成员(实例)内部类

#### 3.1.1  定义方法:

```java
class 外部类{
    // 成员变量
    // 成员方法
    class 内部类{
        // 成员变量
        // 成员方法
    }
}
```

在描述事物时，若一个事物内部还包含其他事物，就可以使用内部类这种结构。比如，电脑类 `Computer` 中包含CPU类 `CPU` ，这时， `CPU` 就可以使用内部类来描述，定义在成员位置。

代码举例:

```java
class Computer{			//外部类
    class CPU{		//内部类

    }
}

```

#### 3.1.2  使用成员内部类

内部类可以直接访问外部类的成员，包括私有成员。

创建内部类对象格式：

```java
外部类名.内部类名 对象名 = new 外部类型().new 内部类型();
```

示例代码：

定义类

```java
public class Computer {

    double price;       // 价格
    String color;       // 颜色
    String brand;       // 品牌

    public class CPU {

        int core;       // 核心数
        int threads;    // 线程数

        public void run() {
            System.out.println("价值" + price + "的电脑的CPU正在运行！");
        }
    }
}

```

测试类

```java
public class Demo01 {

    public static void main(String[] args) {

        // 先创建外部类
        Computer computer = new Computer();
        computer.price = 8000;

        // 通过外部类创建内部类
        Computer.CPU cpu = computer.new CPU();
        cpu.run();

    }
}

```

#### 3.1.3 内外类属性重名问题

如果内部类和外部类的属性名重名了应该怎么办呢?

代码示例：

定义类

```java
public class Demo01 {

    double price=9000.00;

    public class Demo02{
        double price=8000.00;

        public void  method(){
            double price=7000.00;
            System.out.println("直接输出为局部变量"+price);
            System.out.println("访问Demo02的内部类"+this.price);
            System.out.println("访问外部类Demo01"+Demo01.this.price);
        }
    }
}

```

测试代码：

```java
public class Test {
    public static void main(String[] args) {
        Demo01.Demo02 demo02=new Demo01().new Demo02();
        demo02.method();

    }
}
```

### 3.2局部内部类

#### 3.2.1 定义语法

```java
class 外部类名 {
    
    数据类型 变量名;
    
    修饰符 返回值类型 方法名(参数列表) {
        class 内部类 {
            // 成员变量
            // 成员方法
        }
    }
}

```

使用方式: 在定义好局部内部类后,直接就创建对象

#### 3.2.2 使用局部内部类

内部类可以直接访问外部类的成员，包括私有成员。

代码示例：

```java
public class Demo03 {
    public static void main(String[] args) {
        Person person=new Person();
        person.eat();
    }
}

class Person{
    private String name="jack";

    public void eat(){
        class Food{
            private String food;
            public void eat(){
                //使用外部类变量
                System.out.println(name+"正在吃"+food);
            }

            public Food() {
            }

            public Food(String food) {
                this.food = food;
            }

            public String getFood() {
                return food;
            }

            public void setFood(String food) {
                this.food = food;
            }
        }
        Food food=new Food();
        food.setFood("红烧牛肉");
        food.eat();
    }
}
```

## 4.匿名内部类

### 4.1匿名内部类简介

我们在实现接口时必须定义一个类重写其方法，最终创建子类对象调用实现的方法；这一切的过程似乎我们只在乎最后一个步骤，即**创建子类对象调用重写的方法**；

可整个过程却分为如下几步：

- 定义接口 定义方法
- 子类实现接口定义的方法
- 创建子类 调用最终实现的方法

那我们可以将这些繁琐的步骤化简吗？

### 4.2 匿名内部类的使用

语法：

```java
new 父类名或者接口名(){
    // 方法重写
    @Override
    public void method() {
        // 执行语句
    }
};

```

使用实例：

定义接口

```java
public interface Compute{
    int sum(int a,int b);
}
```

测试代码：

```java
public class Test02 {
    public static void main(String[] args) {
        Compute compute=new Compute() {
            public int sum(int a, int b){
                return a+b;
            }
        };
        int sum = compute.sum(100, 200);
        System.out.println(sum);
    }
}
```



# 第十七章集合

## 1.单列集合

## 2.泛型

## 3.双列集合

# 第十八章异常

## 1. 异常概述

### 1.1 什么是异常

程序执行过程中发生了不正常的情况,而这种不正常的情况叫做:异常

java语言是很完善的语言,提供了异常处理方式,以下程序执行过程中出现了不正常情况。

java把该异常信息打印输出到控制台,提供程序员参考.程序员看到异常信息之后,可以对程序进行修改让程序更加健壮

**什么是异常：**	程序执行过程中的不正常情况

**异常的作用：**    提高程序的健壮性

> 注意：语法错误并不是异常，语法错了编译都不能通过（但Java有提供编译时异常），不会生成字节码文件，根本不能运行；

### 1.2 常见的异常

默认情况下，出现异常时JVM默认的处理方式是中断程序执行，因此我们需要控制异常，当出现异常后进行相应修改，提供其他方案等操作，不要让程序中断执行；

- 空指针异常`java.lang.NullPointerException`

  ```java
  String str=null;
  str.length();
  ```

- 数组下标越界异常`java.lang.ArrayIndexOutOfBoundsException`

  ```java
  int[] arr={1,2,3};
  System.out.println(arr[3]);
  ```

- 类型转换异常`java.lang.ClassCastException`

  ```java
  public class ExceptionTest01 {
      public static void main(String[] args) {
          A a=new B();
          C c=(C)a;
      }
  }
  
  class A{
  
  }
  class B extends A{
  
  }
  class C extends A{
  
  }
  ```

- 算数异常：`java.lang.ArithmeticException`

  ```java
  int i=1/0;
  ```

- 日期格式化异常：`java.text.ParseException`

  ```java
  SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
  Date parse = sdf.parse("2000a10-24");
  ```

  

### 1.3 异常体系

Java程序运行过程中所发生的异常事件可分为两类：

![](https://foruda.gitee.com/images/1665205608055925677/e0a58fdb_10637153.png)

- **Error**：表示严重错误，一般是JVM系统内部错误、资源耗尽等严重情况，无法通过代码来处理；
- **Exception**：表示异常，一般是由于编程不当导致的问题，可以通过Java代码来处理，使得程序依旧正常运行；

> Tips：我们平常说的异常指的就是Exception；因为Exception可以通过代码来控制，而Error一般是系统内部问题，代码处理不了；

### 1.4异常分类

异常的分类是根据是在编译器检查异常还是在运行时检查异常；

- 编译时期异常：在编译时期就会检查该异常，如果没有处理异常，则编译失败；
- 运行时期异常：在运行时才出发异常，编译时不检测异常；

> Tips：在Java中如果一个类直接继承与Exception，那么这个异常将是编译时异常；如果继承与RuntimeException，那么这个类是运行时异常。即使RuntimeException也继承与Exception；

![](https://foruda.gitee.com/images/1665205629399158077/dd03a874_10637153.png)

编译时异常举例:

```java
public class ExceptionTest02 {
    public static void main(String[] args) {
        SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd");        
        //编译时异常必须处理
        Date date=sdf.parse("2000-02-18");
    }
}

```

![](https://foruda.gitee.com/images/1665206118213964995/4f5e8fb4_10637153.png)

运行时异常举例:

```java
//运行时异常不用处理
int i = 1 / 0;
```

## 2.异常处理

Java程序的执行过程中如出现异常，会自动生成一个异常类对象，该异常对象将被提交给Java运行时系统（JVM），这个过程称为抛出(throw)异常。如果一个方法内抛出异常，该异常会被抛到调用方法中。如果异常没有在调用方法中处理，它继续被抛给这个调用方法的调用者。这个过程将一直继续下去，直到异常被处理。这一过程称为捕获(catch)异常。如果一个异常回到main()方法，并且main()也不处理，则程序运行终止。

```java
public class ExceptionTest {
    public static void main(String[] args) {
        /*
        程序执行到此处发生了ArithmeticException异常,
        底层new了一个ArithmeticException异常对象
        然后抛出了,由于是main方法调用了100/0
        所有这个异常ArithmeticException抛给了main方法,
        main方法没有处理,将这个异常抛给了JVM
        JVM最终终止程序
        ArithmeticException继承了RuntimeException,属于运行时异常
        在编写程序阶段不需要对这种异常进行预先的处理
         */
        System.out.println(100/0);
        //这里的hello world没有执行 输出
        System.out.println("hello world");
    }
}

```

异常处理有两种方式:

- 在方法声明的位置上，使用throws关键字，抛给上一级。谁调用我，我就抛给谁。抛给上一级。
- 使用try..catch语句进行异常的捕捉。这件事发生了，谁也不知道，因为我给抓住了。

> 举例：
>
> 是某集团的一个销售员，因为我的失误，导致公司损失了1000元，
> “损失1000元”这可以看做是一个异常发生了。我有两种处理方式，
> 第一种方式：我把这件事告诉我的领导【异常上抛throws】
> 第二种方式：我自己掏腰包把这个钱补上。【异常的捕捉 try..catch】

在java中异常也是一个类我们可以去实例化异常 

代码示例：

```java
public class ExceptionTest {
    public static void main(String[] args) {
        //通过"异常类"实例化"异常对象"
        NumberFormatException nfe=new NumberFormatException("数字格式化异常！");
        //java.lang.NumberFormatException: 数字格式化异常！
        System.out.println(nfe);

        //通过"异常类"实例化"异常对象"
        NullPointerException npe=new NullPointerException("空指针异常发生了");
        //java.lang.NullPointerException: 空指针异常发生了
        System.out.println(npe);
    }
}

```



### 2.1异常的捕获

#### 2.1.1语法

异常的捕获和处理需要采用 try 和 catch 来处理，具体格式如下：

`try..catch(){}`

```java
try {
	// 可能会出现异常的代码
} catch (Exception1 e) {
	// 处理异常1
} catch (Exception2 e) {
	// 处理异常2
} catch (ExceptionN e) {
	// 处理异常N
}
```

示例代码:

```java
public class ExceptionTest03 {
    public static void main(String[] args) {
        method();
        System.out.println("程序结束啦~~");
    }
    public static void method(){
        try {
            String str=null;
            System.out.println(str.length());
        }catch (Exception e){//这里写异常的类型
            System.out.println("执行代码出现了异常");
        }
    }
}
```

执行结果:

```java
执行代码出现了异常
程序结束啦~~
```

> 注意:这里捕捉到了 下面的代号会继续执行

#### 2.1.2 异常常用方法

在Throwable类中具备如下几个常用异常信息提示方法：

- `public void printStackTrace()`：获取异常的追踪信息；
  包含了异常的类型,异常的原因,还包括异常出现的位置,在开发和调试阶段,都得使用printStackTrace。
- `public String getMessage()`：异常的错误信息；

异常触发被抓捕时，异常的错误信息都被封装到了catch代码块中的Exception类中了，我可以通过该对象获取异常错误信息；

示例代码:

```java
public class ExceptionTest03 {
    public static void main(String[] args) {
        method();
        System.out.println("程序结束啦~~");
    }
    public static void method(){
        try {
            String str=null;
            System.out.println(str.length());
        }catch (Exception e){//这里写异常的类型
        	System.out.println("异常的错误信息"+e.getMessage());
            //打印异常错误的跟踪信息
            e.printStackTrace();
        }
    }
}

```

> 异常的追踪信息可以帮助我们追踪异常的调用链路，一步一步找出异常所涉及到的方法，在实际开发非常常用；

#### 2.2.3 finally

1. 在finally子句中的代码是最后执行的,并且是一定会执行的,即使try语句块中的代码出现了异常.
2. finally子句必须和try一起出现,不能单独使用

finally语句通常使用在哪些情况下呢?

- 通常在finally语句块中完成资源的释放/关闭
- 因为finally中的代码比较有保障
- 即使try语句块中的代码出现了异常,finally中代码也会正常执行

代码示例：

```java
public class ExceptionTest03 {
    public static void main(String[] args) {
        method();
        System.out.println("程序结束啦~~");
    }
    public static void method(){
        try {
            String str=null;
            System.out.println(str.length());
        }catch (Exception e){//这里写异常的类型
            System.out.println("执行代码出现了异常");
        }finally {
            System.out.println("这里的代码一定会执行,常常释放一些资源");
        }
    }
}

```

测试结果:

```
执行代码出现了异常
这里的代码一定会执行,常常释放一些资源
程序结束啦~~
```

> 注意点:
>
> - try和finally,没有catch是可以的
> - try不能单独使用
> - try finally可以一起使用的
>
> final finally finalize有什么区别
>     final关键字
>         final修饰的类无法继承
>         final修饰的方法无法覆盖
>         final修饰的变量不能重新赋值
>     finally 关键字
>         和try一起联合使用.
>         finally语句块中的代码是必须执行的
>     finalize标识符
>         是一个Object类中的方法名
>         这个方法是由垃圾回收期GC负责调用的

return和finally

```java
public class finallyTest04 {
    public static void main(String[] args) {
        int result=m();
        System.out.println("mian:"+result);//100
    }
    /*
    java语法规则(有一些规则是不能破坏的,一旦这么说了,就必须这么做！)
        java中有一条这样的规则:
            方法体中的代码必须遵循自上而下顺序依次逐行执行(亘古不变的语法)
        java中还有一条语法规则:
            return语句一旦执行,整个方法必须结束(亘古不变的)
 */
    public static int m(){
        int i=100;
        try{
            //这样代码出现在int i=100;下面,所以最终结果必须是返回100
            //return语句还必须是最后执行的,一旦执行,整个方法结束
            //return是最后执行
            return i;
        }finally {
            i++;
            System.out.println("m:"+i);
        }
    }
}
/*
反编译之后的效果
    public static int m(){
        int i=100;
        int j=i;
        i++;
        return j;
}
*/
```



#### 2.2.4 格式总结

- `try...catch(){}`：

  ```java
  try {
  	// 可能会出现异常的代码
  } catch (Exception1 e) {
  	// 处理异常1
  } catch (Exception2 e) {
  	// 处理异常2
  } catch (ExceptionN e) {
  	// 处理异常N
  }
  
  ```

  > Tips：后处理的异常必须是前面处理异常的父类异常； 也就是异常从上到下  越来越大

- `try..catch(){}...finally{}`

  ```java
  try {
  	// 可能会出现异常的代码
  } catch (Exception1 e) {
  	// 处理异常1
  } catch (Exception2 e) {
  	// 处理异常2
  } catch (ExceptionN e) {
  	// 处理异常N
  } finally {
  	// 不管是否出现异常都会执行的代码
  }
  
  ```

  > finally关键字:finally括号内部的代码一定会执行

- `try...finally{}`

  ```java
  try {
  	// 可能会出现异常的代码
  }  finally {
  	// 不管是否出现异常都会执行的代码
  }
  
  ```

### 2.2 异常的抛出(throw)

下方我们的案例就是用运行时异常,所以不用处理也可以

我们已经学习过出现异常该怎么抓捕了，有时候异常就当做提示信息一样，在调用者调用某个方法出现异常后及时针对性的进行处理，目前为止异常都是由JVM自行抛出，当然我们可以选择性的自己手动抛出某个异常；

Java提供了一个**throw**关键字，它用来抛出一个指定的异常对象；抛给上一级；

> Tips：自己抛出的异常和JVM抛出的异常是一样的效果，都要进行处理，如果是自身抛出的异常一直未处理，最终抛给JVM时程序一样会终止执行；

语法格式：

```java
throw new 异常类名(参数);
```

示例:

```java
throw new NullPointerException("调用方法的对象是空的！");

throw new ArrayIndexOutOfBoundsException("该索引在数组中不存在，已超出范围");

```

代码示例:

```java
package com.dfbz.demo01;

public class Demo03 {
    public static void main(String[] args) {
        method(null);
        System.out.println("我还会执行吗？");
    }

    public static void method(Object object) {
        if (object == null) {
            // 手动抛出异常(抛出异常后,后面的代码将不会被执行)
            throw new NullPointerException("这个对象是空的！不能调用方法！");
        }
        System.out.println(object.toString());
    }
}

```

> 在上方就说出，如果异常捕获了,下面的代码就会执行,如果没有捕获 下面的代码就不会执行就会终止
>
> 在方法method()中 出现了异常 处理方式为抛出 没有捕获 所以下面的代码不会执行
>
> 在main方法中 调用了method()方法 并且method()方法把异常抛给了 main 所以 main方法下面的代码也不会执行

try...catch进行捕获

```java
package com.dfbz.demo01;

public class Demo03 {
    public static void main(String[] args) {
        try {
            method(null);
        } catch (Exception e) {
            System.out.println("调用method方法出现异常了");
        }
        System.out.println("我还会执行吗？");
    }

    public static void method(Object object) {
        if (object == null) {
            // 手动抛出异常(抛出异常后,后面的代码将不会被执行)
            throw new NullPointerException("这个对象是空的！不能调用方法！");
        }
        System.out.println("如果出现了异常我是不会执行了，你能执行到这里说明没有异常");
        System.out.println(object.toString());
    }
}

```

执行结果

```
调用method方法出现异常了
我还会执行吗？
```

### 2.4 异常的声明(throws)

#### 2.4.1 运行时异常

在定义方法时，可以在方法上声明异常，用于提示调用者；

Java提供throws关键字来声明异常；关键字**throws**运用于方法声明之上，用于表示当前方法不处理异常，而是提醒该方法的调用者来处理异常(抛出异常)；

```java
public class ExceptionTest {
    public static void main(String[] args) {

        // 可以处理,也可以不处理
        method("你好~");

        // 编译时异常必须处理
        try {
            method2("hello~");
        } catch (ParseException e) {
            System.out.println("出现异常啦！");
        }
    }

    // 调用此方法可能会出现空指针异常,提示调用者处理异常
    public static void method(Object obj) throws NullPointerException {
        System.out.println(obj.toString());
    }

    // 抛出的不是运行时异常,调用者调用该方法时必须处理
    public static void method2(Object obj) throws ParseException {
        System.out.println(obj.toString());
    }

    // 也可以同时抛出多个异常
    public static void method3(Object obj) throws ClassCastException,ArithmeticException {
        System.out.println(obj.toString());
    }
}

```

#### 2.4.2 编译时异常

在声明和抛出异常时需要注意如下几点：

- 如果是抛出（throw）编译是异常，那么必须要处理，可以选择在方法上声明，或者try…catch处理
- 如果调用的方法上声明（throws）了编译时异常，那么在调用方法时就一定要处理这个异常，可以选择继续网上抛，也可以选择try…catch处理

```java
// 这里我们只是用编译时异常来举例,运行时异常不用处理也可以
public class ExceptionTest04 {
    public static void main(String[] args) {
        //向上声明的 需要自己处理
        try {
            m1(2);
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
        
        // m2已经自己捕捉了 不用处理
        m2(2);
    }
    // 但是 一般是往上抛(throw)的异常 建议不要自己捕捉 因为那样没有意义 所以大部分是往上声明
    public static void m1(int num) throws ClassNotFoundException {
        if (num==1){
            //可以进行 声明
            throw new ClassNotFoundException("自己定义的");
        }
    }

    public static void m2(int num){
        if (num==1){
            //可以进行捕捉
            try {
                throw new ClassNotFoundException("自己定义的");
            } catch (ClassNotFoundException e) {
                e.printStackTrace();
            }
        }
    }
}
```



## 3.自定义异常

我们说了Java中不同的异常类，分别表示着某一种具体的异常情况，那么在开发中总是有些异常情况是Java中没有定义好的，此时我们根据自己业务的异常情况来定义异常类。

我们前面提到过异常分类**编译时异常**和**运行时异常**：

- 继承于`java.lang.Exception`的类为编译时异常，编译时必须处理；
- 继承于`java.lang.RuntimeException`的类为运行时异常，编译时可不处理；

步骤:

- 第一步：编写一个类继承Exception或者RuntimeException
- 第二步：提供两个构造方法,一个无参的,一个带有String参数的 然后super(s);

```java
public class MyException extends Exception{
    public MyException(){}
    public MyException(String s){
        super(s);
    }
}
/*
这个是运行时异常
class M extends RuntimeException{
    public M() {
    }

    public M(String message) {
        super(message);
    }
}

 */

```



## 4.方法的重写与异常(之前遗留问题)

之前在讲解方法的覆盖的时候,当时遗留了一个问题

重写之后的方法不能比重写之前的方法抛出更多(更宽泛)的异常,可以更少

1、子类重写父类方法要抛出与父类一致的异常，或者不抛出异常
2、子类重写父类方法所抛出的异常不能超过父类的范畴（仅指检查型异常 编译时异常）
    备注：子类重写的方法可以抛出任何运行期异常
子类可以抛任何运行时异常，和父类一样 或者更少 更小的异常

```java
class Aniaml{
    public void doSome(){

    }
    public void doOther() throws Exception{

    }
}
class Cat extends Aniaml{
    /*
    编译报错
    public void doSome() throws Exception{

     }

    编译正常
   public void doOther(){

   }

     编译正常
    public void doOther() throws Exception{

    }
    */
    //编译正常
    public void doOther() throws NullPointerException{

    }

}
```



# 第十九章IO流

## 1.File类

## 2.IO流概述

## 3. 字节流

## 4.字符流

## 5.IO的异常处理

## 6.属性集

## 7.转换流

## 8.缓冲流

## 9.序列流

## 10.打印流

## 11.其他流

# 第二十章多线程

## 1.多线程概述

## 2.java中的多线程

## 3.线程安全

## 4.线程的等待和唤醒

## 5.线程状态

## 6.线程池

# 第二十一章反射

# 第二十二章注解

# 第二十三章TCP、UDP、网络通信

## 1. 网络编程概述

## 2.网络分层

## 3.网络名称

## 4.网络协议

## 5.Java实现UDP应用程序

# 第二十四章类加载