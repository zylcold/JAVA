# Android Fragment中监听事件
[原地址](http://blog.csdn.net/jdsjlzx/article/details/20695279)
<!-- create time: 2014-09-29 17:30:37  -->

##问题：
Fragment中没有提供监听touch事件的方法。

##解决方案：
Activity(或者能够监听touch的fragment中)中能够监听touch事件。
于是在Activity中写一个接口，MyOnTouchListener，在需要监听touch事件的fragment中实现这个窗口。



JAVA:

    /**
    * 以下的几个方法用来，让fragment能够监听touch事件
    */
    private ArrayList<MyOnTouchListener> onTouchListeners = new     
        ArrayList<MyOnTouchListener>(10);

    @Override
    public boolean dispatchTouchEvent(MotionEvent ev) {
        for (MyOnTouchListener listener : onTouchListeners) {
            listener.onTouch(ev);
        }
        return super.dispatchTouchEvent(ev);
    }

    public void registerMyOnTouchListener(MyOnTouchListener myOnTouchListener) {
        onTouchListeners.add(myOnTouchListener);
    }

    public void unregisterMyOnTouchListener(MyOnTouchListener myOnTouchListener) {
        onTouchListeners.remove(myOnTouchListener);
    }

    public interface MyOnTouchListener {
        public boolean onTouch(MotionEvent ev);
    }

> dispatchTouchEvent 可以监听所有的关于屏幕的行为

JAVA:

    private GestureDetector mGestureDetector;

    MainActivity.MyOnTouchListener myOnTouchListener;

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
        Bundle savedInstanceState) 
    {
        Log.e(TAG, "onCreateView");

        View view = inflater.inflate(R.layout.fragment_contact, container,
            false);
        this.view = view;

        mGestureDetector = new GestureDetector(getActivity(),
            this);


        myOnTouchListener = new MainActivity.MyOnTouchListener() {

            @Override
            public boolean onTouch(MotionEvent ev) {
                boolean result = mGestureDetector.onTouchEvent(ev);
                return result;
            }
       };
       ((MainActivity) getActivity().registerMyOnTouchListener(myOnTouchListener);

        return view;
    }

实现OnGestureListener或者OnDoubleTapListener接口或者其他callback()
###OnGestureListener中的方法
* 按下时调用 
boolean onDown(MotionEvent e);
* 按住时调用
void onShowPress(MotionEvent e);
* 敲击时调用
boolean onSingleTapUp(MotionEvent e);
* 滑动时调用
boolean onScroll(MotionEvent e1, MotionEvent e2, float distanceX, float distanceY);
* 长按时调用
void onLongPress(MotionEvent e);
* 抬起时调用
boolean onFling(MotionEvent e1, MotionEvent e2, float velocityX, float velocityY);

