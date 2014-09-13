# Java的并交差集

<!-- create time: 2014-09-11 21:59:33  -->


##并集
list1.addAll(list2);
   
##交集
list1.retainAll(list2);

##差集
list1.removeAll(list2);
      
      
##无重复并集
list2.removeAll(list1);

list1.addAll(list2);