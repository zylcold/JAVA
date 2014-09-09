# 创建ActionBar －Android


##官方文档 －－> xml 创建
 [链接] (file:///Users/Yun/Library/Application%20Support/Dash/DocSets/Android/Android.docset/Contents/Resources/Documents/docs/guide/topics/ui/actionbar.html#Adding)
 
* 创建xml
    xml：
        
        <menu xmlns:android="http://schemas.android.com/apk/res/android" 
        >
        <item android:id="@+id/action_search"
          android:icon="@drawable/ic_action_search"
          android:title="@string/action_search"
          yourapp:showAsAction="ifRoom" />
        <item android:id="@+id/action_compose"
          android:icon="@drawable/ic_action_compose"
          android:title="@string/action_compose" />
        </menu>
        
* 加载xml布局
    
    java：
        
        @Override
        public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu items for use in the action bar
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.main_activity_actions, menu);
        return super.onCreateOptionsMenu(menu);
        }
        
* 监听事件

   java：
   
       @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle presses on the action bar items
        switch (item.getItemId()) {
            case R.id.action_search:
                openSearch();
                return true;
            case R.id.action_compose:
                composeMessage();
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }
    }
    
    
    
##不使用布局文件创建

 * 添加按钮
 
   java：
   
       private void addMenuButton(Menu menu) {
		MenuItem item = menu.add(0, 0, 0, "编辑");

		{
			item.setIcon(R.drawable.ic_setting);
			item.setShowAsAction(MenuItem.SHOW_AS_ACTION_ALWAYS);
		}
		item.setOnMenuItemClickListener(this);

	}
	

* 加载布局

java：
    
    @Override
	public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
		addMenuButton(menu);
		super.onCreateOptionsMenu(menu, inflater);
	}
	
* 监听事件

    实现OnMenuItemClickListener接口
    java：
        
        @Override
	    public boolean onMenuItemClick(MenuItem item) {
		    switch (item.getItemId()) {
		    case 0:
			    T.showShort(mainActivity, "Demo");
			    break;

		    default:
		   	    break;
	        }
		    return false;
	    }
 > Fragment中需要在onCreate状态下 设置 setHasOptionsMenu(true); 
 
 
 
