# Java 

1. ###char类型是否可以储存一个汉字？

    **是。**
    java 语言中使用Unicode字符集，可以存储65535个字符。所以java的字符类型被定义为双字节(16位)。
    
2. ###Final 

    final 修饰的变量 其值不允许在程序运行时修改。
    final 修饰的类 不允许有子类。
    final 修饰的方法 不允许被重写。
    final 修饰的参数 不允许被修改。
    
3. ###局部变量，当局部变量的方法调用结束后，java虚拟机将自动释放局部变量所占用的资源。
4. ###如何比较 4 － 3.6 和 0.4 ?

    System.out.print(4-3.6 == 0.4); ==> false
    
    使用BigDecimal类来进行浮点数的运算结果。
    
   java:
   
       BigDecimal x  = new BigDecimal("4");
       BigDecimal y = new BigDecimal("3.6");
       BigDecimal z = x.subtract(y);
       double value = z.doubleValue();
       a =  value == 0.4; 
       System.out.print(a);  // ==> true
   
 5. ###如何最有效的计算2 乘 16
 
     * 2*16
     * 2 << 4 //最有效
     
     在计算机中，通常位运算的效率最高。
    > java提供 左移，右移和无符号右移 运算符。 << >> >>>
    > 左移 将左侧的操作数乘以2的n次幂
    > 右移 将左侧的操作数除以2的n次幂
    
6. ### switch 语句

    条件表达式类型：任何byte ，short， int ，char
    
7. ### 跳出多重循环

    借助Label机制。所谓Label，就是紧接冒号的标示符。该标示符将被放置在循环语句之前。
    可以使用continue label或者 break label 跳出本次循环或者结束循环。
    
  java:
  
      public static void main(String[] args){
        label:
            for (int i = 1; i <= 7 ; i ++){
                for (int kong = 7; kong > i - 1;kong-- ){
                    System.out.print(kong);
                    if (kong == 5){
                        break label;
                    }
                }
            }
        System.out.print("跳出循环");
    }  
 
## 数组   
 
8. ###将数组arr1 中的部分数据复制到arr2 中

    * for循环
    * int[] arr2 = Arrays.copyOfRange(arr1 , 5, arr1.length) //推荐
    
9. ###如何进行数组的检索

    *binarySearch(Object[] a , Object key) //-> 数组 ，搜索的值
    *binarySearch(Object[] a , int fromIndex , int toIndex ,Object key)
    // 数组 ，起始（包含），结束（不包含），搜索的值。
    
    返回值为所在位置。

## 面向对象

10. ###静态语句块

   静态语句块在使用其所在类时就被分配的内存并执行语句块中的代码，因此可以在静态语句块中进行初始化操作，如数据库连
   接，初始化图像。
   
11. ###如何使用反射创建对象（issue96）

    * 通过调用Class的newInstance（）方法，获得该类的对象 -->无参构造函数时使用
    * java.lang.reflect.Constructor类提供一个参数可变的newInstance(Object...obj)方法，通过
        Constructor类的实例调用该方法，可以根据累的指定构造方法创建对象 -->有参构造函数时使用

12. ###如何通过反射调用方法

    在Java中，通过getMethod()方法或getMethods()方法访问方法时，将返回Method类型的对象或数组。每个Method对
    象代表一个方法，在获取到Method对象后，可通过其invoke()方法来执行方法。
    
13. ###如何通过反射访问字段（成员变量）

    在Java中，通过getField()方法或getFields()方法访问字段(成员变量)时，将返回Field类型的对象或数组。每个Field对象代表一个字段（成员变量），利用Field对象提供的相关方法可以访问对应字段。

14. ###在Java语言规范中，对equals()方法有何要求？

    * 自反性：对于任何非空引用值x，x.equals(x)都应返回true；
    * 对称性：对于任何非空引用值x和y，当且仅当y.equals（x）返回true时，x.equals（y）才应返回true；
    * 传递性：对于任何非空引用值x，y和z，如果x.equals（y）返回true，并且y.equals（z）返回true，那么
        x.equals（z）应返回true； 
    * 一致性：对于任何非空引用值x和y，多次调用x.eqyals（y）返回true或始终返回false；
    * 对于任何非空引用值x，x.equals（null）都应返回false。
    * 在重写equals（）方法时，通常也需要重写hashCode（）方法。
    
## 字符串与包装类
15. int和integer有什么区别？

    java提供了两种不同的类型，即引用类型和基本类型。为实现基本数据类型到面向对象的转化，java为每个基本数据类型提供了对应的包装类（封装包）。boolean <-> Boolean , float <-> Float, char <-> Character, byte <-> Byte , int <-> Integer, double <-> Double, short <-> Short, long <-> Long;
    int是Java的基本数据类型，Integer是包装类。Java将包装类作为对象使用，而基本数据类型不是对象。
    JDK5.0中新增了自动装包，拆包机制，实现包装类和基本数据类型之间的自动转换。无需手动转换。


16. 时间日期格式化

       转换符  | 含义                      |显示方式
       ------ | ------------------------ | --------
       %td    |一月中的第几天（01～31）     | 05
       %te    |一月中的第几天（1～31）       | 5
       %tm    |两位的月份                  | 01
       %ty    |两位的年份                  | 14
       %tY    |4位的年份                   | 2014
       %tj    |一年中的第几天（001～366）    | 078
       %ta    |指定语言环境的星期简称        | Sun
       %tA    |指定语言中的星期全称         | Sunday
       %tb    |指定语言环境的月份简称       | Jan
       %tB    |指定语言环境的月份全称       | January
       %tH    |两位24小时制的小时 (00~23)  | 22
       %tI    |两位12小时制的小时（01～12） | 08
       %tk    |24小时制的小时（00～23）    | 08
       %tl    |12小时制的小时（1～12）     | 8
       %tM    |两位小时中的分钟(00~59)     | 08
       %tS    |两位小时中的秒（00～60）    | 09(60是支持闰秒所需的特殊值)
       %tL    |3位秒中的毫秒(000~999)     |666
       %tN    |9位秒中的毫微秒            |0000000000～9999999999
       %tp    |特定语言环境的上午下午标记（小写）| am,pm
       %tZ    |表示时区缩写的形式的字符串    | CST
       %ts    |自1970年1月1日00:00:00到现在经过的秒数 |Long.MIN_VALUE/1000~Long.MAX>VALUE/1000之间
       %tQ    |自1970年1月1日00:00:00到现在经过的毫秒数| 同上
       %tR    |24小时制时间 (%tH:%tM)     |13:18
       %tT    |24小时制时间 (%tH:%tM:%tS) |13:18:40
       %tr    |12小时制时间 (%tI:%tM:%tS %Tp) |11:09:03 AM
       %tD    |日期 （%tm/%td/%ty）        |02/28/10
       %tF    |ISO8601格式完整日期（%tY-%tm-%td）|2014-09-08
       %tc    |日期和时间（%ta %tb %td %tT %tZ %tY）|Sat Feb 28 22:20:43 CST 2009
       
    java:
        
        Date date = new Date();
        System.out.println("指定语言环境下的星期简称：" 
                       + String.format(Locale.US, "%ta", date));
        System.out.println("星期全称：" + String.format("tA", date));
       
       
       
 17. ###String ， StringBuilder 和 StringBuffer？
 
    > **String**创建的是长度固定的字符串对象。虽可以通过“＋” 扩展，但“＋” 会产生一个新的String实例。  
    > **StringBuilder***对象是一个可变的字符序列。大大提高了频繁添加字符串的效率。  
    > **StringBuffer** 也是一个包含缓冲区的字符串对象。不同的是StringBuilder是``非线程安全``，StringBuffer是``线程安全``的。在效率上，StringBuilder要高于StringBuffer。
       
 18. ###Collection和Collections不同？
 
   > Collection ==> Interface Collection<E>  定义一个集合用的接口。
   > Collections ==> Class 专门为集合类定义的工具类。提供多种静态方法。
   常用的方法；
   排序：sort（）方法
   乱序：shuffle（）方法
   常规数据处理：reverse（），fill（），copy（），swap（），addAll（）
   查找：binarySearch（）
   组成：frequency（），disjoint（）
   查找极值：min（），max（）
   
 19. ###遍历集合的方式。
 
     * 普通for循环 for(int i = 0; i < list.size(); i ++){}
     * for循环增强版 for(String item : list){}
     * 使用迭代器 Iterator 可以用来遍历集合类和删除指定的元素。
         Interator 接口中的常用方法。
         hasNext() 判断集合中是否函数元素
         remove()删除当前元素  ==>是迭代过程中删除元素的安全方法
         next()游标后移，返回当前元素。
        以下场景推荐Iterator
           迭代过程中删除集合中的元素，如实现过滤功能。
           并行迭代多元素。
  
   一个简单例子:
       
       
       public static void main(String[] args){
            Collection<Integer> collection = new ArrayList<Integer>();
            for (int i = 0; i < 5; i++) {
                collection.add(i);
            }
            System.out.println("其中为偶数的是：");
            //使用Iterator过滤器
            for(Iterator<Integer> iterator = collection.iterator(); iterator.hasNext();){
                if (iterator.next() % 2 == 1 ){
                    iterator.remove();
                }
            }
            System.out.println(collection);
        }
 
 迭代器更灵活。
 
16. ###Iterator接口与ListInterator接口


  
    |            | ListIterator       | Iterator   |
    |------------ |------------------- | --------  |
    |遍历方向      | 序号由小至大和由大至小 | 序号由小至大|
    |遍历中修改元素 |     支持            | 不支持     |    
    |遍历中增加元素 |     支持            | 不支持     |
    |遍历到的元素符号|    可以获得         | 不能获得   |           
    
17. ###Iterator 和 Enumeration 区别

    Iterator 是在Java SE 1.2中新增。
    Enumeration 是在Java SE 1.0 定义的。
    
    相对于Enumeration 新增了remove() 方法
    Enumeration 中hasMoreElements() <==> hasNext()
    Enumeration 中nextElement() <==> next()
    
    Iterator 目的是取代 Enumeration 
    
18. ###ArrayList 和 LinkedList 区别

    ArrayList类相当于数据结构中的线性表，它在底层使用数组来存储元素，因此适合快速的获取指定位置的元素。当删除和添加元素时，后面的元素位置要发生变化，开销较大。
    LinkedList类相当于数据结构中的链表，它在底层使用对象来保存元素。因此适合元素的增加和删除，但是，获得指定元素是，要从头开始遍历，开销较大。
    
    在开发过程中，同长采用面向接口的编程方法。
    List<String> list = new ArrayList<String>();
    此时如果需要从列表中删除元素，可以将实现类换成LinkedList，如下：
    list ＝ new LinkedList<String>();
    
19. ###ArrayList 和 Vector区别
    
    Verctor是在JDK1.0 中提供的集合类，ArrayList是在JDK1.2 提供的集合类，
    Verctor类中有些方法是支持同步的。Verctor类适合于需要线程安全的场合。
    Verctor类的效率比ArrayList差。 
    
20. ###Map接口特性。

    Map接口通常由2个常用实现类。
    HashMap 用于快速保存，查找数据。
    TreeMap 支持排序功能。
    LinkedMap 能够保存键值的添加顺序。
 


##数学
21. ###随机数

    1. 平方取中法。＝》最终会退化到0，无法继续产生随机数。
    2. 线性同余法。（Random类使用的算法）
    
    在java中
    1. 使用Math类中的random()方法
        返回一个0.0到1.0之间的伪随机数。包括0.0 不包括 1.0
    2. 使用Random类。   
    
22. ### 完成高精度整数运算

    BigInteger类。
    add() +
    subtract() -
    multiply() *
    divide() /
    remainder() %
    negte() -this 相反数
    abs() |this|
    divideAndRemainder() this/val 的商和余数，结果是BigInteger数组
    gcd()返回this和val的最大公约数
    max()this，val的最大值
    min()this,val的最小值
    signum()this的符号。正数为1，负数为－1，0为0
    
    Java:
    
        BigInteger number1 ＝ new BigInteger（“13”）;
        number1.negte()
23. ### 完成高精度浮点数运算

    DigDecimal类
    方法同上。
    
##异常

##输入／输出
1. 字节输入流：InputStream类
    所有字节输入流的父类，抽象类。
    FileInputStream：使用字节方式读取文件，通常用于读取非字符类型文件。
    ObjectInputStream：用于读取ObjectOutputStream保存的对象。
    BufferedInputStream：用于缓冲字节输入流。
    ZipInputStream：用于读取ZIP文件格式的数据。
2. 字节输出流： OutputStream
    同上。
    FilOutputStream：使用字节方式写入文件，通常用于写入非字符类型文件
    ObjectOutputStream：用于输出java对象。
    BufferedOutputStream：用于缓冲字节输出流。
    ZipOutStream：用于写入ZIP文件格式的数据。
3. 字符输入流：Reader类。
    同上。
    InputStreamReader：从字节流到字符流转换的桥梁。
    BufferedReader：用于缓冲字符输入对象。
    FileReader：用于从文件中读取字符。
4. 字符输出流：Writer类
    同上。
    OutputStreamWrite：用于从字节流到字符流转换的桥梁。
    BufferedWriter： 用于缓冲字符输出对象。
    FileWriter：用于向文件中写入字符。
    PrintWriter：向文本输出流打印对象格式化表示。
      
5. 如何在磁盘上创建文件。

   File类中提供了创建文件和文件夹的方法。
   creatNewFile() 当文件不存在时创建。
   mkdir() 用于创建一个文件夹
   mkdirs() 用于创建一个文件夹，支持自动创建其他必须文件夹
   
   在日常开发中 mkdirs()更为常用。
   
6. 如何创建临时文件。

    在File类中，提供了两种创建临时文件的方法。    
    * 在默认的临时文件夹中创建临时文件。
        createTempFile(String prefix, String suffix);
        prefix 是临时文件名的前缀。至少3个字符
        suffix 是临时文件的后缀，如果为null ，则使用.tmp
        
   * 在指定文件夹中创建临时文件
       creatTempFile(String prefix, String suffix, File directory);
       directory 是指定的文件夹。
       
   > 使用临时文件来保存程序运行中生成的信息，虽然简化了编程，但也增加了系统的负担。
   
7. 如何获得磁盘中的全部文件？

    使用File类中提供的listFile() 方法，可以获得当前文件夹中包含的全部文件和子文件夹，通过递归可获得全部文件。
    
    在File类中并没有直接提供获得指定文件夹中全部文件的方法，但可通过简单的递归实现，但一定要注意推出递归的条件，避免出现死循环。
    
    
8. 有关JAVA 1.4 新加入的NIO包。

    在javaIO中，使用流来读写数据，即每次处理一个字节。效率并不理想。后来加入的缓冲类，如BufferedReader类提高效率。
    在NIO中，使用块来读写数据，即每次处理一个数据库。能大幅提高效率，缺点时失去流方式所具有的优雅和简单的特性。
    新IO中核心对象包括通道（Channel）和缓冲区（Buffer）。
    通道是对原IO流的模拟，数据的传递是通过通道完成。发送给通道的数据先放入缓冲区，从通道读取数据也要先读到缓冲区。
    缓冲区；新IO包含的缓冲区有ByteBuffer，ShortBuffer，IntBuffer，LongBuffer，FloatBuffer，DoubleBuffer。 
    通道：不需要定义InputStream和OutputStream对象即可完成数据读写操作。同时通道中的数据是以块为单位，因此不能将字节写入通道。
    在JDK 7 中新增了NIO.2来简化文件的相关操作。

     
9. 使用NIO进行读写操作

    * 使用NIO读数据
    
        1. 从FileInputStream 类中获得FileChannel对象。
        2. 创建缓冲区Buffer。
        3. 将数据从FileChannel读入Buffer中
        
     java:
     
            FileInputStream fis = null;
            fis = new FileInputStream("src/image/readerme.txt");
            FileChannel channel = fis.getChannel();
            ByteBuffer buffer = ByteBuffer.allocate(1024);
            channel.read(buffer);
            System.out.println(new String(buffer.array()));
    * 使用NIO写数据
    
        1. 从FileOutputStream 类中获得FileChannel对象。
        2. 创建缓冲区Buffer并放入要写出的数据。
        3. 将缓冲区Buffer中的数据使用通道写入文件中。
   
   java:
              
        String message = "Java Programing Dictionary is a wonderful teacher for
                             you";
        FileOutputStream fos = null;
        fos = new FileOutputStream("src/image/readerme.txt");
        FileChannel channel = fos.getChannel();
        ByteBuffer buffer = ByteBuffer.allocate(1024);
        buffer.put(message.getBytes());
        buffer.flip();
        channel.write(buffer);
10. 内存映射文件IO

    内存映射文件IO是一种读写的方式，比继续流和通道的方式快很多。
    在NIO中提供了内存映射文件IO的功能，有3种方式。
   
    方式名称       |  方式说明
    -------------|------------------------------------------
    PRIVATE      | 缓冲可读写，但不会影响到文件
    READ_ONLY    | 缓冲只读，如果写入会抛出ReadOnlyBufferException
    READ_WRITE   | 缓冲可读写，修改会影响文件
    
    


 
     
## 枚举类型与范型

1. 枚举类型

    枚举类型用来表示由固定常量组成的集合。1.5新增。
    定义枚举类型时使用enum关键字。保存元素名称是使用大写。
 
  java: 
     
        public enum Dire{
            EAST,
            SOUTH,
            WEST,
            NORTH,
        }            
  调用Dire.EAST
     
  优势：
  
  1. 枚举类型都继承了Enum类。包含了常用的枚举操作。
  2. 枚举类型中可以增加域和方法。
  3. 编译器自动为枚举类型中增加新方法。
      编译器在遇到枚举类型时，自动为其增加values()和valueOf()方法。前者返回一个包含全部枚举的数
      组。后者返回当前字符串对应的枚举元素。
      
      使用编译器增加的values()来遍历全部元素。
      
      java:
      
          public class Text{
              public static void main(String[] args){
                  for(Dire d : Dire.values()){
                      System.out.println(d);
                  }
              }
          }
2. 在枚举中定义域和方法。

    与普通类的差异：
    * 枚举元素要写在域和方法前。
    * 编写完枚举元素需要使用分号分割域和方法。
    * 如果编写构造方法，则要在定义枚举元素时体现。
      在编写构造方法是，注意在其方法权限修饰符只有private和无权限修饰符（包范围可见）
      枚举类型会自动创建枚举元素，但不能使用构造方法创建枚举类型对象。
      
    java:
    
        public enum PizzaInfor {
            SMALL(8, 2.0, "小号巴萨"), MIDDLE(10, 1.8, "中号巴萨"), LARGE(12, 1.7, "大
                      号巴萨"),;
            private int size;
            private double price;
            private String description;
            private PizzaInfor(int size, double price, String description){
                this.description = description;
                this.price = price;
                this.size = size;
            }

            @Override
            public String toString() {
                return description + "的价格：" + size * price + "元";
            }  
        }
3. 协变。

    在java中，数组支持协变。
    e.g. :
        
        Integer[] intArray = new Integer[5];
        Number[] numArray = new Number[5];
        
    但对于范型而言不支持协变，因为这样会破坏类型安全。
    
    
4. 范型中的擦除。

    在程序编译后，会将范型中的类型信息擦出。
    如：
        
        boobean result ＝ （new ArrayList<Number>().getClass() == new 
            ArrayList<Integer>().getClass()）;  
    result ==> true
    
    由于擦除机制，导致很多常用功能不能实现，如创建范型化数组。
    
        T［］ array ＝ new T ［10］；
    此时可以利用java的反射机制，
java:

        public static <T> T[] createGenericArray(Class<T> type, int size){
            return (T[])Array.newInstance(type, size);
        }
      
        
  
## 线程

1. 创建新线程。

    1. 继承Thread类。
    2. 实现Runnable借口。
    通常推荐使用实现Runnable接口实现新线程。
    
2. 线程中的常见属性。

    ID属性：用于标示线程，可使用Thread类中的getId（）方法获得该属性，不许修改。
    
    Name属性：用于标示线程，主要是为了方便程序区分线程。通过getName()和setName()获取和设置。
    
    Priority属性：用于标示线程的优先级。java线程优先级范围1～10.可以通过
        getPriority(),setPriority() 获取和设置。
        
    Daemon属性：用于表示线程是否是守护线程。守护线程的作用是为其他线程提供服务。如果系统中仅剩下守
     护线程，则虚拟机会退出。可以使用setDaemon()设置线程。
  
3. 导致线程停止的几种状况。

    * 线程在执行时，抛出InterruptedException异常。
    * 线程执行了sleep()方法。
    * 更高优先级的程序处于可运行状态。
    * 如果当前线程执行了InputStream类中的read()方法。
 
4. Object类中提供哪些线程相关方法。

    定义了3个与线程密切相关的方法，即wait(),notify()和notifyAll()。其中wait()中具有3种重载形
        式。  
    
    notify()方法：唤醒在此对象监视器上等待的线程。
    notifyAll()方法：唤醒在此对象监视器上等待的所有线程。
    wait()方法：线程处于等待状态，直到其他线程调用此对象的notify()或notifyAll()
    wait(long timeout)方法：毫秒级
    wait(long timeout, int nanos)方法：时间精度是纳秒级。
    
    
5. 创建有返回值的线程

    使用Callable接口可以创建有返回值的线程。
    
    接口定义如下:
    
        public interface Callable<T>{
            V call() thorow Exception;
        }  
  
     
     
6. 线程池

    如果系统中需要创建大量短声明周期的线程，则应该使用线程池。
    
    在java SE 5.0 新增加了创建线程池的Executors类，提供了一些静态方法用于获得线程池。
    
    newCachedThreadPool()创建的线程池可以没有可用线程时创建一个新线程。
    
    newFixedTreadPool() 可以创建一个固定大小的线程池。
    
    线程池使用完毕后应使用ExecutorService借口中定义的shutdown()方法关闭线程。
     
    
    java中还提供了类似线程池的线程组类（TreadGroup类）。
    
    
7. 终止线程
  
 
   不推荐使用stop()和suspend()
   stop()方法在线程终止之前没有对其做任何的清楚操作，不具有安全性。
   suspend()方法，具有固有的死锁倾向。如果目标进程挂起时在保护关键系统关键资源的监视器上保持有锁，则在目标进程重新开始之前任何进程都不能访问该资源。如果重新开始目标进程的线程想再调用resume()之前锁定改监视器，则会发生死锁现象。
   推荐利用boolean值来终止运行中的进程。
   
  java:
  
      private class Zhu implements Runnable{
          private boolean stopped = true;
          public void setStopped(boolean stopped){
              this.stopped = stopped;
          }
          
          public void run(){
              while(stoped){
                  System.out.println("");
              }
          }
          
      }
      
 还可以使用isInterrupted()方法和Interrupted()方法实现线程的安全终止。
 
8. 同步锁解决共享资源的冲突；

    java:
    
        public class SysncLockDemo{
            private finnal ReentratLock lock = new ReetratLock(); //创建锁
            //实现同步方法。
            public void synMethod(){
                locl.lock() //加锁
                try{
                    //功能代码
                }finally{
                   lock.unlock() //释放锁
                }
            }
        }
  
   >同步锁是从JDK 1.5 开始。





 