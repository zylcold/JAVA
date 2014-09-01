# JAVA String去除最后一个字符

java：

         String str = "abdcd";
         if(str!= null){
           //substring为截取字符串从第0位到倒数第二位。
           //substring（0,5） 截取的就是0,1,2,3,4这四个位
           //置的字符
           String d = str.substring(0,str.length()-1);
           System.out.println(d);---》输出abdc
          ｝