# Android ContextMenu 实现
  两种：

1. Floating Context Menu
2. Contextual Action Mode

##第一种 Floating Context Menu：

1. 覆盖Activity的onCreateContenxtMenu()方法，调用Menu的add方法添加菜单项（MenuItem）。
2. 覆盖Activity的onContextItemSelected()方法，响应上下文菜单菜单项的单击事件。
3. 调用registerForContextMenu()方法，为视图注册上下文菜单。
　　


##第二种 Contextual Action bar (CAB)

    Action Mode是Android 3.0以后出现的，
    我们可以使用AppCompat库使Action Mode兼容至Android 2.1。
    
    
1. 创建ActionMode.Callback 实例。

e.g.
java:

    private ActionMode.Callback mActionModeCallback = new 
    ActionMode.Callback() {  
  
        @Override  
        public boolean onCreateActionMode(ActionMode mode, Menu menu) {  
            // Inflate a menu resource providing context menu items  
            MenuInflater inflater = mode.getMenuInflater();  
            inflater.inflate(R.menu.context_menu_individual, menu);  
            return true;  
        }  
  
        @Override  
        public boolean onPrepareActionMode(ActionMode mode, Menu menu) {  
            // TODO Auto-generated method stub  
            return false;  
        }  
  
        @Override  
        public boolean onActionItemClicked(ActionMode mode, MenuItem item)     
        {  
            switch (item.getItemId()) {  
            case R.id.menu_copy:  
  
                mode.finish(); // Action picked, so close the CAB  
                return true;  
           
            default:  
                return false;  
            }  
        }  
  
        @Override  
        public void onDestroyActionMode(ActionMode mode) {  
            mActionMode = null;  
        }  
    };  
      

2. this.startActionMode(事例化对象); 调用。

[例子1](http://blog.csdn.net/a623891391/article/details/25222207)
[例子2](http://www.technotalkative.com/contextual-action-bar-cab-android/)
[例子3](http://www.cnblogs.com/mengdd/p/3565213.html)


[ActionBar 概览](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2012/1014/437.html)