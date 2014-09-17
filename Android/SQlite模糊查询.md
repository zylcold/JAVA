# SQlite查询

<!-- create time: 2014-09-11 21:46:51  -->


##SQL模糊查询

[原地址](http://blog.sina.com.cn/s/blog_5da93c8f0100tdha.html)
###1. 使用db.query方法查询

    >  select * from users where name like %searcherFilter% ;
    
JAVA:
  
  
    Cursor cursor = db.query(TABLE_NAME, null, "name like '%" + searcherFilter + "%'", null, null, null, null);
    或
    Cursor cursor = db.query(TABLE_NAME, null, "name like ？", new String[]{"%"+searcherFilter+"%"}, null, null, null);  
    
    多项查询
    Cursor cursor = db.query(TABLE_NAME, null, "name like ？ or anthor like ？ ", new String[]{"%"+searcherFilter+"%", "%"+searcherFilter+"%"}, null, null, null); 
      
###2. 使用Sql语句

 JAVA:
    
    Cursor cursor=db.execure("select * from table_name where name like '%"+searcherFilter＋ "%'");    
            
            
            
            
#####在使用完Cursor后，要关闭Cursor，cursor.close()；
#####如果不关闭，虽然前台不会force close，但后台会报错:DatabaseObjectNotClosedException
#####在使用完SQLiteDatabase后，同样需要关闭。db.close();否则报错如Cursor。
#####但两者报错时点不同。不关闭Cursor的话，在调用新的Activity时就会报错。
#####而不关闭SQLiteDatabase的话，在推出程序，重新进入时就会报错。SQLite <wbr>模糊查询


##sql语句：

###1.排序查询

 > SELECT * FROM customer where isdelete=0 ORDER BY customer_bucket ASC;
 
 从customer表找出isdelete中为0所有数据并按customer_bucket的首字母的ASCII顺序从小到大的顺序排列
 
 > select * from table_name where name like %h% ;
 
 从table_name 中找出含有h的数据。％h 中％代指之前的文字 
 