# java
ioc原理 
public class UserService{

}
public class UserSerlet{
  //得到UserService 的对象
  //原始 ：new 创建
  UserFactory.getService();
  
  }
  
  第一步 创建xml 配置文件，配置要创建的对象类
 <bean id ="userService" class="cn.itcast.UserService"/ >
 
 第二部 创建工厂类 ，使用dom4j解析配置文件+反射 
 
 //返回UserService 对象的方法 
 public static UserService get Service(){
   //1使用dom4j解析xml文件
   //根据id值 userService, 得到id值对应的class属性值
   String classValue ="class属性值";
   //2 使用反射创建类对象
   Class clazz =Class.forName(classValue);
   //创建类对象
   UserService service =clazz.newInstance();
   return service;
 }
--------- 2018.7.3--------------------
