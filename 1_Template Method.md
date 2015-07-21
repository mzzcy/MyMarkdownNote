####**Template Method：**
#####**定义:**
 >**Define the skeleton of an algorithm in an operation,deferring some steps to subclasses.Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.**

也就是说模板方法定义了一系列算法步骤，子类可以去实现/覆盖其中某些步骤，但不能改变这些步骤的执行顺序。

#####**作用：**
* 解决代码冗余
* 易于扩展
* 父类提供算法的框架，子类不能更改其代码执行顺序
* 父类可以把重要的元素定义为final/priavte

#####**示例：**
```java
//父类
public abstract class HappyPeople{
	pulibc void celebrateSpringFestival(){
    	subscribeTicket():
        travel();
        celebrate();
    }
	protected final void subscribeTicket(){
		System.out.println("Buying ticket...");
    }
    //留给子类实现
    protected abstract void travel();
    protected final void celebrate(){
    	System.out.println("Happy Chinese New Year!");
    }
}
```

```java
//子类
public class PassengerByAir extends HappyPeople{
	@Override
    protected void travel(){
    	System.out.println("Travelling by Air...");
    }
}
```

####**防止子类的泛滥：引入回调**
如数据库查询中的需求，因对查询结果的处理不同，不能每种都去生成一个子类来实现。
在JAVA中使用匿名内部类来实现回调。

**回调表示一段可执行逻辑的引用，我们把该引用传递到另外一段逻辑里供这段逻辑适时调用。**

#####**示例：**
```java
//定义一个接口
import java.sql.ResultSet;

public interface ResultSetHandler<T>{
	public T handle(ResultSet rs);
}
```

```java
import java.sql.*;

public class SimpleJdbcQueryTemplate{
	public <T>T query(String queryString,ResultSetHandler<T> rsHandler){
    	//define variables...

		try{
        	connection = getCollection();	//get a db connection
            stmt = connection.prepareStatement(queryString);
            ResultSet rs = stmt.executeQuery();
            return rsHandler.handle(rs);
        }catch(SQLException ex){
			...
    	}finally{
        	//close the statement & connection...
        }
    }
    //other methods...
}
```























