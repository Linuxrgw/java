# java
1、包：
作用：避免类重名；控制访问权限
定义：物理上是文件夹；逻辑上是有逻辑关系的类的集合
命名规范：
1、全部小写   
2、第一级 指该项目的类型，如com,org,gov等，
   第二级 指项目所开发或者运行的公司名称，如：chinasofti,icss,huawei等
   第三级 指项目的名称，如：corejava,bcms,oa,erp等
   第四级 指项目模块的名称，如：bean,action,exception,chapter01等
    eg：com.icss.bookshop.entity

使用：import:导入外部包的类
      package:编译到此目录下
2、 访问权限修饰符
 1）public ：公共权限   修饰类、属性、方法。可以被任意类访问
 2）protected：受保护的权限   修饰属性、方法。   可以被同包类访问，如果不是同包类，必须是该类的子类才可以访问。
 3）default：同包权限  修饰类、属性、方法。只能被同包的类访问
 4）private：私有权限  修饰属性、方法。 只能在本类中访问

3、封装性：
   封装性是一种信息隐藏技术    
    两个含义 ：对象的全部属性和全部方法结合在一起，形成一个不可分割的独立单位 尽可能隐藏对象的内部结构。
   主要体现：属性使用private权限； 方法使用public权限 

-----------------------------------------修饰符--------------------------------------------------------

1、静态属性：
   1、static属性可以使用对象调用，也可以直接用类名调用。
   2、静态属性是类的所有对象共享的，即不管创建了多少个对象，静态属性在内存中只有一个。
 
2、静态方法：
 1、任何方法都可以直接调用静态方法
 2、静态方法不能直接调用非静态方法，需要创建对象，用对象名调用非静态方法
 本类中
 静态方法：调用---静态方法
           不可以直接调用---非静态方法
 非静态方法：直接调用---静态方法
             可以直接调用---非静态方法
3、静态块
1、静态块只有在类加载的时候被执行一次，不管创建多少个对象，都不会再执行。
2、如果一个类加载的时候，总要预先做一些事情，则可以放在静态块中，例如，读取一个属性文件，进行一些常规配置，写一些日志等。
3、类中可以有多个静态块，按照顺序执行。

4、final属性
   1、被final修饰的属性---常量，不能被修改
   2、要么直接赋值；要么在构造方法里面赋值，如果有多个构造方法，那么每一个构造方法都要赋值，否则报错
   3、总的原则：保证创建每一个对象的时候，final属性的值是确定的
   4、在方法参数前面加final关键字，为了防止数据在方法体中被修改。
       private static final double pai = 3.14;  //通常和static一起使用
    private final int lev;   //必须每个构造方法都要赋值，否则报错
    
    public FinalTest() {
        lev = 1;
    }
    public FinalTest(String i){
        lev = 0;
    }
    
    //在方法参数前面加final关键字，为了防止数据在方法体中被修改。
    public void test(final int x){
//        x=12; //如果赋值会保存   
    }

5、属性和局部变量的区别
   属性：类中声明的变量或常量称为属性，也叫成员变量。可以使用访问权限修饰符，static、 final来修饰。作用域是整个类，有默认初始值。
   局部变量：方法里的变量或者常量，不能使用权限修饰符，不能使用static，可以使用final，没有默认值，必须手动初始化，遇到重名遵守就近原则。
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84428346 
版权声明：本文为博主原创文章，转载请附上博文链接！
