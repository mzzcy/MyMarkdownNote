###**Singleton:**
####**最简单的单例:**
```java
public class Singleton{
	private static Singleton instance = new Singleton();
    //other fields...
	private Singleton(){}
    public static Singleton getInstance(){
    	retrun instance;
    }
    //other methods...
}
```

**特点：**
* 定义的实例变量和构造方法都为private修饰，只能通过公用方法来获取实例对象
* 实例变量其实也能定义为public类型，这样不用getInstance()方法来获取实例对象，但这样可读性就降低了，并且直接使用实例变量名，增加与客户类之间的耦合度，当改变这个变量名时，客户类也得跟着改变。
* 此模式是线程安全的，JVM在加载类时，对于static属性的初始化只能由一个线程执行且仅一次

####**延迟创建实例：**
出于性能的考虑，希望延迟实例化单例对象，而static属性在加载类时就会被初始化，如何在第一次使用该类的实例时才去实例化呢？

#####**UnThreadSafeSingleton:线程不安全的,仅适合用单线程**
```java
public class UnThreadSafeSingleton{
	//variables and constructors...
    public static UnThreadSafeSingleton getInstance(){
		if(instance == null){
			instance = new UnThreadSafeSingleton();
        }
        retrun instance;
    }
}
```

#####**ThreadSafeSingleton:线程安全的,但高并发访问时效率不佳**
```java
public class ThreadSafeSingleton{
	//variables and constructors...
    public static synchronized ThreadSafeSingleton getInstance(){
		if(instance == null){
			instance = new ThreadSafeSingleton();
        }
        retrun instance;
    }
}
```

#####**Double-Check Locking：线程安全的，且效率优**
```java
public class DoubleCheckSingleton{
	private volatile static DoubleCheckSingleton instance = null;
    //constructors
    public static DoubleCheckSingleton getInstance(){
    	if(instance == null){
			synchronized(DoubleCheckSingleton.class){
				if(instance == null) instance = new DoubleCheckSingleton();
            }
        }
        return instance;
    }
}
```
属性instance被volatile修饰的，因为volatile具有synchronized的可见性特点，也就是说线程能够自动发现volatile变量的最新值，这样，如果instance实例化成功，其它全程便能立即发现。

>注：此程序只有在JAVA 5以后的版本才能正常执行，这是由于JAVA平台内存模式容许out-of-order writes 引起的，如有两个线程的执行顺序：
a.T1发现instance没有被实例化，它获得锁，并去实例化此对象，JVM容许在没有完全实例化完成时,instance变量就指向此实例，因为这些步骤可以是out-of-order writes的，此时instance==null为flase,之前的版本(1.5)用volatile关键字修饰也无效。
b.在初始化完成之前，T2进入此方法，发出instance已经不为null了，T2便使用这个未完全初始化的实例对象，则可以引起系统崩溃。

#####**LazyLoadedSingleton**
```java
public class LazyLoadedSingleton{
	private LazyLoadedSingleton(){}
    private static class LazyHolder{
    	private static final LazyLoadedSingleton singletonInstance = new LazyLoadedSingleton();
    }
    public static LazyLoadedSingleton getInstance(){
		return LazyHolder.singletonInstance;
    }
}
```
这是一种线程安全的延迟单例初始化的方法，称为Initialization on demand holder模式。
当JVM加载这个类时，因为它本身没有static修饰的属性，所以加载完这个类后即可返回。只有第一次调用getInstance()方法时，JVM才会加载LazyHolder这个类，且它有一个static修饰的属性，这个即是想要得到的实例，所以在这时才初始化这个属性。















