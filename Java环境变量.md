####1新建系统变量JAVA_HOME：
变量名：JAVA_HOME
变量值：C:\Program Files\Java\jdk1.8.0
作用：方便下面两个变量的引用；让第三的软件知道JDK在哪个位置。

####2新建系统变量CLASSPATH：
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
作用：它的作用与import、package关键字有关。
比如当你写下improt java.util.*时，编译器面对import关键字时，就知道你要引入java.util这个package中的类，面这个package就在classpath的目录下。其中.表示在当前目录中查找.class文件。比如使用java test.class时。

####3在Path中添加：
变量名：Path
添加变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
作用：在cmd下方便使用相关工具。