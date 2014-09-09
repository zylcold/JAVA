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
  
   一个简单例子：
       
       
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
 
       
   




 