# java
# java
目的：
使初学者能更好的去了解SSH框架。
给以后的自己，也给别人一个参考。
尝试搭建一个完整的SSH框架项目。
 

一、SSH三大框架的概述

　　ssh为 struts+spring+hibernate的一个集成框架，是目前较流行的一种Web应用程序开源框架。

　  集成SSH框架的系统从职责上分为四层：表示层、业务逻辑层、数据持久层和域模块层（实体层），以帮助开发人员在短期内搭建结构清晰、可复用性好、维护方便的Web应用程序。

　　struts2：　　

　　　　1、什么是struts2：

　　　　　　Struts2是一个基于MVC设计模式的Web应用框架，它本质上相当于一个servlet，在MVC设计模式中，Struts2作为控制器(Controller)来建立模型与视图的数据交互。Struts 2是Struts的下一代产品，是在 struts 1和WebWork的技术基础上进行了合并的全新的Struts 2框架。其全新的Struts 2的体系结构与Struts 1的体系结构差别巨大。Struts 2以WebWork为核心，采用拦截器的机制来处理用户的请求，这样的设计也使得业务逻辑控制器能够与ServletAPI完全脱离开，所以Struts 2可以理解为WebWork的更新产品。虽然从Struts 1到Struts 2有着太大的变化，但是相对于WebWork，Struts 2的变化很小。

　　　　2、struts2框架的运行结构：

　　　　

 

　　　　解析：客户端发送请求(HttpServletRequest)到服务器，服务器接收到请求就先进入web.xml配置文件看看有没有配置过滤器，发现有struts2的过滤器，然后就找到struts.xml配置文件，struts.xml配置文件里有定义一个action，然后就去找到类名叫IndexAction这个类(此action类必须是继承ActionSupport接口)，并且实现了execute()方法，返回一个字符串为"success"给struts.xml配置文件，struts.xml配置文件的action会默认调用IndexAction类的execute()方法，result接收到了返回的字符串，然后查找结果字符串对应的(Result），result就会调用你指定的jsp页面将结果呈现，最后响应回给客户端。

　　

　　spring：

　　　1、什么是spring?

　　　　　　Spring是一个轻量级控制反转(IoC)和面向切面(AOP)的容器框架。　　　　　　　

　　　　　　　　轻量——从大小与开销两方面而言Spring都是轻量的。完整的Spring框架可以在一个大小只有1MB多的JAR文件里发布。并且Spring所需的处理开销也是微不足道的。此外，Spring是非侵入式的：典型地，Spring应用中的对象不依赖于Spring的特定类。 
　　　　　　　　控制反转——Spring通过一种称作控制反转（IoC）的技术促进了松耦合。当应用了IoC，一个对象依赖的其它对象会通过被动的方式传递进来，而不是这个对象自己创建或者查找依赖对象。你可以认为IoC与JNDI相反——不是对象从容器中查找依赖，而是容器在对象初始化时不等对象请求就主动将依赖传递给它。
　　　　　　　　面向切面——Spring提供了面向切面编程的丰富支持，允许通过分离应用的业务逻辑与系统级服务（例如审计（auditing）和事务（transaction）管理）进行内聚性的开发。应用对象只实现它们应该做的——完成业务逻辑——仅此而已。它们并不负责（甚至是意识）其它的系统级关注点，例如日志或事务支持。
　　　　　　　　容器——Spring包含并管理应用对象的配置和生命周期，在这个意义上它是一种容器，你可以配置你的每个bean如何被创建——基于一个可配置原型（prototype），你的bean可以创建一个单独的实例或者每次需要时都生成一个新的实例——以及它们是如何相互关联的。然而，Spring不应该被混同于传统的重量级的EJB容器，它们经常是庞大与笨重的，难以使用。
　　　　　　　　框架——Spring可以将简单的组件配置、组合成为复杂的应用。在Spring中，应用对象被声明式地组合，典型地是在一个XML文件里。Spring也提供了很多基础功能（事务管理、持久化框架集成等等），将应用逻辑的开发留给了你。
 

　　　　2、spring的流程图：　　　　



　　　　解析：上图是在struts结构图的基础上加入了spring流程图，在web.xml配置文件中加入了spring的监听器，在struts.xml配置文件中添加“<constant name="struts.objectFactory" value="spring" />”是告知Struts2运行时使用Spring来创建对象，spring在其中主要做的就是注入实例，将所有需要类的实例都由spring管理。

 

　　hibernate：

　　　1、什么是hibernate？

　　　　Hibernate是一个开放源代码的对象关系映射框架，它对JDBC进行了非常轻量级的对象封装，它将POJO与数据库表建立映射关系，是一个全自动的orm框架，hibernate可以自动生成SQL语句，自动执行，使得Java程序员可以随心所欲的使用对象编程思维来操纵数据库。 Hibernate可以应用在任何使用JDBC的场合，既可以在Java的客户端程序使用，也可以在Servlet/JSP的Web应用中使用，最具革命意义的是，Hibernate可以在应用EJB的J2EE架构中取代CMP，完成数据持久化的重任。

 　　　2、hibernate的核心构成和执行流程图：

　　　　

　　　　　　

　　　　　　

　　　3、为什么使用Hibernate？

　　　　 1). 对JDBC访问数据库的代码做了封装，大大简化了数据访问层繁琐的重复性代码。

　　　　2)、Hibernate是一个优秀的ORM实现。他很大程度的简化DAO层的编码工作，将软件开发人员从大量相同的数据持久层相关编程工作中解放出来，使开发更对象化了。

　　　　3)、移植性好，支持各种数据库，如果换个数据库只要在配置文件中变换配置就可以了，不用改变hibernate代码。

　　　　4)、支持透明持久化，因为hibernate操作的是纯粹的（pojo）java类，没有实现任何接口，没有侵入性。所以说它是一个轻量级框架。

 

二、搭建一个完整的SSH框架项目。

　　注意事项：　

　　　　1、本文提纲：本文通过一个将所有图书借记卡信息查询出来并显示到JSP页面的项目实例讲解SSH的整合。创建Struts项目，整合Hibernate，整合Spring。

　　　　2、仅是创建SSH项目，对于其他的扩展例如Struts的国际化，Hibernate的缓存优化，Spring的AOP等，本博文涉及不到。想学习更多的东西请搜索其他博文。

　　　　3、本项目的搭建环境：

　　　　　　　Windows 8-64位，Eclipse(开发工具)，jdk1.8.0_91，Tomcat 8.0，struts-2.3.30-apps，spring-framework-4.2.2.RELEASE，hibernate-release-5.2.2.Final，sql sever2008.

　　　

第一步：在eclipse(开发工具)里创建web项目(项目名称：ssh)，并生成web.xml文件。　　

　　

第二步：导入本次项目要使用到的jar包。

　　　struts-2.3.30-apps官网下载地址：http://struts.apache.org/download.cgi#struts252

　

　　spring-framework-4.2.2.RELEASE官网下载地址：https://repo.spring.io/webapp/#/artifacts/browse/tree/General/libs-release-local/org/springframework/spring/4.2.2.RELEASE/spring-framework-4.2.2.RELEASE-dist.zip

 



 

　　hibernate-release-5.2.2.Final官网下载地址：http://hibernate.org/orm/

　　

 

　　struts2(jar)包：

　　

　　spring(jar)包：



　　注意：struts2-spring-plugin-2.3.30.jar,commons-logging-1.1.3.jar是struts的jar包

 　　hibernate(jar)包：

　　　　

 

　　　sql sever数据库(jar)包:

　　　　

　　　将所有的项目要用的jar包放入lib文件里：

 　　　　

　　　　　

 

第三步：在配置文件web.xml配置一个struts2的过滤器和spring监听器。



复制代码
 1 <?xml version="1.0" encoding="UTF-8"?>
 2 <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" id="WebApp_ID" version="3.1">
 3     <display-name>ssh</display-name>
 4     <welcome-file-list>
 5       <welcome-file>index.action</welcome-file>
 6     </welcome-file-list>
 7   
 8       <!-- struts2的过滤器 -->
 9     <filter>
10         <filter-name>struts2</filter-name>
11         <filter-class>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter</filter-class>
12     </filter>
13 
14     <filter-mapping>
15         <filter-name>struts2</filter-name>
16         <url-pattern>/*</url-pattern>
17     </filter-mapping>
18     
19     
20     <!-- spring的监听器配置开始 -->
21     <context-param>  
22         <param-name>contextConfigLocation</param-name>  
23         <param-value>classpath:applicationContext.xml</param-value>  
24     </context-param>
25     <listener>
26         <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
27     </listener>
28 </web-app>
复制代码
 

第四步：在Java Resources下的src目录下创建四个包(package)进行分层。



 

第五步：根据数据库表的字段编写BookCard(实体类)和BookCard.hbm.xml(映射文件)放到ssh.entity包里。



BookCard(实体类)：

复制代码
 1 package ssh.entity;
 2 
 3 import java.math.BigDecimal;
 4 import java.util.Date;
 5 
 6 /*
 7  * 跟数据库表一致，作为一个java对象
 8  * 1个对象代表的是数据库表中的一行记录
 9  * 1个属性代表的是表中的一个字段
10  */
11 public class BookCard {
12     private int cid  ;
13     private String name;
14     private String sex ;
15     private Date cardDate;
16     private BigDecimal deposit;
17     
18     //定义get()、set()方法
19     public int getCid() {
20         return cid;
21     }
22     public void setCid(int cid) {
23         this.cid = cid;
24     }
25     public String getName() {
26         return name;
27     }
28     public void setName(String name) {
29         this.name = name;
30     }
31     public String getSex() {
32         return sex;
33     }
34     public void setSex(String sex) {
35         this.sex = sex;
36     }
37     public Date getCardDate() {
38         return cardDate;
39     }
40     public void setCardDate(Date cardDate) {
41         this.cardDate = cardDate;
42     }
43     public BigDecimal getDeposit() {
44         return deposit;
45     }
46     public void setDeposit(BigDecimal deposit) {
47         this.deposit = deposit;
48     }
49 
50 }
复制代码
 

 BookCard.hbm.xml(映射文件)：

复制代码
 1 <?xml version="1.0" encoding="UTF-8"?>
 2 <!DOCTYPE hibernate-mapping PUBLIC 
 3 "-//Hibernate/Hibernate Mapping DTD 3.0//EN" 
 4 "http://www.hibernate.org/dtd/hibernate-mapping-3.0.dtd">
 5 
 6 <hibernate-mapping>
 7     <class name="ssh.entity.BookCard" table="BookCard">
 8         <!-- 卡号 -->
 9         <id name="cid" column="cid">
10             <generator class="native"></generator>
11         </id>
12         <!-- 姓名 -->
13         <property name="name" column="name"></property>
14         <!-- 性别 -->
15         <property name="sex" column="sex"></property>
16         <!-- 办卡日期 -->
17         <property name="cardDate" column="cardDate"></property>
18         <!-- 押金 -->
19         <property name="deposit" column="deposit"></property>
20     </class>
21 </hibernate-mapping>
复制代码
 

第六步：在ssh.service包里编写IndexService(接口类)和IndexServiceImpl(实现类)。

 

IndexService(接口类)：

复制代码
 1 package ssh.service;
 2 
 3 import java.util.List;
 4 
 5 import ssh.dao.IndexDao;
 6 import ssh.entity.BookCard;
 7 
 8 //创建一个IndexService接口类
 9 public interface IndexService {
10     
11     
12     public List<BookCard> getAllBookCard();
13 
14 }
复制代码
IndexServiceImpl(实现类)：

复制代码
 1 package ssh.service;
 2 
 3 import java.util.List;
 4 
 5 import ssh.dao.IndexDao;
 6 import ssh.entity.BookCard;
 7 
 8 //创建IndexServiceImpl(实现类)实现IndexService接口
 9 public class IndexServiceImpl implements IndexService {
10 
11     //dao实例使用注入方式
12     private IndexDao id;
13     //用于注入使用
14     public void setId(IndexDao id) {
15         this.id = id;
16     }
17 
18 
19     @Override
20     public List<BookCard> getAllBookCard() {
21         //本类应该编写业务逻辑的代码，
22         //但本例没有业务逻辑，就不用写。
23         
24         //访问数据库的代码，不会出现在service这一层
25         //交给dao来操作数据库
26         List<BookCard> myBookCardList = id.getAllBookCard();
27         
28         //进行其它的业务逻辑操作，比如增加多一个选项，是否过期
29         //本例不需要
30         //....
31         
32         return myBookCardList;
33     }
34 
35 }
复制代码
 

 第七步：在ssh.dao包里编写IndexDao(接口类)和IndexDaoImpl(实现类)。



 

 IndexDao(接口类)：

复制代码
 1 package ssh.dao;
 2 
 3 import java.util.List;
 4 
 5 import ssh.entity.BookCard;
 6 
 7 //创建IndexDao(接口类)
 8 public interface IndexDao {
 9     
10     public List<BookCard> getAllBookCard();
11     
12 }
复制代码
 

IndexDaoImpl(实现类)：

复制代码
 1 package ssh.dao;
 2 
 3 import java.util.List;
 4 
 5 import org.hibernate.Session;
 6 import org.hibernate.SessionFactory;
 7 import org.hibernate.query.Query;
 8 
 9 import ssh.entity.BookCard;
10 
11 //创建IndexDaoImpl(实现类)实现IndexDao接口
12 public class IndexDaoImpl implements IndexDao {
13     
14     //在SSH的设计理念：要使用某个实例，那么就定义声明一个对象，然后
15     //给它添加set方法（用于spring注入进来）
16     //实现不要关注这个实例来自于那里，以及怎么创建，或者它是谁    
17     private SessionFactory sessionFactory;
18     
19     public void setSessionFactory(SessionFactory sessionFactory) {
20         this.sessionFactory = sessionFactory;
21     }
22 
23 
24     @Override
25     public List<BookCard> getAllBookCard() {
26         
27         //sessionFactory这个实例可以自己按常规的hibernate传统写法创建
28         //也可以交给spring去托管
29         /*
30         Configuration cfg = new Configuration().configure();
31         sessionFactory = cfg.buildSessionFactory();*/
32         
33         //获取session
34         Session session = sessionFactory.openSession();
35             
36         //后面当使用JPA的时候，EntityManager 类似于 Session
37         Query query = session.createQuery("from BookCard");
38         
39         //将所有的数据查询出来并放到List集合里
40         List<BookCard> list = query.getResultList();
41         
42         //将集合遍历循环
43         for(BookCard bookCard:list){
44             //打印输出到控制台
45             System.out.println(bookCard);
46         }
47         
48         //关闭session
49         session.close();
50         //关闭sessionFactory
51         sessionFactory.close();
52         //返回list集合
53         return list;
54         
55     }
56 
57 }
复制代码
 

第八步：编写IndexAction(action类)。



复制代码
 1 package ssh.action;
 2 
 3 import java.text.DecimalFormat;
 4 import java.util.List;
 5 
 6 import com.opensymphony.xwork2.ActionContext;
 7 import com.opensymphony.xwork2.ActionSupport;
 8 
 9 import ssh.entity.BookCard;
10 import ssh.service.IndexService;
11 
12 //创建IndexAction(action类)继承ActionSupport接口
13 public class IndexAction extends ActionSupport {
14     
15     private static final long serialVersionUID = 1L;
16     
17     //声明service，但不给它创建具体的实现类的实例，
18     private IndexService is = null;
19     //添加set()方法
20     public void setIs(IndexService is) {
21         this.is = is;
22     }
23     
24     //编写execute()方法
25     public String execute() {
26         
27         //获取IndexService实例，调用getAllBookCard()方法
28         //将结果保存到List集合里
29         List<BookCard> myBookCardList = is.getAllBookCard();
30         
31         //将查询出来的结构集打印到控制台
32         System.out.println("结果集："+myBookCardList.size());
33         
34         //获取Context上下文对象
35         ActionContext ac = ActionContext.getContext();
36         //将myBookCardList集合添加到上下文对象里
37         ac.put("myBookCardList", myBookCardList);
38         
39         //返回一个字符串
40         return "success";
41     }
42     
43     //金额格式转换
44     public String formatDouble(double s){
45         DecimalFormat fmat=new DecimalFormat("\u00A4##.0"); 
46         return fmat.format(s);
47     }
48     
49 }
复制代码
 

第九步：编写struts.xml(struts配置文件)、applicationContext.xml(spring配置文件)、hibernate.cfg.xml(hibernate配置文件)。

　　注:将这些配置文件放到src里。



struts.xml：

复制代码
 1 <?xml version="1.0" encoding="UTF-8"?>
 2 <!DOCTYPE struts PUBLIC
 3     "-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
 4     "http://struts.apache.org/dtds/struts-2.3.dtd">
 5 <!-- 上面的头，注意版本，从样例里复制过来 showcase.war\WEB-INF\src\java\struts.xml -->
 6 
 7 <struts>
 8     <!-- 告知Struts2运行时使用Spring来创建对象 -->
 9     <constant name="struts.objectFactory" value="spring" />
10     
11     <!-- 第1步：先定义一个包 -->
12     <package name="mypck001" extends="struts-default">
13         <!-- 第2步：定义一个action，配置跳转信息 name 类似于Servlet @WebServlet("/IndexServlet") 
14             http://xxxx/xxx/Index.action http://xxxx/xxx/Index class 对应于自己写的Action类 当不写method属性时，默认调用的是execute
15             class="ssh.action.IndexAction" ** new ssh.action.IndexAction()
16             设计思想：关心了具体的实现类必须改为不要关注那个实现类 加入spring后，struts的action节点的class属性意义发生变化，直接引用spring帮忙创建的实例 
17         -->
18         <action name="Index" class="myIndexAction">
19             <!-- 跳转是forward/WEB-INF/是防止jsp不经过action就可以访问-->
20             <!-- result接收返回的字符串，然后做对应的事情 -->
21             <result name="success">/WEB-INF/jsp/index.jsp</result>
22         </action>
23     </package>
24 </struts>
复制代码
 

applicationContext.xml：

复制代码
 1 <?xml version="1.0" encoding="UTF-8"?>
 2 <beans xmlns="http://www.springframework.org/schema/beans"    
 3         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
 4         xmlns:p="http://www.springframework.org/schema/p"  
 5         xmlns:aop="http://www.springframework.org/schema/aop"   
 6         xmlns:context="http://www.springframework.org/schema/context"  
 7         xmlns:jee="http://www.springframework.org/schema/jee"  
 8         xmlns:tx="http://www.springframework.org/schema/tx"  
 9         xsi:schemaLocation="    
10             http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-4.2.xsd  
11             http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.2.xsd  
12             http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.2.xsd
13             http://www.springframework.org/schema/jee http://www.springframework.org/schema/jee/spring-jee-4.2.xsd  
14             http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-4.2.xsd">
15     <!-- 类似于财务部门一样，类就是钱，所有需要类的实例都由srping去管理 -->
16     <bean id="myIndexAction" class="ssh.action.IndexAction" scope="prototype">
17         <!-- setIs(myIndexService) -->
18         <property name="is" ref="myIndexService"/>
19     </bean>
20     
21     <!-- myIndexService = new ssh.service.IndexServiceImpl() -->
22     <bean id="myIndexService" class="ssh.service.IndexServiceImpl" scope="prototype">
23         <property name="id" ref="myIndexDao"/>
24     </bean>
25     
26     <bean id="myIndexDao" class="ssh.dao.IndexDaoImpl" scope="prototype">
27         <!-- 把sessionFactory 注入给IndexDao -->
28         <property name="sessionFactory" ref="sessionFactory" />
29     </bean>
30     
31      <!-- 添加sessionFactory bane ，注意，该类是Spring提供的 -->
32     <bean id="sessionFactory" class="org.springframework.orm.hibernate5.LocalSessionFactoryBean" scope="prototype">
33         <!-- 注入Hibernate 配置文件路径,前面要加上  classpath:-->
34         <property name="configLocation" value="classpath:hibernate.cfg.xml"/>
35     </bean>
36     
37 </beans>
38             
复制代码
 

 hibernate.cfg.xml：

复制代码
 1 <?xml version="1.0" encoding="utf-8"?>
 2 <!DOCTYPE hibernate-configuration PUBLIC 
 3 "-//Hibernate/Hibernate Configuration DTD 3.0//EN" 
 4 "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
 5 
 6 <hibernate-configuration>
 7     <session-factory>
 8         <!-- 数据库连接配置 -->
 9         <property name="connection.driver_class">com.microsoft.sqlserver.jdbc.SQLServerDriver</property>
10         <property name="connection.url">jdbc:sqlserver://localhost:1433;DatabaseName=CardDB</property>
11         <property name="connection.username">sa</property>
12         <property name="connection.password">123456</property>
13         <!-- 每个数据库都有1个，针对特定的关系型数据库生成优化的SQL -->
14         <property name="dialect">org.hibernate.dialect.SQLServer2008Dialect</property>
15         
16         <!-- 设置默认的数据库连接池 -->
17         <property name="connection.pool_size">5</property>
18         
19         <!-- 显示SQL -->
20         <property name="show_sql">true</property>
21         
22         <!-- 格式化SQL -->
23         <property name="format_sql">true</property>
24         
25         <!-- 根据schema更新数据表的工具 -->
26         <property name="hbm2ddl.auto">update</property>        
27         
28         <!-- 数据表映射配置文件 -->
29         <mapping resource="ssh/entity/BookCard.hbm.xml"/>
30         
31     </session-factory>
32 </hibernate-configuration>
复制代码
 

第十步：创建一个index.jsp页面将所有数据取出来显示到页面上。

　　注：跳转是forward，将jsp放到/WEB-INF/是防止jsp不经过action就可以访问。



复制代码
 1 <%@ page language="java" contentType="text/html; charset=UTF-8"
 2     pageEncoding="UTF-8"%>
 3 <%@ taglib uri="/struts-tags" prefix="s" %>
 4 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
 5 <html>
 6 <head>
 7 <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
 8 <title>Insert title here</title>
 9 </head>
10 <body>
11 
12 <table border="1">
13     <tr>        
14         <td>卡号</td>
15         <td>姓名</td>
16         <td>性别</td>
17         <td>办卡日期</td>
18         <td>押金</td>
19     </tr>
20     <!-- 使用struts2标签库中的iterator将所有数据遍历循环显示出来 -->
21     <s:iterator value="#myBookCardList" status="bcs">
22         <tr>    
23             <td><s:property value="cid"></s:property></td>
24             <td><s:property value="name"></s:property></td>
25             <td><s:property value="sex"></s:property></td>
26             <td><s:date name="cardDate" format="yyyy年MM月dd日"></s:date></td>
27             <td><s:property value="%{formatDouble(deposit)}"></s:property></td>
28         </tr>
29     </s:iterator>
30     <!-- 判断查询出来等于0，就显示“没有查找到数据” -->
31     <s:if test="myBookCardList.size()==0">
32         <tr>                    
33             <td colspan="7">没有查找到数据</td>
34         </tr>
35     </s:if>
36 </table>
37 </body>
38 </html>
复制代码
 

运行结果：

　　浏览器显示：

　　 

　　控制台输出：

 　　

 

　　总结：在SSH中使用Struts作为系统的整体基础架构，负责MVC的分离，在Struts框架的模型部分，控制业务跳转，利用Hibernate框架对持久层提供支持，Spring做支持，支持struts和hibernate。具体做法是：用面向对象的分析方法根据需求提出一些模型，将这些模型实现为基本的Java对象，然后编写基本的DAO(Data Access Objects)接口，并给出Hibernate的DAO实现，采用Hibernate架构实现的DAO类来实现Java类与数据库之间的转换和访问，最后由Spring做支持，支持struts和hibernate。其实ssh框架最主要的本质是：“高内聚、低耦合”。
