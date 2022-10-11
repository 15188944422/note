# JDBC 总结

## 六步骤:

### 	1.注册驱动

- 注册驱动的主要功能就是告诉java用的那个品牌的数据库

- ```java
  //其中 DriverManger中有一个静态方法 可以注册驱动
  //static void registerDriver(Driver driver)
  Driver driver=new com.mysql.cj.jbdc.Driver();
  DriverManger.registerDriver(driver);
  
  //但是这种写法太繁琐了 因为Driver源代码中有静态代码块来实现 
  //只要类加载的时候就会注册 我们指定Class.formName("路径名称")这里就会返回一个java类
  //我们不用返回任何类型 只要类加载就可以了
  //注意：在mysql驱动 8.0以上的版本 路径是com.mysql.cj.jdbc.Driver这的
  //8.0以下 Driver在com.mysql.jdbc.Driver
  Class.forName("com.mysql.cj.jdbc.Driver");
  ```

  

### 2.获取连接

- ```java
  /*
  DriverManager中有一个静态方法：
  	 public static Connection getConnection
  	 	(String url, String user,String password)throws SQLException
  	 	其中url写法为 jdbc:mysql://localhost:3306/bjpowernode(这里就是数据库名字)
  	 	user:数据库的用户名
  	 	password：数据库密码
  */
  String url="jdbc:mysql://localhost:3306/bjpowernode";
  String user="root";
  String password="root";
  
  Connection connection=DriverManager.getConnection(url,user,password);
  ```

  

### 3.获取数据库操作对象

- Statement专门执行SQL语句的

- ```java
  /*
  Connection中有一个实例方法为
  	public Statement createStatement(){}
  	创建一个Statement对象 用于将SQL语句发送到数据库
  */
  Statement statement=connection.createStatement();
  ```

### 4.执行SQL

- ```java
  String sql="SQL语句";
  
  /*
  这里有两种情况：
  	第一种:就是DML（数据操作语言）：insert delete update，对表当中的数据进行增删改。
  		这一种我们需要调用Statement中的int executeUpdate(insert/update/delete) 
  		它返回的是：影响数据库中的记录条数
  		这一种不需要处理查询结果集
  		
  	第二种:就是DQL（数据查询语言）: 查询语句，凡是select语句都是DQL。
  		这一种我们需要调用Statement中的
  			public Resultset executeQuery(select语句)	throws SQLException; 
  			执行给定的SQL语句，返回单个ResultSet对象。 
  			ResultSet resultSet=statement.executeQuery(sql);
  			
  */
  
  //第一种情况就直接 调用方法即可
  int count=statement.executeUpdate(sql);
  
  //第二种 需要在第五步中 处理查询结果集
  ResultSet resultSet=statemet.executeQuery(sql);
  
  
  ```

  

### 5.处理查询结果集合

- ```java
  /*
  	根据第四步的resultSet
  		方法boolean next()throws SQLException
  			ResultSet光标最初位于第一行之前;
  			第一次调用方法next使第一行成为当前行; 
  			第二个调用使第二行成为当前行，依此类推。 
  			当调用next方法返回false时，光标位于最后一行之后。
  			任何调用需要当前行的ResultSet方法将导致抛出SQLException  
  			true如果新的当前行有效; false如果没有更多的行
  		方法
  			String getString()
  			int getInt
  			double getDouble
  			.....
  			来取出数据库当中的数据
  		一般用的就是用 getString  返回的就是String类型的
  		
  */
  
  //这里可以用到循环
  while(resultSet.next()){
      String name=resultSet.getString("name");
      String name=resultSet.getString("name");
      .....
  }
  ```

  

### 6.释放资源

- ```java
  /*
  注意了：
  	释放资源的时候我们要从小到大去释放资源
  	ResultSet Statement Connection	
  */
  resultSet.close();
  Statement.close();
  Connection.colse();
  ```

## 不用查询结果集的综合写法

```java
/*
首先得会先搭一个架子
*/
public static void main(String[] args){
    Connection connection=null;
    Statement statement=null;
    try{
        //注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");
        //获取连接
        String url="jdbc:mysql://localhost:3306/bjpowernode";
        String user="root";
        String password="root";   
        connection=DriverManager.getConnection(url,user,password);     
        //获取数据库操作对象
        statement=connection.createStatement();
        //执行sql
        String sql="insert into t_student(no,name,cno) values(9,'zhangbao','110')";
        int count=statement. executeUpdate(sql);
    }catch(SQLException e){
        e.printStackTrace();
    }finally{
        //释放资源 从小到大依次释放
        if(statement!=null){
            try{
                statement.close();
            }catch(SQLException e){
                e.printStackTrace();
            }
        }
        if(connection !=null){
            try{
                connection.close();
            }catch(SQLException e){
                e.printStackTrace();
            }
        }

    }
}
```

## 带有查询结果集的

```java
public static void main(String[] args){
    Connection connection=null;
    Statement statement=null;
    ResultSet resultSet=null;
    try{
        //注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");
        //获取连接
        String url="jdbc:mysql://localhost:3306/bjpowernode";
        String user="root";
        String password="root";
        connection=DriverManager.getConnection(url,user,password);
        //获取数据库操作对象      
        statement=connection.createStatement();
        //执行sql
        String sql="select * from t_student";
        resultSet=statement.executeQuery(sql);
        //处理查询结果集合
        while(resultSet.next()){
            String no=resultSet.getString("no");
            String name=resultSet.getString("name");
            String cno=resultSet.getString("cno");
            System.out.printf(no+"/"+name+"/"+cno);
        }
    }catch(SQLExcetion e){
        e.printStackTrace();
    }finally{
        if(resultSet!=null){
            try{
                resultSet.close();
            }catch(SQLException e){
                e.printStackTrace();
            }
        }
        if(statement !=null){
           try{
                statement.close();
            }catch(SQLException e){
                e.printStackTrace();
            }
        }
        if(connection !=null){
           try{
                connection.close();
            }catch(SQLException e){
                e.printStackTrace();
            }
        }
    }
}

```

## 资源绑定器配置文件

​	

```properties
driver=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/bjpowernode
user=root
password=root
```

```java
	public static void main(String[] args){
		
		//使用资源绑定器,绑定配置文件
		ResourceBundle resourceBundle=ResourceBundle.getBundle("jdbc");
		String driver=resourceBundle.getString("driver");
		String url=resourceBundle.getString("url");
		String user=resourceBundle.getString("user");
		String password=resourceBundle.getString("password");

		Connection connection=null;
		Statement statement=null;
		try{
		//1.注册驱动
		Class.forName(driver);
		//2.获取连接
		connection=DriverManager.getConnection(url,user,password);
		//3.获取数据库操作对象
		statement=connection.createStatement();
		//4.执行sql语句
		String sql="update t_student set name='宋三' where no=9";
		int count=statement.executeUpdate(sql);
		System.out.println(count==1?"修改成功":"修改失败");
		}catch(Exception e){
			e.printStackTrace();
		}finally{
			//6.释放资源
			if(statement!=null){
				try{
					statement.close();
				}catch(SQLException e){
					e.printStackTrace();
				}
			}
			if(connection!=null){
				try{
					connection.close();
				}catch(SQLException e){
					e.printStackTrace();
				}
			}
		}
	
	}
```



## 关于SQL注入的问题及解决方法

### 如果写一个SQL代码来判断用户名和密码是否正确

- ```java
  /*
  表为 t_user
  */
  //下面就是一条sql语句进行字符串的拼接
  //查询出来 loginName=输入的 loginPwd=输入的
  String sql="select * from t_user where loginName='"+loginName(输入的)+"' and 				  	 loginPwd='"+loginPwd(输入的)+"'";	
  ```

- 这行代码的问题就是 当我们输入

  - ```
    用户名:fdsa
    密码: fdsa' or '1'='1
    登录成功
    这种现象被称为SQL注入(黑客经常使用)
    也就是
    select * from t_user where loginName='fdsa' and loginPwd='fdsa' or '1'=1 注意了or是上去的
    ```

### 导致SQL注入的根本原因是什么？

1. 用户输入的信息中含义sql语句的关键字,并且这些关键字参与sql语句的编译过程导致sql语句的原意被扭曲,进而达到了sql注入的问题

### 解决办法	

1. ​	解决sql注入的问题：

   - 只要用户提供的信息不参与SQL语句的编译过程,问题就解决了
     即使用户提供的信息中含有SQL语句的关键字,但是没有参与编译,不起作用
     要想用户信息不参与SQL语句的编译,那么必须使用java.sql.PreparedStatement
     PreparedStatement接口继承了java.sql.Statement
     PreparedStatement是属于预编译的数据库操作对象
     PreparedStatement的原理:是预先对SQL语句的框架进行编译,然后再给SQL语句传"值"

2. 解决sql注入的关键是什么？

   - 用户提供的信息即使含有sql语句的关键字,但是这些关键字没有参与编译不起作用！！

3. 对比一下Statement和PreparedStatement?

   - Statement存在sql注入问题,PreparedStatement解决了sql注入问题
     Statement是编译一次执行一次.PreparedStatement是编译一次,可执行n次.PreparedStatement执行效率较高
     PreparedStatement会在编译阶段做类型的安全检查.
   - 综上所述：PreparedStatement使用较多,只要在极少数的情况下使用Statement

4. 什么时候必须使用Statement呢

   - 业务方面要求必须支持SQL注入的时候
     Statement支持SQL注入,凡是业务方面要求是需要进行sql语句进行拼接的,必须使用Statement.

5. 代码写法

   - ```java
     /*
     String sql="select * from t_user where loginName='"+loginName+"' and 			loginPwd='"+loginPwd+"'";	
     就这个来说
      loginName='"+loginName
      loginPwd='"+loginPwd 就是举例子而已
     */
     
     public static void main(String[] args){
         //打标记的意识
         boolean loginSuccess=false;
         Connection connection=null;
         PreparedStatement preparedStatement=null;
         ResultSet resultSet=null;
         try{
             //注册驱动
             Class.forName("com.mysql.cj.jdbc.Driver");
             
             //获取连接
             String url="jdbc:mysql://localhost:3306/bjpowernode";
             String user="root";
             String password="root";
             connection=DriverManager.getConnection(url,root,password);
             
             //3.获取预编译的数据库操作对象
             //SQL语句的框子.其中一个?,表示一个占位符,一个?将来接受一个"值".注意：占位符不能用单引号括起来
             String sql="select * from t_user where loginName=? and loginPaw=?";
              //程序执行到此处,会发生SQL语句框子给DBMS,然后DBMS进行sql语句的预先编译
             preparedStatement=connection.prepareStatement(sql);
              //给占位符?传值(第一个?下标是1,第二个?下标是2,所有JDBC中从下标1开始.)
             preparedStatement.setString(1,loginName);
             preparedStatement.setString(2,loginPwd);
             
             //4.执行sql
             resultSet=preparedStatement.executeQuery();
             //处理查询结果集
             if(resultset.next()){
                     //登录成功
                  loginSuccess=true;
             }
         }catch(Exception e){
             e.printStackTrace();
         }finally{
            if(resultSet!=null){
                try{
                    resultSet.close();
                }catch(SQLException e){
                    e.printStackTrace();
                }
            }
             if(preparedStatement !=null){
                 try{
                     preparedStatement.close();
                 }catch(SQLException e){
                     e.printStackTrace();          
                 }
             }
             if(connection !=null){
                 try{
                     connection.close();
                 }catch(SQLException e){
                     e.printStackTrace();
                 }
             }
         }
     }
     ```

### PreparedStatement完成DML(insert detele update)

- ​	

  ```java
  public static void main(String[] args){
      Connection conn=null;
      PreparedStatement ps=null;
      ResultSet rs=null;
      try{
           //注册驱动
          Class.forName("com.mysql.cj.jdbc.Driver");
          
          //获取连接
          String url="jdbc:mysql://localhost:3306/bjpowernode";
          String user="root";
          String password="root";
          connection=DriverManager.getConnection(url,root,password);
          
          //3.获取预编译的数据库操作对象
          
          /* 	这个是insert
          	String sql="insert into dept_bak(deptno,dname,loc) values(?,?,?)";
              ps=connection.prepareStatement(sql);
              ps.setInt(1,60);
              ps.setString(2,"销售部");
              ps.setString(3,"上海");
  
              
              这个是update
              String sql="update dept_bak set dname=?,loc=? where deptno=?";
              ps=connection.prepareStatement(sql);
              ps.setString(1,"研发余部");
              ps.setString(2,"北京");
              ps.setInt(3,60);
  
              */
  
          //delete
          String sql="delete from dept_bak where deptno=?";
          ps=connection.prepareStatement(sql);
          ps.setInt(1,60);
          //4.执行SQL
          int count=ps.executeUpdate();
          System.out.println(count);
      }catch(Exception e){
           e.printStackTrace();
      }finally{
         if(resultSet!=null){
             try{
                 resultSet.close();
             }catch(SQLException e){
                 e.printStackTrace();
             }
         }
          if(preparedStatement !=null){
              try{
                  preparedStatement.close();
              }catch(SQLException e){
                  e.printStackTrace();          
              }
          }
          if(connection !=null){
              try{
                  connection.close();
              }catch(SQLException e){
                  e.printStackTrace();
              }
          }
      }
  }
  ```

## 写一个关于JDBC的工具类

```java
/*
其中 代码有好多是冗余的 就比如每次都要去 Class.forName("com.mysql.cj.jdbc.Driver")
每次都要获取Connection 关闭 close()

所以要写一个
JDBC工具类 简化JDBC编程
*/
public class DBUtil{
    //这里我们可以使用资源配置文件
	ResourceBundle resourceBundle=ResourceBundle.getBundle("这里就说一个路径");
    String url=resourceBundle.getString("url");
	String user=resourceBundle.getString("user");
	String password=resourceBundle.getString("password");
    
    /**
     * 工具类中的构造方法都是私有的
     * 因为工具类当中的方法都是静态的,不需要new对象,直接采用类名调用
     */
    private DBUtil(){
        
    }
    //静态代码块在累加的时候执行 并且只执行一次
    static{
        ResourceBundle resourceBundle=ResourceBundle.getBundle("这里就说一个路径");
        String driver=resourceBundle.getString("driver");
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
    
    /*
    获取数据库连接对象
    */
    public static Connection getConnection() throws SQLExcetion{//这里要抛出异常
      return DriverManager.getConnection(url,user, password);  
    }
    
    /*
    释放资源
    数据库操作对象 注意这里不要写PreparedStatement 因为面向抽象编程 Statement时PreparedStatement的父类
    */
     public static void close(Connection connection, Statement statement,ResultSet resultSet){
        if (resultSet != null) {
            try {
                resultSet.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (statement != null) {
            try {
                statement.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (connection != null) {
            try {
                connection.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
}
```

## JDBC的事务机制：

```java

/*
JDBC事务机制:
    1.JDBC中的事务是自动提交的
        只要执行任意一条DML语句,则自动提交一次,这是JDBC默认的事务行为
        但是在实际的业务当中,通常都是N条DML语句共同联合才能完成的,必须
        保证他们这些DML语句在同一食物中同时成功或者同时失败
    2.以下程序先来验证以下,JDBC的事务是否是自动提交机制
        测试结果:JDBC中只要执行任意一条DML语句,就提交一次
	
    3.重点三行代码:
        connection.setAutoCommit(false);
        connection.commit();
        connection.rollback();
*/
public static void main(String[] args) {
        Connection connection = null;
        PreparedStatement statement = null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            String url="jdbc:mysql://localhost:3306/bjpowernode";
            String user="root";
            String password="root";
            Connection connection=DriverManager.getConnection(url,user,password);
            //将自动提交机制改为手动提交
            connection.setAutoCommit(false);//开始事务
            String sql = "update t_act set balance=? where actno=?";
            statement = connection.prepareStatement(sql);
            statement.setDouble(1, 10000);
            statement.setInt(2, 111);
            int count = statement.executeUpdate();

            //String s = null;
            //s.toString();

            //再给？传值
            statement.setDouble(1, 10000);
            statement.setInt(2, 222);
            count += statement.executeUpdate();
            System.out.println(count == 2 ? "转账成功" : "转账失败");

            //程序能够走到这里,说明以上程序没有异常,事务结束,手动提交数据
            connection.commit();//提交事务
        } catch (Exception e) {
            if (connection != null) {
                try {
                    connection.rollback();//回滚事务
                } catch (SQLException ex) {
                    ex.printStackTrace();
                }
            }
            e.printStackTrace();
        } finally {
            if (statement != null) {
                try {
                    statement.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if (connection != null) {
                try {
                    connection.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
    }

```

## 悲观锁机制:



## 