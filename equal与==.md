==是操作符
equals()是Object类的方法

==两边是基本类型时，值相同即为true；两是引用类型时，只有指向同一个对象的引用才为true.

==与多态：
==两边为引用类型时，==两边必须是同种类型，或存在着继承关系。否则编译就出错。

Dog dog = new Dog();
Cat cat = new Cat();
dog == cat; //编译出错

Object类中原本的equals()其实就是用==来实现的：
public boolean equals(Object obj){
	if(this == obj)return true;
    else return false;
}
但在JDK中有一些类重写了Object类的equals(),比如常用的包装类（Integer,Double），File类，Date类,String类。比较规则为两上对象类型一致，并且内容也一致就是true.

一般重写equals()方法：
```java
public class Person{
	private String name;
    public Person(String name){this.name=name}
    
    public bolean equals(Object o){
    	if(this==0)return true;  //若引用一样则直接为true
        if(!o instanceof Person)return false;  //若类型不同，且不存在引用则直接false
        final Person other = (Person)o;   //为什么还要向上转型？
        if(this.name().equals(other.name()))
        	return true;
        else
        	return false;
    }

}
```

instanceof操作符：
obj instanceof ClassName
左边为一个**对象的引用**，右边为一个**类名** 或者 **接口名**。

Dog dog = new Dog();
dog instanceof XXX为true的情况：
* Dog类
* Dog类的直接或间接父类。
* Dog类实现的接口，以及所有父类实现的接口。

instanceof与多态，与==多态一样。


















