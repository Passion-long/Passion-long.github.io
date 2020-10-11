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
* sleep不会释放**锁**，wait会释放**锁**。  
* sleep不依赖于同步器synchronized，wait依赖synchronized关键字。  
* sleep不需要被唤醒（使用interrupt()方法吵醒休眠中的线程sleep），wait需要notify()或者notigyAll()唤醒。  
  
<details>  
<summary>什么是线程同步？</summary>  
   
所谓线程同步就是若干个线程都需要使用一个synchronized修饰的方法，即程序中的若干个线程都需要使用一个方法，而这个方法用synchronized给予了修饰。多个线程调用synchronized方法必须遵循同步机制。  
线程同步机制：当一个线程A使用synchronized的方法时，其他线程想使用这个synchronized方法时就必须等待，直到线程A使用完该synchronized方法。  
   
</details>  
   
<details>  
<summary>什么是线程联合？</summary>  
   
一个线程在占有CPU资源期间，可以让其他线程调用join()和本线程联合，比如，线程A希望联合线程B，那么线程A在占有CPU资源期间，可通过执行如下代码来联合线程B。B.join();  
线程A在占有CPU资源期间一旦联合B线程，那么A线程将立刻中断执行，一直等到它联合的线程B执行完毕，A线程再重新排队等待CPU资源，以便恢复执行。如果A准备联合的B线程已经结束，那么B.join()不会产生任何效果。  
   
</details>  
  
<details>  
<summary>什么是计时器线程？</summary>  
   
Timer类：  
Java提供了一个很方便的Timer类，该类在javax.swing包中。当某些操作需要周期性地执行，就可以使用计时器。我们使用Timer类的构造方法Timer(int a, Object b)创建一个计时器，其中的参数a的单位是毫秒，确定计时器每隔a毫秒“振铃”一次，参数b是计时器的监视器。  
  
振铃与ActionEvent事件：  
计时器发生的振铃事件是ActionEvent类型事件。当振铃事件发生时，监视器b就会监视到这个事件，监视器b就回调ActionListener接口中的actionPerformed(ActionEvent e)方法。因此当振铃每隔a毫秒发生一次时，方法actionPerformed(ActionEvent e)就被执行一次。需要特别注意的是，计时器的监视器b必须是组件类（例如，JFrame、JButton等）的子类的实例，否则计时器无法启动。  
  
计时器的启动与停止：  
计时器调用start()方法启动计时器，使用方法stop()停止计时器，使用restart()重新启动计时器。  
  
</details>  
  
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
  
**19. Java中Comparable和Comparator接口的区别？**  
  
Comparable：  
* Comparable可以认为是一个内部比较器，实现了Comparable接口。Comparable是排序接口。若一个类实现了Comparable接口，就意味着“该类支持排序”。  
* 接口中通过int x.compareTo(y)来比较x和y的大小。若返回负数，意味着x比y小；返回零，意味着x等于y；返回正数，意味着x大于y。  
  
Comparator：  
* Comparator可以认为是一个外部比较器，没有实现Comparable接口。我们可以通过“实现Comparator类来新建一个比较器”，然后通过该比较器对类进行排序。  
* 接口中通过int compare(T o1, T o2)和上面的x.compareTo(y)类似，定义排序规则后返回正数，零和负数分别代表大于，等于和小于。  
  
```
Collections里面的两个sort方法：  
public static <T extends Comparable<? super T>> void sort(List<T> list) {//内部比较器
  list.sort((Comparator)null);
}

public static <T> void sort(List<T> list, Comparator<? super T> c) {//外部比较器
  list.sort(c);
}
? super T 表示所有T的超类，只用于参数
```
具体代码区别可以参考：[Java中Comparable和Comparator接口区别分析](https://blog.csdn.net/qq_37267015/article/details/77371353)  
  
**20. 多态怎么理解？**  
* 一个类的不同子类在重写方法时可以各自产生适合其子类对象的行为。  
  
**21. 上转型对象的特性？**  
* 上转型对象不能操作子类新增的成员变量；不能调用子类新增的方法。  
* 上转型对象可以访问子类继承或隐藏的变量，也可以调用子类继承或重写的方法。  
  
**22. [图解LinkedHashMap参考这篇文章](https://www.jianshu.com/p/8f4f58b4b8ab)**  
  
  



