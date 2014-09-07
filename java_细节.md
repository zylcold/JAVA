# Java 细节

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

       转换符 | 含义                    |显示方式
       ---- | ----------------------  | --------
       %td   | 一月中的第几天（01～31）   | 05
       %te   |一月中的第几天（1～31）     | 5
       
   




 