# java
排序：选择排序和冒泡排序
 冒泡排序原理：冒泡排序的基本原理是对存放原始数据的数组，按从前往后的方向进行多次扫描，每次扫描称为一趟。当发现相邻两个数据的次序与排序要求的大小次序不符合时，即将这两个数据进行互换。这样，较小的数据就会逐个向前移动，好象气泡向上浮起一样。
  int[] ary = {13,24,1,6,90,5};
    //多少趟排序
    for(int i = 0;i<ary.length-1;i++){
        //每一趟排序，比较数
        for(int j = 0;j<ary.length-1-i;j++){
            
            //比较如果前一个大于后面的数，交换
            if (ary[j]>ary[j+1]) {
                //交换
                int temp = ary[j];
                ary[j] = ary[j+1];
                ary[j+1] = temp;
            }
        }
    }

  选择排序的原理;每一趟从待排序的记录中选出最小的元素，顺序放在已排好序的序列最后，直到全部记录排序完毕
  int[] ary = {1,3,5,2,4};
     //做n趟排序
     for(int i = 0;i<ary.length-1;i++){
         int k = i;
         //选最小值
         for(int j = k+1;j<ary.length;j++){
             if (ary[j] < ary[k]) {
                 k = j;  //记录的是最小值的位置
            }
         }
         
         //结束本行排序，找到最小位置交互
         if (i!=k) {
            int temp = ary[i];
            ary[i] = ary[k];
            ary[k] = temp;
        } 
     }


枚举类型：enum 的全称为 enumeration， 是 JDK 1.5中引入的新特性，存放在 java.lang 包中。
        eg： public enum EnumTest {
            MON,TUE,WEN,THU,FAR,STA,SUN;
             }  
       使用：EnumTest e =  EnumTest.MON;

递归：
 定义一个方法时，出现本方法调用本方法的过程叫做递归。
 特点：1、必然后一个边界条件 2、使用递归代码往往更加简洁，可读性强。    
 /*5*4*3*2*1
  * 求5的阶乘
  */
 public static int g(int n){
     
     if (n==1) {  //边界条件
        return 1;
     }else{
        return n*g(n-1); //自己调用自己
     }
 }
 
 
 /*斐波那契数列：0，1，1，2，3，5，8......第40位的数。
  * 
  */
 public static int f(int n){
     if (n==1) {
        return 0;
    }else if(n==2){
        return 1;
    }else {
        return f(n-1)+f(n-2);
    }
 }
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84430781 
版权声明：本文为博主原创文章，转载请附上博文链接！
