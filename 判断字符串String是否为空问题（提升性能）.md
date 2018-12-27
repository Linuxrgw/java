# java
判断字符串String是否为空问题
一、判断一个字符串str不为空的方法有：

　　1、str == null;

　　2、"".equals（str）；

　　3、str.length <= 0;

　　4、str.isEmpty（）；

　　注意：length是属性，一般集合类对象拥有的属性，取得集合的大小。

　　例如：数组。length就是取得数组的长度。

　　length（）是方法，一般字符串类对象有该方法，也是取得字符串长度。

　　例如：字符串。length（）；

　　说明：

　　1、null表示这个字符串不指向任何的东西，如果这时候你调用它的方法，那么就会出现空指针异常。

　　2、""表示它指向一个长度为0的字符串，这时候调用它的方法是安全的。

　　3.、null不是对象，""是对象，所以null没有分配空间，""分配了空间，例如：

　　String str1 = null; str引用为空

　　String str2 = ""; str引用一个空串

　　str1还不是一个实例化的对象，而str2已经实例化。

　　对象用equals比较，null用等号比较。

　　如果str1=null;下面的写法错误：

　　if（str1.equals（""）||str1==null）{ }

　　正确的写法是 if（str1==null||str1.equals（""））{ //所以在判断字符串是否为空时，先判断是不是对象，如果是，再判断是不是空字符串 }

　　4. 所以，判断一个字符串是否为空，首先就要确保他不是null,然后再判断他的长度。

　　String str = xxx;

　　if（str != null && str.length（） != 0） { }

　　二、以下是java 判断字符串是否为空的四种方法：

　　四种方法执行的效率分别如下：

　　JudgeString1耗时：625ms

　　JudgeString2耗时：125ms

　　JudgeString3耗时：234ms

　　JudgeString4耗时：109ms

复制代码
 1 　/**
 2 
 3 　　* 判断字符串是否为空的效率问题
 4 
 5 　　*/
 6 
 7 public class JudgeStringIsEmptyOrNot {
 8 
 9 　　public static void main（String[] args） {
10 
11 　　    JudgeString1（"w_basketboy", 10000）；
12 
13 　　    JudgeString2（"w_basketboy", 10000）；
14 
15 　　    JudgeString3（"w_basketboy", 10000）；
16 
17 　　    JudgeString4（"w_basketboy", 10000）；
18 
19 　　}
20 
21 　　/**
22 
23 　　* 方法一： 最多人使用的一个方法， 直观， 方便， 但效率很低；
24 
25 　　* 方法二： 比较字符串长度， 效率高， 是最好的一个方法；
26 
27 　　* 方法三： Java SE 6.0 才开始提供的方法， 效率和方法二几乎相等， 但出于兼容性考虑， 推荐使用方法二；
28 
29 　　* 方法四： 这是一种比较直观，简便的方法，而且效率也非常的高，与方法二、三的效率差不多；
30 
31 　　*/
32 
33 public static void JudgeString1（String str, long num） {
34 　　long startTiem = System.currentTimeMillis（）；
35 　　for （int i = 0; i < num; i++） {
36 　        for （int j = 0; j < num; j++） {
37 　    　    if （str == null || "".equals（str）） {
38 　　        }
39 　　    }
40 　　}
41     long endTime = System.currentTimeMillis（）；
42 　 System.out.println（"function1耗时：" + （endTime - startTiem） + "ms"）；
43 
44 }
45 
46 public static void JudgeString2（String str, long num） {
47 　　long startTiem = System.currentTimeMillis（）；
48 　　for （int i = 0; i < num; i++） {
49 　    　for （int j = 0; j < num; j++） {
50 　　        if （str == null || str.length（） <= 0） {
51 　　        }
52 　　    }
53 　　}
54 　　long endTime = System.currentTimeMillis（）；
55 　　System.out.println（"function4耗时：" + （endTime - startTiem） + "ms"）；
56 }
57 
58 public static void JudgeString3（String str, long num） {
59 　　long startTiem = System.currentTimeMillis（）；
60 　　for （int i = 0; i < num; i++） {
61 　　    for （int j = 0; j < num; j++） {
62 　　        if （str == null || str.isEmpty（）） {
63 
64 　　        }
65 　　    }
66 　　}
67 　　long endTime = System.currentTimeMillis（）；
68 　　System.out.println（"function3耗时：" + （endTime - startTiem） + "ms"）；
69 
70 　　}
71 
72 public static void JudgeString4（String str, long num） {
73 　　long startTiem = System.currentTimeMillis（）；
74 　　for （int i = 0; i < num; i++） {
75 　　    for （int j = 0; j < num; j++） {
76 　　        if （str == null || str == ""） {
77 　　        }
78 　　    }
79 　　}
80 　　long endTime = System.currentTimeMillis（）；
81 　　System.out.println（"function4耗时：" + （endTime - startTiem） + "ms"）；
82 　　}      
转载自：https://www.cnblogs.com/ayan/p/3524816.html
