#android LinearLayout添加分隔线  

##方案一

  >可以放置一个ImageView组件，然后将其设为分隔线的颜色或图形。
  
  xml:
  
      <ImageView   
        android:layout_width="fill_parent"  
        android:layout_height="1dp"  
        android:background="#ffffff"  
        />  
        
##方案二


   >在Android3.0及以上版本，LinearLayout支持直接显示分隔线。
   
   设置<LinearLayout>标签的`android:showDividers`属性可以再LinearLayout的相应位置显示分隔线。如果有多个LinearLayout，显示效果和在LinearLayout之间加分隔线是一样的。

   android:showDividers属性可以设置如下4个值：
   
   none：不显示分隔线；
    
   beginning：在LinearLayout的开始处显示分隔线；
    
   end：在Linearlayout的结尾处显示分隔线；
    
   middle：在LinearLayout中的每两个组件间显示分隔线：

   除了需要设置android:showDividers属性外，`还要设置android:divider属性`，该属性表示分隔线的图像，需要一个Drawable ID