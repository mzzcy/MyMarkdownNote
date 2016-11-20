#####**什么是java的局部变量，成员变量，全局变量？**
[原链接](http://zhidao.baidu.com/question/173252839.html)
```java
public class Test {
   private String name;//成员变量，也是全局变量.在JAVA里全局变量和成员变量是一个意思。
   public void changeName() {
       String n = "tomoya";//n就是局部变量
       name = n;
   }
}
```
>[原链接](http://zhidao.baidu.com/link?url=-UcJbTXj9bX0-32LwI4TRQqVWCEDLoC_HT3knQjaY6UBrxb1UiDnmMZ5xX1XhqWVi8L2DZ9zFIUMwEvAVMexKa)
从来只有成员变量和局部变量的区别。
我们就好比一个类是一个公司,
成员变量就是这个公司的正式员工,一直存在,与公司同生同灭..
而局部变量就是临时工,公司请临时工来做一点事情,做完,临时工就没有了,被销毁了!(好灵异)

>确实有人把成员变量叫成全局变量.那是以这个类作为全部

>其实还有一种比成员变量更大的...可能你不懂,不过以后你就知道了.
我建一个公用类,我在里面声明一个静态变量,那么,我在任何地方都可以用它了..它也被通俗的叫做<全局变量>



#####**JAVA类变量？**
[原链接](http://blog.chinaunix.net/uid-26434689-id-3328442.html)
类变量（也叫静态变量）是类中独立于方法之外的变量，用static 修饰。（static表示“全局的”、“静态的”，用来修饰成员变量和成员方法，或静态代码块（静态代码块独立于类成员，jvm加载类时会执行静态代码块，每个代码块只执行一次，按顺序执行））。
```java
public class Variable{
     static int allClicks=0;//类变量
     String str="hello world";//实例变量
     public void method(){
        int i =0;//局部变量
     }
}
```

成员变量也称为:“域”，“实例变量”，在实体类或数据类中被称为“属性”或“字段”。当成员变量可以改变时，被称为对象的状态。
#####**java中，什么是成员方法？**
```java
public class Student {
    private String name ;//name是Student的成员变量

public String getName(){ //getName就是成员方法，定义在Student中的方法
        return this.name ;
    }
}
```

#####**Java中的属性和字段有什么区别?**
1、Java中的属性和字段有什么区别？
答：Java中的属性，通常可以理解为get和set方法。而字段，通常叫做“类成员”。

这两个概念是完全不同的。

属性只局限于类中方法的声明，并不与类中其他成员相关。例如：
void setA(String s){}
String getA(){}
当一个类中拥有这样一对方法时，我们可以说，这个类中拥有一个可读写的a属性(注意是小写a)。如果去掉了set的方法，则是可读属性，反之亦然。

类成员(字段)，通常是在类中定义的类成员变量，例如：
public class A{
private String s = "123";
}
我们可以说A类中有一个成员变量叫做s。






















