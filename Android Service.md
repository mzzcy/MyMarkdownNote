###**Android Service**
启动方式：startService() bindService()

startService()启动后，一直在后台运行,通常不与其它组件交互
bindService()与其它组件交互，并可在进程间通信IPC，

服务中常重写的方法：
onStartCommand()：在其它组件使用startService()时回调
onBind()：其它组件使用bindService()回调
onCreate()：The system calls this method when the service is first created,to perform one-time setup procedures (before it calls either onStartCommand() or onBind()). If the service is already running, this method is not called.
onDestroy()：The system calls this method when the service is no longer used and is being destroyed

使用startService()启动服务后，服务会一直运行直到它自动使用stopSelf()或者别一个组件使用stopService()方法

当一个组件使用bindService()创建服务时（onStartCommand()没有执行），系统只有在组件bound它时才运行，一旦所有客户unbound时，系统就会把服务destroy

服务的运行在主线程中，为什么启动它的组件消毁了，它还可以运行，怎么理解？

IntentService()：
所有任务自动在work线程中执行，不占用主线程。
所有任务按先后顺序在work queue中排列，等待执行，适合完成单线程任务。
work queue中的任务执行完成后，会自动停止，不必调用stopSelf()访求。
通常只写构造方法，和onHandleIntent()方法。

Service():

















