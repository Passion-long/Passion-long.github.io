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
  
4. 说一下HashMap的实现原理？  
* HashMap基于Hash算法实现，通过put(key,value)存储，get(key)来获取value。  
* 当传入key时，HashMap会根据key，调用hash(Object key)方法，计算出hash值，根据hash值保存在Node对象里，Node对象保存在数组里。  
* 当计算出的值相同时，称之为hash冲突，HashMap的做法是用链表和红黑树存储相同hash值的value。  
* 当hash冲突的个数：小于等于8使用链表；大于8时，使用红黑树解决链表查询慢的问题。  
* JDK1.7是基于数组+链表实现，JDK1.8是基于数组+链表+红黑树实现。  
* JDK1.7是头插法，JDK1.8是尾插法。  
* 在插入时，1.7先判断是否需要扩容，再插入，1.8先进行插入，插入完再判断是否需要扩容。  
  
5. 非静态方法不存在线程安全的问题。  
  
6. UML中有哪些常用的图？  
* 用例图  
* 类图  
* 时序图  
  
7. 
