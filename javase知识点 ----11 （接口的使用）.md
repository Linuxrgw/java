# java
1、接口的声明形式
  [访问权限修饰符] interface 接口名 [extends 父接口名列表]{

    [public] [static] [final] 常量;

    [public] [abstract] 方法;
 }

注意：1、访问权限修饰符：可选，用于指定接口的访问权限，可选值为public。即使省略，也依然是public。
      2、接口名：要求首字母大写。
      3、extends 父接口名列表：可选参数，用于指定要定义的接口继承于哪个父接口。当使用extends关键字时，父接口名为必选参数。父接口可以存在多个，用逗号隔开。
      4、方法：接口中的方法都是抽象方法。
      5、就算不写public static final 依然是常量。
      6、就算不写public abstract 依然是抽象方法。


2、实现类的声明形式：
   [访问权限修饰符] class 类名 [extends 父类名] [implements 接口列表]{}
 
  注意：1、访问权限修饰符：可选参数，用于指定类的访问权限，可选值为public、abstract和final。
        2、类名：首字母大写
        3、extends 父类名：可选参数，用于指定要定义的类继承于哪个父类。当使用extends关键字时，父类名为必选参数
        4、implements 接口列表：可选参数，用于指定该类实现的是哪些接口。当使用implements关键字时，接口列表为必选参数。当接口列表中存在多个接口名时，各个接口名之间                                使用逗号分隔。
        5、类最多只能继承一个类，即单继承，而一个类却可以同时实现多个接口

3、java接口继承接口的原则
   1、Java接口可以继承多个接口
   2、接口继承接口依然使用关键字extends，不要错用成implements
   3、接口继承接口的声明形式：Interface3 extends Interface0, Interface1, interface……

4、接口继承与类继承对比：Java类的继承是单一继承，Java接口的继承是多重继承。

5、抽象类和接口的区别
        abstract class                     interface
属性         不用限制                             静态常量
构造方法         有构造方法                             没有
普通方法         可以有具体方法，也可以有抽象方法     必须是抽象方法
子类         单一继承                             多重实现

6、面向接口编程：登入     

7、compareable接口
   Arrays.sort() 用来排序
   （1）如果是基本数据类型排序，可以直接排序  eg：int[] ary01 = {5,1,3,4};Arrays.sort(ary01); 
   （2）如果是对象数组的排序，必须要实现compareable接口，重写compareto的方法。
 
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84429610 
版权声明：本文为博主原创文章，转载请附上博文链接！
