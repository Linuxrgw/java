# java
1、异常和错误的区别
  异常指的是运行过程中的不正常事件，可以被异常机制处理，程序能够继续运行下去；
  错误不能够被处理，发生错误后，程序就终止，程序员需要修改源代码才能解决错误；
  
2、异常体系：
   Throwable类有两个直接子类：Exception类（运行期异常（所有RuntimeException的子类）和编译期异常（除了运行期以外的））、Error类。

3、
try{
      可能抛出异常的代码块;
}catch(异常类型  变量名){
       处理异常的代码;
}finally{
      不管什么情况，一定被执行的代码块；
}


注意：1、当try的语句发生异常，此条语句后面的语句就不再执行了
     

4、catch里面可以写什么？
    1、可以写任意需要对异常进行处理的代码；
    2、可以调用异常对象的方法，例如printStackTrace，查看异常发生的栈轨迹

注意：一个try后面可以写多个catch
     catch语句的异常类型必须从子类到父类的顺序，否则编译错误；


5、我们可以发现程序中有这样几种情况：
没抛出异常；     try-finally--继续执行程序
抛出异常并被处理了；   try - catch --finally--继续执行程序
抛出异常没有被处理；   try--catch异常匹配失败，跳出catch--finally--终止程序


6、catch及finally的可选特性
  1、必须有try，catch可以有1个或多个，finally最多1个，可以没有，不能有多个；
  2、还有另外一种组合：只有try和finally，没有catch

7、finally与return的执行顺序
  1、总之 finally 永远执行！除非前面有System.exit(0)退出虚拟机。
  2、return在finally之后执行

8、throw、throws
throw 异常对象；eg：throw new Exception();
或者
catch(Exception e){
    throw e;
}

throws用在方法声明处，声明该方法可能发生的异常类型；
注意：1、一个方法如果使用了throws，那么调用该方法时，编译器会提醒必须处理这些异常，否则编译错误；
     2、throws后可以声明多种类型，用逗号隔开即可；
     3、抽象方法也可以使用throws声明该方法可能抛出的异常类型；


9、自定义异常
基本语法
public  class 异常类名 extends Exception{
        public 异常类名(String msg){
            super(msg);
     }
 }
 
 在程序中使用自定义异常大致可以分为以下几步
1、创建自定义异常类
2、在方法中通过throw 关键字抛出自定义异常
3、如果在当前抛出异常的方法中处理异常，可以使用try-catch语句捕获并处理，否则在方法的声明处通过throws关键字声明该异常
4、调用throws声明该异常的方法时，使用try  catch捕获自定义的异常类型，并在catch中进行处理
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84429921 
版权声明：本文为博主原创文章，转载请附上博文链接！
