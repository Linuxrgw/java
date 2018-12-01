# java
1、什么是集合？存储对象的容器，面向对象语言对事物的体现都是以对象的形式，所以为了方便对多个对象的操作，存储对象，集合是存储对象最常用的一种方式。
2、集合与数组的区别
   1、数组和集合类都是容器
   2、数组长度是固定的，集合长度是可变的。
    3、数组中可以存储基本数据类型，集合只能存储对象
   4、数组中存储数据类型是单一的，集合中可以存储任意类型的对象。
3、集合类的特点：用于存储对象，长度是可变的，可以存储不同类型的对象。
4、集合的三大接口
   Collection: 单列集合，三个子接口  
     (1) List: 有存储顺序, 可重复       
         ArrayList: 数组实现, 查找快, 增删慢。由于是数组实现, 在增和删的时候会牵扯到数组增容, 以及拷贝元素. 所以慢。数组是可以直接按索引查找, 所以查找时较快。               LinkedList:链表实现, 增删快, 查找慢。由于链表实现, 增加时只要让前一个元素记住自己就可以, 删除时让前一个元素记住后一个元素, 后一个元素记住前一个元素. 这样                     的增删效率较高但查询时需要一个一个的遍历, 所以效率较低。     
         Vector:数组实现，和ArrayList原理相同, 但线程安全, 效率略低。
    (2) Set: 无存储顺序, 不可重复，set中没有索引      
        HashSet---底层是哈希码表，基于HashMap实现的       
        TreeSet--- 底层是二叉树 元素不重复，并且实现了排序。           
    (3)Queue:队列，实现了先进先出
    Map: 键值对形式存储---Key值不允许重复，如果重复，则覆盖。            
        HashMap-- key值的hashCode和equals保证元素唯一性            
        TreeMap--不仅可以保证key不重复，还可以对value数据进行排序。            
        HashTable--实现同步
   Iterator：迭代接口
5、ArrayList
List的特点：有序存储(不是数据的排序，是存入的顺序)，可重复
常用方法：
boolean add(Object o)    在列表的末尾顺序添加元素，起始索引位置从0开始
void add(int index,Object o)    在指定的索引位置添加元素。索引位置必须介于0和列表中元素个数之间
int size()    返回列表中的元素个数
Object get(int index)    返回指定索引位置处的元素。取出的元素是Object类型，使用前需要进行强制类型转换
boolean contains(Object o)    判断列表中是否存在指定元素
boolean remove(Object o)    从列表中删除元素
Object    remove(int index)    从列表中删除指定位置元素，起始索引位置从0开始

 
6、LinkedList
LinkedList采用链表存储方式。插入、删除元素时效率比较高
常用方法：
void    addFirst(Object o)    在列表的首部添加元素
void    addLast(Object o)    在列表的末尾添加元素
Object    getFirst()    返回列表中的第一个元素
Object    getLast()    返回列表中的最后一个元素
Object    removeFirst()    删除并返回列表中的第一个元素
Object    removeLast()    删除并返回列表中的最后一个元素


集合的三种遍历方式：
for foreach  迭代器

迭代器的方法：
获取到迭代器的时候，迭代器中有一个指针指向了集合中的第一个元素。
hasNext() ：当前指针是否有指向元素，如果有返回true，否则返回false。
next():获取当前指针指向的元素并返回当前元素，然后指针向下移动一个单位。

7、Vector
Vector 底层维护了一个Object数组实现的，实现与ArrayList是一样的，但是Vector是线程安全的，操作效率低。
特有的方法：
     void addElement(E obj)  在集合末尾添加元素
     E elementAt( int index) 返回指定角标的元素
     Enumeration elements()  返回集合中的所有元素，封装到Enumeration对象中

Enumeration 接口：
      boolean hasMoreElements()  测试此枚举是否包含更多的元素。 
      E nextElement() 如果此枚举对象至少还有一个可提供的元素，则返回此枚举的下一个元素。
说出ArrayList与Vector的区别？
      相同点：ArrayList与Vector的底层都是由Object数组实现的。
      不同点：1、ArrayList是线程不同步的，操作效率高。Vector是线程同步的，效率低。
              2、ArrayList是JDK1.2出现的。Vector是jdk1.0的时候出现的。

8、HashSet
  set接口特点：无存储顺序 不重复，没有索引
  不重复：彼此调用equals方法比较，都返回false
  如果想让重复的对象不插入，要重写hashcode和equals方法。
  注意：1、往HashSet添加元素的时候，HashSet会先调用元素的hashcode方法得到元素的哈希值，然后通过元素的哈希值经过移位等运算，就可以算出该元素在哈希表中的存储位置。
        2、情况1：如果算出元素存储的位置目前没有任何元素存储，那么该元素可以直接存储在该位置上。 情况2：如果算出元素存储的位置目前已经有其它元素存储了，那么会调用该           元素的equals方法与改位置的元素再比一次，如果equals返回的是true，那么该元素与该位置上的元素视为重复元素，不允许添加，如果equals方法返回的是false，那么该           元素进行添加。
        3、哈希表的特点：桶式结构 一个位置可以存放多个元素

9、TreeSet
   TreeSet特点：无序  不重复  可按照规则排序
   注意：1、TreeSet中存放的对象必须实现Comparable接口，否则报错
         2、TreeSet存储原理：底层使用二叉树数据结构实现    存储规则：左小右大
         3、如果比较元素的时候，compareTo方法返回的是0，那么该元素就被视为重复元素，不允许添加（TreeSet与hashcode和equals方法是没有任何关系的）

10、HashMap
   HashMap的特点：
   HashMap中元素的key值不能重复，即彼此调用equals方法，返回为false。
   排列顺序是不固定的。底层使用哈希表实现。如果出现了相同的键，那么后添加的数据的值会取代之前的值。

常用方法
Object put(Object key, Object val)    以“键-值对”的方式进行存储
Object get (Object key)    根据键返回相关联的值，如果不存在指定的键，返回null
Object remove (Object key)    删除由指定的键映射的“键-值对”
int size()    返回元素个数
Set keySet ()    返回键的集合
Collection values ()    返回值的集合
boolean    containsKey (Object key)    如果存在由指定的键映射的“键-值对”，返回true

11、TreeMap
   适用于按自然顺序或自定义顺序遍历键(key)。
   TreeMap根据key值排序，key值需要实现Comparable接口，重写compareTo方法。TreeMap根据compareTo的逻辑，对key进行排序。

12、Properties
    Properites类是Hashtable类的子类，所以也间接地实现了Map接口。在实际应用中，常使用Properties类对属性文件进行处理。
    常用方法：load()加载文件；
              getProperty(key);通过key值获得对应的value值
              setProperty（String?key,String?value)给properties文件中写值。 
13、Collections：是集合类的工具类，与数组的工具类Arrays类似
    使用步骤：
    1、要想使用Collections工具类排序，先给实体类实现Compareable接口，重写compareTo方法
    2、Collections.sort(list)  Collections类对ArrayList的排序使用
--------------------- 
作者：Ren_gw 
来源：CSDN 
原文：https://blog.csdn.net/Ren_gw/article/details/84430585 
版权声明：本文为博主原创文章，转载请附上博文链接！
