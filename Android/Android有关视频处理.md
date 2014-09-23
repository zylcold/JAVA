# Android有关视频处理

<!-- create time: 2014-09-21 16:43:58  -->

视频播放通常使用SufaceView和MediaPlayer来播放视频。（MediaPlayer没有提供输出图像的界面，可以结合SufaceView实现视频播放功能）

#MediaPlayer的生命周期。

##Idle状态 ->使用new创建MediaPlayer/调用了reset()方法后
    
    当使用new关键词创建MediaPlayer或者调用了reset()方法时，
    该MediaPlayer对象处于idle状态。
    
    
##Initialized状态 ->调用setDataSource()方法后

    表示播放文件已经准备就绪
    
##Prepared状态 ->调用prepare()方法后

    表示可以播放媒体文件
    
##Preparing状态 ->调用prepare()方法后

    如果异步准备完成则触发OnPreparedListener的onPrepared()方法，
    这个状态表示MediaPlay转变成Prepared状态。
    
    
##Started状态 ->调用start()方法后

    表示MediaPlayer正在播放文件。
    此时，可以通过isplaying()判断状态。
    seekTo()跳转到指定时间。
##Paused状态 ->调用pause()方法后

    此时调用start()则会继续播放，进入Started状态
    
##Stop状态 ->调用stop()方法后(在Started或者Paused状态下)
    
    如果想要重新播放，需要通过prepaerAsync()和prepare()回到Prepare状态才能重新开始。
    
    
##PlaybackCompleted状态 ->文件播放完毕且没有循环播放

    触发OnCompletionListener的onCompletion()方法
    
##Error状态 -> 出现错误时

    触发OnErrorListener.onError()事件，进入Error状态。
    通过setOnErrorListener(android.media.MediaPlay.OnErrorListener)可以设置改监听器
    如果MediaPlayer进入Error状态，可以通过调用reset()来恢复，重新回到Idle状态。
    
    