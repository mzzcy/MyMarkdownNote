#####**Object:**
Object类是所有JAVA类的最终祖先，如果一个类声明时没有包含extends，那么这个类直接继承Object类。

Object类常用的方法，包括wait(),notify(),notifyAll(),equals(),hashCode(),toString(),finalize()等。

equal():与==一样，当且仅当两边指向同一个对象时，值为true。但在许多类中重写了这个方法，内容相同即为true。如包装类，Date,String

toString()默认返回格式为：类名@对象的十六进制哈希码，如java.lang.Object@273d3c

#####**String 和 StringBuffer:**
String类的构造方法：
* String()
* String(String value)：  字符串参数指定字符串的内容。
* String(char[] value)：  字符数组参数指定字符串的内容。
* String(byte[] bytes)：  根据本地平台默认的字符编码，由字节数组构造一个字符串。
* String(byte[] String charsetName):  根据字符编码来构造。

String类常用方法：
* **length()**：　返回字符串的字符个数。
* **char charAt(int index)**：返回字符串中index位置上的字符,取值为0~length-1。
* **getChars(int srcBegin,int srcEnd,char dst[],int dstBegin)**：把字符串取到dst[]中来。
* **equals(object str)**　和　**equalsIgnore(object str)**：后者不区别大小写。
* **int compareTo(String str)**：前者大返回1，后者大返回-1，相等返回0;
* **indexOf和lastIndexOf()**：在字符串中检索特定字符或字符串，前者从最前面开始找，后者从最后面开始找，返回所在的第一个字符的位置，从0开始计算。找不到返回-1。
`str.indexOf('e');`		//从最左边开始找，第一个出现e的位置
`str.indexOf('e',2);`	//从位置2开始第一次出现e的位置

* **concat(String str)**：把字符串str附加到当前字符串上，并返回符加后的字符串的对象，该方法并不改变原字符串。
* **substring： substring(int beginIndex)** 或 **substring(int beginIndex,int endIndex)**
```java
String str = "0123456";
String sub1 = str.substring(2);
String sub2 = str.substring(2,5);
System.out.println(str);	//打印0123456
System.out.println(sub1);	//23456
System.out.println(sub2);	//234
```

* **String[] split(String regex)**：根据regex把原来字符串分割为几个子字符串数组：
```java
String[] result;
String str = "user=Linda";
result = str.split("=");	//result={"user","Linda"}
str = "11::14";
result= str.split(":");		//result={"11","","14"}
```
* **replaceAll(String regex,String replacement)** 和 **replaceFirst(String regex,String replacement)**，把源字符串中的regex替换为replacement。前者替换所有，后者只替换第一个元素

* **trim() ：**去除字符串首尾的空格
* **String valueOf():**把基本类型转换为String类型，包含多种重载形式，如valueOf(int a),valueOf(Short a),valueOf(double a)等：
`System.out.println(Stirng.valueOf(-129));`		//打印-129
`System.out.println(String.valueOf(-129.12D));`	//打印-129.12
* **toUpperCase() 和 toLowerCase():**前者把所有字母转换为大写，后者把所有字母转换为小写

#####**“hello” 与 new String("hello")的区别：**
方式一：String s1="hello" ,s2="hello";
方式二：String s1=new String("hello"),s2=new String("hello");
第一种方式中，"hello"为直接数，JAVA虚拟机把它作为编译时常量，在内存中只会为它分配一个内存，之后可以重复使用，因此s1==s2为true。而在第二方式中，s1==s2为false。

**StringBuffer：**
构造方法：
* StringBuffer():建立一个空的缓冲区，默认长度为16.
* StringBuffer(int length)：建立一个长度为length的空缓冲区。
* StringBuffer(String str): 缓冲区初始化内容为字符串str,并提供了16个字符的空间供再次分配。

常用方法：
* length(): 返回字符串的字符个数
* append(): 向缓冲区内添加新的字符串：
```java
StringBuffer sb = new StringBuffer();
sb.append("Hello");
sb.append("World");
System.out.println(sb);		//打印HelloWorld
```

* toString(): 返回缓冲区内的字符串
* charAt(int index) 和 setCharAt(int index,char ch): 前者与String中的用法相同，后者是改变在index处的值
* getChars(int srcBegin,int srcEnd,char[] dst,int dstBegin): 用法与String中相同。`
* substring()：与String中的用法相同
* insert(int offset,String str)：在字符串中的offset位置插入字符串str
```java
StringBuffer sb = new StringBuffer("0456");
sb.insert(1,"123");
System.out.println(sb);		//打印0123456
```

**String 与 StringBuffer区别：**
* String类是不可变类，而StringBuffer类是可变类。String中的许多方法并不能改变它本身，而是返回一个改变的后的新的对象。
* String类覆盖了Object类的equals()方法，而StringBuffer类没有覆盖Object类的equals(),所以SB的内容相同使用eqauals()方法也返回false
* 两者的toString()方法实现也不同，String类的toString()方法返回当前String实例本身的引用，使用==都是true，而StringBuffer类的toString()方法返回一个新的String对象引用
* String类对象可以使用操作符+连接，而SB不行

#####**包装类：**
JAVA用包装类来把基本数据转换为对象，第个JAVA基本类型在java.lang包中都有一个相应的包装类：
Byte,Short,Integer,Long,Float,Doulbe,Boolean,Character
包装类主要能提供一些方便的方法。

包装类的构造方法：
* 所有包装类都可以用和它对应的基本数据类型数据来作为参数，来构造他的实例：
```java
Boolean bln = new Boolean(true);
Character c = new Character('c');
Byte b = new Byte((byte)1);		//int类型的直接数需要强制类型转换
Short s = new Short((short)1);	//同上
Integer i = new Integer(1);
Long l = new Long(1);
Float f = new Float(1.0f);
Double d - new Double(1.0);
```

* 除Character类以外，其它包装类都可以以一个字符串为参数来构造它们的实例：

    ```java
    Integer i = new Integer("123");
    Double d = new Double("123.45D");
    Float f = new Float("123.45F");

    注：当Boolean类的构造方法参数为String类型时，如果字符串内容为true（不区别大小分），则为true，其它一律为false:
    new Boolean("TrUE");		//为true
    new Boolean("23EFX");		//为false

    当使用String来构造相应的包装类时，字符串不能为null,且该字符必须可以解析为相应的基本类型数据，否则编译虽能通过，运行时会抛出NumberFormatException运行时异常:
    System.out.println(new Double("123.11D"));		//打印123.11
    System.out.println(new Byte("123D"));			//抛出异常
    ```

包装类常用方法：
Character类 和 Boolean类直接继承Object类，其它6种都是java.Object.Number的直接子类。
其中Number类主要的方法：
* **byteValue()**
* **shortValue()**
* **intValue()**
* **longVaule()**
* **doubleValue()**
* **floatValue()**
以上方法都是返回对应的**基本类型数据**
* **toString()**，以字符串形式返回包装对象所表示的**基本类型数据**
* **valueOf(String s)**静态工厂方法，可以根据String类型的参数来创建包装类对象:
```java
Double d = Double.valueOf("123");		//合法
Integer i = Integer.valueOf("12");		//合法
Integer i = Integer.valueOf("abc");		//运行时抛出 NumberFormatException
```
* **parseXXX(String str)**静态方法，能把字符串转换为相应的基本类型的数据,XXX表示基本数据类型的名称：
```java
int i = Integer.parseInt("123");	//合法 i = 123
double d = Double.parseDouble("abc");	//抛出 NumberFormatException
```

#####**总结**上面的**类型转换**的几个方法：
**String类的valueOf()静态方法**：
基本类型--->String类型
包含多种重载形式，如valueOf(int　a),valueOf(Short a),valueOf(double a)等：
`System.out.println(Stirng.valueOf(-129));`		//打印-129
`System.out.println(String.valueOf(-129.12D));`	//打印-129.12

基本数据--->包装类：new 构造方法　传入
String--->包装类：new 构造方法　传入


包装类--->基本数据：byteValue,intValue... （除了CB）
包装类--->String：toString()方法	（除了CB）
String--->包装类：静态方法valueOf,`Double d=Double.valueOf("123");`（除了CB）
String--->基本数据：parseXXX(String str)  `int i=Integer.parseInt("123");`（除了CB）

包装类特点：
* 所有包装类都是final类型，因此不能创建子类
* 包装类是不可变类
* JDK1.5后允许基本类型和包装类型进行混合数学运算，而在之前的版本，数学运算必须是基本类型，并且结果也是基本类型：

```java
//在1.5之前的版本
int a=1,b;
b=a+1-2*4;		//合法
Integer c=a+1-2*4;		//编译出错，结果必须是基本类型
b=a+new Integer(1)-new Integer(2)*4;	//编译出错，操作元应是基本类型

//在1.5之前的版本要这样来实现：
public static Integer add(Integer a,Integer b){
	//包装类--->基本类型
    int sum=a.intValue()+b.intValue();
    //基本类型--->包装类
    return new Integer(sum);
}

//1.5之后
public static Integer add(Integer a,Integer b){
	return a+b;
}

```
#####**Math类：**
abs()：绝对值
ceil()：大于或等于参数的最小整数，返回类型为double
floor()：小于或等于参数的最大整数，返回类型为double
max(),min()：求两个参数的最大、最小值
random()：求0.0到1.0之间的double类型随机数，包含0.0，但没有1.0
round()：四舍五入，参数为double类型，返回long类型；参数为float类型，返回int类型
sin(),cos(),tan()：正弦，余弦，正切函数
exp()：求自然对数的幂，exp(x)=e^x
pow()：幂运算，pow(2,3):2^3
sqrt()：平方根

#####**Random类：**
nextInt()：返回下一个int类型的随机数，大于等于0，在int范围内
nextInt(int n),大于等于0，小于n
nextLong(),大于等于0，在Long范围内
nextFloat()：float类型，大于等于0，小于1.0
nextDouble()：double类型，大于等于0，小于1.0
nextBoolean()：随机返回true或false

#####**处理日期的类：**
**java.util.Date：**包装了一个Long类型的数据，表示与GMT（格林尼治标准时间）的1970年1月1日00:00:00这一刻相距的毫秒数
**java.text.DateFormat：**对日期格式化
**java.util.Calendar：**可灵活地设置或读取日期的年月日时分秒等信息
```java
Date date = new Date();
System.out.println(date.getTime());		//getTime()得到毫秒数，打印1143096101969
System.out.println(date);				//打印 Thu Mar 23 14:46:41 CST 2006
```
new Date()类默认构造方法调用**System.currentTimeMills()**方法来获取当前的时间，new Date()等价于：new Date(System.currentTimeMills())




























