# 动态改变actionbar的menu菜单MenuItem的显示

创建一个Actionbar过程，一般。

* onCreateOptionsMenu(Menu menu, MenuInflater inflater);加载布局。
   
   添加menu 方式:
    
    1. 代码添加
    2. xml添加 getMenuInflater().inflate(R.menu.list_option, menu);
    
    
 ``但这个onCreateOptionsMenu在activity的整个周期中只被调用一次，之后都不会变化``
 
 
* onPrepareOptionsMenu(Menu menu);加载布局。

   其在每次点击菜单都会调用此方法（每次在display menu之前，都会去呼叫）。
   
   在onPrepareOptionsMenu(Menu menu)函数中，最好如下使用：
   
   java 
  
   ```
      super.onPrepareOptionsMenu(menu);
      menu.clear();
   ```
   ``因为如果没有clear而直接add的话，那么菜单中菜单项是会“追加”的，这样随着你不停的点
      menu键，菜单项就不停的增加。``
      
      
      
  但当要求无需点击menu就实现Actionbar改变时，
解决的办法是在你要更新菜单项的地方加上：(原生Actionbar)
  ```
 mActivity.getWindow().invalidatePanelMenu(Window.FEATURE_OPTIONS_PANEL);```
 
 
 第三方（如ActionBarSherlock），那么调用：
 那么调用 invalidateOptionsMenu();