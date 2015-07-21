一个JAVA应用只能包含一个类或者接口是public，且java源文件名命名要与public一致；
包：把java类放到指定的包中，一个java源文件只有一个package语句。且必须放在第一行，注释不算；

包引用：
除了java.lang中的类（Thread,Exception,System,Integer,String）被自动加引入外，一个类要使用别一个包中的类时，就需要声明包引用；

包名需和文件夹路径匹配，比如：
`com.abc.dollapp.doll.Doll`类，应该放在`dollapp\src\com\abc\dollapp\doll`目录下

import语句不能导致引入类的初始化。

若引入的两个包中包含相同的类名，在使用时要使用完整路径：
```java
package com.abc.dollapp.main;
import com.abc.bookstore,Book;
import com.abc.hotel.Book;

public class AppMain{
	public static void main(String args[]){		//存在两个相同的类名
    	com.abc.bookstore.Book book1 = new com.abc.bookstore.Book();
        com.abc.hotel.Book book2 = new com.abc.hotel.Book();
    }
}
```

**方法的定义：**
```java
返回值类型 方法名（参数列表）{
	方法主体；
}
```

当返回值类型为void时，方法主体可以没有return语句，也可以有return语句，但只能返回空：`return ;`
return语句返回的数值必须和方法前声明的一致；

所以return语句的：
a.结束执行本方法；
b.返回数值；

**main()**
```java
public static void main(String[] args)		//args其实也可以改为其它的名字
public static void main(String args[])
static public void main(String[] args)
```

被static修饰的方法默认都是final类型（不能被子类覆盖），所以在main()方法前加上final也是可以滴：
`final public static void main(String[] args)`

在命令行下可以给main()传递参数：
java com.abc.dollapp.main.MainApp parameter0 parameter1，之后args[0],args[1]与之对应；

**注释语句：**
```java
//text  	在一行中，从//起到这行结束
/* text */  之间的所有都被当作注释，可跨多行
/** text */ 之间的所有都被当作注释，常用在类，类的方法，类的成员之前当作声明，并作为生成文档用
```

**标识符：**
* JAAV中的标识符，首字符必须是**字母、下画线，美元符号，人民币**符号这 **四种**
* 标识符由数字，字母，下画线，美元和人民币等，比用于首字符多了数字
* 标识符没有长度限制
* 不用用保留字作标识符
* 对大小写敏感，大小写不同会被当作不同的字符

非法字符：`try#、7group、open-door`（不能有#,数字不能作首，不能有-）

JAVA命名规则：
* 类名和接口名：使用各个单词首字母大写：`SmallDoll`
* 方法名和变量名：首字母小写，其余单词首字母大写：`bothEyesOfDoll`
* 常量名：所有字母采用大写形式，各个单词用下画线隔开：`final String DEFAULT_COLOR_OF_DOLL = "yellow";`
* 包名：采用小写形式：`com.abc.doolapp`

>关于SDK版本的叫法：
>Sun公司认为JDK1.5的发布是Java语言发展史一里程碑，所以为了表示重要性，从JDK1.5开始叫JDK5.0,之后的版本也采用这样的格式。

**JavaDoc标记：**
在/** text */中，使用一些标记可让javadoc.exe生成文档时识别：
```java
@version
@since   		最长出现在哪个版本
@author
@param	 		方法中的参数
@return			返回值
@throws			抛出的异常
@see			提示可参观的DOC链接
@link			与see一样，区别是link标记能够嵌入到注释语句中，为注释语句中的特定词汇生成链接
@deprecated		用来标明注释的类，变量或方法已经不提倡使用
```

示例：
```java
/**
*设置在默认情况下所说的话
*@param word 在默认情况下据说的话
*@return 无返回值
*@see #getWord
*@since 2.0
*
*/
public void setWord(String word){...}
```
上面使用#getWord，表示引用这个方法，并且这个方法就在这个类中

**Java虚拟机的运行时数据区：**

AppMain.java--->（经编译）AppMain.class--->（加载到）类加载器--->字节码检验器--->解析器--->运行时环境--->各个平台

JAVA虚拟机提供了**程序运行时环境**，运行时环境中最重要的一个资源是**运行时数据区**。
运行时数据区是操作系统为JAVA虚拟机分配的**内存区域**，虚拟机自己管理这块区域。虚拟机自己把这块区域进一步划分为多个区域，包括：**堆区，方法区，栈区**3个类别。

`Doll beibei = new Doll("贝贝")；` 虚拟机在执行这句时：
* 先搜索方法区，查找Doll类的类型信息，第一次当然找不到，便会加载之，加载到方法区。（类中的类型信息和具体的方法也保存在这里）
* 在堆区为一个新的Doll类实例分配内存，并将引用指向方法区Doll类
* 因为beibei在main()方法中定义，属于局部变量，所以被添加到执行main()方法的主线程JAVA方法调用栈中。并将引用指向堆区中的Doll实例。

	

































