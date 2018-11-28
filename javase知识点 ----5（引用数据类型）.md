# java
1、引用数据类型
    1、应用场景：属性 参数 返回值类型
    2、赋值：引用类型都是对象，所以赋值都使用new调用构造方法进行赋值； 例外：String类和包装器类可以直接使用=赋值，一般不使用new

2、基本数据类型和引用数据类型的区别
 1、概念         变量（单纯的值）        对象（引用）
 2、存储位置    在栈中存值                在栈中存引用，在堆中存具体对象的属性值
 3、赋值方式    直接赋值                        new ，String类和包装器类可以直接赋值

3、赋值
   1、基本数据类型之间赋值，是将值进行拷贝，是两块互不影响的空间
   2、引用类型之间赋值，是虚地址之间的赋值  eg：t1 = t2 就是把t2的虚地址赋值给t1，所以t1和t2指向同一块内存

4、==运算
 1、在判断引用数据类型时判断的是地址,即虚地址一样才返回true
 2、在判断基本数据类型时判断的是数值，即二进制一样才返回true   eg：0.3f==0.3  false   0.5f==0.5  true

5、String类
   1、创建对象的两种方式： 1、String str = "abc" 2、使用构造方法赋值：eg:String str2 = new String（"abc"） char[] ary = {'a','b'}  String str3 = new String(ary) 
      
   2、两种创建方式的区别
      1、使用构造方法，每次生成一个新的字符串
      2、直接=赋值，从字符串常量池中取值
   3、String str1 = new String（“abc”）一共创建了几个对象？2个对象
      String str2 =  “abc”；---  在常量池一个对象
      String str3 = new String（str）； --- 堆内存里一个对象 String  
      str = new String（“a”+“b”）一共创建了几个对象？4个对象
      String str = “a” String str = “b” String str = “ab” str是一个对象
   3、获取字符串长度：int length()
   4、equals方法：比较两个字符串的内容是否相等（String类重写了object类里面的equals方法）
   5、常用方法
            String s1 = "etc";
        System.out.println(s1.equalsIgnoreCase("ETC"));  //判断参数字符串是否与当前字符串相等，忽略大小写形式
           //s1位于参数字符串之前，则比较结果为一个负整数。s1位于参数字符串之后，则比较结果为一个正整数。如果这两个字符串相等，则结果为 0
        System.out.println(s1.compareTo("f")); //根据unicode码（字典）比较字符串参数和当前字符串的大小
        System.out.println(s1.startsWith("s"));//判断当前字符串是否以参数为开头
        
        System.out.println(s1.indexOf("c"));   //根据字符串查找它的索引
        System.out.println(s1.indexOf(99));  //搜索字符ch(unicode)在当前字符串中第一次出现的索引，没有出现则返回-1
        
        String s2 = "et@ce";
        System.out.println(s2.indexOf("@"));  //2
        System.out.println(s2.lastIndexOf("e")); //4  //找到最后一个参数字符索引的位置

        char ch = s2.charAt(2);  //用于从指定位置提取单个字符，该位置由index指定，索引值必须为非负
        System.out.println(ch);
        
        String cardNo = "1289";
        String a = cardNo.substring(0,1);  //用于提取 两个参数位置之间的字符串部分
        String b = cardNo.substring(1,2);
        String c = cardNo.substring(2,3);
        String d = cardNo.substring(3,4);
        System.out.println(Integer.parseInt(a)+Integer.parseInt(b)+Integer.parseInt(c)+Integer.parseInt(d));
        
        System.out.println(cardNo.substring(1));  //截取从参数开始到最后一个字符
        System.out.println(" abc ".trim()); //去掉字符串前后的空格
        System.out.println(cardNo.concat(s1));//用于连接两个字符串，并新建一个包含调用字符串的字符串对象
        System.out.println(cardNo.replace("1", "a")); //用于将调用字符串中出现oldChar指定的字符全部都替换为newChar指定的字符

        //Strig类型的不可变性
        String s3 = new String("icss");
        s3 =  s3.toUpperCase();//返回的全是大写字母
        System.out.println(s3); 
        
        //返回当前字符串转化成byte型数组的形式（即字符串在内存中保存的最原始的二进制形态）
        byte[] ary1 = s3.getBytes();
        for (byte e : ary1) {
            System.out.println(e);
        }
        //返回当前字符串的字符数组形式
        char[] ary2 = s3.toCharArray();
        for (char e : ary2) {
            System.out.println(e);
        }

6、StringBuffer与StringBuilder
   1、StringBuffer类用于表示可以修改的字符串，称为字符串缓冲对象
   2、StringBuffer与StringBuilder它们虽然也是字符串，但是它们却不能够直接赋值，必须用new来创建。  
   3、String 和StringBuff StringBuilder区别？
    （1）赋值   String可以用等号赋值也可以用构造方法赋值    StringBuff和StringBuilder只能用new
    （2）String是不可变的，stringBuffer和StringBuilder是可变的
    （3）             StringBuffer    StringBuilder
           线程是否安全    安全            不安全
             效率    相对低            相对高

   4、常用方法
        StringBuffer sbf = new StringBuffer("abc");
    System.out.println(sbf.append("cdf")); //连接
    System.out.println(sbf.reverse()); //倒序
    sbf.insert(5, "Student");    //插入
        System.out.println(sbf);
        sbf.setCharAt(4, '.');      //替换字符
        System.out.println(sbf);

7、包装器类型
   1、在java.lang包下
   2、每一种基本数据类型都对应一种包装器类型
      基本数据类型        包  装  类
      boolean（布尔型）        Boolean
      byte（字节型）        Byte
      char（字符型）        Character
      short（短整型）        Short
      int（整型）        Integer
      long（长整型）        Long
      float（浮点型）        Float
      double（双精度浮点型） Double
   3、valueOf方法，用于将字符串转换成相应包装类的对象。  
      eg:Integer integer = Integer.valueOf(str);  
   4、静态的parseXxx方法（Xxx指代具体的数据类型），用于将字符串转换成相对应的基本数据类型值。
      eg:double d = Double.parseDouble(str);
   5、自动封解箱操作
      int x = 10;
      Integer y = x;//装箱操作
      int z = y; //拆箱操作
   6、Character类中的常用方法
      boolean isLetter(char ch)     判断字符ch是否为英文字母 
      boolean isDigit(char ch)     判断字符ch是否为0~9之间的数字 
      boolean isUpperCase(char ch)     判断字符ch是否为大写形式 
      boolean isLowerCase(char ch)     判断字符ch是否为小写形式 
      boolean isWhitespace(char ch)     判断字符ch是否为空格或换行符 

8、值传递
   值传递的本质是赋值,是把实际参数赋值给形式参数的过程
   1、基本数据类型是值之间进行赋值
   2、引用数据类型虚拟地址之间进行赋值
   值传递
  1、基本数据类型在传递过程中形参改变实参不改变
  2、引用类型在传递过程中形参改变实参也改变。
  3、虽然String 、包装器类本身是引用数据类型，但是按基本数据类型的规则传递。
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84428270 
版权声明：本文为博主原创文章，转载请附上博文链接！
