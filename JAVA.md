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
  
abstract不能和哪些关键字共存？  
private、static、final。  
  
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
* equals方法是一个方法,只能比较引用数据类型,所有的对象都会继承Object类中的方法,如果没有重写Object类中的equals方法,equals方法和==号比较引用数据类型无区别,重写后的equals方法比较的是对象中的属性.(原来这么写的：用来比较两个对象的内容是否相等。)  
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
* ArrayList是线程不安全的,效率高；Vector是线程安全的,效率低。  
* 共同点：都是数组实现的  
  
**14. ArrayList和LinkedList的区别？**  
* ArrayList底层是数组，查询和修改快  
* LinkedList底层是链表，增和删比较快，查询和修改比较慢
* 共同点:都是线程不安全的  
  
**15. HashMap和Hashtable的区别？**  
  
* Hashtable,是线程安全的,效率低,HashMap是,是线程不安全的,效率高。  
* Hashtable不可以存储null键和null值,HashMap可以存储null键和null值。  
  
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
  
22. 
**[图解HashMap原理参考这篇文章](https://www.jianshu.com/p/dde9b12343c1)**  
**[图解LinkedHashMap参考这篇文章](https://www.jianshu.com/p/8f4f58b4b8ab)**  

**23. Java三大注解是什么？**  
1.Java三大注解分别是@Override @Deprecated @Suppresswarnings
2.@Override 注解表名子类中覆盖了超类中的某个方法，如果写错了覆盖形式，编译器会报错
3.@Deprecated 表明不希望别人在以后使用这个类，方法，变量等等
4.@Suppresswarnings 达到抑制编译器产生警告的目的，但是不建议使用，因为后期编码人员看不懂编译器提示的警告，不能更好的选择更好的类去完成任务
  
**23. 下面语句都是创建数组的正确语句：**  
float f[][] = new float[6][6];  
float []f[] = new float[6][6];  
float [][]f = new float[6][6];  
float [][]f = new float[6][];  
  
**24. Java程序初始化顺序：**  
父类的静态代码块  
子类的静态代码块  
父类的普通代码块  
父类的构造方法  
子类的普通代码块  
子类的构造方法  
例子：  
```
class A {
    public A() {
        System.out.println("class A");
    }
    { System.out.println("I'm A class"); } 
    static { System.out.println("class A static"); }
}
public class B extends A {
    public B() {
        System.out.println("class B");
    }
    { System.out.println("I'm B class"); }
    static { System.out.println("class B static"); }
     
    public static void main(String[] args) { 
      new B(); 
    }
}
```  
运行下面代码，输出的结果是:  
class A static  
class B static  
I'm A class  
class A  
I'm B class  
class B  
  
**25. java关键字都是小写。null是关键字，NULL不是关键字，java区分大小写。**  
  
**26. 通过JDBC访问数据库包含下面4步：**  
(1). 载入JDBC驱动程序  
(2). 建立连接  
(3). 执行查询或更新  
(4). 关闭连接  
  
**27. 线程切换状态：**
![Thread](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Thread.png)  
  
**28. 同步代码块中的锁：**  
```
public class Test {
    private synchronized void a() {
    }
    private void b() {
        synchronized (this) {
        }
    }
    private synchronized static void c() {
    }
    private void d() {
        synchronized (Test.class) {
        }
    }
}
```
方法a为同步方法，方法b里面的是同步块，同步方法使用的锁是固有对象this，同步块使用的锁可以是任意对象，但是方法b里面的同步块使用的锁是对象this，所以方法a和方法b锁住的是同一个对象。方法 c为静态同步方法，使用的锁是该类的字节码文件，也就是Test.class。方法d里面的也是同步块，只不过使用的锁是Test.class，所以方法c和方法d锁住的是同一个对象。
  
**29. 重载和重写的区别？重载能改变返回值类型吗？**  
* 重载：本类中出现的方法名一样，参数列表不同的方法。与返回值类型无关。  
* 重写：子类中出现了和父类中方法声明一模一样的方法。与返回值类型有关,返回值是一致的。  
* 重载可以改变返回值类型，只看参数列表。  
  
**30.Java中到底是传值还是传址？**  
* 既是传值,也是传地址,基本数据类型传递的值,引用数据类型传递的地址  
* java中只有传值,因为地址值也是值(出去面试都说这种,支持者是高司令(java之父))  
  
**31.子类对象调用方法的时候：先找子类本身，再找父类。**  
   
**32.面向对象(抽象类和接口的区别)（补充）**  
* A:成员区别
	* 抽象类：
		* 成员变量：可以变量，也可以常量
		* 构造方法：有
		* 成员方法：可以抽象，也可以非抽象
	* 接口：
		* 成员变量：只可以常量
		* 成员方法：只可以抽象
		* 构造方法：无
		
* B:关系区别
	* 类与类
		* 继承，单继承，多层继承
	* 类与接口
		* 实现，单实现，多实现
	* 接口与接口
		* 继承，单继承，多继承
		
* C:设计理念区别
	* 抽象类 被继承体现的是：”is a”的关系。抽象类中定义的是该继承体系的**共性功能。**
	* 接口 被实现体现的是：”like a”的关系。接口中定义的是该继承体系的**扩展功能。**
  
**33.package,import,class有没有顺序关系？**  
* 有，先是package，后是import，最后是class。  
  
**34.四种权限修饰符**
```
* 
				本类	 同一个包下(子类和无关类)	不同包下(子类)	不同包下(无关类)
		private 	Y		
		默认	        Y	        Y
		protected	Y		Y			Y
		public		Y		Y			Y				Y
```
  
**35.内部类访问特点**  
* 内部类可以直接访问外部类的成员，包括私有。  
* 外部类要访问内部类的成员，必须创建对象。  
* 外部类名.内部类名 对象名 = 外部类对象.内部类对象。  
   
**36.常见对象(String类的常见面试题)(掌握)**
* 1.判断定义为String类型的s1和s2是否相等
	* String s1 = "abc";
	* String s2 = "abc";
	* System.out.println(s1 == s2);       //true（常量池中没有这个字符串对象，就创建一个，如果有直接用即可）					
	* System.out.println(s1.equals(s2));  //true		
* 2.下面这句话在内存中创建了几个对象?
	* String s1 = new String("abc");	//创建两个对象，一个在常量池中，一个在堆内存中。
* 3.判断定义为String类型的s1和s2是否相等
	* String s1 = new String("abc");	//记录的是堆内存对象的地址值（栈变量方法，堆对象，方法区里有class和常量池）
	* String s2 = "abc";			//记录的是常量池中的地址值
	* System.out.println(s1 == s2);		//false
	* System.out.println(s1.equals(s2));	//true
* 4.判断定义为String类型的s1和s2是否相等
	* String s1 = "a" + "b" + "c"; 
	* String s2 = "abc";
	* System.out.println(s1 == s2);		//true,java中有常量优化机制
	* System.out.println(s1.equals(s2));	//true（因为String重写了里面的方法，比较的是里面的内容）
* 5.判断定义为String类型的s1和s2是否相等
	* String s1 = "ab";
	* String s2 = "abc";
	* String s3 = s1 + "c";			
	* System.out.println(s3 == s2);		//false
	* System.out.println(s3.equals(s2));	//true
* String面试题5:
![String面试题5](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/String%20interview%20question%205.png)  
  
**37.异常(finally关键字的面试题)**  
* A:面试题1
	* final,finally和finalize的区别
		* final,finally和finalize的区别
		* final可以修饰类,不能被继承
		* 修饰方法,不能被重写
		* 修饰变量,只能赋值一次
		* 
		* finally是try语句中的一个语句体,不能单独使用,用来释放资源
		* 
		* finalize是一个方法,当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法。
* B:面试题2
	* 如果catch里面有return语句，请问finally的代码还会执行吗?如果会，请问是在return前还是return后。（答案：后。catch里面先建立一个返回路径，finally执行后再返回值）
```
package com.heima.test;

public class Test1 {

	public static void main(String[] args) {
		Demo d = new Demo();
		System.out.println(d.method());
	}

}

class Demo {
	public int method() {
		int x = 10;
		try {
			x = 20;
			System.out.println(1/0);
			return x;
		} catch (Exception e) {
			x = 30;
			return x;
		} finally {
			x = 40;
			//return x;					千万不要在finally里面写返回语句,因为finally的作用是为了释放资源,是肯定会执行的
										//如果在这里面写返回语句,那么try和catch的结果都会被改变,所以这么写就是犯罪
		}
	}
}
//输出结果：40
```
  
**38.IO流(内存输出流之黑马面试题)(掌握)**  
* 定义一个文件输入流,调用read(byte[] b)方法,将a.txt文件中的内容打印出来(byte数组大小限制为5)  
```
  	FileInputStream fis = new FileInputStream("a.txt");			//创建字节输入流,关联a.txt
  	ByteArrayOutputStream baos = new ByteArrayOutputStream();		//创建内存输出流
  	byte[] arr = new byte[5];						//创建字节数组,大小为5
  	int len;
  	while((len = fis.read(arr)) != -1) {					//将文件上的数据读到字节数组中
  		baos.write(arr, 0, len);					//将字节数组的数据写到内存缓冲区中
  	}
  	System.out.println(baos);						//将内存缓冲区的内容转换为字符串打印
  	fis.close();
```
**39.逻辑运算符&&和&的区别)(掌握)**
* A:案例演示
	* &&和&的区别?
		* a:最终结果一样。
		* b:&&具有短路效果。左边是false，右边不执行。
		* 	&是无论左边是false还是true,右边都会执行
* B:同理||和|的区别?(和&&预&的区别一样)
* C:开发中常用谁?
	* &&,||,!
  
**40.return和break以及continue的区别?**
* return是结束方法  
* break是跳出循环  
* continue是终止本次循环继续下次循环  
  
**41.Java语言基础(Java中的内存分配以及栈和堆的区别)**  
.class文件运行在内存上,分为下面的几部分:  
* A:栈(掌握)
	* 存储局部变量 
	局部变量:定义在方法声明上和方法中的变量
* B:堆(掌握)
	* 存储new出来的数组或对象 
* C:方法区
	* .class和常量池 
* D:本地方法栈
	* 和系统相关 
* E:程序计数器
	* 给CPU使用
  
**42.面向对象(成员变量和局部变量的区别)(掌握)**  
* A:在类中的位置不同
	* 成员变量：在类中方法外
	* 局部变量：在方法定义中或者方法声明上
* B:在内存中的位置不同
	* 成员变量：在堆内存(成员变量属于对象,对象进堆内存)
	* 局部变量：在栈内存(局部变量属于方法,方法进栈内存)
* C:生命周期不同
	* 成员变量：随着对象的创建而存在，随着对象的消失而消失
	* 局部变量：随着方法的调用而存在，随着方法的调用完毕而消失
* D:初始化值不同
	* 成员变量：有默认初始化值
	* 局部变量：没有默认初始化值，必须定义，赋值，然后才能使用。
	
* 注意事项：
	* 局部变量名称可以和成员变量名称一样，在方法中使用的时候，采用的是就近原则。
	* 基本数据类型变量包括哪些:byte,short,int,long,float,double,boolean,char
	* 引用数据类型变量包括哪些:数组,类,接口,枚举
  
**43.面向对象(静态变量和成员变量的区别)(掌握)**
* **静态变量也叫类变量  成员变量也叫对象变量**
* A:所属不同
	* 静态变量属于类，所以也称为为类变量
	* 成员变量属于对象，所以也称为实例变量(对象变量)
* B:内存中位置不同
	* 静态变量存储于方法区的静态区
	* 成员变量存储于堆内存
* C:内存出现时间不同
	* 静态变量随着类的加载而加载，随着类的消失而消失
	* 成员变量随着对象的创建而存在，随着对象的消失而消失
* D:调用不同
	* 静态变量可以通过类名调用，也可以通过对象调用
	* 成员变量只能通过对 象名调用
  
**44.面向对象(this和super的区别和应用)(掌握)**
* A:this和super都代表什么
	* this:代表当前对象的引用,谁来调用我,我就代表谁
	* super:代表当前对象父类的引用
* B:this和super的使用区别
	* a:调用成员变量
		* this.成员变量 调用本类的成员变量,也可以调用父类的成员变量
		* super.成员变量 调用父类的成员变量
	* b:调用构造方法
		* this(...)	调用本类的构造方法
		* super(...)	调用父类的构造方法
	* c:调用成员方法
		* this.成员方法 调用本类的成员方法,也可以调用父类的方法
		* super.成员方法 调用父类的成员方法
  
**45.数组和集合的区别？**  
* 区别1:   
   * 数组既可以存储基本数据类型,又可以存储引用数据类型,基本数据类型存储的是值,引用数据类型存储的是地址值  
   * 集合只能存储引用数据类型(对象)集合中也可以存储基本数据类型,但是在存储的时候会自动装箱变成对象  
* 区别2:  
   * 数组长度是固定的,不能自动增长  
   * 集合的长度的是可变的,可以根据元素的增加而增长  
* 集合继承体系图：  
![集合体系图](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Set%20system%20diagram.png)  
  
**46.编译期异常和运行期异常的区别？**  
* 编译时异常:编译时异常也叫做未雨绸缪异常(老师自己定义的)。在编译某个程序的时候,有可能会有这样那样的事情发生,比如文件找不到,这样的异常就必须在编译的时候处理
如果不处理编译通不过  
  
* 运行时异常:就是程序员所犯得错误,需要回来修改代码  
  
**47.异常(throw的概述以及和throws的区别)**  
* a:throws  
   * 用在方法声明后面，跟的是异常类名  
   * 可以跟多个异常类名，用逗号隔开  
   * 表示抛出异常，由该方法的调用者来处理  
* b:throw  
   * 用在方法体内，跟的是异常对象名  
   * 只能抛出一个异常对象名  
   * 表示抛出异常，由方法体内的语句处理  
  
**48.异常(finally关键字的面试题)**  
* A:面试题1  
	* final,finally和finalize的区别  
		* final,finally和finalize的区别  
		* final可以修饰类,不能被继承  
		* 修饰方法,不能被重写  
		* 修饰变量,只能赋值一次  
		*   
		* finally是try语句中的一个语句体,不能单独使用,用来释放资源  
		*   
		* finalize是一个方法,当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法。  
* B:面试题2  
	* 如果catch里面有return语句，请问finally的代码还会执行吗?如果会，请问是在return前还是return后。（答案：后。catch里面先建立一个返回路径，finally执行后再返回值）  
  
**49.异常(异常的注意事项及如何使用异常处理)**  
* A:异常注意事项  
	* a:子类重写父类方法时，子类的方法必须抛出相同的异常或父类异常的子类。(父亲坏了,儿子不能比父亲更坏)  
	* b:如果父类抛出了多个异常,子类重写父类时,只能抛出相同的异常或者是他的子集,子类不能抛出父类没有的异常  
	* c:如果被重写的方法没有异常抛出,那么子类的方法绝对不可以抛出异常,如果子类方法内有异常发生,那么子类只能try,不能throws  
* B:如何使用异常处理  
	* 原则:如果该功能内部可以将问题处理,用try,如果处理不了,交由调用者处理,这是用throws  
	* 区别:  
		* 后续程序需要继续运行就try  
		* 后续程序不需要继续运行就throws  
		
	* 如果JDK没有提供对应的异常，需要自定义异常。  
  
















