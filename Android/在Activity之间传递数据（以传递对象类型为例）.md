#在Activity之间传递数据（以传递对象类型为例）

<!-- create time: 2014-09-19 22:32:03  -->

> 在两个activity之间传递数据无非是用Bundle 和Intent.putExtra的重载方法。
> Bundle,putExtra均可可以传递对象，前提是对象必须是可序列化的，序列化却会降低性能，传递的时候要把这个对象序列化，取对象的时候还要进行反序列化。

序列化对象

e.g:

    public class Zhu implements Serializable{
        -->可序列化的类
    }
    
 java:
 
     Zhu zhu = new Zhu();
     Intent intent = new Intent();
     intent.putExtra("class", zhu);
     intent.setClass(this,MianActivity.class);
     
     ->接收
     Zhu zhu1 ＝ (Zhu)this.getIntent().getSerializable("class");
     
OR :

    Zhu zhu = new Zhu();
    Bundle bundle = new Bundle();
    bundle.putSerializable("class", zhu);
    Intent intent = new Intent();
    intent.putExtras(bundle);
    intent.setClass(this,MianActivity.class);
    
    ->接收
    Bundle bundle = getIntent().getExtras();
    Zhu zhu = (Zhu)bundle.getSerializable("class");
[另一个方法](http://www.eoeandroid.com/thread-99364-1-1.html)待整理



##二者的区别
本质上二者无区别，intent在传值的时候会临时生命一个Bundle对象，通过bundle进行传值。

Android.Content.Intent中关于putExtra()方法:

     public Intent putExtra(String name, boolean value) {
        if (mExtras == null) {
            mExtras = new Bundle();
        }
        mExtras.putBoolean(name, value);
        return this;
    }
