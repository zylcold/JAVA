# Android的Window类

<!-- create time: 2014-09-30 22:36:27  -->

转自[博客园GangWang ](http://www.cnblogs.com/GnagWang/ )
    
Android的GUI层并不复杂。它的复杂度类似于WGUI这类基于布局和对话框的GUI，与MFC、QT等大型框架没有可比性，甚至飞漫魏永明的MiniGUI都比它复杂许多。

您也许会问，这样简单的GUI如何实现浏览器呢？原因很简单，浏览器有自己一套GUI。Android浏览器（WebKit）的GUI和Android的GUI实用同一套GDI——Skia，但GUI层是完全不同的设计，分别自成体系。
 
Windown类，位于代码树frameworks\base\core\java\android\view\Windowjava.java文件。连同注释，这个文件总共一千多行，它概括了Android窗口的基本属性和基本功能。 

 Window属性列举如下：
 
   属性                             |    说明
-----------------------------------| ------------------------------------ 
FEATURE_OPTIONS_PANEL = 0;         |      功能不明，参见后面的说明（默认使能） 
FEATURE_NO_TITLE = 1;              |     无标题栏 
FEATURE_PROGRESS = 2;              |   在标题栏上显示加载进度，例如webview加载网页时（条状进度条） 
FEATURE_LEFT_ICON = 3;             |  在标题栏左侧显示一个图标 
FEATURE_RIGHT_ICON = 4;            |  在标题栏右侧显示一个图标 
FEATURE_INDETERMINATE_PROGRESS = 5;|  不确定的进度（圆圈状等待图标） 
FEATURE_CONTEXT_MENU = 6;          | 上下文菜单，相当于PC上的右键菜单（默认使能） 
FEATURE_CUSTOM_TITLE = 7;          |自定义标题栏，该属性不能与其他标题栏属性合用 
FEATURE_OPENGL = 8;                |如果开启OpenGL，那么2D将由OpenGL处理（OpenGL中2D是3D的子集） 
PROGRESS_VISIBILITY_ON = -1;       | 进度条可见 
PROGRESS_VISIBILITY_OFF = -2;      |进度条不可见 
PROGRESS_INDETERMINATE_ON = -3;    |开启不确定模式 
PROGRESS_INDETERMINATE_OFF = -4;   | 关闭不确定模式 
PROGRESS_START = 0;                |第一进度条的最小值 
PROGRESS_END = 10000;              |第一进度条的最大值 
PROGRESS_SECONDARY_START = 20000;  | 第二进度条的最小值 
PROGRESS_SECONDARY_END = 30000;    |第二进度条的最大值 


* 说明：FEATURE_OPTIONS_PANEL的意思大概是：当用户选中菜单时，窗口将调用onOptionsItemSelected函数，以处理菜单功能。如果没有FEATURE_OPTIONS_PANEL选项，那么菜单就不响应了？


1. 隐藏标题栏

  JAVA:

    requestWindowFeature(Window.FEATURE_NO_TITLE); 
2. 在标题栏显示进度条

  JAVA: 

    requestWindowFeature(Window.FEATURE_PROGRESS); 
    setContentView(R.layout.progressbar_1); 
    setProgressBarVisibility(true); 
    final ProgressBar progressHorizontal =     
        (ProgressBar)findViewById(R.id.progress_horizontal); 
    setProgress(progressHorizontal.getProgress() * 100); 
    setSecondaryProgress(progressHorizontal.getSecondaryProgress()* 100); 
3. 使用自定义标题栏 

  JAVA:

    requestWindowFeature(Window.FEATURE_CUSTOM_TITLE); 
    setContentView(R.layout.xxx); 
    getWindow().setFeatureInt(Window.FEATURE_CUSTOM_TITLE,R.layout.my_title_bar); 
4. 清除标题栏内容，而区域保留 

   JAVA:    
                    
      ((ViewGroup)getWindow().findViewById
                    (com.android.internal.R.id.title_container)).removeAllViews(); 
5. 隐藏标题栏
 
   JAVA:
   
    ((ViewGroup)getWindow().findViewById
            (com.android.internal.R.id.title_container)).setVisibility(View.GONE); 
6. 显示标题栏
 
    ...setVisibility(View.VISIBLE); 
    
其他注意事项 
> (1) requestWindowFeature()要在setContentView()之前调用； 
 
> (2) 设置各种Feature，是具有排它性的，一旦设置，后续不可更改为别的类型； 

> (3)当使用TabHost(由ActivityGroup派生)时，各个Tab里的Activity，要么都是NO_TITLE，要么都是CUSTOM_TITLE，无法分别进行设置。

