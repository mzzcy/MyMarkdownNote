####Java集合：

> 集合只能存放对象的引用，长度不定可增。

**Set：**没有重复对象。
**List：**可以有重复对象，与数组相似。
**Map：**Key--Value，Key不能重复。

**Collection接口：**
Set 和 List实现了Collection接口，包含一些实用方法：

boolean add(Object o)：添加一个元素。
void clear()：删除集合中所有对象，不再持有这些对象的引用。
boolean contains(Object o)：判断是否包含。
boolean isEmpty()：判断集合是否为空。
Iterator iterator()：返回一个Iterator对象，可用来遍历集合中元素。
boolean remove(Object o)：删除o对象。
int size()：返回集合元素数目。
Object[] toArray()：返回集合中所有对象的引用给数组。

**Iterator接口中声明的方法：**
hasNext()：判断是否遍历完，是否还有下一个元素。
next()：返回下一个元素，并后移一位。
remove()：删除最近next返回的对象。

>注：Iterator遍历顺序是随机的，不一定按添加时的顺序遍历。

#####Set集合：
主要用两个实现类：HashSet、TreeSet

HashSet <-- LinkedHashSet ：不仅实现了哈希算法，而且实现了链表数据结构，提高插入和删除元素的性能。

HashSet按照哈希算法来存取集合中对象，存取较快。
TreeSet实现了SortedSet接口，具有排序功能。


Set不允许添加重复的对象，它的的add()方法是通过equal()方法来判断是否重复，而不是运算符==。

