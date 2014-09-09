# 限制 EditText 最大输入字符数 --&amp;gt; Android


## 方法一：

在 xml 文件中设置文本编辑框属性作字符数限制

> 如：android:maxLength="10" 即限制最大输入字符个数为10


## 方法二：

在代码中使用InputFilter 进行过滤


```java

 	public class TextEditActivity extends Activity {
   
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.main);
        
            EditText editText = (EditText)findViewById(R.id.entry);
            editText.setFilters(new InputFilter[]{new 
            InputFilter.LengthFilter(20)});
            }
        }
        
        
 	editText.setFilters(new InputFilter[]{new 
	InputFilter.LengthFilter(20)}); 即限定最大输入字符数为20
```


## 方法三：


利用 TextWatcher 进行监听


自定义TextWatcher

```java   
    /*
     * 监听输入内容是否超出最大长度，并设置光标位置
     * */
    public class MaxLengthWatcher implements TextWatcher {

	    private int maxLen = 0;
	    private EditText editText = null;
	
	
	    public MaxLengthWatcher(int maxLen, EditText editText) {
		    this.maxLen = maxLen;
		    this.editText = editText;
	    }

	    public void afterTextChanged(Editable arg0) {
		    // TODO Auto-generated method stub
		
	    }

	    public void beforeTextChanged(CharSequence arg0, int arg1, int     
	        arg2,int arg3) {
		    // TODO Auto-generated method stub
		
	    }

	    public void onTextChanged(CharSequence arg0, int arg1, int     
	    arg2, int arg3) {
		    // TODO Auto-generated method stub
		    Editable editable = editText.getText();
		    int len = editable.length();
		
		    if(len > maxLen){
			    int selEndIndex = Selection.getSelectionEnd(editable);
			    String str = editable.toString();
			    //截取新字符串
			    String newStr = str.substring(0,maxLen);
			    editText.setText(newStr);
			    editable = editText.getText();
			
			    //新字符串的长度
			    int newLen = editable.length();
			    //旧光标位置超过字符串长度
			    if(selEndIndex > newLen){
				    selEndIndex = editable.length();
			    }
			    //设置新光标所在的位置
			    Selection.setSelection(editable, selEndIndex);
			
		    }
	    }

    }
```


调用自定义TextWatcher

   
```java
    public class TextEditActivity extends Activity {
        /** Called when the activity is first created. */
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.main);

		    EditText editText = (EditText) findViewById(R.id.entry);
		    editText.addTextChangedListener(new MaxLengthWatcher(10, 
		    editText));

        }
    }
    
```


 
