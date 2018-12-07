# java
1、输入输出概念：
  入还是出是相对于内存来说的
  把数据读到内存中，称为输入,即input,进行数据的read操作
  从内存往外部设备写数据，称为输出，即output，进行数据的write操作

2、File类
  注意:1、File类是java.io包中很重要的一个类；
       2、在程序中一个File类对象可以代表一个文件或目录；
       3、File对象可以对文件或目录的属性进行操作，如：文件名、最后修改日期、文件大小等；但是不能直接对文件进行读/写操作。
  
  创建对象：
  //在当前项目目录下创建一个与aaa.txt文件名相关联的文件对象
   File f1 = new File("aaa.txt");
  //指明详细的路径以及文件名，请注意双斜线或用反斜杠
    File f2 = new File("C:\\Users\\GuXue\\Desktop\\aaa.txt");
    File f3 = new File("C:/Users/GuXue/Desktop/test.txt");
  //指明详细的路径以及目录名，请注意双斜线
    File f4  = new File("C:/Users/GuXue/Desktop/java");
  
  常用方法：
  boolean exists()    判断文件是否存在，存在返回true，否则返回false
  boolean isFile()    判断是否为文件，是文件返回true，否则返回false
  boolean isDirectory()    判断是否为目录，是目录返回true，否则返回false
  String getName()    获得文件的名称
  String getAbsolutePath()    获得文件的绝对路径
  long length()                   获得文件的长度（字节数）
  boolean createNewFile()throws IOException    创建新文件，创建成功返回true，否则返回false，有可能抛出IOException异常，必须捕捉
  boolean delete()    删除文件，删除成功返回true，否则返回false
  boolean mkdir()     创建由此抽象路径名命名的目录。 eg:f4.mkdir()---创建一个目录

  public String[] list()    将目录下的子目录及文件的名字，返回到String数组中
  public File[] listFiles()    将目录下的子目录及文件的实例返回到File数组中

3、流分类
 （1）流按着数据的传输方向分为：
   -输入流：往内存中读叫输入流。类名以InputStream结尾的类和Reader结尾的类
   -输出流：从内存中往外写叫输出流。类名以OutputStream结尾的类和Writer结尾的类
 
 （2）从数据流编码格式上划分为：
   -字节流：InputStream和OutputStream的子类都是字节流；
            可以读写二进制文件，主要处理音频、图片、歌曲。处理单元为1个字节。
            常用类：FileInputStream、FileOutputStream
   -字符流：Reader和Writer的子类都是字符流；
            主要处理字符或字符串，字符流处理单元为2个字节。主要处理文本。
            常用类：FileReader、FileWriter。
    
   字符流--方式一  FileReader案例
       //创建文件对象
        File file = new File("C:/Users/GuXue/Desktop/test.txt");
        //创建流对象
        FileReader fr = new FileReader(file);
        int i = fr.read();//读一个字符 
        //边读边输出
        while(i!=-1){
            System.out.print((char)i);
            i = fr.read();
        }
        fr.close(); //关闭流并释放与之相关联的任何系统资源。

   字符流--方式二  FileReader案例   
 
       //创建流对象
        FileReader fr = new FileReader(file);
        char[] b = new char[1024];  //创建数组 
        int len = fr.read(b);// 将字符读入数组。
        
        //遍历输出
        for (int i = 0; i < len; i++) {
            System.out.println(b[i]);
        }
   字符流---FileWriter案例
        FileWriter fw = new FileWriter(file,true); //根据给定的文件名以及指示是否附加写入数据的 boolean 值来构造 FileWriter 对象。
        //循环写入单个字符
        for (int i = 100; i < 112; i++) {
            fw.write(i);
        }
        fw.flush();//刷新该流的缓冲

   字节流--FileInputStream
         fis = new FileInputStream(file);
        int i = fis.read();
        while(i!=-1){
          System.out.print((char)i);
           i = fis.read();
      }
  
   
 （3）根据封装类型不同流又分为
   -节点流：如果流封装的是某种特定的数据源，如文件、字符串、字符串数组等，则称为节点流。
            常用节点流对象：字节输入流 FileInputStream、字节输出流 FileOutputStream、字符输入流 FileReader、字符输出流 FileWriter
   -处理流：如果流封装的是其它流对象，称为处理流。处理流提供了缓冲功能，提高读写效率。
            常用处理流对象：缓冲字节输出流 BufferedOutputStream、缓冲字节输入流 BufferedInputStream、缓冲字符输入流 BufferedReader、缓冲字符输出流 BufferedWriter
   readLine()：读取一行
   newLine()：写入一个空行
   flush()：内存数据刷到硬盘上。
   注意：在使用字符缓冲输出流时，一定先flush(),然后再close(),避免数据的丢失。

  处理流----BufferedReader
      //创建流对象--处理流
        BufferedReader br = new BufferedReader(new FileReader(file));
        String line = br.readLine(); //读取一个文本行。
        while(line!=null){
            System.out.println(line);
            line = br.readLine();  
        }

  处理流---一个文件的内容复制到另一个文件中 ---BufferedWriter和BufferedReader 
        BufferedReader bfr = new BufferedReader(new FileReader(file1));  //参数体现了多态
        BufferedWriter bfw = new BufferedWriter(new FileWriter(file2));
        
        String line = bfr.readLine(); //读一行数据
        //读出一行数据，就写入一行数据
        while(line!=null){
            System.out.println(line);
            bfw.write(line); //一行一行的写入
            bfw.newLine(); //写入一个空行的方法newLine()。
            line = bfr.readLine();
        }
        bfw.flush();//刷新数据
        bfw.close();
        bfr.close();
  处理流---BufferedInputStream 和 BufferedOutputStream 
        BufferedInputStream bfr = new BufferedInputStream(new FileInputStream(file1));  //参数体现了多态
        BufferedOutputStream bfw = new BufferedOutputStream(new FileOutputStream(file2));
        
        int i = bfr.read(); //读一行数据
        //读出一行数据，就写入一行数据
        while(i!=-1){
            System.out.print((char)i);
            bfw.write(i); //一行一行的写入
            i = bfr.read();
        }
  

  （4）转换流：字符流与字节流之间的桥梁
      BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
      String line1 = bf.readLine(); 

  （5）分析步骤：
       1、读？写？先读后写
       2、字节流还是字符流？文本   字符流
       3、是否提高效率？是--处理流----BufferedReader   BufferedWriter

       代码步骤：
       1、先来创建File对象
       2、创建流对象
       3、读操作或者是写的操作   边读，边写入
       4、写的时候需要刷新
       5、关闭资源
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84501776 
版权声明：本文为博主原创文章，转载请附上博文链接！
