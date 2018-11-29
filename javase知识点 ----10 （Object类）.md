# java
1、Object类在java.lang包下，是所有类的根类。任何类的对象，都可以调用Object类中的方法，包括数组对象
2、Object和Object[]之间的区别
   1、方法中的形参是Object类型时，任何类型的参数都可以传进去执行。
   2、方法中形参是Object[]类型时，只有对象数组可以传入执行。

3、toString方法：
 1、toString方法可以将任何一个对象转换成字符串返回，返回值的生成算法为：getClass().getName() + '@' + Integer.toHexString(hashCode())。类名@哈希码值的十六进制
 2、如果想让对象直接输出想要的格式，重写toString方法。
4、equals
 1、object类中equals方法比较的是虚地址
 2、String类中的equals方法是重写了object的equals比较的是内容
 3、比较两个对象的时候，要重写equals和hashCode方法，来比较内容相等

5、hashCode方法
   获取对象的哈希码值。同一个对象的哈希码值是唯一的。
6、equals方法与hashCode方法关系
   1、如果两个对象使用equals比较返回true，那么它们的hashCode值一定要相同。
   2、如果两个对象equals比较返回false,那么它们的hashCode值不一定不同
   3、覆盖equals，往往需要覆盖hashCode，保证equals返回true，则hashCode相同；equals返回false，则hashCode不同
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84429559 
版权声明：本文为博主原创文章，转载请附上博文链接！
