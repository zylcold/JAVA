#Android应用程序的组成部分
     
    Android应用程序是由松散耦合的组件构成的，并使用应用程序Manifest绑定到一起。

Manifest描述了每一个组件以及他们之间的交互方式，用于指定元数据、硬件和平台要求、外部库以及必须的权限。

* Activity 应用程序的表示层。
* Service 应用程序中不可见的工作者。
* Content Provider 一个可共享的持久数据存储器。
* Intent 一个强大的应用程序间的消息传递框架。
* Broadcast Receiver  Intent侦听器。
* Widget  通常添加到设备主屏幕的可视化应用程序组件。
* Notification  Notification 允许向用户发送信号，但却不会过分吸引他们注意力或者打断他们当前的Actvity。


## Manifest
    
    包含 Acitity、Service、Content Provider 和 Broadcast Receiver 节点，并使用Intent Filter 和权限来确定这些组件之间以及这些组件和其他应用程序是如何交互的。

>结构

XML：

    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/           
    android"
    package="com.framework.accountant"
    android:versionCode="1"
    android:versionName="1.0" >

     <uses-sdk
        android:minSdkVersion="14"
        android:targetSdkVersion="19" />

      <uses-permission android:name="android.permission.INTERNET" />
     <application
        android:name="com.base.app.MyApplication"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
        <activity
            android:name="com.activity.Load"
        <intent-filter>
           <action android:name="android.intent.action.MAIN" />
           <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        
        </activity>
     </application>
    </manifest>

由一个根manifest标签构成，该标签带有一个设为项目包的 package 属性。

通常包含一个 `xmlns:android` 属性来提供文件内使用的某些系统属性。

`versionCode` 将当前应用程序版本定义为一个整数，每次迭代时这个整数会增加。

`versionName` 可以定义一个显示给用户的版本号。

`installLocation` 是否允许（或首选）将应用程序安装到外部存储器（SD卡等）而不是内部存储器上。         其值,`preferExternal--只要有可能就会安装到外部存储器`；`auto--要求系统决定`；`不指定installLocation属性，用户无法将应用程序移动到外部存储器`。
由于外部存储器存在取出或者拒绝外部存储器的问题，安装到外部存储器对一些应用程序不合适，这些应用程序包括：

    具有Widget、Live Wallpaper和Live Folder的应用程序。
    提供不中断服务的应用程序。
    输入法引擎（Input Method Engine， IME）。
    设备管理器 DeviceAdminReceiver 及管理能力将呗禁用。
   
    
