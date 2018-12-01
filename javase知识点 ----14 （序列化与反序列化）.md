# java
序列化与反序列化
1、Java序列化：把Java对象转换为二进制的数据流 ；
   Java反序列化：把字节序列恢复为Java对象的过程。 
2、应用：（1）永久性保存对象，保存对象的字节序列到本地文件或者数据库中； （2）通过序列化以字节流的形式使对象在网络中进行传递和接收；
3、序列化
   步骤：
   1、将要序列化的对象实现Serializable接口
   2、创建输出流对象 ：ObjectOutputStream
   3、往文件中写入字节序列 ：writeObject
   4、关闭资源：close
    eg：File file = new File("C:\\Users\\GuXue\\Desktop\\test.txt"); //创建F类对象
    ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(file));//创建输出流对象
    User user = new User("zhangdan", 12); //将要序列化的对象 
    oos.writeObject(user); //往文件中写入字节序列（可以对参数指定的obj对象进行序列化，把得到的字节序列写到一个目标输出流中）
    oos.close(); //关闭资源
4、反序列化
      File file = new File("C:\\Users\\GuXue\\Desktop\\test.txt");  //创建File对象
    ObjectInputStream ois = new ObjectInputStream(new FileInputStream(file)); //创建输入流对象
    Object object =  ois.readObject(); //读取字节序列（输入流中读取字节序列，再把它们反序列化成为一个对象，并将其返回。）
    User user = (User)object; //把object类型转换成User
    System.out.println(user);
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84430668 
版权声明：本文为博主原创文章，转载请附上博文链接！
