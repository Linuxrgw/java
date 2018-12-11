# java
1、反射的概念？
   JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取信息以及动态调用对象的方法的功能称为java语言的反射机制。

2、如何做到反射？
   当一个字节码文件加载到内存的时候，jvm会对该字节码进行解剖，然后创建一个对象的Class对象，把字节码文件的信息全部都存储到该Class对象中，我们只要获取到Class对象，我们就可以使用字节码对象设置对象的属性或者调用对象的方法等操作。

3、反射的作用：动态获取类的信息，进一步实现需要的功能 例如：Spring框架通过XML文件描述类的基本信息，使用反射机制动态装配对象

4、Class在java.lang包中；其他类都位于java.lang.reflect包中；反射的使用都是从Class开始

5、Class类
获取Class类实例的三种方式：
方式一：对象名.getClass()
方法二:Class.forName()
方法三：类名.class
   
Class类的常用方法：
getFields()    获得类的public类型的公共属性。
getDeclaredFields()    获得类的所有属性 
getField(String name)    获得类的指定属性
getMethods()    获得类的public类型的方法
getMethod (String name，Class [] args)    获得类的指定方法
getConstrutors()    获得类的public类型的构造方法
getConstrutor(Class[] args)    获得类的特定构造方法
newInstance()    通过类的无参构造方法创建该类的一个对象
getName()    获得类的完整名字
getPackage()    获取此类所属的包
getSuperclass()    获得此类的父类对应的Class对象

6、Constructor类
Constructor类可以通过getXXX方法获得构造方法的基本信息，例如：
  getName:返回构造方法的名字
  getParameterTypes：返回构造方法的参数类型
除了获得构造方法的基本信息，还可以创建实例
newInstance(Object... initargs) ：创建实例

Constructor实例通过Class实例获得，Class类中定义了如下方法
Constructor<T> getConstructor(Class... parameterTypes) ：通过指定参数类型，返回构造方法实例。
Constructor[] getConstructors() ：返回该类的所有构造方法实例。

7、Method类
Method类将类中的方法进行封装，可以动态获得方法的信息，例如
getReturnType：获得方法返回值类型
getName：获得方法名字
getParameterTypes：获得方法参数类型
除了动态获得方法信息外，Method还能动态调用某一个对象的具体方法
invoke(Object obj, Object... args) ：使用obj调用该方法，参数为args

Method实例都是通过Class类的方法获得
Method getMethod(String name, Class... parameterTypes) ：通过指定方法名，参数类型，返回一个Method实例
Method[] getMethods() ：返回该类中所有方法的Method实例


8、Field类
Field类将类的属性进行封装，可以获得属性的基本信息、属性的值，也可以对属性进行赋值
getName：返回属性的名字
getXXX：例如，getFloat返回该属性float类型的值
setXXX：例如，setFloat为属性赋值float类型的值

获得Field实例，都是通过Class中的方法实现
public Field getField(String name)
通过指定Field名字，返回Field实例
注意Field的访问权限 （一定是public）
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84501875 
版权声明：本文为博主原创文章，转载请附上博文链接！
