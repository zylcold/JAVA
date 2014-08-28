#Java里如何判断一个String是空字符串或空格组成的字符串
转自[Java里如何判断一个String是空字符串或空格组成的字符串](http://www.blogjava.net/li40204/archive/2009/07/29/288813.html)

   要判读String是否为空字符串，比较简单，只要判断该String的length是否为0就可以，或者直接用方法isEmpty()来判断。

   但很多时候我们也会把由一些不可见的字符组成的String也当成是空字符串(e.g, space, tab, etc)，这时候就不能单用length或isEmpty()来判断了，因为technically上来说，这个String是非空的。这时候可以用String的方法trim()，去掉前导空白和后导空白，再判断是否为空。
   
   e.g.
   java:
       
       public class TestEmpty{
         public static void main(String[] args){
             String a = "       ";
         
             // if (a.isEmpty())
             if (a.trim().isEmpty()){
                 System.out.println("It is empty");
            }else {
                System.out.println("It is not empty");
                }
            }
        }

结果为It is empty.


> Java Doc

> public String trim()

> Returns a copy of the string, with leading and trailing whitespace omitted.