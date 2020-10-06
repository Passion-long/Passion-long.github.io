# JAVA
**1. Error和Exception的区别？**  
首先，所有的异常都是由Throwable继承而来，但在下一层立即分解为两个分支：Error和Exception  

**Error**  
* 总是不可控制的(unchecked)  
* 经常用来用于表示系统错误或低层资源的错误  
* 如何可能的话，应该在系统级被捕捉       
   
**Exception**  
* 可以是可被控制(checked)或不可控制的(unchecked)  
* 表示一个由程序员导致的错误  
* 应该在应用程序级被处理  
  
**2. 抽象类和接口的区别是什么？**  
  
抽象类：  
*  和普通类（非abstract类）相比，abstract类中可以有abstract方法（非abstract类中不可以有abstract方法）也可以有非abstract方法。  
*  对于abstract类，不能使用new运算符创建该类的对象。  
  
接口：  
*  接口体中包含常量的声明（没有变量）和抽象方法两部分。接口体重只有抽象方法，没有普通的方法。而且接口体中所有的常量的访问权限一定都是public，而且是static常量。所有的抽象方法的访问权限一定都是public。  
  
```
interface Printable {
  public final static int MAX = 100;
  public abstract void add();
  public abstract float sum (float x, float y);
}
```  
**3. 实现多线程的方式？各有什么优点？**  
* 继承 Thread 类，然后调用 start 方法。  
```
 class MyThread extends Thread {
   //重写run方法，线程运行后，跑的就是run方法 
   public void run(){
     //System.out.println("");
   }
   public static void main(String[] args){
     Thread t1 = new MyThread();
        t1.start(); //线程运行,调用的 run()方法.
   }
 }
```
* 实现 Runnable 接口的 run 方法, 然后再用 Thread 类包裹后，调用 start 方法。  
```
 class TestThread implements Runnable{
   @Override
   public void run() {
     // implement run method here 
     //System.out.println("");
   }
  
   public static void main() {
     final TestThread obj = new TestThread();
     Thread t1 = new Thread(obj);
     t1.start();
   }
 }
 ```
*  实现 Callable 接口的 call 方法，用 FutureTask 类包裹 Callable 对象。然后再用 Thread 类包裹 FutureTask 类，并调用 start 方法。call() 方法可以有返回值。  
```
class MyCallable implements Callable {
  @Override
  public Integer call() throws Exception {
    int sum = 0;
    for (int i = 1; i <= 100; i++) {
      sum += i;
    }
    return sum;
  }
  public static void main(String[] args) throws Exception {
    MyCallable mc = new MyCallable(); //实例化 callable

    FutureTask oneTask = new FutureTask(mc); //用FutureTask包裹
    Thread oneThread = new Thread(oneTask); //用Thread包裹
    oneThread.start();
    System.out.print(oneTask.get()); //获取返回值
  }
}
```
* 线程池  
  
**4. 说一下HashMap的实现原理？**  
* HashMap基于Hash算法实现，通过put(key,value)存储，get(key)来获取value。  
* 当传入key时，HashMap会根据key，调用hash(Object key)方法，计算出hash值，根据hash值保存在Node对象里，Node对象保存在数组里。  
* 当计算出的值相同时，称之为hash冲突，HashMap的做法是用链表和红黑树存储相同hash值的value。  
* 当hash冲突的个数：小于等于8使用链表；大于8时，使用红黑树解决链表查询慢的问题。  
* JDK1.7是基于数组+链表实现，JDK1.8是基于数组+链表+红黑树实现。  
* JDK1.7是头插法，JDK1.8是尾插法。  
* 在插入时，1.7先判断是否需要扩容，再插入，1.8先进行插入，插入完再判断是否需要扩容。  
  
**5. 非静态方法不存在线程安全的问题。**  
  
**6. UML中有哪些常用的图？**  
* 用例图  
* 类图  
* 时序图  
  
**7. equals和==的区别？（null==能用）**  
equals  
* 用来比较两个对象的内容是否相等。  
==  
* 对于基本数据类型的变量，==是直接对其值进行比较；  
* 对于引用数据类型的变量，则是对其内存地址的比较。  
  
**8. Integer和int的区别？**  
* Integer是int的包装类，int则是java的一种基本数据类型。  
* Integer变量必须实例化后才能使用，而int变量不需要。  
* Integer实际是对象的引用，当new一个Integer时，实际上是生成一个指针指向此对象；而int则是直接存储数据值。  
* Integer的默认值是null，int的默认值是0。  
  
**9. 内部类和静态内部类区别？**  
内部类：  
* 成员内部类可访问外部类所有的方法和成员变量。  
* 不能有静态的方法和成员变量。  
静态内部类：  
* 只能访问外部类的静态成员变量和静态方法；不能直接访问外部类的非静态成员，但可以通过new外部类().成员的方式访问。  
  
**10. 匿名内部类：**  
* 没有类名，没有class关键字，也没有extends和implements等关键字修饰。  
* 类的定义和对象的实例化同时进行。  
  
**11. sleep和wait的区别？**  
* sleep是线程中的方法，wait是Object中的方法。  
* sleep不会释放锁，wait会释放锁。  
* sleep不依赖于同步器synchronized，wait依赖synchronized关键字。  
* sleep不需要被唤醒（使用interrupt()方法吵醒休眠中的线程sleep），wait需要notify()或者notigyAll()唤醒。  
  
**12. String,StringBuffer和StringBuilder的区别？**  
* 可变性：String不可变，StringBuffer和StringBuilder可变。  
* 线程安全：String不可变，因此是线程安全的。StringBuffer是线程安全的，内部使用synchronized进行同步。StringBuilder不是线程安全的。  
  
**13. Vector与ArrayList的区别？**  
* ArrayList在内存不够时默认是扩展50%+1个，Vector是默认扩展1倍。  
* Vector属于线程安全级别的，但是大多数情况下不使用Vector，因为线程安全需要更大的系统开销。  
  
**14. HashMap和Hashtable的区别？**  
* 历史原因：Hashtable继承Dictionary类，HashMap继承自abstractMap。  
* HashMap允许空的键值对，但最多只有一个空对象，而HashTable不允许。  
* HashTable同步，而HashMap非同步，效率上比HashTable要高。  
  
**15. ArrayList和LinkedList的区别？**  
* ArrayList底层的数据结构是数组，支持随机访问，而LinkedList的底层数据结构是链表。不支持随机访问。使用下标访问一个元素，ArrayList的时间复杂度是O(1)，而LinkedList是O(n)。LinkedList是双向量链表。  
  
**16. Collection与Collections的区别是什么？**  
* Collection是Java集合框架中的基本接口。  
* Collections是Java集合框架提供的一个工具类，其中包含了大量用于操作和返回集合的静态方法。  
  
**17. Java中TreeMap是采用红黑树实现的。**  
  
**18. Java中super关键字的用法？**  
* 用super操作被隐藏的成员变量和方法。  
* 使用super调用父类的构造方法。  
  
**19. Java中的比较器的用法？**




