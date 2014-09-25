# ArrayList初始化

<!-- create time: 2014-09-25 18:23:24  -->
[原地址](http://blog.csdn.net/mercenarylin/article/details/21624875)

方式一：

      ArrayList<String> list = new ArrayList<String>();
      String str01 = String("str01");
      String str02 = String("str02");
      list.add(str01);
      list.add(str02);
方式二：
  
      ArrayList<String> list = new ArrayList<String>(){{add("str01"); 
              add("str02");}};  