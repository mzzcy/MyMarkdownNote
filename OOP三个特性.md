####OOP三个特性：
#####**封装：**
一个类使用private将自身的属性保护起来，把功能逻辑都隐藏起来，只有自己本身能修改，只对外提供要使用的方法的接口，对自身起来了很好的保护作用；对其它类来说，无需关心要调用类的功能实现逻辑，只需要接口即可，减小了耦合性。

#####**多态：**
[原文链接](http://www.cnblogs.com/mengdd/archive/2012/12/25/2832288.html)

**多态==晚绑定**
多态是一种运行期绑定(run-time binding)机制，通过这种机制，实现将函数名绑定到函数具体实现代码目的。
Java多态性的概念也可以被说成**“一个接口，多个方法”。**
因为多态**是一种运行期**的行为，**不是编译期**的行为。

不要把函数重载理解为多态。

**多态：**父类型的引用可以指向子类型的对象。

比如 Parent p = new Child();

当使用多态方式调用方法时，首先检查父类中是否有该方法，如果没有，则编译错误；如果有，再去调用子类的该同名方法。

（注意此处，静态static方法属于特殊情况，静态方法只能继承，不能重写Override，如果子类中定义了同名同形式的静态方法，它对父类方法只起到隐藏的作用。调用的时候用谁的引用，则调用谁的版本。）

多态必须具备**三大特征：**
* 子类继承父类
* 子类覆盖父类
* 父类指向子类。

如果想要调用子类中有而父类中没有的方法，需要进行**强制类型转换**，如上面的例子中，将p转换为子类Child类型的引用。

因为当用父类的引用指向子类的对象，用父类引用调用方法时，找不到父类中不存在的方法。这时候需要进行**向下的类型转换**，将父类引用转换为子类引用。

```java
public class PolyTest
{
    public static void main(String[] args)
    {        
        //向上类型转换
        Cat cat = new Cat();
        Animal animal = cat;
        animal.sing();
                
        //向下类型转换
        Animal a = new Cat();
        Cat c = (Cat)a;
        c.sing();
        c.eat();

        //编译错误
        //用父类引用调用父类不存在的方法
        //Animal a1 = new Cat();
        //a1.eat();
        
        //编译错误
        //向下类型转换时只能转向指向的对象类型        
        //Animal a2 = new Cat();
        //Cat c2 = (Dog)a2;
    }
}
class Animal
{
    public void sing()
    {
        System.out.println("Animal is singing!");
    }
}
class Dog extends Animal
{
    public void sing()
    {
        System.out.println("Dog is singing!");
    }
}
class Cat extends Animal
{
    public void sing()
    {
        System.out.println("Cat is singing!");
    }
    public void eat()
    {
        System.out.println("Cat is eating!");
    }
}
```
#####**两种类型的类型转换:**
（1）向上类型转换（**Upcast**）：将子类型转换为父类型。
对于向上的类型转换，不需要显示指定，即不需要加上前面的小括号和父类类型名。

（2）向下类型转换（**Downcast**）：将父类型转换为子类型。
对于向下的类型转换，必须要显式指定，即必须要使用强制类型转换。

>（参考学习链接：http://docs.oracle.com/javase/tutorial/java/IandI/override.html）






























