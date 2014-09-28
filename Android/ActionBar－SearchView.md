# ActionBar－SearchView

<!-- create time: 2014-09-09 17:35:05  -->

[原地址](http://blog.csdn.net/howlaa/article/details/25136027)
##布局文件

XML：

    <?xml version="1.0" encoding="utf-8"?>
    <menu xmlns:android="http://schemas.android.com/apk/res/android">
      <item 
        android:id="@+id/menu_search" 
        android:icon="@android:drawable/ic_menu_search"
        android:title="@string/action_search"
        android:actionViewClass="android.widget.SearchView" //千万不要忘，
                                                           //不然下面会产生空指针
        android:showAsAction="ifRoom|collapseActionView" />
    </menu>
    
这里showAsAction的collapseActionView 表示允许将searchView扩展到整个actionbar.


##加载布局：

JAVA：

    public boolean onCreateOptionsMenu(Menu menu) { 
    // 加入含有search view的菜单 
        MenuInflater inflater = getMenuInflater(); 
        inflater.inflate(menuId, menu); 
    // 获取SearchView对象 
        SearchView searchView = (SearchView) menu.findItem(R.id.menu_search).getActionView(); 
        if(searchView == null){  
            Log.e("SearchView"，"Fail to get Search View."); 
            return true; 
        } 
        searchView.setIconifiedByDefault(true); // 缺省值就是true，可能不专门进行设置，true的输入框更大
        return true；
     }
     
     
     
##相应调用的方法。

JAVA：

    对应接口onQueryListener

	//点击回车结束输入时执行 
	@Override
	public boolean onQueryTextSubmit(String query) {
		
		// do Somethings
		return false;
	}

	
	 // 每次输入时执行
	@Override
	public boolean onQueryTextChange(String newText) {

		//do Somethings
		return false;
	}


##其他的几个可能的需求：

###改变默认搜索框底下的那条横线的颜色 -> 反射处理

Java：

    	try{
			Class<?> argClass=searchView.getClass();   
            Field ownField = argClass.getDeclaredField("mSearchPlate");  
            //setAccessible  
            ownField.setAccessible(true);  
            View mView = (View) ownField.get(searchView);  
            mView.setBackground(getResources().getDrawable(R.drawable.test));  
		}catch(Exception e){
			e.printStackTrace();
		}
###默认展开searchView:

展开：

    MenuItem searchItem = menu.findItem(R.id.menu_search);
	searchItem.expandActionView();

设置文字：

    searchView.setQuery("ok", false);  
    
展开同时虚拟键盘也打开，影响体验，关闭虚拟键盘的方法是使searView清除焦点：

    searchView.clearFocus(); 	
	