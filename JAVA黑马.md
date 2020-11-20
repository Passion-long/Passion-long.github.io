### 01.09_Java语言基础(JRE和JDK的概述)(掌握)
* A:什么是JRE
	* 包括Java虚拟机(JVM Java Virtual Machine)和Java程序所需的核心类库等，如果想要运行一个开发好的Java程序，计算机中只需要安装JRE即可。
	* JRE:JVM+类库。 
* B:什么是JDK
	* JDK是提供给Java开发人员使用的，其中包含了java的开发工具，也包括了JRE。所以安装了JDK，就不用在单独安装JRE了。
	* 其中的开发工具：编译工具(javac.exe)  打包工具(jar.exe)等
 	* JDK:JRE+JAVA的开发工具。
* C:为什么JDK中包含一个JRE
	* 为什么JDK中包含一个JRE呢？
		* 开发完的程序，需要运行一下看看效果。
* D:JDK,JRE,JVM的作用和关系
### 01.17_Java语言基础(Path环境变量的配置方式2)(掌握)
* A:先配置JAVA_HOME
* B:再修改path
* C:最后说一下path是有先后顺序关系的
  
* path和classpath的区别
	* path配置的是可执行的文件.exe,配置后可以在不同的盘符下访问path路径下的可执行文件
	* classpath配置的java的类文件,就是.class文件
### 01.21_Java语言基础(关键字的概述和使用)(掌握)
* A:什么是关键字
	* 被Java语言赋予特定含义的单词 
* B:关键字的特点
	* 组成关键字的字母全部小写 
* C:常见关键字
	* public static void class等 
* D:关键字的注意事项
	* goto和const作为保留字存在,目前并不使用,类似Editplus这样的高级记事本,针对关键字有特殊的颜色标记，非常直观 
### 01.22_Java语言基础(标识符的概述和组成规则)(掌握)
* A:什么是标识符
	* 就是给类,接口,方法,变量等起名字时使用的字符序列 
* B:标识符的组成规则
	* 英文大小写字母
	* 数字字符
	* $和_ 
* C:标识符注意事项
	* 1,不能使用关键字
	* 2,不能数字开头 
### 01.23_Java语言基础(标识符中常见的命名规则)(了解)
* 见名知意
* A:包
	* 最好是域名倒过来,要求所有的字母小写 
* B:类或者接口
	* 如果是一个单词首字母大写
	* 如果是多个单词每个单词首字母大写(驼峰标识) 
* C:方法或者变量
	* 如果是一个单词全部小写
	* 如果是多个单词,从第二个单词首字母大写 
* D:常量
	* 如果是一个单词,所有字母大写
	* 如果是多个单词,所有的单词大写,用下划线区分每个单词 
## day03笔记
### 03.02_Java语言基础(逻辑运算符&&和&的区别)(掌握)
* A:案例演示
	* &&和&的区别?
		* a:最终结果一样。
		* b:&&具有短路效果。左边是false，右边不执行。
		* 	&是无论左边是false还是true,右边都会执行
* B:同理||和|的区别?(和&&预&的区别一样)
* C:开发中常用谁?
	* &&,||,!
### 03.03_Java语言基础(位运算符的基本用法1)(了解)
* A:位运算符有哪些
	* &,|,^,~ ,>>,>>>,<<,没有<<<
* B:案例演示
	* 位运算符的基本用法1
	
	* &,|,^,~ 的用法
	* &:有0则0
	* |:有1则1
	* ^:相同则0，不同则1
	* ~:按位取反
### 03.04_Java语言基础(位异或运算符的特点及面试题)(掌握)
* A:案例演示
	* 位异或运算符的特点
  
	* ^的特点：一个数据对另一个数据位异或两次，该数本身不变。  
    System.out.println(5 ^ 10 ^ 10);  //结果是5  
    System.out.println(5 ^ 10 ^ 5); //结果是10  
* B:面试题：
	* 请自己实现两个整数变量的交换  
  	  int x = 10;  
      int y = 5;  
      //不需要定义第三方变量,有可能超出int的取值范围.  
      x = x + y;  
      y = x - y;  
      x = x - y;  
      //不需要定义第三方变量,通过^来做.  
      x = x ^ y;  //10 ^ 5  
      y = x ^ y;  //10 ^ 5 ^ 5, y = 10  
      x = x ^ y;  //10 ^ 5 ^ 10, x = 5  
      
### 03.05_Java语言基础(位运算符的基本用法2及面试题)(了解)
* A:案例演示 >>,>>>,<<的用法:
```
  <<:左移	左边最高位丢弃，右边补齐0
  >>:右移	最高位是0，左边补齐0;最高为是1，左边补齐1
  >>>:无符号右移 无论最高位是0还是1，左边补齐0  

  //左移,向左移动几位就是乘以2的几次幂  
  System.out.println(12 << 1);		//24  
  System.out.println(12 << 2);		//48  
  //右移,向右移动几位就是除以2的几次幂  
  System.out.println(12 >> 1);  
  System.out.println(12 >> 2);  
  //最有效率的算出2 * 8的结果  
  System.out.println(2 << 3);  
```
    
### 03.21_Java语言基础(选择结构switch语句的注意事项)(掌握)
* A:案例演示
	* a:case后面只能是常量，不能是变量，而且，多个case后面的值不能出现相同的
	* b:default可以省略吗?
		* 可以省略，但是不建议，因为它的作用是对不正确的情况给出提示。
		* 特殊情况：
			* case就可以把值固定。
			* A,B,C,D
	* c:break可以省略吗?
		* 最后一个可以省略,其他最好不要省略
		* 会出现一个现象：case穿透。
		* 最终我们建议不要省略
	* d:default一定要在最后吗?
		* 不是，可以在任意位置。但是建议在最后。
	* e:switch语句的结束条件
		* a:遇到break就结束了
		* b:执行到switch的右大括号就结束了
    
    //B:看程序写结果：

		int x = 2;
		int y = 3;
		switch(x){
			default:
				y++;
			case 3:
				y++;
			case 4:
				y++;
		}
		System.out.println("y="+y);//结果是6,碰到}才结束.  
    
### 04.13_Java语言基础(循环结构九九乘法表)
* A:案例演示
	* 需求：在控制台输出九九乘法表。
* B:代码优化
* 
		注意：
		'\x' x表示任意，\是转义符号,这种做法叫转移字符。放在单引号可以,放在双引号也可以.  
		
		'\t'	tab键的位置
		'\r'	回车
		'\n'	换行
		'\"'
		'\''
### 04.16_Java语言基础(控制跳转语句标号)  
* 标号:标记某个循环对其控制  
```
  outer: for (int i = 1;i <= 10 ;i++ ) {		//outer就是标号,只要是合法的标识符即可,例如可以是a.  
    System.out.println("i = " + i);  
    inner: for (int j = 1;j <= 10 ;j++ ) {  
      System.out.println("j = " + j);  
      break outer;//用于跳出外层循环  
    }  
  }  
```
* 标号组成规则:其实就是合法的标识符  
```
  下面这个语句是正确的.http:是标号,//后面是注释
  System.out.println("大家好");
  http://www.heima.com
  System.out.println("才是真的好");
  最终输出结果是:
  大家好
  才是真的好
```
### 04.18_Java语言基础(控制跳转语句return语句)
* A:return的作用
	* 返回
	* 其实它的作用不是结束循环的，而是结束方法的。
* B:案例演示
	* return和break以及continue的区别?
	* return是结束方法
	* break是跳出循环
	* continue是终止本次循环继续下次循环
### 04.25_Java语言基础(方法重载概述和基本使用)
* A:方法重载概述
	* 求和案例
		* 2个整数
		* 3个整数
		* 4个整数
* B:方法重载：
	* 在同一个类中，方法名相同，参数列表不同。与返回值类型无关。
	
	* 参数列表不同：
		* A:参数个数不同
		* B:参数类型不同
		* C:参数的顺序不同(算重载,但是在开发中不用)
### 05.03_Java语言基础(Java中的内存分配以及栈和堆的区别)  
.class文件运行在内存上,分为下面的几部分:  
* A:栈(掌握)
	* 存储局部变量 
	局部变量:定义在方法声明上和方法中的变量
* B:堆(掌握)
	* 存储new出来的数组或对象 
* C:方法区
	* 面向对象部分讲解(相当于我们的代码仓库,源文件->字节码文件(.class)->内存(方法区)) 
* D:本地方法区
	* 和系统相关 
* E:寄存器
	* 给CPU使用
### 05.07_Java语言基础(数组的初始化静态初始化及内存图)  
* A:静态初始化的格式：
	* 格式：数据类型[] 数组名 = new 数据类型[]{元素1,元素2,…};
	* 简化格式：数据类型[] 数组名 = {元素1,元素2,…};  
```
//数据类型[] 数组名 = new 数据类型[]{元素1,元素2,…};
//int[] arr = new int[5]{11,22,33,44,55};	//不允许动静结合
int[] arr2 = {11,22,33,44,55};			//静态初始化的简写形式

//int[] arr;					//声明数组引用,无错误.
//arr = new int[]{11,22,33,44,55};

//int[] arr2;
//arr2 = {11,22,33,44,55};			//简写形式声明和赋值在同一行,有错误.
```
### 05.11_Java语言基础(数组的操作3翻转)  
```
/*
数组元素反转
1,明确返回值类型void
2,明确参数列表int[] arr
*/

public static void reverseArray(int[] arr) {
	for (int i = 0;i < arr.length / 2 ; i++) {
		//arr[0]和arr[arr.length-1-0]交换
		//arr[1]和arr[arr.length-1-1]交换
		//arr[2]和arr[arr.lentth-1-2]
		//...

		int temp = arr[i];
		arr[i] = arr[arr.length-1-i];
		arr[arr.length-1-i] = temp;
	}
}
```
### 05.11_Java语言基础(二维数组概述和格式1的讲解)  
```
/*
* A:二维数组概述
* B:二维数组格式1
	* int[][] arr = new int[3][2]; 
* C:二维数组格式1的解释
* D:注意事项
	* a:以下格式也可以表示二维数组
		* 1:数据类型 数组名[][] = new 数据类型[m][n];
		* 2:数据类型[] 数组名[] = new 数据类型[m][n];
	* B:注意下面定义的区别
	* 
			int x;
			int y;
			int x,y;
			
			int[] x;
			int[] y[];
			
			int[] x,y[];	x是一维数组,y是二维数组
*/
```
### 05.20_Java语言基础(Java中的参数传递问题及图解)  
```
/*
基本数据类型的值传递,不改变原值,因为调用后就会弹栈,局部变量随之消失
引用数据类型的值传递,改变原值,因为即使方法弹栈,但是堆内存数组对象还在,可以通过地址继续访问

Java中到底是传值还是传址
1,既是传值,也是传地址,基本数据类型传递的值,引用数据类型传递的地址
2,java中只有传值,因为地址值也是值(出去面试都说这种,支持者是高司令(java之父))
*/
```
* 基本数据类型的值传递:  
![基本数据类型的值传递](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Value%20transfer%20of%20basic%20data%20type.png)  
  
* 引用数据类型的值传递:  
![引用数据类型的值传递](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Value%20transfer%20of%20reference%20data%20type.png)  

### 06.01_面向对象(面向对象思想概述)(了解)  
* D:面向对象思想特点
	* a:是一种更符合我们思想习惯的思想
	* b:可以将复杂的事情简单化
	* c:将我们从执行者变成了指挥者
* G:面向对象特征
	* 封装(encapsulation)
	* 继承(inheritance)
	* 多态(polymorphism)

### 06.07_面向对象(一个对象的内存图)(掌握)  
* A:画图演示
	* 一个对象  
![引用数据类型的值传递](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Memory%20graph%20of%20one%20object.png)  
  
### 06.10_面向对象(成员变量和局部变量的区别)(掌握)  
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
### 06.12_面向对象(匿名对象的概述和应用)(掌握)  
* A:什么是匿名对象
	* 没有名字的对象 
* B:匿名对象应用场景
	* a:调用方法，仅仅只调用一次的时候。
		* 那么，这种匿名调用有什么好处吗?
			* 节省代码 
		* 注意：调用多次的时候，不适合。匿名对象调用完毕就是垃圾。可以被垃圾回收器回收。
	* b:匿名对象可以作为实际参数传递
* C:案例演示
	* 匿名对象应用场景
```
class Demo2_Car {
	public static void main(String[] args) {
		/*Car c1 = new Car();			//创建有名字的对象
		c1.run();
		c1.run();

		new Car().run();			//匿名对象调用方法
		new Car().run();	*/		//匿名对象只适合对方法的一次调用,因为调用多次就会产生多个对象,不如用有名字的对象	
	
		//匿名对象是否可以调用属性并赋值?有什么意义?
		/*
		匿名对象可以调用属性,但是没有意义,因为调用后就变成垃圾
		如果需要赋值还是用有名字对象
		*/
		new Car().color = "red";
		new Car().num = 8;
		new Car().run();
	}
}

class Car {
	String color;			//颜色
	int num;			//轮胎数

	public void run() {
		System.out.println(color + "..." + num);
	}
}
```
### 06.13_面向对象(封装的概述)(掌握)
* A:封装概述
	* 是指隐藏对象的属性和实现细节，仅对外提供公共访问方式。

* B:封装好处
	* 隐藏实现细节，提供公共的访问方式
	* 提高了代码的复用性
	* 提高安全性。
* C:封装原则
	* 将不需要对外提供的内容都隐藏起来。
	* 把属性隐藏，提供公共方法对其访问。
### 06.14_面向对象(private关键字的概述和特点)(掌握)
* A:人类赋值年龄的问题
* B:private关键字特点
	* a:是一个权限修饰符
	* b:可以修饰成员变量和成员方法
	* c:被其修饰的成员只能在本类中被访问
* C:案例演示
	* 封装和private的应用：
	* A:把成员变量用private修饰
	* B:提供对应的getXxx()和setXxx()方法//这个最重要了,取值;有getXxx()和setXxx()方法的叫java bean类  
	* private仅仅是封装的一种体现形式,不能说封装就是私有	
### 06.15_面向对象(this关键字的概述和应用)(掌握)
* A:this关键字特点
	* 代表当前对象的引用 
* B:案例演示
	* this的应用场景
	* 用来区分成员变量和局部变量重名
### 07.01_面向对象(构造方法Constructor概述和格式)(掌握)
* A:构造方法概述和作用
	* 给对象的数据(属性)进行初始化
* B:构造方法格式特点
	* a:方法名与类名相同(大小也要与类名一致)
	* b:没有返回值类型，连void都没有
	* c:没有具体的返回值return;构造方法也是有return语句的,格式是return;;
	* d:构造方法不能用对象调用.
### 07.02_面向对象(构造方法的重载及注意事项)(掌握)
* A:案例演示
	* 构造方法的重载
	* 重载:方法名相同,与返回值类型无关(构造方法没有返回值),只看参数列表
* B:构造方法注意事项
	* a:如果我们没有给出构造方法，系统将自动提供一个无参构造方法。
	* b:如果我们给出了构造方法，系统将不再提供默认的无参构造方法。
		* 注意：这个时候，如果我们还想使用无参构造方法，就必须自己给出。建议永远自己给出无参构造方法
### 07.06_面向对象(创建一个对象的步骤)(掌握)
* A:画图演示
	* 画图说明一个对象的创建过程做了哪些事情?
	* Student s = new Student();
	* 1,Student.class加载进内存
	* 2,声明一个Student类型引用s
	* 3,在堆内存创建对象,
	* 4,给对象中属性默认初始化值
	* 5,属性进行显示初始化
	* 6,构造方法进栈,对对象中的属性赋值,构造方法弹栈
	* 7,将对象的地址值赋值给s
![创建一个对象的步骤](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/To%20create%20an%20object.png)  
### 07.10_面向对象(static关键字的特点)(掌握)
* A:static关键字的特点
	* a:随着类的加载而加载
	* b:优先于对象存在
	* c:被类的所有对象共享
		* 举例：咱们班级的学生应该共用同一个班级编号。
		* 其实这个特点也是在告诉我们什么时候使用静态?
			* 如果某个成员变量是被所有对象共享的，那么它就应该定义为静态的。
		* 举例：
			* 饮水机(用静态修饰)
			* 水杯(不能用静态修饰)
			* 共性用静态,特性用非静态
	* d:可以通过类名调用
		* 其实它本身也可以通过对象名调用。
		* **推荐**使用类名调用。
		* 静态修饰的内容一般我们称其为：与类相关的，类成员
* B:案例演示
	* static关键字的特点
### 07.11_面向对象(static的注意事项)(掌握)
* A:static的注意事项
	* a:在静态方法中是没有this关键字的
		* 如何理解呢?
			* 静态是随着类的加载而加载，this是随着对象的创建而存在。
			* 静态比对象先存在。
	* b:静态方法只能访问静态的成员变量和静态的成员方法
		* 静态方法：
			* 成员变量：只能访问静态变量
			* 成员方法：只能访问静态成员方法
		* 非静态方法：
			* 成员变量：可以是静态的，也可以是非静态的
			* 成员方法：可是是静态的成员方法，也可以是非静态的成员方法。
		* 简单记：
			* 静态只能访问静态。(**总结:类不能访问实例,或者叫做静态不能访问非静态.**)
* B:案例演示
	* static的注意事项
### 07.12_面向对象(静态变量和成员变量的区别)(掌握)
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
### 07.13_面向对象(main方法的格式详细解释)(了解)
* A:格式
	* public static void main(String[] args) {}
* B:针对格式的解释
	* public 被jvm调用，访问权限足够大。
	* static 被jvm调用，不用创建对象，直接类名访问
	* void被jvm调用，不需要给jvm返回值
	* main 一个通用的名称，虽然不是关键字，但是被jvm识别
	* String[] args 以前用于接收键盘录入的
* C:演示案例
	* 通过args接收键盘例如数据
```
class Demo3_Main {
	public static void main(String[] args) {			
		System.out.println(args.length);
		for (int i = 0;i < args.length ;i++ ) {
			System.out.println(args[i]);
		}
	}
}

cmd输入:java Demo3_Main haha xixi hehe
cmd输出:
3
haha
xixi
hehe
```
### 07.14_面向对象(工具类中使用静态)(了解)
* A:制作一个工具类
	* ArrayTool
	* 1,获取最大值
	* 2,数组的遍历
	* 3,数组的反转
* 如果一个类中所有的方法都是静态的,需要再多做一步,**私有构造方法**,目的是不让其他类创建本类对象,直接用类名.调用即可
### 07.15_面向对象(说明书的制作过程)(了解)
* A:对工具类加入文档注释
* B:通过javadoc命令生成说明书
	* @author(提取作者内容)
	* @version(提取版本内容)
	* javadoc -d 指定的文件目录 -author -version ArrayTool.java  (类必须是public的)
	* @param 参数名称//形式参数的变量名称
	* @return 函数运行完返回的数据
### 08.01_面向对象(代码块的概述和分类)(了解)(面试的时候会问,开发不用或者很少用)
* A:代码块概述
	* 在Java中，使用{}括起来的代码被称为代码块。
* B:代码块分类
	* 根据其位置和声明的不同，可以分为局部代码块，构造代码块，静态代码块，同步代码块(多线程讲解)。
* C:常见代码块的应用
	* a:局部代码块 
		* 在方法中出现；限定变量生命周期，及早释放，提高内存利用率
	* b:构造代码块 **(初始化块)**
		* 在类中方法外出现；多个构造方法方法中相同的代码存放到一起，每次调用构造都执行，并且在构造方法前执行
	* c:静态代码块 
		* 在类中方法外出现，并加上static修饰；用于给类进行初始化，在加载的时候就执行，并且只执行一次。
		* 一般用于加载驱动
		* 静态代码块优先于主方法执行
###08.02_面向对象(代码块的面试题)(掌握)
* A:看程序写结果
* 
		class Student {
			static {//只执行一次
				System.out.println("Student 静态代码块");
			}
			
			{
				System.out.println("Student 构造代码块");
			}
			
			public Student() {
				System.out.println("Student 构造方法");
			}
		}
	
		class Demo2_Student {
			static {
				System.out.println("Demo2_Student静态代码块");
			}
			
			public static void main(String[] args) {
				System.out.println("我是main方法");
				
				Student s1 = new Student();
				Student s2 = new Student();
			}
		}
```
输出结果:
Demo2_Student静态代码块
我是main方法
Student 静态代码块
Student 构造代码块
Student 构造方法
Student 构造代码块
Student 构造方法
```
### 08.04_面向对象(继承的好处和弊端)(掌握)
* A:继承的好处
	* a:提高了代码的复用性
	* b:提高了代码的维护性
	* c:让类与类之间产生了关系，是多态的前提
* B:继承的弊端
	* 类的耦合性增强了。
	
	* 开发的原则：高内聚，低耦合。
	* 耦合：类与类的关系
	* 内聚：就是自己完成某件事情的能力
### 08.05_面向对象(Java中类的继承特点)(掌握)
* A:Java中类的继承特点
	* a:Java只支持单继承，不支持多继承。(一个儿子只能有一个爹)(多继承有安全隐患)
		* 有些语言是支持多继承，格式：extends 类1,类2,...
	* b:Java支持多层继承(继承体系)
* B:案例演示
	* Java中类的继承特点
		* 如果想用这个体系的所有功能用最底层的类创建对象
		* 如果想看这个体系的共性功能,看最顶层的类 
### 08.06_面向对象(继承的注意事项和什么时候使用继承)(掌握)
* A:继承的注意事项
	* a:子类只能继承父类所有非私有的成员(成员方法和成员变量)
	* b:子类不能继承父类的构造方法，但是可以通过super(马上讲)关键字去访问父类构造方法。
	* c:不要为了部分功能而去继承
	* 项目经理 姓名 工号 工资 奖金
	* 程序员	姓名 工号 工资
* B:什么时候使用继承
	* 继承其实体现的是一种关系："is a"。
		Person
			Student
			Teacher
		水果
			苹果
			香蕉
			橘子
			
	采用假设法。
		如果有两个类A,B。只有他们符合A是B的一种，或者B是A的一种，就可以考虑使用继承。
### 08.07_面向对象(继承中成员变量的关系)(掌握)
* A:案例演示
	* a:不同名的变量
	* b:同名的变量(就近原则)
		* 子父类出现同名的变量只是在讲课中举例子有,在开发中是不会出现这种情况的
		* 子类继承父类就是为了使用父类的成员,那么如果定义了同名的成员变量没有意义了
### 08.08_面向对象(this和super的区别和应用)(掌握)
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
### 08.09_面向对象(继承中构造方法的关系)(掌握)
* A:案例演示
	* 子类中所有的构造方法默认都会访问父类中空参数的构造方法
* B:为什么呢?
	* 因为子类会继承父类中的数据，可能还会使用父类的数据。
	* 所以，子类初始化之前，一定要先完成父类数据的初始化。
	
	* 其实：
		* 每一个构造方法的第一条语句默认都是：super() Object类最顶层的父类。
### 08.10_面向对象(继承中构造方法的注意事项)(掌握)
* A:案例演示
	* 父类没有无参构造方法,子类怎么办?
	* super解决(调用父类的构造方法)
	* this解决(调用子类的构造方法)
* B:注意事项
	* super(…)或者this(….)必须出现在构造方法的第一条语句上
### 08.11_面向对象(继承中的面试题)(掌握)
* 这个题很经典
```
class Test2_Extends {
	public static void main(String[] args) {
		Zi z = new Zi();
	}
	/*
	1,jvm调用了main方法,main进栈
	2,遇到Zi z = new Zi();会先将Fu.class和Zi.class分别加载进内存,再创建对象,当Fu.class加载进内存
	父类的静态代码块会随着Fu.class一起加载,当Zi.class加载进内存,子类的静态代码块会随着Zi.class一起加载
	第一个输出,静态代码块Fu,第二个输出静态代码块Zi
	3,走Zi类的构造方法,因为java中是分层初始化的,先初始化父类,再初始化子类,所以先走的父类构造,但是在执行
	父类构造时,发现父类有构造代码块,构造代码块是优先于构造方法执行的所以
	第三个输出构造代码块Fu,第四个输出构造方法Fu
	4,Fu类初始化结束,子类初始化,第五个输出的是构造代码块Zi,构造方法Zi
	*/
}
class Fu {
	static {
		System.out.println("静态代码块Fu");//输出顺序:1
	}

	{
		System.out.println("构造代码块Fu");//3
	}

	public Fu() {
		System.out.println("构造方法Fu");//4
	}
}

class Zi extends Fu {
	static {
		System.out.println("静态代码块Zi");//2
	}

	{
		System.out.println("构造代码块Zi");//5
	}

	public Zi() {
		System.out.println("构造方法Zi");//6
	}
}
```
### 08.12_面向对象(继承中成员方法关系)(掌握)
* A:案例演示
	* a:不同名的方法
	* b:同名的方法(叫做重写,也可以使用super调用父类同名的成员方法)

### 08.13_面向对象(方法重写概述及其应用)(掌握)
* A:什么是方法重写
	* 重写:子父类出现了一模一样的方法(注意:返回值类型可以是子父类,这个我们学完面向对象讲) 
* B:方法重写的应用：
	* 当子类需要父类的功能，而功能主体子类有自己特有内容时，可以重写父类中的方法。这样，即沿袭了父类的功能，又定义了子类特有的内容。
* C:Java中的类名可以是中文的,因为Java中.class文件编码是Unicode编码,Unicode囊括了世界上所有的语言.
* D:案例演示
	* a:定义一个手机类。
```
class Demo7_Phone {
	public static void main(String[] args) {
		Ios8 i = new Ios8();
		i.siri();
		i.call();
	}
}
class Ios7 {
	public void call() {
		System.out.println("打电话");
	}

	public void siri() {
		System.out.println("speak English");
	}
}
class Ios8 extends Ios7 {
	public void siri() {
		
		System.out.println("说中文");
		super.siri();//注意:这里不是构造方法,super可以放在第二句;但是在构造方法里面,super必须放在第一句.
	}
}
输出结果:
说中文
speak English
打电话
```
### 08.14_面向对象(方法重写的注意事项)(掌握)
* A:方法重写注意事项
	* a:父类中私有方法不能被重写
		* 因为父类私有方法子类根本就无法继承
	* b:子类重写父类方法时，访问权限不能更低
		* 最好就一致
	* c:父类静态方法，子类也必须通过静态方法进行重写
		* 其实这个算不上方法重写，但是现象确实如此，至于为什么算不上方法重写，多态中我会讲解(静态只能覆盖静态)
		
	* 子类重写父类方法的时候，最好声明一模一样。
* B:案例演示
	* 方法重写注意事项

### 08.15_面向对象(方法重写的面试题)(掌握)
* A:方法重写的面试题
	* Override和Overload的区别?Overload能改变返回值类型吗?
	* overload可以改变返回值类型,只看参数列表
	* 方法重写：子类中出现了和父类中方法声明一模一样的方法。与返回值类型有关,返回值是一致(或者是子父类)的
	
	* 方法重载：本类中出现的方法名一样，参数列表不同的方法。与返回值类型无关。

	* 子类对象调用方法的时候：
		* 先找子类本身，再找父类。
### 08.19_面向对象(final关键字修饰类,方法以及变量的特点)(掌握)
* A:final概述
	* final是最终的 
* B:final修饰特点
	* 修饰类，类不能被继承
	* 修饰变量，变量就变成了常量，只能被赋值一次
	* 修饰方法，方法不能被重写
* C:案例演示
	* final修饰特点
* D:常量命名规范,如果是一个单词,所有字母大写,如果是多个单词,每个单词都大写,中间用下划线隔开.
* E:final修饰变量叫做常量,一般会与public static共用
### 08.20_面向对象(final关键字修饰局部变量)(掌握)
* A:案例演示
	* 方法内部或者方法声明上都演示一下(了解)

	* 基本类型，是值不能被改变
	* 引用类型，是地址值不能被改变,对象中的属性可以改变
### 08.21_面向对象(final修饰变量的初始化时机)(掌握)
* A:final修饰变量的初始化时机
	* 成员变量的默认初始化值是无效值
	* 在对象构造完毕前即可
```
class Demo2_Final {
	public static void main(String[] args) {
		final int num = 10;
		//num = 20;
		System.out.println(num);

		final Person p = new Person("张三",23);
		//p = new Person("李四",24);
		p.setName("李四");
		p.setAge(24);

		System.out.println(p.getName() + "..." + p.getAge());

		method(10);
		method(20);
	}

	public static void method(final int x) {
		System.out.println(x);
	}
}
```
### 09.01_面向对象(多态的概述及其代码体现)
* A:多态(polymorphic)概述
	* 事物存在的多种形态 
* B:多态前提
	* a:要有继承关系。
	* b:要有方法重写。
	* c:要有父类引用指向子类对象。
### 09.02_面向对象(多态中的成员访问特点)
```
class Demo2_Polymorphic {
	public static void main(String[] args) {
		/*Father f = new Son();					//父类引用指向子类对象
		System.out.println(f.num);//输出10

		Son s = new Son();
		System.out.println(s.num);//输出20*/

		Father f = new Son();
		//f.print();//输出son
		f.method();//输出father static method		      //相当于是Father.method()
	}
}
/*
成员变量
编译看左边(父类),运行看左边(父类);"编译看左边的意思就是,如果左边没有对应的变量或者方法,则编译不通过,就会报错."
成员方法
编译看左边(父类)，运行看右边(子类)。动态绑定
静态方法
编译看左边(父类)，运行看左边(父类)。
(静态和类相关，算不上重写，所以，访问还是左边的)
只有非静态的成员方法,编译看左边,运行看右边 
*/
class Father {
	int num = 10;
	public void print() {
		System.out.println("father");
	}

	public static void method() {
		System.out.println("father static method");
	}
}

class Son extends Father {
	int num = 20;

	public void print() {
		System.out.println("son");
	}

	public static void method() {
		System.out.println("son static method");
	}
}
```
* 多态中的成员变量:
![多态中的成员变量](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Member%20variables%20in%20polymorphism.png)  
* 多态中的成员方法:
![多态中的成员方法](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Member%20methods%20in%20polymorphism.png)  

### 09.07_面向对象(多态的好处和弊端)
* A:多态的好处
	* a:提高了代码的维护性(继承保证)
	* b:提高了代码的扩展性(由多态保证)
* B:案例演示
	* 多态的好处
	* 可以当作形式参数,可以接收任意子类对象
* C:多态的弊端
	* **不能使用子类的特有属性和行为。**
* D:案例演示
	method(Animal a)
	method(Cat c)
* //Animal a = new Cat();		开发的时候很少在创建对象的时候用父类引用指向子类对象,直接创建子类对象更方便,可以使用子类中的特有属性和行为,当做参数的时候用多态最好,因为扩展性强.

### 09.08_面向对象(多态中的题目分析题)
* A:看下面程序是否有问题，如果没有，说出结果
* 
		class Fu {
			public void show() {
				System.out.println("fu show");
			}
		}
	
		class Zi extends Fu {
			public void show() {
				System.out.println("zi show");
			}
	
			public void method() {
				System.out.println("zi method");
			}
		}
	
		class Test1Demo {
			public static void main(String[] args) {
				Fu f = new Zi();
				f.method();
				f.show();
			}
		}
* B:看下面程序是否有问题，如果没有，说出结果
* 
		class A {
			public void show() {
				show2();
			}
			public void show2() {
				System.out.println("我");
			}
		}
		class B extends A {
			public void show2() {
				System.out.println("爱");
			}
		}
		class C extends B {
			public void show() {
				super.show();
			}
			public void show2() {
				System.out.println("你");
			}
		}
		public class Test2DuoTai {
			public static void main(String[] args) {
				A a = new B();
				a.show();
				
				B b = new C();
				b.show();
			}
		}
### 09.09_面向对象(抽象类的概述及其特点)
* A:抽象类概述
	* 抽象就是看不懂的 
* B:抽象类特点
	* a:抽象类和抽象方法必须用abstract关键字修饰
		* abstract class 类名 {}
		* public abstract void eat();
	* b:抽象类不一定有抽象方法，有抽象方法的类一定是抽象类或者是接口
	* c:抽象类不能实例化那么，抽象类如何实例化呢?
		* 按照多态的方式，由具体的子类实例化。其实这也是多态的一种，抽象类多态。
	* d:抽象类的子类
		* 要么是抽象类
		* 要么重写抽象类中的所有抽象方法
* C:案例演示
	* 抽象类特点B:抽象类特点
	* a:抽象类和抽象方法必须用abstract关键字修饰
		* abstract class 类名 {}
		* public abstract void eat();
	* b:抽象类不一定有抽象方法，有抽象方法的类一定是抽象类或者是接口
	* c:抽象类不能实例化那么，抽象类如何实例化呢?
		* 按照多态的方式，由具体的子类实例化。其实这也是多态的一种，抽象类多态。
	* d:**抽象类的子类**
		* **要么是抽象类**
		* **要么重写抽象类中的所有抽象方法**
### 09.10_面向对象(抽象类的成员特点)
* A:抽象类的成员特点
	* a:成员变量：既可以是变量，也可以是常量。abstract是否可以修饰成员变量?不能修饰成员变量
	* b:构造方法：有。
		* 用于子类访问父类数据的初始化。
	* c:成员方法：既可以是抽象的，也可以是非抽象的。
* B:案例演示
	* 抽象类的成员特点
* C:抽象类的成员方法特性：
	* a:抽象方法 强制要求子类做的事情。
	* b:非抽象方法 子类继承的事情，提高代码复用性。
### 09.15_面向对象(抽象类中的面试题)
* A:面试题1
	* 一个抽象类如果没有抽象方法，可不可以定义为抽象类?如果可以，有什么意义?
	* 可以
	* 这么做目的只有一个,就是不让其他类创建本类对象,交给子类完成
* B:面试题2
	* abstract不能和哪些关键字共存
```
class Demo4_Abstract {
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}
/*
* A:面试题1
	* 一个抽象类如果没有抽象方法，可不可以定义为抽象类?如果可以，有什么意义?
	* 可以
	* 这么做目的只有一个,就是不让其他类创建本类对象,交给子类完成
* B:面试题2
	* abstract不能和哪些关键字共存
	abstract和static
	被abstract修饰的方法没有方法体
	被static修饰的可以用类名.调用,但是类名.调用抽象方法是没有意义的
	abstract和final
	被abstract修饰的方法强制子类重写
	被final修饰的不让子类重写,所以他俩是矛盾
	abstract和private
	被abstract修饰的是为了让子类看到并强制重写
	被private修饰不让子类访问,所以他俩是矛盾的
*/

abstract class Demo {
	//public static abstract void print();		//错误: 非法的修饰符组合: abstract和static
	//public final abstract void print();		//错误: 非法的修饰符组合: abstract和final
	private abstract void print();				//错误: 非法的修饰符组合: abstract和private
}
```
### 09.16_面向对象(接口的概述及其特点)
* A:接口概述
	* 从狭义的角度讲就是指java中的interface
	* 从广义的角度讲对外提供规则的都是接口 
* B:接口特点
	* a:接口用关键字interface表示	
		* interface 接口名 {}
	* b:类实现接口用implements表示
		* class 类名 implements 接口名 {}
	* c:接口不能实例化
		* 那么，接口如何实例化呢?
		* 按照多态的方式来实例化。
	* d:接口的子类
		* a:可以是抽象类。但是意义不大。
		* b:可以是具体类。要重写接口中的所有抽象方法。(推荐方案)
	* e:接口中的方法都是抽象的。
	
* C:案例演示
	* 接口特点
### 09.17_面向对象(接口的成员特点)
* A:接口成员特点
	* 成员变量；只能是常量，并且是静态的并公共的。
		* 默认修饰符：public static final。他们三个是没有顺序的，可以是：public final static；public static final；static public final；static final public；final public static；final static public。 建议：自己手动给出。
	* 构造方法：接口没有构造方法。
	* 成员方法：只能是抽象方法。
		* 默认修饰符：public abstract。建议：自己手动给出。
* B:案例演示
	* 接口成员特点
```
interface Inter {
	public static final int num = 10;
	//public Inter(){}					接口中没有构造方法

	/*public void print() {				接口中不能定义非抽象方法
	
	}*/

	public abstract void print();
}
class Demo /*extends Object*/ implements Inter {	//一个类不写继承任何类,默认继承Object类
	public void print() {
		//num = 20;
		System.out.println(num);
	}

	public Demo() {
		super();//默认继承Object，所以可以使用super()
	}

}
```
### 09.18_面向对象(类与类,类与接口,接口与接口的关系)
* A:类与类,类与接口,接口与接口的关系
	* a:类与类：
		* 继承关系,只能单继承,可以多层继承。
	* b:类与接口：
		* 实现关系,可以单实现,也可以多实现。
		* 并且还可以在继承一个类的同时实现多个接口。
	* c:接口与接口：
		* 继承关系,可以单继承,也可以多继承。
* B:案例演示
	* 类与类,类与接口,接口与接口的关系
```
class Demo3_Interface {
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}

interface InterA {
	public abstract void printA();
}

interface InterB {
	public abstract void printB();
}

interface InterC extends InterB,InterA {
}
//class Demo implements InterA,implements InterB {		//这么做不允许是非法的
class Demo extends Object implements InterA,InterB {		//这样写可以，implements只能写一次
	public void printA() {
		System.out.println("printA");
	}

	public void printB() {
		System.out.println("printB");
	}
}
```
### 09.19_面向对象(抽象类和接口的区别)
* A:成员区别
	* 抽象类：
		* 成员变量：可以变量，也可以常量
		* 构造方法：有
		* 成员方法：可以抽象，也可以非抽象
	* 接口：
		* 成员变量：只可以常量
		* 成员方法：只可以抽象
		
* B:关系区别
	* 类与类
		* 继承，单继承
	* 类与接口
		* 实现，单实现，多实现
	* 接口与接口
		* 继承，单继承，多继承
		
* C:设计理念区别
	* 抽象类 被继承体现的是：”is a”的关系。抽象类中定义的是该继承体系的**共性功能。**
	* 接口 被实现体现的是：”like a”的关系。接口中定义的是该继承体系的**扩展功能。**
### 10.05_面向对象(import关键字的概述和使用)(掌握)
* A:案例演示
	* 为什么要有import
		* 其实就是让有包的类对调用者可见,不用写全类名了 
* B:导包格式
	* import 包名;
	* 注意：
	* 这种方式导入是到类的名称。
	* 虽然可以最后写*，但是不建议。
* C:package,import,class有没有顺序关系(面试题)
	* 有，先是package，后是import，最后是class。
### 10.06_面向对象(四种权限修饰符的测试)(掌握)
* A:案例演示
	* 四种权限修饰符
* B:结论
```
* 
				本类	 同一个包下(子类和无关类)	不同包下(子类)	不同包下(无关类)
		private 	Y		
		默认	        Y	        Y
		protected	Y		Y			Y
		public		Y		Y			Y				Y
```
### 10.08_面向对象(内部类概述和访问特点)(了解)
* A:内部类概述
* B:内部类访问特点
	* a:内部类可以直接访问外部类的成员，包括私有。
	* b:外部类要访问内部类的成员，必须创建对象。
	* 外部类名.内部类名 对象名 = 外部类对象.内部类对象;
* C:案例演示
	* 内部类极其访问特点
```
class Demo1_InnerClass {
	public static void main(String[] args) {
		//外部类名.内部类名 = 外部类对象.内部类对象
		Outer.Inner oi = new Outer().new Inner();			//创建内部类对象
		oi.method();
	}
}

class Outer {
	private int num = 10;
	class Inner {
		public void method() {
			System.out.println(num);
		}
	}
}
```
### 10.11_面向对象(成员内部类的面试题)(掌握)
class Test1_InnerClass {
	public static void main(String[] args) {
		Outer.Inner oi = new Outer().new Inner();
		oi.show();
	}
}
//要求：使用已知的变量，在控制台输出30，20，10。
//内部类之所以能获取到外部类的成员,是因为他能获取到外部类的引用外部类名.this
class Outer {
	public int num = 10;
	class Inner {
		public int num = 20;
		public void show() {
			int num = 30;
			System.out.println(num);
			System.out.println(this.num);
			//System.out.println(new Outer().num); //使用对象来访问成员变量
			System.out.println(Outer.this.num);
		}
	}
}
### 10.12_面向对象(局部内部类访问局部变量的问题)(掌握)
* A:案例演示
	* 局部内部类访问局部变量必须用final修饰
	* 局部内部类在访问他所在方法中的局部变量必须用final修饰,为什么?
		因为当调用这个方法时,局部变量如果没有用final修饰,他的生命周期和方法的生命周期是一样的,当方法弹栈,这个局部变量也会消失,那么如果局部内部类对象还没有马上消失想用这个局部变量,就没有了,如果用final修饰会在类加载的时候进入常量池,即使方法弹栈,常量池的常量还在,也可以继续使用

		但是jdk1.8取消了这个事情,所以我认为这是个bug,虽然取消,如果在书写代码时候,没有手动添加,系统底层也会默给你final
```
class Demo1_InnerClass {
	public static void main(String[] args) {
		Outer o = new Outer();
		o.method();
	}
}
//局部内部类
class Outer {
	public void method() {
		int num = 10; //Demo1_InnerClass.java:13: 错误: 从内部类中访问本地变量num; 需要被声明为最终类型
		class Inner {
			public void print() {
				System.out.println(num);
			}
		}

		Inner i = new Inner();
		i.print();
	}

	/*public void run() {
		Inner i = new Inner();				//局部内部类,只能在其所在的方法中访问
		i.print();
	}*/
}
```
### 10.13_面向对象(匿名内部类的格式和理解)
* A:匿名内部类
	* 就是内部类的简化写法。
* B:前提：存在一个类或者接口
	* 这里的类可以是具体类也可以是抽象类。
* C:格式：
* 
		new 类名或者接口名(){
			重写方法;
		}
* D:本质是什么呢?
	* 是一个继承了该类或者实现了该接口的子类匿名对象。
* E:案例演示
	* 按照要求来一个匿名内部类
```
class Demo1_NoNameInnerClass {
	public static void main(String[] args) {
		Outer o = new Outer();
		o.method();
	}
}

interface Inter {
	public void print();
}

class Outer {
	class Inner implements Inter {
		public void print() {
			System.out.println("print");
		}
	}

	public void method(){
		//Inner i = new Inner();
		//i.print();
		//new Inner().print();
		//Inter i = new Inner();			//父类引用指向子类对象
		
		new Inter() {						//实现Inter接口
			public void print() {			//重写抽象方法
				System.out.println("print");
			}
		}.print();
	}
}
```
### 10.14_面向对象(匿名内部类重写多个方法调用)
* A:案例演示
	* 匿名内部类的方法调用
```
class Demo2_NoNameInnerClass {
	public static void main(String[] args) {
		Outer o = new Outer();
		o.method();
	}
}

interface Inter {
	public void show1();
	public void show2();
}
//匿名内部类只针对重写一个方法时候使用
class Outer {
	public void method() {
		Inter i = new Inter(){
			public void show1() {
				System.out.println("show1");
			}

			public void show2() {
				System.out.println("show2");
			}

			/*public void show3() {
				System.out.println("show3");
			}*/
		};

		i.show1();
		i.show2();
		//i.show3();						//匿名内部类是不能向下转型的,因为没有子类类名
	}
}
```

### 10.16_面向对象(匿名内部类的面试题)
* A:面试题
```
// abstract和static不能一块用
class Test2_NoNameInnerClass {
	public static void main (String[] args) {
		//Outer.method().show();// 链式编程，每次调用方法后还能继续调用方法，证明调用方法返回的是对象。
		Inter i = Outer.method();
		i.show();
	}
}
//按照要求，补齐代码
interface Inter {
	void show();
}

class Outer {
	//补齐代码
	public static Inter method () {
		return new Inter() {
			@java.lang.Override
			public void show() {
				System.out.println("HelloWorld");
			}
		}
	}
}
//要求在控制台输出代码
```
### 11.05_Java开发工具(Eclipse中内容辅助键的使用)(掌握)
* A:Alt+/ 起提示作用
* B:main+alt+/,syso+alt+/,给出其他提示
* C:补充输出语句,选中需要输出的部分,alt+/选择最后一项即可
* C:定义自己的alt + /
	* windows--perference-Java-Editor-Templates--New
### 11.06_Java开发工具(Eclipse中快捷键的使用)(掌握)
* A:新建 ctrl + n
* B:格式化  ctrl+shift+f
* C:导入包  ctrl+shift+o 
* D:注释  ctrl+/,ctrl+shift+/,ctrl+shift+\
* E:代码上下移动 选中代码alt+上/下箭头
* F:查看源码  选中类名(F3或者Ctrl+鼠标点击)
* G:查找具体的类 ctrl + shift + t
* H:查找具体类的具体方法 ctrl + o
* I:给建议 ctrl+1,根据右边生成左边的数据类型,生成方法
* J:删除代码 ctrl + d
* K:抽取方法alt + shift + m 
* L:改名alt + shift + r 
* M:向下复制一行Ctrl + alt + 下键

### 11.07_Java开发工具(Eclipse中如何提高开发效率)(掌握)
* alt + shift + s
* A:自动生成构造方法
* B:自动生成get/set方法
```
package com.heima.bean;

public class Person extends Object{

	private String name;
	private int age;

	public Person() {   					//alt + shift + s 再 + c 生成空参构造
		super();
	}

	public Person(String name, int age) {  	//alt + shift + s 再 + o 根据本地字段(成员变量)生成有参构造
		super();
		this.name = name;
		this.age = age;
	}

	public String getName() {				//alt + shift + s 再 + r 生成get和set方法
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

}

```
### 11.17_常见对象(Object类的getClass()方法)(在反射的时候掌握)
* A:案例演示
	* public final Class getClass()
	* a:返回此 Object 的运行时类。
	* b:可以通过Class类中的一个方法，获取对象的真实类的全名称。	
		* public String getName()
```
package com.heima.object;

import com.heima.bean.Student;

public class Demo2_GetClass {

	public static void main(String[] args) {
		Student s = new Student("张三", 23);
		// Class clazz = new Class();

		Class clazz = s.getClass();//获取该对象的字节码文件
		String name = clazz.getName();//获取类的名称（反射的时候还要详细讲这块）
		System.out.println(name);//输出：com.heima.bean.Student
	}
}
```
### 11.18_常见对象(Object类的toString()方法)(掌握)
* A:案例演示
	* public String toString()
	* a:返回该对象的字符串表示。
* 
		
		public Stirng toString() {
			return name + "," + age;
		}
	* b:它的值等于： 
		* getClass().getName() + "@" + Integer.toHexString(hashCode()) 
	* c:由于默认情况下的数据对我们来说没有意义，一般建议重写该方法。
* B:最终版
	* 自动生成
* C:如果直接打印对象的引用，会默认调用toString方法
### 11.19_常见对象(Object类的equals()方法)(掌握)
* A:案例演示
	* a:指示其他某个对象是否与此对象“相等”。 
	* b:默认情况下比较的是对象的引用是否相同。
	* c:由于比较对象的引用没有意义，一般建议重写该方法。因为在开发中我们通常比较的是对象中的属性值，我们认为 相同属性是同一个对象，这样我们就需要重写equals方法。
### 11.20_常见对象(==号和equals方法的区别)(掌握)
* ==是一个比较运算符号,既可以比较基本数据类型,也可以比较引用数据类型,基本数据类型比较的是值,引用数据类型比较的是地址值
* equals方法是一个方法,只能比较引用数据类型,所有的对象都会继承Object类中的方法,如果没有重写Object类中的equals方法,equals方法和==号比较引用数据类型无区别,重写后的equals方法比较的是对象中的属性
### 12.04_常见对象(String类的构造方法)(掌握)
* A:常见构造方法
	* public String():空构造
	* public String(byte[] bytes):把字节数组转成字符串
	* public String(byte[] bytes,int index,int length):把字节数组的一部分转成字符串
	* public String(char[] value):把字符数组转成字符串
	* public String(char[] value,int index,int count):把字符数组的一部分转成字符串
	* public String(String original):把字符串常量值转成字符串
* B:案例演示	
	* 演示String类的常见构造方法
### 12.05_常见对象(String类的常见面试题)(掌握)
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
### 12.06_常见对象(String类的判断功能)(掌握)
* A:String类的判断功能
	* boolean equals(Object obj):比较字符串的内容是否相同,区分大小写
	* boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
	* boolean contains(String str):判断大字符串中是否包含小字符串
	* boolean startsWith(String str):判断字符串是否以某个指定的字符串开头
	* boolean endsWith(String str):判断字符串是否以某个指定的字符串结尾
	* boolean isEmpty():判断字符串是否为空。
	* ""和null的区别：
		* ""是字符串常量,同时也是一个String类的对象,既然是对象当然可以调用String类中的方法
		* null是空常量,不能调用任何的方法,否则会出现空指针异常,null常量可以给任意的引用数据类型赋值
```
	public static void main(String[] args) {
		String s1 = "heima";
		String s2 = "";
		String s3 = null;
		
		System.out.println(s1.isEmpty());	//false
		System.out.println(s2.isEmpty());	//true
		System.out.println(s3.isEmpty());	//java.lang.NullPointerException
	}
```
### 12.08_常见对象(String类的获取功能)(掌握)
* A:String类的获取功能
	* int length():获取字符串的长度。
	* char charAt(int index):获取指定索引位置的字符
	* int indexOf(int ch):返回指定字符在此字符串中第一次出现处的索引。
	* int indexOf(String str):返回指定字符串在此字符串中第一次出现处的索引。
	* int indexOf(int ch,int fromIndex):返回指定字符在此字符串中从指定位置后第一次出现处的索引。
	* int indexOf(String str,int fromIndex):返回指定字符串在此字符串中从指定位置后第一次出现处的索引。包含头，不包含尾。
	* lastIndexOf
	* String substring(int start):从指定位置开始截取字符串,默认到末尾。
	* String substring(int start,int end):从指定位置开始到指定位置结束截取字符串。
* B:String类的转换功能
	* byte[] getBytes():把字符串转换为字节数组。
	* char[] toCharArray():把字符串转换为字符数组。
	* static String valueOf(char[] chs):把字符数组转成字符串。底层是由String类的构造方法完成的。
	* static String valueOf(int i):把int类型的数据转成字符串。
		* 注意：String类的valueOf方法可以把任意类型的数据转成字符串。


	* String toLowerCase():把字符串转成小写。(了解)
	* String toUpperCase():把字符串转成大写。
	* String concat(String str):把字符串拼接。用+拼接字符串更强大,可以用字符串与任意类型相加；concat方法调用的和传入的都必须是字符串。
### 12.12_常见对象(按要求转换字符)(链式编程掌握)
* A:案例演示
	* 需求：把一个字符串的首字母转成大写，其余为小写。(只考虑英文大小写字母字符)
```
package com.heima.test;

public class Test4 {
	public static void main(String[] args) {
		String s = "woaiHEImaniaima";
		String s2 = s.substring(0, 1).toUpperCase().concat(s.substring(1).toLowerCase());
		System.out.println(s2);
	}
}

```
### 12.14_常见对象(String类的其他功能)
* A:String的替换功能及案例演示
	* String replace(char old,char new)
	* String replace(String old,String new)
* B:String的去除字符串两空格及案例演示
	* String trim()
* C:String的按字典顺序比较两个字符串及案例演示
	* int compareTo(String str)(暂时不用掌握)
	* int compareToIgnoreCase(String str)(了解)
### 13.1_常见对象(StringBuffer和String的相互转换)
```
public class Demo6_StringBuffer {

	/**
	 * * A:String -- StringBuffer
		* a:通过构造方法
		* b:通过append()方法
	* B:StringBuffer -- String
		* a:通过构造方法
		* b:通过toString()方法
		* c:通过subString(0,length);

	 */
	public static void main(String[] args) {
		//demo1();
		StringBuffer sb = new StringBuffer("heima");
		
		String s1 = new String(sb);				//通过构造将StringBuffer转换为String
		System.out.println(s1);
		
		String s2 = sb.toString();				//通过toString方法将StringBuffer转换为String
		System.out.println(s2);
		
		String s3 = sb.substring(0, sb.length());		//通过截取子字符串将StringBuffer转换为String
		System.out.println(s3);
	}

	private static void demo1() {
		StringBuffer sb1 = new StringBuffer("heima");		//通过构造方法将字符串转换为StringBuffer对象
		System.out.println(sb1);
		
		StringBuffer sb2 = new StringBuffer();
		sb2.append("heima");					//通过append方法将字符串转换为StringBuffer对象
		System.out.println(sb2);
	}

}
```
### 13.2_常见对象(StringBuffer和StringBuilder的区别)
* A:面试题
	* StringBuffer是jdk1.0版本的，是线程安全的，效率低
	* StringBuilder是jdk1.5版本的，是线程不安全的，效率高
	* String是一个不可变的字符序列
	* StringBuffer，StringBuilder是可变的字符序列
### 13.3_常见对象(String和StringBuilder分别作为参数传递)
* A:形式参数问题
	* String作为参数传递
	* StringBuffer作为参数传递 
* B:案例演示
	* 基本数据类型的值传递,不改变其值
	* 引用数据类型的值传递,改变其值
	* String类虽然是引用数据类型,但是他当作参数传递时和基本数据类型是一样的
```
package com.heima.stringbuffer;

public class Demo7_StringBuffer {
	public static void main(String[] args) {
		String s = "heima";
		System.out.println(s);
		change(s);
		System.out.println(s);
		
		
		System.out.println("---------------------");
		StringBuffer sb = new StringBuffer();
		sb.append("heima");
		System.out.println(sb);
		change(sb);
		System.out.println(sb);
	}

	public static void change(StringBuffer sb) {
		sb.append("itcast");
	}

	public static void change(String s) {
		s += "itcast";
	}

}
输出结果：
heima
heima
---------------------
heima
heimaitcast
```
### 13.16_常见对象(冒泡排序和选择排序)
```
package com.heima.array;

public class Demo1_Array {

	/**
	 * * A:案例演示
	* 数组高级冒泡排序代码
	* 数组高级选择排序代码
	 */
	public static void main(String[] args) {
		int[] arr = {24, 69, 80, 57, 13};
		bubbleSort(arr);
		//selectSort(arr);
		print(arr);
	}
	
	/*
	 * 冒泡排序
	 * 1,返回值类型,void
	 * 2,参数列表,int[] arr
	 * 
	 * 	第一次:arr[0]与arr[1],arr[1]与arr[2],arr[2]与arr[3],arr[3]与arr[4]比较4次
		第二次:arr[0]与arr[1],arr[1]与arr[2],arr[2]与arr[3]比较3次
		第三次:arr[0]与arr[1],arr[1]与arr[2]比较2次
		第四次:arr[0]与arr[1]比较1次
	 */
	
	public static void bubbleSort(int[] arr) {
		for (int i = 0; i < arr.length - 1; i++) {				//外循环只需要比较arr.length-1次就可以了
			for (int j = 0; j < arr.length - 1 - i; j++) {		//-1为了防止索引越界,-i为了提高效率
				if(arr[j] > arr[j+1]) {
					/*int temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j+1] = temp;*/
					swap(arr,j,j+1);
				}
			}
		}
	}
	
	/*
	 * 打印数组
	 * 1,返回值类型void
	 * 2,参数列表int[]arr
	 */
	
	public static void print(int[] arr) {
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + " ");
		}
	}
	
	/*
	 * 选择排序
	 * 1,返回值类型void
	 * 2,参数列表int[] arr
	 * 
	 * 	第一次:arr[0]分别与arr[1-4]比较,比较4次
		第二次:arr[1]分别与arr[2-4]比较,比较3次
		第三次:arr[2]分别与arr[3-4]比较,比较2次
		第四次:arr[3]与arr[4]比较,比较1次
	 */
	
	public static void selectSort(int[] arr) {
		for (int i = 0; i < arr.length - 1; i++) {				//只需要比较arr.length-1次
			for (int j = i + 1; j < arr.length; j++) {
				if(arr[i] > arr[j]) {
					/*int temp = arr[i];
					arr[i] = arr[j];
					arr[j] = temp;*/
					swap(arr,i,j);
				}
			}
		}
	}
	
	/*
	 * 换位操作
	 * 1,返回值类型,void
	 * 2,参数列表int[] arr.int i,int j
	 * 
	 * 如果某个方法,只针对本类使用,不想让其他类使用就可以定义成私有的
	 */
	
	private static void swap(int[] arr,int i,int j) {
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}
}

```
### 13.19_常见对象(基本类型包装类的概述)
* A:为什么会有基本类型包装类
	* 将基本数据类型封装成对象的好处在于可以在对象中定义更多的功能方法操作该数据。
* B:常用操作
	* 常用的操作之一：用于基本数据类型与字符串之间的转换。
* C:基本类型和包装类的对应
* 
		byte 			Byte
		short			Short
		int			Integer
		long			Long
		float			Float
		double			Double
		char			Character
		boolean			Boolean
```
package com.heima.wrapclass;
public class Demo1_Integer {
	public static void main(String[] args) {
		System.out.println(Integer.toBinaryString(60));//转换为二进制
		System.out.println(Integer.toOctalString(60));//转换为八进制
		System.out.println(Integer.toHexString(60));//转换为十六进制
	}
}
```
### 13.21_常见对象(String和int类型的相互转换)
* A:int -- String
	* a:和""进行拼接
	* b:public static String valueOf(int i)
	* c:int -- Integer -- String(Integer类的toString方法())
	* d:public static String toString(int i)(Integer类的静态方法)
* B:String -- int
	* a:String -- Integer -- int
		* public static int parseInt(String s)
基本数据类型包装类有八种,其中七种都有parseXxx的方法,可以将这七种的字符串表现形式转换成基本数据类型,char的包装类Character中没有pareseXxx的方法,字符串到字符的转换通过toCharArray()就可以把字符串转换为字符数组.
```
private static void demo1() {
	//int ----> String int转换成String
	int i = 100;
	String s1 = i + "";				//推荐用
	String s2 = String.valueOf(i);			//推荐用

	Integer i2 = new Integer(i);
	String s3 = i2.toString();

	String s4 = Integer.toString(i);
	System.out.println(s1);

	//String----> int String 转换int
	String s = "200";
	Integer i3 = new Integer(s);
	int i4 = i3.intValue();				//将Integer转换成了int数

	int i5 = Integer.parseInt(s);			//将String转换为int,推荐用这种
}
```
### 13.21_常见对象(JDK5的自动装箱和自动拆箱)
* A:JDK5的新特性
	* 自动装箱：把基本类型转换为包装类类型
	* 自动拆箱：把包装类类型转换为基本类型
* B:案例演示
	* JDK5的新特性自动装箱和拆箱

	* Integer ii = 100;
	* ii += 200;
* C:注意事项
	* 在使用时，Integer  x = null;代码就会出现NullPointerException。
	* 建议先判断是否为null，然后再使用。
* D:Integer和String使用new一个对象再判断时，都重写了equals方法，因此比较的都是里面的内容是不是相等，而不是判断地址是不是相等。而使用Integer/String i = 97/"abc"时，这个时候因为都在常量池中，所以使用==和equals都是相等的。
* E:-128到127是byte的取值范围,如果在这个取值范围内,自动装箱就不会新创建对象,而是从常量池中获取,如果超过了byte取值范围就会再新创建对象.
### 14.09_常见对象(Pattern和Matcher的概述)
* A:Pattern和Matcher的概述
* B:模式和匹配器的典型调用顺序
	* 通过JDK提供的API，查看Pattern类的说明
	* 典型的调用顺序是: 
```
Pattern p = Pattern.compile("a*b");//获取到正则表达式
Matcher m = p.matcher("aaaaab");//获取匹配器
boolean b = m.matches();//看是否能匹配,匹配就返回true
```
### 14.11_常见对象(Math类概述和方法使用)
* A:Math类概述
	* Math 类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。 
* B:成员方法
	* public static int abs(int a)
	* public static double ceil(double a)//ceil:天花板.向上取整，但是结果是一个double值。
	* public static double floor(double a)//floor:地板.向下取整，但是结果是一个double值。
	* public static int max(int a,int b) min自学
	* public static double pow(double a,double b)
	* public static double random()
	* public static int round(float a) //四舍五入
	* public static double sqrt(double a)
### 14.12_常见对象(Random类的概述和方法使用)
* A:Random类的概述
	* 此类用于产生随机数如果用相同的种子创建两个 Random 实例，
	* 则对每个实例进行相同的方法调用序列，它们将生成并返回相同的数字序列。
* B:构造方法
	* public Random()
	* public Random(long seed)//seed固定后，下次还是生成一样的随机数
* C:成员方法
	* public int nextInt()
	* public int nextInt(int n)(重点掌握)//生成0到n范围内的随机数，包含0不包含n
### 14.13_常见对象(System类的概述和方法使用)
* A:System类的概述
	* System 类包含一些有用的类字段和方法。它不能被实例化。 
* B:成员方法
	* public static void gc()
	* public static void exit(int status)
	* public static long currentTimeMillis()
	* pubiic static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length) 
* C:案例演示
	* System类的成员方法使用
```
package com.heima.otherclass;

public class Demo3_System {

	public static void main(String[] args) {
		//demo1();
		//demo2();
		//demo3();
		
		int[] src = {11,22,33,44,55};
		int[] dest = new int[8];
		for (int i = 0; i < dest.length; i++) {
			System.out.println(dest[i]);
		}
		
		System.out.println("--------------------------");
		System.arraycopy(src, 0, dest, 0, src.length);		//将数组内容拷贝
		
		for (int i = 0; i < dest.length; i++) {
			System.out.println(dest[i]);
		}
	}

	public static void demo3() {
		long start = System.currentTimeMillis();		//1秒等于1000毫秒
		for(int i = 0; i < 1000; i++) {
			System.out.println("*");
		}
		long end = System.currentTimeMillis();			//获取当前时间的毫秒值
		
		System.out.println(end - start);
	}

	public static void demo2() {
		System.exit(1);							//非0状态是异常终止,退出jvm
		System.out.println("11111111111");
	}

	public static void demo1() {
		for(int i = 0; i < 100; i++) {
			new Demo();
			System.gc();						//运行垃圾回收器,相当于呼喊保洁阿姨
		}
	}

}

class Demo {									//在一个源文件中不允许定义两个用public修饰的类

	@Override
	public void finalize() {					//finalize()是Object中的方法，通过System.gc调用
		System.out.println("垃圾被清扫了");
	}							
	
}
```
### 14.14_常见对象(BigInteger类的概述和方法使用)
* A:BigInteger的概述
	* 可以让超过Integer范围内的数据进行运算
* B:构造方法
	* public BigInteger(String val)
* C:成员方法
	* public BigInteger add(BigInteger val)
	* public BigInteger subtract(BigInteger val)
	* public BigInteger multiply(BigInteger val)
	* public BigInteger divide(BigInteger val)
	* public BigInteger[] divideAndRemainder(BigInteger val)//取除数和余数
### 14.15_常见对象(BigDecimal类的概述和方法使用)
* A:BigDecimal的概述
	* 由于在运算的时候，float类型和double很容易丢失精度，演示案例。
	* 所以，为了能精确的表示、计算浮点数，Java提供了BigDecimal

	* 不可变的、任意精度的有符号十进制数。
* B:构造方法
	* public BigDecimal(String val)
* C:成员方法
	* public BigDecimal add(BigDecimal augend)
	* public BigDecimal subtract(BigDecimal subtrahend)
	* public BigDecimal multiply(BigDecimal multiplicand)
	* public BigDecimal divide(BigDecimal divisor)
* D:案例演示
	* BigDecimal类的构造方法和成员方法使用
```
package com.heima.otherclass;

import java.math.BigDecimal;

public class Demo5_BigDecimal {

	public static void main(String[] args) {
		//System.out.println(2.0 - 1.1);
		/*BigDecimal bd1 = new BigDecimal(2.0);		//这种方式在开发中不推荐,因为不够精确
		BigDecimal bd2 = new BigDecimal(1.1);
		
		System.out.println(bd1.subtract(bd2));*/
		
		/*BigDecimal bd1 = new BigDecimal("2.0");	//通过构造中传入字符串的方式,开发时推荐
		BigDecimal bd2 = new BigDecimal("1.1");
		
		System.out.println(bd1.subtract(bd2));*/
		
		BigDecimal bd1 = BigDecimal.valueOf(2.0);	//这种方式在开发中也是推荐的
		BigDecimal bd2 = BigDecimal.valueOf(1.1);
		
		System.out.println(bd1.subtract(bd2));
	}

}
```
### 14.16_常见对象(Date类的概述和方法使用)(掌握)
* A:Date类的概述
	* 类 Date 表示特定的瞬间，精确到毫秒。 
* B:构造方法
	* public Date()
	* public Date(long date)
* C:成员方法
	* public long getTime()
	* public void setTime(long time)
```
package com.heima.otherclass;

import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class Demo7_SimpleDateFormat {
l
	public static void main(String[] args) throws ParseException {
		//demo1();
		//demo2();
		//demo3();
		
		//将时间字符串转换成日期对象
		String str = "2000年08月08日 08:08:08";
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
		Date d = sdf.parse(str);						//将时间字符串转换成日期对象
		System.out.println(d);
	}

	public static void demo3() {
		Date d = new Date();							//获取当前时间对象
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");//创建日期格式化类对象
		System.out.println(sdf.format(d));				//将日期对象转换为字符串
	}

	public static void demo2() {
		Date d = new Date();							//获取当前时间对象
		SimpleDateFormat sdf = new SimpleDateFormat();	//创建日期格式化类对象
		System.out.println(sdf.format(d));	 			//88-6-6 下午9:31
	}

	public static void demo1() {
		//DateFormat df = new DateFormat();				//DateFormat是抽象类,不允许实例化
		//DateFormat df1 = new SimpleDateFormat();
		DateFormat df1 = DateFormat.getDateInstance();	//相当于父类引用指向子类对象,右边的方法返回一个子类对象
	}

}
```
### 14.19_常见对象(Calendar类的概述和获取日期的方法)(掌握)
* A:Calendar类的概述
	* Calendar 类是一个抽象类，它为特定瞬间与一组诸如 YEAR、MONTH、DAY_OF_MONTH、HOUR 等日历字段之间的转换提供了一些方法，并为操作日历字段（例如获得下星期的日期）提供了一些方法。
* B:成员方法
	* public static Calendar getInstance()
	* public int get(int field)


### 14.20_常见对象(Calendar类的add()和set()方法)(掌握)
* A:成员方法
	* public void add(int field,int amount)
	* public final void set(int year,int month,int date)
* B:案例演示
	* Calendar类的成员方法使用
### 14.21_常见对象(如何获取任意年份是平年还是闰年)(掌握)
* A:案例演示
	* 需求：键盘录入任意一个年份，判断该年是闰年还是平年
```
import java.util.Scanner;
public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNext()) {
            int i = scanner.readInt();
            System.out.println(((i % 4 == 0 && i % 100 != 0) || i % 400 == 0) ? "闰年" : "平年" );
        }
    }
}
```
### 15.02_集合框架(集合的由来及集合继承体系图)
* A:集合的由来
	* 数组长度是固定,当添加的元素超过了数组的长度时需要对数组重新定义,太麻烦,java内部给我们提供了集合类,能存储任意对象,长度是可以改变的,随着元素的增加而增加,随着元素的减少而减少 
* B:数组和集合的区别
	* 区别1 : 
		* 数组既可以存储基本数据类型,又可以存储引用数据类型,基本数据类型存储的是值,引用数据类型存储的是地址值
		* 集合只能存储引用数据类型(对象)集合中也可以存储基本数据类型,但是在存储的时候会自动装箱变成对象
	* 区别2:
		* 数组长度是固定的,不能自动增长
		* 集合的长度的是可变的,可以根据元素的增加而增长
* C:数组和集合什么时候用
		* 1,如果元素个数是固定的推荐用数组
		* 2,如果元素个数不是固定的推荐用集合
* D:集合继承体系图：
![集合体系图](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Set%20system%20diagram.png)  
### 15.03_集合框架(Collection集合的基本功能测试)
* A:案例演示	
* 
		基本功能演示
		
		boolean add(E e)
		boolean remove(Object o)
		void clear()
		boolean contains(Object o)
		boolean isEmpty()
		int size()

* B:注意:
* 
		collectionXxx.java使用了未经检查或不安全的操作.
		注意:要了解详细信息,请使用 -Xlint:unchecked重新编译.
		java编译器认为该程序存在安全隐患
		温馨提示:这不是编译失败,所以先不用理会,等学了泛型你就知道了
		
		add方法如果是List集合一直都返回true,因为List集合中是可以存储重复元素的
		如果是Set集合当存储重复元素的时候,就会返回false
		
		ArrayList的父类的父类重写toString方法,所以在打印对象的引用的时候,输出的结果不是Object类中toString的结果
* C:@SuppressWarnings({ "rawtypes", "unchecked" })//保持原始类型，不检查。
### 15.04_集合框架(集合的遍历之集合转数组遍历)
* A:集合的遍历
	* 其实就是依次获取集合中的每一个元素。
* B:案例演示
	* 把集合转成数组，可以实现集合的遍历
	* toArray()
	*
		
			Collection coll = new ArrayList();
			coll.add(new Student("张三",23));		//Object obj = new Student("张三",23);
			coll.add(new Student("李四",24));
			coll.add(new Student("王五",25));
			coll.add(new Student("赵六",26));
			
			Object[] arr = coll.toArray();				//将集合转换成数组
			for (int i = 0; i < arr.length; i++) {
				Student s = (Student)arr[i];			//强转成Student
				System.out.println(s.getName() + "," + s.getAge());
			}
### 15.05_集合框架(Collection集合的带All功能测试)
* A:案例演示
* 
		带All的功能演示
		
		boolean addAll(Collection c)//将c2中的每一个元素添加到c1中
		boolean removeAll(Collection c)//删除的是交集
		boolean containsAll(Collection c)//判断调用的集合是否包含传入的集合
		boolean retainAll(Collection c)//取交集,取交集,如果调用的集合改变就返回true,如果调用的集合不变就返回false
* alt + shift + r改名
```
c1.addAll(c2);							//将c2中的每一个元素添加到c1中
c1.add(c2);							//将c2看成一个对象添加到c1中
```
### 15.06_集合框架(集合的遍历之迭代器遍历)
* A:迭代器概述
	* 集合是用来存储元素,存储的元素需要查看,那么就需要迭代(遍历) 
* B:案例演示
	* 迭代器的使用
		
			Collection c = new ArrayList();
			c.add("a");
			c.add("b");
			c.add("c");
			c.add("d");
			
			Iterator it = c.iterator();						//获取迭代器的引用
			while(it.hasNext()) {							//集合中的迭代方法(遍历)
				System.out.println(it.next());
			}
### 15.07_集合框架(Collection存储自定义对象并遍历)
* A:案例演示
	* Collection存储自定义对象并用迭代器遍历
	* 
			Collection c = new ArrayList();
			
			c.add(new Student("张三",23));
			c.add(new Student("李四",24));
			c.add(new Student("王五",25));
			c.add(new Student("赵六",26));
			c.add(new Student("赵六",26));
			
			for(Iterator it = c.iterator();it.hasNext();) {
				Student s = (Student)it.next();						//向下转型
				System.out.println(s.getName() + "," + s.getAge());	//获取对象中的姓名和年龄
			}
			System.out.println("------------------------------");
			Iterator it = c.iterator();								//获取迭代器
			while(it.hasNext()) {									//判断集合中是否有元素
				//System.out.println(((Student)(it.next())).getName() + "," + ((Student)(it.next())).getAge());
				Student s = (Student)it.next();						//向下转型
				System.out.println(s.getName() + "," + s.getAge());	//获取对象中的姓名和年龄
			}
### 15.08_集合框架(迭代器的原理及源码解析)(了解)
* A:迭代器原理
	* 迭代器原理:迭代器是对集合进行遍历,而每一个集合内部的存储结构都是不同的,所以每一个集合存和取都是不一样,那么就需要在每一个类中定义hasNext()和next()方法,这样做是可以的,但是会让整个集合体系过于臃肿,迭代器是将这样的方法向上抽取出接口,然后在每个类的内部,定义自己迭代方式,这样做的好处有二,第一规定了整个集合体系的遍历方式都是hasNext()和next()方法,第二,代码有底层内部实现,使用者不用管怎么实现的,会用即可 
* B:迭代器源码解析
	* 1,在eclipse中ctrl + shift + t找到ArrayList类
	* 2,ctrl+o查找iterator()方法
	* 3,查看返回值类型是new Itr(),说明Itr这个类实现Iterator接口
	* 4,查找Itr这个内部类,发现重写了Iterator中的所有抽象方法 
### 15.09_集合框架(List集合的特有功能概述和测试)
* A:List集合的特有功能概述（E就是Object）
	* void add(int index,E element)
	* E remove(int index)
	* E get(int index)
	* E set(int index,E element)
### 15.10_集合框架(List集合存储学生对象并遍历)
* A:案例演示
	* 通过size()和get()方法结合使用遍历。

			List list = new ArrayList();
			list.add(new Student("张三", 18));
			list.add(new Student("李四", 18));
			list.add(new Student("王五", 18));
			list.add(new Student("赵六", 18));
			
			for(int i = 0; i < list.size(); i++) {
				Student s = (Student)list.get(i);
				System.out.println(s.getName() + "," + s.getAge());
			}
### 15.11_集合框架(并发修改异常产生的原因及解决方案)
* A:案例演示
	* 需求：我有一个集合，请问，我想判断里面有没有"world"这个元素，如果有，我就添加一个"javaee"元素，请写代码实现。

			List list = new ArrayList();
			list.add("a");
			list.add("b");
			list.add("world");
			list.add("d");
			list.add("e");
			
			/*Iterator it = list.iterator();
			while(it.hasNext()) {
				String str = (String)it.next();
				if(str.equals("world")) {
					list.add("javaee");			//这里会抛出ConcurrentModificationException并发修改异常
				}
			}*/
* B:ConcurrentModificationException出现
	* 迭代器遍历，集合修改集合
* C:解决方案
	* a:迭代器迭代元素，迭代器修改元素(ListIterator的特有功能add)
	* b:集合遍历元素，集合修改元素

			ListIterator lit = list.listIterator();		//如果想在遍历的过程中添加元素,可以用ListIterator中的add方法
			while(lit.hasNext()) {
				String str = (String)lit.next();
				if(str.equals("world")) {
					lit.add("javaee");	
					//list.add("javaee");
				}
			}
### 15.12_集合框架(ListIterator)(了解)
* boolean hasNext()是否有下一个
* boolean hasPrevious()是否有前一个
* Object next()返回下一个元素
* Object previous();返回上一个元素
### 15.13_集合框架(Vector的特有功能)(了解)
* A:Vector类概述（Vector已经被ArrayList替代了）
* B:Vector类特有功能
	* public void addElement(E obj)
	* public E elementAt(int index)
	* public Enumeration elements()
* C:案例演示	
	* Vector的迭代

			Vector v = new Vector();				//创建集合对象,List的子类
			v.addElement("a");
			v.addElement("b");
			v.addElement("c");
			v.addElement("d");
			
			//Vector迭代
			Enumeration en = v.elements();			//获取枚举
			while(en.hasMoreElements()) {			//判断集合中是否有元素
				System.out.println(en.nextElement());//获取集合中的元素
			}
### 15.14_集合框架(数据结构之数组和链表)
* A:数组
	* 查询快修改也快
	* 增删慢
* B:链表
	* 查询慢,修改也慢
	* 增删快
### 15.15_集合框架(List的三个子类的特点)
* A:List的三个子类的特点
* 
		ArrayList:
			底层数据结构是数组，查询快，增删慢。
			线程不安全，效率高。
		Vector:
			底层数据结构是数组，查询快，增删慢。
			线程安全，效率低。
		Vector相对ArrayList查询慢(线程安全的)
		Vector相对LinkedList增删慢(数组结构)
		LinkedList:
			底层数据结构是链表，查询慢，增删快。
			线程不安全，效率高。

		Vector和ArrayList的区别
			Vector是线程安全的,效率低
			ArrayList是线程不安全的,效率高
		共同点:都是数组实现的
		ArrayList和LinkedList的区别
			ArrayList底层是数组结果,查询和修改快
			LinkedList底层是链表结构的,增和删比较快,查询和修改比较慢
		共同点:都是线程不安全的
* B:List有三个儿子，我们到底使用谁呢?
		查询多用ArrayList
		增删多用LinkedList
		如果都多ArrayList
### 16.01_集合框架(去除ArrayList中重复字符串元素方式)(掌握)
* A:案例演示
	* 需求：ArrayList去除集合中字符串的重复值(字符串的内容相同)
	* 思路：创建新集合方式

			/**
			 *  A:案例演示
			 * 需求：ArrayList去除集合中字符串的重复值(字符串的内容相同)
			 * 思路：创建新集合方式
			 */
			public static void main(String[] args) {
				ArrayList list = new ArrayList();
				list.add("a");
				list.add("a");
				list.add("b");
				list.add("b");
				list.add("b");
				list.add("c");
				list.add("c");
				list.add("c");
				list.add("c");
				
				System.out.println(list);
				ArrayList newList = getSingle(list);
				System.out.println(newList);
			}
		
			/*
			 * 去除重复
			 * 1,返回ArrayList
			 * 2,参数列表ArrayList
			 */
			public static ArrayList getSingle(ArrayList list) {
				ArrayList newList = new ArrayList();			//创建一个新集合
				Iterator it = list.iterator();					//获取迭代器
				while(it.hasNext()) {							//判断老集合中是否有元素
					String temp = (String)it.next();			//将每一个元素临时记录住
					if(!newList.contains(temp)) {				//如果新集合中不包含该元素
						newList.add(temp);						//将该元素添加到新集合中
					}
				}
				return newList;									//将新集合返回
			}
### 16.03_集合框架(LinkedList的特有功能)(掌握)
* A:LinkedList类概述
* B:LinkedList类特有功能
	* public void addFirst(E e)及addLast(E e)
	* public E getFirst()及getLast()
	* public E removeFirst()及public E removeLast()
	* public E get(int index);
### 16.05_集合框架(用LinkedList模拟栈数据结构的集合并测试)(掌握)
* A:案例演示
	* 需求：请用LinkedList模拟栈数据结构的集合，并测试
	* 创建一个类将Linked中的方法封装
	* 
			public class Stack {
				private LinkedList list = new LinkedList();		//创建LinkedList对象
				
				public void in(Object obj) {
					list.addLast(obj);							//封装addLast()方法
				}
				
				public Object out() {
					return list.removeLast();					//封装removeLast()方法
				}
				
				public boolean isEmpty() {
					return list.isEmpty();						//封装isEmpty()方法
				}
			}
### 16.06_集合框架(泛型概述和基本使用)(掌握)
* A:泛型概述
* B:泛型好处
	* 提高安全性(将运行期的错误转换到编译期) 
	* 省去强转的麻烦
* C:泛型基本使用
	* <>中放的必须是引用数据类型 
* D:泛型使用注意事项
	* 前后的泛型必须一致,或者后面的泛型可以省略不写(1.7的新特性菱形泛型)  
### 16.08_集合框架(泛型的由来)(了解)
* A:案例演示
	* 泛型的由来:通过Object转型问题引入
	* 早期的Object类型可以接收任意的对象类型，但是在实际的使用中，会有类型转换的问题。也就存在这隐患，所以Java提供了泛型来解决这个安全问题。
	
### 16.09_集合框架(泛型类的概述及使用)(了解)
* A:泛型类概述<T>
	* 把泛型定义在类上
* B:定义格式
	* public class 类名<泛型类型1,…>
* C:注意事项	
	* 泛型类型必须是引用类型
* D:案例演示
	* 泛型类的使用

### 16.10_集合框架(泛型方法的概述和使用)(了解)
* A:泛型方法概述
	* 把泛型定义在方法上
* B:定义格式	
	* public <泛型类型> 返回类型 方法名(泛型类型 变量名)//方法泛型需要与类的泛型一致
* C:案例演示
	* 泛型方法的使用
```
package com.heima.bean;

public class Tool<Q> {						//Q在创建对象的时候赋值
	private Q q;

	public Q getObj() {
		return q;
	}

	public void setObj(Q q) {
		this.q = q;
	}
	
	public<T> void show(T t) {				//非静态方法泛型最好与类的泛型一致
		System.out.println(t);				//如果不一致,需要在方法上声明该泛型
	}
	
	public static<W> void print(W w) {		//静态方法必须声明自己的泛型，这里既是W改为Q，也上类中的Q不一样，是静态方法自己的Q
		System.out.println(w);				//静态方法随着类的加载而加载
	}
	
}
```
### 16.11_集合框架(泛型接口的概述和使用)(了解)
* A:泛型接口概述
	* 把泛型定义在接口上
* B:定义格式	
	* public interface 接口名<泛型类型>
* C:案例演示
	* 泛型接口的使用
```
package com.heima.generic;

public class Demo4_Generic {

	public static void main(String[] args) {

	}
}

interface Inter<T> {
	public void show(T t);
}

/*class Demo implements Inter<String> {		//推荐用这种

	@Override
	public void show(String t) {
		System.out.println(t);
	}
	
}*/

class Demo<T> implements Inter<T> {		//没有必要在实现接口的时候给自己类加泛型

	@Override
	public void show(T t) {
		System.out.println(t);
	}
	
}
```
### 16.12_集合框架(泛型高级之通配符)(了解)
* A:泛型通配符<?>(类似斗地主中的赖子)
	* 任意类型，如果没有明确，那么就是Object以及任意的Java类了
* B:? extends E
	* 向下限定，E及其子类
```
package com.heima.generic;

import java.util.ArrayList;
import java.util.List;

import com.heima.bean.Person;
import com.heima.bean.Student;

public class Demo5_Generic {

	public static void main(String[] args) {
		//List<?> list = new ArrayList<Integer>();		//当右边的泛型是不确定时,左边可以指定为?
		ArrayList<Person> list1 = new ArrayList<>();		//Student extends Teacher
		list1.add(new Person("张三", 23));
		list1.add(new Person("李四", 24));
		list1.add(new Person("王五", 25));
		
		ArrayList<Student> list2 = new ArrayList<>();
		list2.add(new Student("赵六", 26));
		list2.add(new Student("周七", 27));
		
		list1.addAll(list2);
		System.out.println(list1);
		
	}

}

```
* C:? super E(TreeSet再讲)
	* 向上限定，E及其父类
### 16.13_集合框架(增强for的概述和使用)(掌握)
* A:增强for概述
	* 简化数组和Collection集合的遍历
* B:格式：(使用快捷键fore,然后按Alt + /)
* 
		for(元素数据类型 变量 : 数组或者Collection集合) {
			使用变量即可，该变量就是元素
		}
* C:案例演示
	* 数组，集合存储元素用增强for遍历
* D:好处
	* 简化遍历
* E:增强for循环底层依赖的是迭代器(Iterator)

### 16.14_集合框架(ArrayList存储字符串和自定义对象并遍历增强for版)(掌握)
* A:案例演示
	* ArrayList存储字符串并遍历增强for版
	* 
			ArrayList<String> list = new ArrayList<>();
			list.add("a");
			list.add("b");
			list.add("c");
			list.add("d");
			
			for(String s : list) {
				System.out.println(s);
			}
### 16.15_集合框架(三种迭代的能否删除)(掌握)
* 普通for循环,可以删除,但是索引要--
* 迭代器,可以删除,但是必须使用迭代器自身的remove方法,否则会出现并发修改异常
* 增强for循环不能删除
```
package com.heima.jdk5;

import java.util.ArrayList;
import java.util.Iterator;

import com.heima.bean.Person;

public class Demo1_Foreach {

	public static void main(String[] args) {
		//demo1();
		//demo2();
		ArrayList<String> list = new ArrayList<>();
		list.add("a");
		list.add("b");
		list.add("b");
		list.add("c");
		list.add("d");
		
		//1,普通for循环删除,索引要--
		/*for(int i = 0; i < list.size(); i++) {
			if("b".equals(list.get(i))) {
				list.remove(i--);							//通过索引删除元素
			}
		}*/
		
		//2,迭代器删除
		/*Iterator<String> it = list.iterator();
		while(it.hasNext()) {
			if("b".equals(it.next())) {
				//list.remove("b");							//不能用集合的删除方法,因为迭代过程中如果集合修改会出现并发修改异常
				it.remove();
			}
		}*/
		
		/*for(Iterator<String> it2 = list.iterator(); it2.hasNext();) {
			if("b".equals(it2.next())) {
				//list.remove("b");							//不能用集合的删除方法,因为迭代过程中如果集合修改会出现并发修改异常
				it2.remove();
			}
		}*/
		//3,增强for循环,增强for循环不能删除,只能遍历
		for (String string : list) {
			if("b".equals(string)) {
				list.remove("b");
			}
		}
		System.out.println(list);
	}

	public static void demo2() {
		ArrayList<Person> list = new ArrayList<>();
		list.add(new Person("张三", 23));
		list.add(new Person("李四", 24));
		list.add(new Person("王五", 25));
		list.add(new Person("赵六", 26));
		
		for (Person person : list) {
			System.out.println(person);
		}
	}

	public static void demo1() {
		int[] arr = {11,22,33,44,55};
		for (int i : arr) {
			System.out.println(i);
		}
		
		ArrayList<String> list = new ArrayList<>();
		list.add("a");
		list.add("b");
		list.add("c");
		list.add("d");
		
		for (String string : list) {
			System.out.println(string);
		}
	}

}
```
### 16.16_集合框架(静态导入的概述和使用)(了解)
* A:静态导入概述
* B:格式：
	* import static 包名….类名.方法名;
	* 可以直接导入到方法的级别
* C:注意事项
	* 方法必须是静态的,如果有多个同名的静态方法，容易不知道使用谁?
	这个时候要使用，必须加前缀。由此可见，意义不大，所以一般不用，但是要能看懂。
```
package com.heima.jdk5;

import static java.util.Arrays.sort;			//静态导入
import static java.util.Arrays.toString;		//静态导入

public class Demo2_StaticImport {

	public static void main(String[] args) {
		int[] arr = {55,22,33,44,11};
		sort(arr);							//排序
		//System.out.println(toString(arr));
	}
}
```
### 16.17_集合框架(可变参数的概述和使用)(掌握)
* A:可变参数概述
	* 定义方法的时候不知道该定义多少个参数
* B:格式
	* 修饰符 返回值类型 方法名(数据类型…  变量名){}
* C:注意事项：
	* 这里的变量其实是一个数组
	* 如果一个方法有可变参数，并且有多个参数，那么，可变参数肯定是最后一个
```
package com.heima.jdk5;

public class Demo3_ChangeableArgs {

	public static void main(String[] args) {
		int[] arr = {11,22,33,44,55};
		//print(arr);
		print(11,22,33,44,55);
		System.out.println("---------------");
		//print();
	}
	
	/*public static void print(int[] arr) {
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
	}*/
	
	public static void print(int ... arr) {			//可变参数其实是一个数组
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
	}
}

```
### 16.18_集合框架(Arrays工具类的asList()方法的使用)(掌握)
* A:案例演示
	* Arrays工具类的asList()方法的使用
	* Collection中toArray(T[] a)泛型版的集合转数组
```
package com.heima.jdk5;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Demo4_AsList {
	/**
	 * 数组转换成集合
	 * 数组转换成集合虽然不能增加或减少元素,但是可以用集合的思想操作数组,也就是说可以使用其他集合中的方法
	 */
	public static void main(String[] args) {
		//demo1();
		//demo2();
		//集合转数组,加泛型的
		ArrayList<String> list = new ArrayList<>();
		list.add("a");
		list.add("b");
		list.add("c");
		list.add("d");
		
		String[] arr = list.toArray(new String[10]);		//当集合转换数组时,数组长度如果是小于等于集合的size时,转换后的数组长度等于集合的size
									//如果数组的长度大于了size,分配的数组长度就和你指定的长度一样
		for (String string : arr) {
			System.out.println(string);
		}
	}

	public static void demo2() {
		//int[] arr = {11,22,33,44,55};			
		//List<int[]> list = Arrays.asList(arr);		//基本数据类型的数组转换成集合,会将整个数组当作一个对象转换
		//System.out.println(list);
		Integer[] arr = {11,22,33,44,55};			//将数组转换成集合,数组必须是引用数据类型,每一个值代表对象
		List<Integer> list = Arrays.asList(arr);
		System.out.println(list);
	}

	public static void demo1() {
		String[] arr = {"a","b","c"};
		List<String> list = Arrays.asList(arr);			//将数组转换成集合
		//list.add("d");					//不能添加
		System.out.println(list);
	}

}

```
### 16.19_集合框架(集合嵌套之ArrayList嵌套ArrayList)(掌握)
* A:案例演示
	* 集合嵌套之ArrayList嵌套ArrayList
```
package com.heima.list;

import java.util.ArrayList;

import com.heima.bean.Person;

public class Demo5_ArrayListArrayList {

	/**
	 * * A:案例演示
	 * 集合嵌套之ArrayList嵌套ArrayList
	 * 案例:
	 * 我们学科,学科又分为若个班级
	 * 整个学科一个大集合
	 * 若干个班级分为每一个小集合
	 */
	public static void main(String[] args) {
		ArrayList<ArrayList<Person>> list = new ArrayList<>();
		
		ArrayList<Person> first = new ArrayList<>();				//创建第一个班级
		first.add(new Person("杨幂", 30));
		first.add(new Person("李冰冰", 33));
		first.add(new Person("范冰冰", 20));
		
		ArrayList<Person> second = new ArrayList<>();
		second.add(new Person("黄晓明", 31));
		second.add(new Person("赵薇", 33));
		second.add(new Person("陈坤", 32));
		
		//将班级添加到学科集合中
		list.add(first);
		list.add(second);
		
		//遍历学科集合
		for(ArrayList<Person> a : list) {
			for(Person p : a) {
				System.out.println(p);
			}
		}
	}

}
```
### 17.04_集合框架(HashSet存储自定义对象保证元素唯一性的原理)
* 1.HashSet原理
	* 我们使用Set集合都是需要去掉重复元素的，如果在存储的时候逐个equals()比较，效率较低，哈希算法提高了去重复的效率，降低了使用equals()方法的次数
	* 当HashSet调用add()方法存储对象的时候，先调用对象的hashCode()方法得到一个哈希值，然后在集合中查找是否有哈希值相同的对象
		* 如果没有哈希值相同的对象就直接存入集合
		* 如果有哈希值相同的对象，就和哈希值相同的对象逐个进行equals()比较，比较结果为false就存入，true则不存
* 2.将自定义类的对象存入HashSet去重复
	* 类中必须重写hashCode()和equals()方法
	* hashCode()：属性相同的对象返回值必须相同，属性不同的返回值尽量不同(提高效率)
	* equals()：属性相同返回true，属性不同返回false，返回false的时候存储
### 17.05_集合框架(LinkedHashSet的概述和使用)
* 1. LinkedHashSet底层是链表实现的，是set集合中唯一一个能保证怎么存就怎么取的集合对象，因为是HashSet的子类，所以也是保证元素唯一的，与HashSet的原理一样。
### 17.09_集合框架(TreeSet存储Integer类型的元素并遍历)
* 1. TreeSet原理
	 * TreeSet集合是用来对象元素进行排序的,同样他也可以保证元素的唯一
	 * 当compareTo方法返回0的时候集合中只有一个元素
	 * 当compareTo方法返回正数的时候集合会怎么存就怎么取
	 * 当compareTo方法返回负数的时候集合会倒序存储
* 2.解释：二叉树：两个叉
	* 小的存储在左边（负数），大的存储在右边（整数），相等就不存（0）.
	* compareTo方法，在TreeSet集合如何存储元素取决于compareTo方法的返回值.
	* 返回0，集合中只有一个元素
	* 返回1，集合会怎么存就怎么取
	* 返回-1，集合会将存储的元素倒序
	* 返回num = this.age - o.age，集合会按从小到大的顺序输出（二叉树的中序遍历）
	
### 17.15_集合框架(TreeSet原理)
* 1. 特点
	* TreeSet是用来排序的，可以指定一个顺序，对象存入之后会按照指定的顺序排列
* 2. 使用方式
	* a.自然排序(Comparable)
		* TreeSet类的add()方法中会把存入的对象提升为Comparable类型
		* 调用对象的compareTo()方法和集合中的对象比较
		* 根据compareTo()方法返回的结果进行存储
		```
		class Person implements Comparable<Person> {
			/*****省略*****/
			public int compareTo(Person o) {
				int length = this.name.length() - o.name.length();		//比较长度为主要条件
				int num = length == 0 ? this.name.compareTo(o.name) : length;	//比较内容为次要条件
				return num == 0 ? this.age - o.age : num;			//比较年龄为次要条件
			}
		}
		public class Demo3_TreeSet {
			public static void main(String[] args) {
				demo1();
			}
			public static void demo1() {
				TreeSet<Integer> ts = new TreeSet<>();
				ts.add(3);
				ts.add(1);
				ts.add(1);
				ts.add(2);
				ts.add(2);
				ts.add(3);
				ts.add(3);

				System.out.println(ts);
			}

		}
		```
	* b.比较器顺序(Comparator)
		* 创建TreeSet的时候可以制定一个Comparator
		* 如果传入了Comparator的子类对象，那么TreeSet就会按照比较器中的顺序排序
		* add()方法内部会自动调用Comparator接口中的compare()方法排序
		* 调用的对象时compare方法的第一个参数，集合中的对象是compare方法的第二个参数
		* 例子如下面的17.16、17.17、17.18、17.19.
	* c.两种方式的区别
		* TreeSet构造函数什么都不传，默认按照类中的Comparable的顺序(没有就报错ClassCastException)
		* TreeSet如果传入Comparator，就优先按照Comparator
```
TreeSet构造方法摘要：
TreeSet(Comparator<? super E> comparator) 
          构造一个新的空 TreeSet，它根据指定比较器进行排序。
```
### 17.16_集合框架的练习
```
package com.heima.test;

import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;
import java.util.TreeSet;

public class Test4 {

	/**
	 * 在一个集合中存储了无序并且重复的字符串,定义一个方法,让其有序(字典顺序),而且还不能去除重复
	 * 
	 * 分析:
	 * 1,定义一个List集合,并存储重复的无序的字符串
	 * 2,定义方法对其排序保留重复
	 * 3,打印List集合
	 */
	public static void main(String[] args) {
		//1,定义一个List集合,并存储重复的无序的字符串
		ArrayList<String> list = new ArrayList<>();
		list.add("aaa");
		list.add("aaa");
		list.add("ccc");
		list.add("ddd");
		list.add("fffffffffff");
		list.add("heima");
		list.add("itcast");
		list.add("bbbb");
		list.add("aaa");
		list.add("aaa");
		
		//2,定义方法对其排序保留重复
		sort(list);
		
		//3,打印list
		System.out.println(list);
	}
	
	/*
	 * 定义方法,排序并保留重复
	 * 分析:
	 * 1,创建TreeSet集合对象,因为String本身就具备比较功能,但是重复不会保留,所以我们用比较器
	 * 2,将list集合中所有的元素添加到TrreSet集合中,对其排序,保留重复
	 * 3,清空list集合
	 * 4,将TreeSet集合中排好序的元素添加到list中
	 */
	public static void sort(List<String> list) {
		//1,创建TreeSet集合对象,因为String本身就具备比较功能,但是重复不会保留,所以我们用比较器
		TreeSet<String> ts = new TreeSet<>(new Comparator<String>() {//实现Comparator接口，重写里面的compare方法，匿名内部类

			@Override
			public int compare(String s1, String s2) {
				int num = s1.compareTo(s2);					//比较内容为主要条件
				return num == 0 ? 1 : num;					//保留重复
			}
		});
		//2,将list集合中所有的元素添加到TrreSet集合中,对其排序,保留重复
		ts.addAll(list);
		//3,清空list集合
		list.clear();
		//4,将TreeSet集合中排好序的元素添加到list中
		list.addAll(ts);
	}

}
```
### 17.17_集合框架的练习
```
package com.heima.test;

import java.util.Comparator;
import java.util.Scanner;
import java.util.TreeSet;

public class Test5 {

	/**
	 * 从键盘接收一个字符串, 程序对其中所有字符进行排序,例如键盘输入: helloitcast程序打印:acehillostt
	 * 分析:
	 * 1,键盘录入字符串,Scanner
	 * 2,将字符串转换为字符数组
	 * 3,定义TreeSet集合,传入比较器对字符排序并保留重复
	 * 4,遍历字符数组,将每一个字符存储在TreeSet集合中
	 * 5,遍历TreeSet集合,打印每一个字符
	 */
	public static void main(String[] args) {
		//1,键盘录入字符串,Scanner
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入一个字符串");
		String line = sc.nextLine();
		//2,将字符串转换为字符数组
		char[] arr = line.toCharArray();
		//3,定义TreeSet集合,传入比较器对字符排序并保留重复
		TreeSet<Character> ts = new TreeSet<>(new Comparator<Character>() {

			@Override
			public int compare(Character c1, Character c2) {
				//int num = c1 - c2;				//自动拆箱
				int num = c1.compareTo(c2);
				return num == 0 ? 1 : num;
			}
		});
		
		//4,遍历字符数组,将每一个字符存储在TreeSet集合中
		for(char c : arr) {
			ts.add(c);							//自动装箱
		}
		
		//5,遍历TreeSet集合,打印每一个字符
		for(Character c : ts) {
			System.out.print(c);
		}
	}

}
```
### 17.18_集合框架的练习
```
package com.heima.test;

import java.util.Comparator;
import java.util.Scanner;
import java.util.TreeSet;

public class Test6 {

	/**
	 * 程序启动后, 可以从键盘输入接收多个整数, 直到输入quit时结束输入. 把所有输入的整数倒序排列打印.
	 * 
	 * 1,创建Scanner对象,键盘录入
	 * 2,创建TreeSet集合对象,TreeSet集合中传入比较器
	 * 3,无限循环不断接收整数,遇到quit退出,因为退出是quit,所以键盘录入的时候应该都以字符串的形式录入
	 * 4,判断是quit就退出,不是将其转换为Integer,并添加到集合中
	 * 5,遍历TreeSet集合并打印每一个元素
	 */
	public static void main(String[] args) {
		//1,创建Scanner对象,键盘录入
		Scanner sc = new Scanner(System.in);
		//2,创建TreeSet集合对象,TreeSet集合中传入比较器
		TreeSet<Integer> ts = new TreeSet<>(new Comparator<Integer>() {

			@Override
			public int compare(Integer i1, Integer i2) {
				//int num = i2 - i1;					//自动拆箱
				int num = i2.compareTo(i1);
				return num == 0 ? 1 : num;
			}
		});
		//3,无限循环不断接收整数,遇到quit退出,因为退出是quit,所以键盘录入的时候应该都以字符串的形式录入
		while(true) {
			String line = sc.nextLine();				//将键盘录入的字符串存储在line中
			if("quit".equals(line)) {
				break;
			}
			//4,判断是quit就退出,不是将其转换为Integer,并添加到集合中
			Integer i = Integer.parseInt(line);
			ts.add(i);
		}
		
		// 5,遍历TreeSet集合并打印每一个元素
		for (Integer integer : ts) {
			System.out.println(integer);
		}
	}

}

```
### 17.19_集合框架的练习
```
package com.heima.test;

import java.util.Comparator;
import java.util.Scanner;
import java.util.TreeSet;

import com.heiam.bean.Student;

public class Test7 {

	/**
	 * * A:案例演示
	 * 需求：键盘录入5个学生信息(姓名,语文成绩,数学成绩,英语成绩),按照总分从高到低输出到控制台。
	 * 
	 * 分析:
	 * 1,定义一个学生类
	 * 		成员变量:姓名,语文成绩,数学成绩,英语成绩,总成绩
	 * 		成员方法:空参,有参构造,有参构造的参数分别是姓名,语文成绩,数学成绩,英语成绩
	 * 			  toString方法,在遍历集合中的Student对象打印对象引用的时候会显示属性值
	 * 2,键盘录入需要Scanner,创建键盘录入对象
	 * 3,创建TreeSet集合对象,在TreeSet的构造函数中传入比较器,按照总分比较
	 * 4,录入五个学生,所以以集合中的学生个数为判断条件,如果size是小于5就进行存储
	 * 5,将录入的字符串切割,用逗号切割,会返回一个字符串数组,将字符串数组中从二个元素转换成int数,
	 * 6,将转换后的结果封装成Student对象,将Student添加到TreeSet集合中
	 * 7,遍历TreeSet集合打印每一个Student对象
	 */
	public static void main(String[] args) {
		//2,键盘录入需要Scanner,创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入学生成绩格式是:姓名,语文成绩,数学成绩,英语成绩");
		//3,创建TreeSet集合对象,在TreeSet的构造函数中传入比较器,按照总分比较
		TreeSet<Student> ts = new TreeSet<>(new Comparator<Student>() {

			@Override
			public int compare(Student s1, Student s2) {
				int num = s2.getSum() - s1.getSum();
				return num == 0 ? 1 : num;
			}
		});
		//4,录入五个学生,所以以集合中的学生个数为判断条件,如果size是小于5就进行存储
		while(ts.size() < 5) {
			//5,将录入的字符串切割,用逗号切割,会返回一个字符串数组,将字符串数组中从二个元素转换成int数,
			String line = sc.nextLine();
			String[] arr = line.split(",");
			int chinese = Integer.parseInt(arr[1]);
			int math = Integer.parseInt(arr[2]);
			int english = Integer.parseInt(arr[3]);
			//6,将转换后的结果封装成Student对象,将Student添加到TreeSet集合中
			ts.add(new Student(arr[0], chinese, math, english));
		}
		
		//7,遍历TreeSet集合打印每一个Student对象
		System.out.println("排序后的学生信息:");
		for (Student s : ts) {
			System.out.println(s);
		}
	}

}
```
### 18.02_集合框架(Map集合的功能概述)
* A:Map集合的功能概述
	* a:添加功能
		* V put(K key,V value):添加元素。
			* 如果键是第一次存储，就直接存储元素，返回null
			* 如果键不是第一次存在，就用值把以前的值替换掉，返回以前的值
	* b:删除功能
		* void clear():移除所有的键值对元素
		* V remove(Object key)：根据键删除键值对元素，并把值返回
	* c:判断功能
		* boolean containsKey(Object key)：判断集合是否包含指定的键
		* boolean containsValue(Object value):判断集合是否包含指定的值
		* boolean isEmpty()：判断集合是否为空
	* d:获取功能
		* Set<Map.Entry<K,V>> entrySet():
		* V get(Object key):根据键获取值
		* Set<K> keySet():获取集合中所有键的集合
		* Collection<V> values():获取集合中所有值的集合
	* e:长度功能
		* int size()：返回集合中的键值对的个数
	
### 18.03_集合框架(Map集合的遍历之键找值)
* A:键找值思路：
	* 获取所有键的集合
	* 遍历键的集合，获取到每一个键
	* 根据键找值
* B:案例演示
	* Map集合的遍历之键找值

			HashMap<String, Integer> hm = new HashMap<>();
			hm.put("张三", 23);
			hm.put("李四", 24);
			hm.put("王五", 25);
			hm.put("赵六", 26);
			
			/*Set<String> keySet = hm.keySet();		//获取集合中所有的键
			Iterator<String> it = keySet.iterator();	//获取迭代器
			while(it.hasNext()) {				//判断单列集合中是否有元素
				String key = it.next();			//获取集合中的每一个元素,其实就是双列集合中的键
				Integer value = hm.get(key);		//根据键获取值
				System.out.println(key + "=" + value);	//打印键值对
			}*/
			
			for(String key : hm.keySet()) {			//增强for循环迭代双列集合第一种方式
				System.out.println(key + "=" + hm.get(key));
			}
### 18.04_集合框架(Map集合的遍历之键值对对象找键和值)
* A:键值对对象找键和值思路：
	* 获取所有键值对对象的集合
	* 遍历键值对对象的集合，获取到每一个键值对对象
	* 根据键值对对象找键和值
* B:案例演示
	* Map集合的遍历之键值对对象找键和值
	
			HashMap<String, Integer> hm = new HashMap<>();
			hm.put("张三", 23);
			hm.put("李四", 24);
			hm.put("王五", 25);
			hm.put("赵六", 26);
			/*Set<Map.Entry<String, Integer>> entrySet = hm.entrySet();	//获取所有的键值对象的集合
			Iterator<Entry<String, Integer>> it = entrySet.iterator();//获取迭代器
			while(it.hasNext()) {
				//Map.Entry<String, Integer> en = it.next();		//父类引用指向子类对象，获取键值对对象
				Entry<String, Integer> en = it.next();			//直接获取的是子类对象，获取键值对对象（因为Entry是个内部类，Entry实现了Map.Entry）
				String key = en.getKey();				//根据键值对对象获取键
				Integer value = en.getValue();				//根据键值对对象获取值
				System.out.println(key + "=" + value);
			}*/
			
			for(Entry<String,Integer> en : hm.entrySet()) {
				System.out.println(en.getKey() + "=" + en.getValue());
			}
### 18.06_集合框架(LinkedHashMap的概述和使用)
* A:案例演示
	* LinkedHashMap的特点
		* 底层是链表实现的可以保证怎么存就怎么取
### 18.07_集合框架(TreeMap集合键是Student值是String的案例)
* A:案例演示
	* TreeMap集合键是Student值是String的案例
### 18.08_集合框架(统计字符串中每个字符出现的次数)
* A:案例演示
	* 需求：统计字符串中每个字符出现的次数
			String str = "aaaabbbcccccccccc";
			char[] arr = str.toCharArray();						//将字符串转换成字符数组
			HashMap<Character, Integer> hm = new HashMap<>();	//创建双列集合存储键和值
			
			for(char c : arr) {									//遍历字符数组
				/*if(!hm.containsKey(c)) {						//如果不包含这个键
					hm.put(c, 1);								//就将键和值为1添加
				}else {											//如果包含这个键
					hm.put(c, hm.get(c) + 1);					//就将键和值再加1添加进来
				}
				
				//hm.put(c, !hm.containsKey(c) ? 1 : hm.get(c) + 1);
				Integer i = !hm.containsKey(c) ? hm.put(c, 1) : hm.put(c, hm.get(c) + 1);
						}
			
			for (Character key : hm.keySet()) {					//遍历双列集合
				System.out.println(key + "=" + hm.get(key));
			}
### 18.10_集合框架(HashMap和Hashtable的区别)
* A:面试题
	* HashMap和Hashtable的区别
		* Hashtable是JDK1.0版本出现的,是线程安全的,效率低,HashMap是JDK1.2版本出现的,是线程不安全的,效率高
		* Hashtable不可以存储null键和null值,HashMap可以存储null键和null值
* B:案例演示	
	* HashMap和Hashtable的区别
### 18.11_集合框架(Collections工具类的概述和常见方法讲解)
* A:Collections类概述
	* 针对集合操作 的工具类
* B:Collections成员方法
* 
		public static <T> void sort(List<T> list)
		public static <T> int binarySearch(List<?> list,T key)
		public static <T> T max(Collection<?> coll)
		public static void reverse(List<?> list)
		public static void shuffle(List<?> list)//随机置换，可以用来洗牌
	
### 18.15_集合框架(泛型固定下边界)
	 * 泛型固定下边界
	 * ? super E  
	 * 
	 * 泛型固定上边界
	 * ? extends E
```
package com.heima.collections;

import java.util.ArrayList;
import java.util.Comparator;
import java.util.TreeSet;

import com.heima.bean.BaseStudent;
import com.heima.bean.Student;

public class Demo2_Genric {

	/**
	 * 泛型固定下边界
	 * ? super E  
	 * 
	 * 泛型固定上边界
	 * ? extends E
	 */
	public static void main(String[] args) {
		//demo1();
		TreeSet<Student> ts1 = new TreeSet<>(new CompareByAge());
		ts1.add(new Student("张三", 33));
		ts1.add(new Student("李四", 13));
		ts1.add(new Student("王五", 23));
		ts1.add(new Student("赵六", 43));
		
		TreeSet<BaseStudent> ts2 = new TreeSet<>(new CompareByAge());
		ts2.add(new BaseStudent("张三", 33));
		ts2.add(new BaseStudent("李四", 13));
		ts2.add(new BaseStudent("王五", 23));
		ts2.add(new BaseStudent("赵六", 43));
		
		System.out.println(ts2);
	}

	public static void demo1() {
		ArrayList<Student> list1 = new ArrayList<>();
		list1.add(new Student("张三", 23));
		list1.add(new Student("李四", 24));
		
		ArrayList<BaseStudent> list2 = new ArrayList<>();
		list2.add(new BaseStudent("王五", 25));
		list2.add(new BaseStudent("赵六", 26));
		
		list1.addAll(list2);
	}

}

class CompareByAge implements Comparator<Student> {

	@Override
	public int compare(Student s1, Student s2) {
		int num = s1.getAge() - s2.getAge();
		return num == 0 ? s1.getName().compareTo(s2.getName()) :  num;
	}
	
}
```

### 19.01_异常(异常的概述和分类)
* A:异常的概述
	* 异常就是Java程序在运行过程中出现的错误。
* B:异常的分类
	* 通过API查看Throwable
	* Error
		* 服务器宕机,数据库崩溃等
	* Exception
C:异常的继承体系
	* Throwable
		* Error	
		* Exception
			* RuntimeException

### 19.03_异常(try...catch的方式处理异常1)
* A:异常处理的两种方式
	* a:try…catch…finally
		* try catch
		* try catch finally
		* try finally 
	* b:throws
* B:try...catch处理异常的基本格式
	* try…catch…finally
* C:案例演示
	* try...catch的方式处理1个异常
	* 案例演示：
	* try...catch的方式处理多个异常
	* JDK7以后处理多个异常的方式及注意事项
	* 
	* 安卓,客户端开发,如何处理异常?try{}catch(Exception e){}
	* ee,服务端开发,一般都是底层开发,从底层向上抛
	* 
	* try后面如果跟多个catch,那么小的异常放前面,大的异常放后面,根据多态的原理,如果大的放前面,就会将所有的子类对象接收
	* 后面的catch就没有意义了
	
### 19.05_异常(编译期异常和运行期异常的区别)
* A:编译期异常和运行期异常的区别
	* Java中的异常被分为两大类：编译时异常和运行时异常。
	* 所有的RuntimeException类及其子类的实例被称为运行时异常，其他的异常就是编译时异常
	
	* 编译时异常
		* Java程序必须显示处理，否则程序就会发生错误，无法通过编译
	* 运行时异常
		* 无需显示处理，也可以和编译时异常一样处理
* B:案例演示
	* 编译期异常和运行期异常的区别
```
* 编译期异常和运行期异常的区别
编译时异常也叫做未雨绸缪异常(老师自己定义的)
未雨绸缪:在做某些事情的时候要做某些准备
编译时异常:在编译某个程序的时候,有可能会有这样那样的事情发生,比如文件找不到,这样的异常就必须在编译的时候处理
如果不处理编译通不过

运行时异常:就是程序员所犯得错误,需要回来修改代码
```
### 19.06_异常(Throwable的几个常见方法)
* A:Throwable的几个常见方法
	* a:getMessage()
		* 获取异常信息，返回字符串。
	* b:toString()
		* 获取异常类名和异常信息，返回字符串。
	* c:printStackTrace()
		* 获取异常类名和异常信息，以及异常出现在程序中的位置。返回值void。
* B:案例演示
	* Throwable的几个常见方法的基本使用
```
package com.heima.exception;

public class Demo5_Throwable {

	public static void main(String[] args) {
		try {
			System.out.println(1/0);
		} catch (Exception e) {			//Exception e = new ArithmeticException("/ by zero");
			//System.out.println(e.getMessage());		//获取异常信息
			//System.out.println(e); 		//调用toString方法,打印异常类名和异常信息
			e.printStackTrace();		//jvm默认就用这种方式处理异常
		}
	}

}
```
### 19.08_异常(throw的概述以及和throws的区别)
* A:throw的概述
	* 在功能方法内部出现某种情况，程序不能继续运行，需要进行跳转时，就用throw把异常对象抛出。
* B:案例演示	
	* 分别演示编译时异常对象和运行时异常对象的抛出
* C:throws和throw的区别
	* a:throws
		* 用在方法声明后面，跟的是异常类名
		* 可以跟多个异常类名，用逗号隔开
		* 表示抛出异常，由该方法的调用者来处理
	* b:throw
		* 用在方法体内，跟的是异常对象名
		* 只能抛出一个异常对象名
		* 表示抛出异常，由方法体内的语句处理
### 19.09_异常(finally关键字的特点及作用)
* A:finally的特点
	* 被finally控制的语句体一定会执行
	* 特殊情况：在执行到finally之前jvm退出了(比如System.exit(0))
* B:finally的作用
	* 用于释放资源，在IO流操作和数据库操作中会见到
* C:案例演示
	* finally关键字的特点及作用
* return语句相当于是方法的最后一口气,那么在他将死之前会看一看有没有finally帮其完成遗愿,如果有就将finally执行后再彻底返回。

### 19.10_异常(finally关键字的面试题)
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
### 19.11_异常(自定义异常概述和基本使用)
* A:为什么需要自定义异常
	* 通过名字区分到底是神马异常,有针对的解决办法 
	* 举例：人的年龄
* B:自定义异常概述
	* 继承自Exception
	* 继承自RuntimeException
* C:案例演示
	* 自定义异常的基本使用
```
package com.heima.exception;
class Person {
	public void setAge(int age) throws AgeOutOfBoundsException {
		if(age >0 && age <= 150) {
			this.age = age;
		}else {
			//Exception e = new Exception("年龄非法");
			//throw e;
			throw new AgeOutOfBoundsException("年龄非法");
		}
	}
}

public class Demo8_Exception {

	public static void main(String[] args) {

	}

}

class AgeOutOfBoundsException extends Exception {

	public AgeOutOfBoundsException() {
		super();
		
	}

	public AgeOutOfBoundsException(String message) {
		super(message);
		
	}
	
}
```
### 19.12_异常(异常的注意事项及如何使用异常处理)
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
* C:alt + shif + z (try catch快捷键)
### 19.14_File类(File类的概述和构造方法)
* A:File类的概述
	* File更应该叫做一个路径
		* 文件路径或者文件夹路径  
		* 路径分为绝对路径和相对路径
		* 绝对路径是一个固定的路径,从盘符开始
		* 相对路径相对于某个位置,在eclipse下是指当前项目下,在dos下
	* 查看API指的是当前路径
	* 文件和目录路径名的抽象表示形式
* B:构造方法
	* File(String pathname)：根据一个路径得到File对象
	* File(String parent, String child):根据一个目录和一个子文件/目录得到File对象
	* File(File parent, String child):根据一个父File对象和一个子文件/目录得到File对象
* C:案例演示
	* File类的构造方法
### 19.15_File类(File类的创建功能)
* A:创建功能
	* public boolean createNewFile():创建文件 如果存在这样的文件，就不创建了
	* public boolean mkdir():创建文件夹 如果存在这样的文件夹，就不创建了
	* public boolean mkdirs():创建文件夹,如果父文件夹不存在，会帮你创建出来
* B:案例演示
	* File类的创建功能

	* 注意事项：
		* 如果你创建文件或者文件夹忘了写盘符路径，那么，默认在项目路径下。
### 19.16_File类(File类的重命名和删除功能)
* A:重命名和删除功能
	* public boolean renameTo(File dest):把文件重命名为指定的文件路径
	* public boolean delete():删除文件或者文件夹
* B:重命名注意事项
	* 如果路径名相同，就是改名。
	* 如果路径名不同，就是改名并剪切。
* C:删除注意事项：
	* Java中的删除不走回收站。
	* 要删除一个文件夹，请注意该文件夹内不能包含文件或者文件夹
### 19.17_File类(File类的判断功能)
* A:判断功能
	* public boolean isDirectory():判断是否是目录
	* public boolean isFile():判断是否是文件
	* public boolean exists():判断是否存在
	* public boolean canRead():判断是否可读（windows系统认为所有的文件都是可读的）
	* public boolean canWrite():判断是否可写（windows系统可以设置为不可写）
	* public boolean isHidden():判断是否隐藏
* B:案例演示
	* File类的判断功能
### 19.18_File类(File类的获取功能)
* A:获取功能
	* public String getAbsolutePath()：获取绝对路径
	* public String getPath():获取构造方法中传入路径
	* public String getName():获取名称
	* public long length():获取长度。字节数
	* public long lastModified():获取最后一次的修改时间，毫秒值
	* public String[] list():获取指定目录下的所有文件或者文件夹的名称数组（仅为了获取文件名）
	* public File[] listFiles():获取指定目录下的所有文件或者文件夹的File数组（获取文件对象） 
* B:案例演示
	* File类的获取功能
* File dir = new File("F:/双元课堂/day19/ccc.txt");//这样写可以
* File dir = new File("F:\\双元课堂\\day19\\ccc.txt");//这样写也可以
### 19.20_File类(文件名称过滤器的概述及使用)
* A:文件名称过滤器的概述
	* public String[] list(FilenameFilter filter)
	* public File[] listFiles(FileFilter filter)
* B:文件名称过滤器的使用
	* 需求：判断E盘目录下是否有后缀名为.jpg的文件，如果有，就输出该文件名称
* C:源码分析
	* 带文件名称过滤器的list()方法的源码
### 20.01_IO流(IO流概述及其分类)
* 1.概念
	* IO流用来处理设备之间的数据传输
	* Java对数据的操作是通过流的方式
	* Java用于操作流的类都在IO包中
	* 流按流向分为两种：输入流，输出流。
	* 流按操作类型分为两种：
		* 字节流 : 字节流可以操作任何数据,因为在计算机中任何数据都是以字节的形式存储的
		* 字符流 : 字符流只能操作纯字符数据，比较方便。
* 2.IO流常用父类
	* 字节流的抽象父类：
		* InputStream 
		* OutputStream
	* 字符流的抽象父类：
		* Reader 
		* Writer		
* 3.IO程序书写
	* 使用前，导入IO包中的类
	* 使用时，进行IO异常处理
	* 使用后，释放资源

### 20.02_IO流(FileInputStream)
* read()一次读取一个字节
* 
		FileInputStream fis = new FileInputStream("aaa.txt");	//创建一个文件输入流对象,并关联aaa.txt
		int b;							//定义变量,记录每次读到的字节
		while((b = fis.read()) != -1) {				//将每次读到的字节赋值给b并判断是否是-1，文件的结束标记是-1
			System.out.println(b);				//打印每一个字节
		}
		fis.close();						//关闭流释放资源
### 20.03_IO流(read()方法返回值为什么是int)
* read()方法读取的是一个字节,为什么返回是int,而不是byte
* 
		因为字节输入流可以操作任意类型的文件,比如图片音频等,这些文件底层都是以二进制形式的存储的,如果每次读取都返回byte,有可能在读到中间的时候遇到111111111
		那么这11111111是byte类型的-1,我们的程序是遇到-1就会停止不读了,后面的数据就读不到了,所以在读取的时候用int类型接收,如果11111111会在其前面补上
		24个0凑足4个字节,那么byte类型的-1就变成int类型的255了这样可以保证整个数据读完,而结束标记的-1就是int类型
### 20.04_IO流(FileOutputStream)
* write()一次写出一个字节
* 
		FileOutputStream fos = new FileOutputStream("bbb.txt");	//如果没有bbb.txt,会创建出一个
		//fos.write(97);					//虽然写出的是一个int数,但是在写出的时候会将前面的24个0去掉,所以写出的是一个byte
		fos.write(98);
		fos.write(99);
		fos.close();
### 20.05_IO流(FileOutputStream追加)
* A:案例演示
	* FileOutputStream的构造方法写出数据如何实现数据的追加写入
* 
		FileOutputStream fos = new FileOutputStream("bbb.txt",true);	//如果没有bbb.txt,会创建出一个
		//fos.write(97);						//虽然写出的是一个int数,但是在写出的时候会将前面的24个0去掉,所以写出的一个byte
		fos.write(98);
		fos.write(99);
		fos.close();

### 20.06_IO流(拷贝图片)
* FileInputStream读取
* FileOutputStream写出

		FileInputStream fis = new FileInputStream("致青春.mp3");//创建输入流对象,关联致青春.mp3
		FileOutputStream fos = new FileOutputStream("copy.mp3");//创建输出流对象,关联copy.mp3
		
		int b;
		while((b = fis.read()) != -1) {
			fos.write(b);
		}
		
		fis.close();
		fos.close();
		

### 20.07_IO流(拷贝音频文件画原理图)
* A:案例演示
	* 字节流一次读写一个字节复制音频
* 弊端:效率太低

### 20.08_IO流(字节数组拷贝之available()方法)
* A:案例演示
	* int read(byte[] b):一次读取一个字节数组
	* write(byte[] b):一次写出一个字节数组
	* available()获取读的文件所有的字节个数
* 弊端:有可能会内存溢出 
	
		FileInputStream fis = new FileInputStream("致青春.mp3");
		FileOutputStream fos = new FileOutputStream("copy.mp3");
		byte[] arr = new byte[fis.available()];					//根据文件大小做一个字节数组
		fis.read(arr);								//将文件上的所有字节读取到数组中
		fos.write(arr);								//将数组中的所有字节一次写到了文件上
		fis.close();
		fos.close();
		
### 20.09_IO流(定义小数组)
* write(byte[] b)
* write(byte[] b, int off, int len)写出有效的字节个数

		
### 20.10_IO流(定义小数组的标准格式)
* A:案例演示
	* 字节流一次读写一个字节数组复制图片和视频
		FileInputStream fis = new FileInputStream("致青春.mp3");
		FileOutputStream fos = new FileOutputStream("copy.mp3");
		int len;
		byte[] arr = new byte[1024 * 8];					//自定义字节数组
		
		while((len = fis.read(arr)) != -1) {
			//fos.write(arr);
			fos.write(arr, 0, len);							//写出字节数组写出有效个字节个数
		}
		
		fis.close();
		fos.close();
### 20.11_IO流(BufferedInputStream和BufferOutputStream拷贝)
* A:缓冲思想
	* 字节流一次读写一个数组的速度明显比一次读写一个字节的速度快很多，
	* 这是加入了数组这样的缓冲区效果，java本身在设计的时候，
	* 也考虑到了这样的设计思想(**装饰设计模式**后面讲解)，所以提供了字节缓冲区流
* B.BufferedInputStream
	* BufferedInputStream内置了一个缓冲区(数组)
	* 从BufferedInputStream中读取一个字节时
	* BufferedInputStream会一次性从文件中读取8192个, 存在缓冲区中, 返回给程序一个
	* 程序再次读取时, 就不用找文件了, 直接从缓冲区中获取
	* 直到缓冲区中所有的都被使用过, 才重新从文件中读取8192个
* C.BufferedOutputStream
	* BufferedOutputStream也内置了一个缓冲区(数组)
	* 程序向流中写出字节时, 不会直接写到文件, 先写到缓冲区中
	* 直到缓冲区写满, BufferedOutputStream才会把缓冲区中的数据一次性写到文件里
* D.拷贝的代码 

		FileInputStream fis = new FileInputStream("致青春.mp3");			//创建文件输入流对象,关联致青春.mp3
		BufferedInputStream bis = new BufferedInputStream(fis);			//创建缓冲区对fis装饰
		FileOutputStream fos = new FileOutputStream("copy.mp3");		//创建输出流对象,关联copy.mp3
		BufferedOutputStream bos = new BufferedOutputStream(fos);		//创建缓冲区对fos装饰
		
		int b;
		while((b = bis.read()) != -1) {		
			bos.write(b);
		}
		
		bis.close();						//只关装饰后的对象即可
		bos.close();
	 
* E.小数组的读写和带Buffered的读取哪个更快?
	* 定义小数组如果是8192个字节大小和Buffered比较的话
	* 定义小数组会略胜一筹,因为读和写操作的是同一个数组
	* 而Buffered操作的是两个数组

### 20.12_IO流(flush和close方法的区别)
* flush()方法（QQ聊天）
	* 用来刷新缓冲区的,刷新后可以再次写出 
* cl8ose()方法
	* 用来关闭流释放资源的的,如果是带缓冲区的流对象的close()方法,不但会关闭流,还会再关闭流之前刷新缓冲区,关闭后不能再写出 
### 20.13_IO流(字节流读写中文) 
* 字节流读取中文的问题
	* 字节流在读中文的时候有可能会读到半个中文,造成乱码 
* 字节流写出中文的问题
	* 字节流直接操作的字节,所以写出中文必须将字符串转换成字节数组 
	* 写出回车换行 write("\r\n".getBytes());

### 20.14_IO流(流的标准处理异常代码1.6版本及其以前)
* try finally嵌套

		FileInputStream fis = null;
		FileOutputStream fos = null;
		try {
			fis = new FileInputStream("aaa.txt");
			fos = new FileOutputStream("bbb.txt");
			int b;
			while((b = fis.read()) != -1) {
				fos.write(b);
			}
		} finally {
			try {
				if(fis != null)
					fis.close();
			}finally {
				if(fos != null)
					fos.close();
			}
		}

### 20.15_IO流(流的标准处理异常代码1.7版本)
* try close

		try(
			FileInputStream fis = new FileInputStream("aaa.txt");
			FileOutputStream fos = new FileOutputStream("bbb.txt");
			MyClose mc = new MyClose();
		){
			int b;
			while((b = fis.read()) != -1) {
				fos.write(b);
			}
		}
* 原理
	* 在try()中创建的流对象必须实现了AutoCloseable这个接口,如果实现了,在try后面的{}(读写代码)执行后就会自动调用,流对象的close方法将流关掉 

### 20.16_IO流(图片加密)
* 给图片加密

		BufferedInputStream bis = new BufferedInputStream(new FileInputStream("a.jpg"));
		BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("b.jpg"));
		
		int b;
		while((b = bis.read()) != -1) {
			bos.write(b ^ 123);//解密的时候再次异或就可以了
		}
		
		bis.close();
		bos.close();

### 20.17_IO流(拷贝文件)
* 在控制台录入文件的路径,将文件拷贝到当前项目下

		Scanner sc = new Scanner(System.in);
		System.out.println("请输入一个文件路径");
		String line = sc.nextLine();					//将键盘录入的文件路径存储在line中
		File file = new File(line);					//封装成File对象
		FileInputStream fis = new FileInputStream(file);
		FileOutputStream fos = new FileOutputStream(file.getName());
		
		int len;
		byte[] arr = new byte[8192];					//定义缓冲区
		while((len = fis.read(arr)) != -1) {
			fos.write(arr,0,len);
		}
		
		fis.close();
		fos.close();

### 20.18_IO流(录入数据拷贝到文件)
* 将键盘录入的数据拷贝到当前项目下的text.txt文件中,键盘录入数据当遇到quit时就退出

		Scanner sc = new Scanner(System.in);
		FileOutputStream fos = new FileOutputStream("text.txt");
		System.out.println("请输入:");
		while(true) {
			String line = sc.nextLine();
			if("quit".equals(line))
				break;
			fos.write(line.getBytes());
			fos.write("\r\n".getBytes());
		}
		
		fos.close();

### 21.01_IO流(字符流FileReader)
* 1.字符流是什么
	* 字符流是可以直接读写字符的IO流
	* 字符流读取字符, 就要先读取到字节数据, 然后转为字符. 如果要写出字符, 需要把字符转为字节再写出.    
* 2.FileReader
	* FileReader类的read()方法可以按照字符大小读取
* 
		FileReader fr = new FileReader("aaa.txt");				//创建输入流对象,关联aaa.txt
		int ch;
		while((ch = fr.read()) != -1) {							//将读到的字符赋值给ch
			System.out.println((char)ch);						//将读到的字符强转后打印
		}
		
		fr.close();												//关流 

### 21.02_IO流(字符流FileWriter)
* FileWriter类的write()方法可以自动把字符转为字节写出

		FileWriter fw = new FileWriter("aaa.txt");
		fw.write("aaa");
		fw.close();

### 21.03_IO流(字符流的拷贝)
	FileReader fr = new FileReader("a.txt");
	FileWriter fw = new FileWriter("b.txt");
	
	int ch;
	while((ch = fr.read()) != -1) {
		fw.write(ch);
	}
	
	fr.close();
	fw.close();//Writer类中有一个2k的小缓冲区,如果不关流,就会将内容写到缓冲区里,关流会将缓冲区内容刷新,再关闭
### 21.04_IO流(什么情况下使用字符流)
* 字符流也可以拷贝文本文件, 但不推荐使用. 因为读取时会把字节转为字符, 写出时还要把字符转回字节.
* 程序需要读取一段文本, 或者需要写出一段文本的时候可以使用字符流
* 读取的时候是按照字符的大小读取的,不会出现半个中文
* 写出的时候可以直接将字符串写出,不用转换为字节数组
* 字符流和字节流哪个拷贝纯文本更好：
![字符流和字节流哪个拷贝纯文本更好](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Character%20stream%20and%20byte%20stream.png)  
### 21.05_IO流(字符流是否可以拷贝非纯文本的文件)
* 不可以拷贝非纯文本的文件
* 因为在读的时候会将字节转换为字符,在转换过程中,可能找不到对应的字符,就会用?代替,写出的时候会将字符转换成字节写出去
* 如果是?,直接写出,这样写出之后的文件就乱了,看不了了  

### 21.06_IO流(自定义字符数组的拷贝)
*	
		
		FileReader fr = new FileReader("aaa.txt");			//创建字符输入流,关联aaa.txt
		FileWriter fw = new FileWriter("bbb.txt");			//创建字符输出流,关联bbb.txt
		
		int len;
		char[] arr = new char[1024*8];					//创建字符数组
		while((len = fr.read(arr)) != -1) {				//将数据读到字符数组中
			fw.write(arr, 0, len);					//从字符数组将数据写到文件上
		}
		
		fr.close();							//关流释放资源
		fw.close();	

### 21.07_IO流(带缓冲的字符流) 
* BufferedReader的read()方法读取字符时会一次读取若干字符到缓冲区, 然后逐个返回给程序, 降低读取文件的次数, 提高效率
* BufferedWriter的write()方法写出字符时会先写到缓冲区, 缓冲区写满时才会写到文件, 降低写文件的次数, 提高效率
* 
		BufferedReader br = new BufferedReader(new FileReader("aaa.txt"));	//创建字符输入流对象,关联aaa.txt
		BufferedWriter bw = new BufferedWriter(new FileWriter("bbb.txt"));	//创建字符输出流对象,关联bbb.txt
		
		int ch;				
		while((ch = br.read()) != -1) {						//read一次,会先将缓冲区读满,从缓冲去中一个一个的返给临时变量ch
			bw.write(ch);							//write一次,是将数据装到字符数组,装满后再一起写出去
		}
		
		br.close();								//关流
		bw.close();  


### 21.08_IO流(readLine()和newLine()方法)	
* BufferedReader的readLine()方法可以读取一行字符(不包含换行符号)
* BufferedWriter的newLine()可以输出一个跨平台的换行符号"\r\n"
* 
		BufferedReader br = new BufferedReader(new FileReader("aaa.txt"));
		BufferedWriter bw = new BufferedWriter(new FileWriter("bbb.txt"));
		String line;
		while((line = br.readLine()) != null) {
			bw.write(line);
			//bw.write("\r\n");					//只支持windows系统
			bw.newLine();						//跨平台的
		}
		
		br.close();
		bw.close(); 

### 21.09_IO流(将文本反转)
* 将一个文本文档上的文本反转,第一行和倒数第一行交换,第二行和倒数第二行交换
* 注意事项:
	* 流对象尽量晚开早关
### 21.10_IO流(LineNumberReader) 
* LineNumberReader是BufferedReader的子类, 具有相同的功能, 并且可以统计行号
	* 调用getLineNumber()方法可以获取当前行号
	* 调用setLineNumber()方法可以设置当前行号
* 
		LineNumberReader lnr = new LineNumberReader(new FileReader("aaa.txt"));
		String line;
		lnr.setLineNumber(100);									//设置行号
		while((line = lnr.readLine()) != null) {
			System.out.println(lnr.getLineNumber() + ":" + line);//获取行号
		}
		
		lnr.close(); 

### 21.11_IO流(装饰设计模式)
* 装饰设计模式的好处是:
* 耦合性不强,被装饰的类的变化与装饰类的变化无关
* 
		interface Coder {
			public void code();
		}
		
		class Student implements Coder {
		
			@Override
			public void code() {
				System.out.println("javase");
				System.out.println("javaweb");
			}
			
		}
		
		class HeiMaStudent implements Coder {
			private Student s;				//获取到被包装的类的引用
			public HeiMaStudent(Student s) {		//通过构造函数创建对象的时候,传入被包装的对象
				this.s = s;
			}
			@Override
			public void code() {				//对其原有功能进行升级
				s.code();
				System.out.println("数据库");
				System.out.println("ssh");
				System.out.println("安卓");
				System.out.println(".....");
			}
			
		} 

### 21.12_IO流(使用指定的码表读写字符) 
* FileReader是使用默认码表读取文件, 如果需要使用指定码表读取, 那么可以使用InputStreamReader(字节流,编码表)
* FileWriter是使用默认码表写出文件, 如果需要使用指定码表写出, 那么可以使用OutputStreamWriter(字节流,编码表)
* 
		BufferedReader br = 									//高效的用指定的编码表读
				new BufferedReader(new InputStreamReader(new FileInputStream("UTF-8.txt"), "UTF-8"));
		BufferedWriter bw = 									//高效的用指定的编码表写
				new BufferedWriter(new OutputStreamWriter(new FileOutputStream("GBK.txt"), "GBK"));
		int ch;
		while((ch = br.read()) != -1) {
			bw.write(ch);
		}
		
		br.close();
		bw.close();
### 21.13_IO流(转换流图解)
* 画图分析转换流
* 转换流图解：
![转换流图解](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Conversion%20flow.png)  
### 21.14_IO流(获取文本上字符出现的次数)
* 获取一个文本上每个字符出现的次数,将结果写在times.txt上

### 21.15_IO流(试用版软件)
* 当我们下载一个试用版软件,没有购买正版的时候,每执行一次就会提醒我们还有多少次使用机会用学过的IO流知识,模拟试用版软件,试用10次机会,执行一次就提示一次您还有几次机会,如果次数到了提示请购买正版

### 21.16_File类(递归)
* 5的阶乘	
```
 * 递归:方法自己调用自己
 * 5!
 * 5 * 4 * 3 * 2 * 1
 * 
 * 5 * fun(4)(代表4!)
 * 		4 * fun(3)(代表3!)
 * 				3 * fun(2)(代表2!) 
 * 						2 * fun(1)(代表1!)
 * 递归的弊端:不能调用次数过多,容易导致栈内存溢出
 * 递归的好处:不用知道循环次数
 * 
 * 构造方法是否可以递归调用?
 * 构造方法不能使用递归调用
 * 
 * 递归调用是否必须有返回值?
 * 不一定(可以有,也可以没有,比如直接打印)
```
### 21.17_File类(练习)
* 需求:从键盘输入接收一个文件夹路径,打印出该文件夹下所有的.java文件名

### 21.18_IO流(总结)
* 1.会用BufferedReader读取GBK码表和UTF-8码表的字符
* 2.会用BufferedWriter写出字符到GBK码表和UTF-8码表的文件中
* 3.会使用BufferedReader从键盘读取一行

### 22.01_IO流(序列流)(了解)
* 1.什么是序列流
	* 序列流可以把多个字节输入流整合成一个, 从序列流中读取数据时, 将从被整合的第一个流开始读, 读完一个之后继续读第二个, 以此类推.
* 2.使用方式
	* 整合两个: SequenceInputStream(InputStream, InputStream)
	* 
			FileInputStream fis1 = new FileInputStream("a.txt");			//创建输入流对象,关联a.txt
			FileInputStream fis2 = new FileInputStream("b.txt");			//创建输入流对象,关联b.txt
			SequenceInputStream sis = new SequenceInputStream(fis1, fis2);	//将两个流整合成一个流
			FileOutputStream fos = new FileOutputStream("c.txt");			//创建输出流对象,关联c.txt
			
			int b;
			while((b = sis.read()) != -1) {									//用整合后的读
				fos.write(b);												//写到指定文件上
			}
			
			sis.close();
			fos.close(); 
### 22.02_IO流(序列流整合多个)(了解)
* 整合多个: SequenceInputStream(Enumeration)
* 
		FileInputStream fis1 = new FileInputStream("a.txt");	//创建输入流对象,关联a.txt
		FileInputStream fis2 = new FileInputStream("b.txt");	//创建输入流对象,关联b.txt
		FileInputStream fis3 = new FileInputStream("c.txt");	//创建输入流对象,关联c.txt
		Vector<InputStream> v = new Vector<>();					//创建vector集合对象
		v.add(fis1);								//将流对象添加
		v.add(fis2);
		v.add(fis3);
		Enumeration<InputStream> en = v.elements();				//获取枚举引用
		SequenceInputStream sis = new SequenceInputStream(en);	//传递给SequenceInputStream构造
		FileOutputStream fos = new FileOutputStream("d.txt");
		int b;
		while((b = sis.read()) != -1) {
			fos.write(b);
		}
	
		sis.close();
		fos.close();

### 22.03_IO流(内存输出流*****)(掌握)  

* 1.什么是内存输出流
	* 该输出流可以向内存中写数据, 把内存当作一个缓冲区, 写出之后可以一次性获取出所有数据
* 2.使用方式
	* 创建对象: new ByteArrayOutputStream()
	* 写出数据: write(int), write(byte[])
	* 获取数据: toByteArray()
	* 
			FileInputStream fis = new FileInputStream("a.txt");
			ByteArrayOutputStream baos = new ByteArrayOutputStream();
			int b;
			while((b = fis.read()) != -1) {
				baos.write(b);
			}
			
			//byte[] newArr = baos.toByteArray();				//将内存缓冲区中所有的字节存储在newArr中
			//System.out.println(new String(newArr));
			System.out.println(baos);
			fis.close();
### 22.04_IO流(内存输出流之黑马面试题)(掌握)
* 定义一个文件输入流,调用read(byte[] b)方法,将a.txt文件中的内容打印出来(byte数组大小限制为5)
* 
			FileInputStream fis = new FileInputStream("a.txt");			//创建字节输入流,关联a.txt
			ByteArrayOutputStream baos = new ByteArrayOutputStream();		//创建内存输出流
			byte[] arr = new byte[5];						//创建字节数组,大小为5
			int len;
			while((len = fis.read(arr)) != -1) {					//将文件上的数据读到字节数组中
				baos.write(arr, 0, len);					//将字节数组的数据写到内存缓冲区中
			}
			System.out.println(baos);						//将内存缓冲区的内容转换为字符串打印
			fis.close();
### 22.05_IO流(随机访问流概述和读写数据)(了解)
* A:随机访问流概述
	* RandomAccessFile概述
	* RandomAccessFile类不属于流，是Object类的子类。但它融合了InputStream和OutputStream的功能。
	* 支持对随机访问文件的读取和写入。

* B:read(),write(),seek()
	
### 22.06_IO流(对象操作流ObjecOutputStream)(了解)
* 1.什么是对象操作流
	* 该流可以将一个对象写出, 或者读取一个对象到程序中. 也就是执行了序列化和反序列化的操作.
* 2.使用方式
	* 写出: new ObjectOutputStream(OutputStream), writeObject()

			public class Demo3_ObjectOutputStream {
	
				/**
				 * @param args
				 * @throws IOException 
				 * 将对象写出,序列化
				 */
				public static void main(String[] args) throws IOException {
					Person p1 = new Person("张三", 23);
					Person p2 = new Person("李四", 24);
			//		FileOutputStream fos = new FileOutputStream("e.txt");
			//		fos.write(p1);
			//		FileWriter fw = new FileWriter("e.txt");
			//		fw.write(p1);
					//无论是字节输出流,还是字符输出流都不能直接写出对象
					ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("e.txt"));//创建对象输出流
					oos.writeObject(p1);
					oos.writeObject(p2);
					oos.close();
				}
			
			}
### 22.07_IO流(对象操作流ObjectInputStream)(了解)
* 读取: new ObjectInputStream(InputStream), readObject()
	* 
			public class Demo3_ObjectInputStream {

				/**
				 * @param args
				 * @throws IOException 
				 * @throws ClassNotFoundException 
				 * @throws FileNotFoundException 
				 * 读取对象,反序列化
				 */
				public static void main(String[] args) throws IOException, ClassNotFoundException {
					ObjectInputStream ois = new ObjectInputStream(new FileInputStream("e.txt"));
					Person p1 = (Person) ois.readObject();
					Person p2 = (Person) ois.readObject();
					System.out.println(p1);
					System.out.println(p2);
					ois.close();
				}
			
			}
	
### 22.08_IO流(对象操作流优化)(了解)
*　将对象存储在集合中写出

	Person p1 = new Person("张三", 23);
	Person p2 = new Person("李四", 24);
	Person p3 = new Person("马哥", 18);
	Person p4 = new Person("辉哥", 20);
	
	ArrayList<Person> list = new ArrayList<>();
	list.add(p1);
	list.add(p2);
	list.add(p3);
	list.add(p4);
	
	ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("f.txt"));
	oos.writeObject(list);									//写出集合对象
	
	oos.close();
* 读取到的是一个集合对象

		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("f.txt"));
			ArrayList<Person> list = (ArrayList<Person>)ois.readObject();	//泛型在运行期会被擦除,索引运行期相当于没有泛型
		//想去掉黄色可以加注解			
		@SuppressWarnings("unchecked")
			for (Person person : list) {
				System.out.println(person);
			}
		
		ois.close();
### 22.09_IO流(加上id号)(了解)
* 注意
	* 要写出的对象必须实现Serializable接口才能被序列化
	* 不用必须加id号

### 22.10_IO流(数据输入输出流)(了解)
* 1.什么是数据输入输出流
	* DataInputStream, DataOutputStream可以按照基本数据类型大小读写数据
	* 例如按Long大小写出一个数字, 写出时该数据占8字节. 读取的时候也可以按照Long类型读取, 一次读取8个字节.
* 2.使用方式
	* DataOutputStream(OutputStream), writeInt(), writeLong() 

			DataOutputStream dos = new DataOutputStream(new FileOutputStream("b.txt"));
			dos.writeInt(997);
			dos.writeInt(998);
			dos.writeInt(999);
			
			dos.close();
	* DataInputStream(InputStream), readInt(), readLong()

			DataInputStream dis = new DataInputStream(new FileInputStream("b.txt"));
			int x = dis.readInt();
			int y = dis.readInt();
			int z = dis.readInt();
			System.out.println(x);
			System.out.println(y);
			System.out.println(z);
			dis.close();

### 22.11_IO流(打印流的概述和特点)(掌握)
* 1.什么是打印流
	* 该流可以很方便的将对象的toString()结果输出, 并且自动加上换行, 而且可以使用自动刷出的模式
	* System.out就是一个PrintStream, 其默认向控制台输出信息

			PrintStream ps = System.out;
			ps.println(97);					//其实底层用的是Integer.toString(x),将x转换为数字字符串打印
			ps.println("xxx");
			ps.println(new Person("张三", 23));
			Person p = null;
			ps.println(p);					//如果是null,就返回null,如果不是null,就调用对象的toString()
* 2.使用方式
	* 打印: print(), println()
	* 自动刷出: PrintWriter(OutputStream out, boolean autoFlush, String encoding) 
	* 打印流只操作数据目的
	* PrintStream和PrintWriter分别是打印的字节流和字符流,只操作数据目的的

			PrintWriter pw = new PrintWriter(new FileOutputStream("g.txt"), true);
			pw.write(97);					//查找码表,找到对应的a并打印
			pw.print("大家好");
			pw.println("你好");				//自动刷出,只针对的是println方法
			pw.close();

### 22.12_IO流(标准输入输出流概述和输出语句)
* 1.什么是标准输入输出流(掌握)
	* System.in是InputStream, 标准输入流, 默认可以从键盘输入读取字节数据
	* System.out是PrintStream, 标准输出流, 默认可以向Console中输出字符和字节数据
* 2.修改标准输入输出流(了解)
	* 修改输入流: System.setIn(InputStream)
	* 修改输出流: System.setOut(PrintStream)
	* 
			System.setIn(new FileInputStream("a.txt"));				//修改标准输入流
			System.setOut(new PrintStream("b.txt"));				//修改标准输出流
			
			InputStream in = System.in;						//获取标准输入流
			PrintStream ps = System.out;						//获取标准输出流
			int b;
			while((b = in.read()) != -1) {						//从a.txt上读取数据
				ps.write(b);							//将数据写到b.txt上
			}
			
			in.close();
			ps.close();

### 22.13_IO流(修改标准输入输出流拷贝图片)(了解)
		System.setIn(new FileInputStream("IO图片.png"));		//改变标准输入流
		System.setOut(new PrintStream("copy.png")); 		//改变标准输出流
		
		InputStream is = System.in;				//获取标准输入流
		PrintStream ps = System.out;				//获取标准输出流
		
		int len;
		byte[] arr = new byte[1024 * 8];
		
		while((len = is.read(arr)) != -1) {
			ps.write(arr, 0, len);
		}
		
		is.close();
		ps.close();
### 22.14_IO流(两种方式实现键盘录入)(了解)
* A:BufferedReader的readLine方法。
	* BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
* B:Scanner


### 22.15_IO流(Properties的概述和作为Map集合的使用)(了解)
* A:Properties的概述
	* Properties 类表示了一个持久的属性集。
	* Properties 可保存在流中或从流中加载。
	* 属性列表中每个键及其对应值都是一个字符串。 
* B:案例演示
	* Properties作为Map集合的使用
	
### 22.16_IO流(Properties的特殊功能使用)(了解)
* A:Properties的特殊功能
	* public Object setProperty(String key,String value)
	* public String getProperty(String key)
	* public Enumeration<String> stringPropertyNames()
* B:案例演示
	* Properties的特殊功能
	
### 22.17_IO流(Properties的load()和store()功能)(了解)
* A:Properties的load()和store()功能
* B:案例演示
	* Properties的load()和store()功能
	
### 23.注意递归传递值的时候不要用var++或者++var就可以了，因为返回的时候会改变var的值，直接用var + 1就可以了。  
  

### 24.01_多线程(多线程的引入)(了解)
* 1.什么是线程
	* 线程是程序执行的一条路径, 一个进程中可以包含多条线程
	* 多线程并发执行可以提高程序的效率, 可以同时完成多项工作
* 2.多线程的应用场景
	* 红蜘蛛同时共享屏幕给多个电脑
	* 迅雷开启多条线程一起下载
	* QQ同时和多个人一起视频
	* 服务器同时处理多个客户端请求
	
### 24.02_多线程(多线程并行和并发的区别)(了解)
* 并行就是两个任务同时运行，就是甲任务进行的同时，乙任务也在进行。(需要多核CPU)
* 并发是指两个任务都请求运行，而处理器只能按受一个任务，就把这两个任务安排轮流进行，由于时间间隔较短，使人感觉两个任务都在运行。
* 比如我跟两个网友聊天，左手操作一个电脑跟甲聊，同时右手用另一台电脑跟乙聊天，这就叫并行。
* 如果用一台电脑我先给甲发个消息，然后立刻再给乙发消息，然后再跟甲聊，再跟乙聊。这就叫并发。

### 24.03_多线程(Java程序运行原理和JVM的启动是多线程的吗)(了解)
* A:Java程序运行原理
	* Java命令会启动java虚拟机，启动JVM，等于启动了一个应用程序，也就是启动了一个进程。该进程会自动启动一个 “主线程” ，然后主线程去调用某个类的 main 方法。
	
* B:JVM的启动是多线程的吗
	* JVM启动至少启动了垃圾回收线程和主线程，所以是多线程的。

### 24.04_多线程(多线程程序实现的方式1)(掌握)
* 1.继承Thread
	* 定义类继承Thread
	* 重写run方法
	* 把新线程要做的事写在run方法中
	* 创建线程对象
	* 开启新线程, 内部会自动执行run方法
	* 
		
			public class Demo2_Thread {
		
				/**
				 * @param args
				 */
				public static void main(String[] args) {
					MyThread mt = new MyThread();						//4,创建自定义类的对象
					mt.start();								//5,开启线程
					
					for(int i = 0; i < 3000; i++) {
						System.out.println("bb");
					}
				}
			
			}
			class MyThread extends Thread {								//1,定义类继承Thread
				public void run() {								//2,重写run方法
					for(int i = 0; i < 3000; i++) {						//3,将要执行的代码,写在run方法中
						System.out.println("aaaaaaaaaaaaaaaaaaaaaaaaaaaa");
					}
				}
			}

### 24.05_多线程(多线程程序实现的方式2)(掌握)
* 2.实现Runnable
	* 定义类实现Runnable接口
	* 实现run方法
	* 把新线程要做的事写在run方法中
	* 创建自定义的Runnable的子类对象
	* 创建Thread对象, 传入Runnable
	* 调用start()开启新线程, 内部会自动调用Runnable的run()方法

			public class Demo3_Runnable {
				/**
				 * @param args
				 */
				public static void main(String[] args) {
					MyRunnable mr = new MyRunnable();					//4,创建自定义类对象
					//Runnable target = new MyRunnable();
					Thread t = new Thread(mr);						//5,将其当作参数传递给Thread的构造函数
					t.start();								//6,开启线程
					
					for(int i = 0; i < 3000; i++) {
						System.out.println("bb");
					}
				}
			}
			
			class MyRunnable implements Runnable {							//1,自定义类实现Runnable接口
				@Override
				public void run() {								//2,重写run方法
					for(int i = 0; i < 3000; i++) {						//3,将要执行的代码,写在run方法中
						System.out.println("aaaaaaaaaaaaaaaaaaaaaaaaaaaa");
					}
				}
				
			}

### 24.06_多线程(实现Runnable的原理)(了解)
* 查看源码
	* 1,看Thread类的构造函数,传递了Runnable接口的引用 
	* 2,通过init()方法找到传递的target给成员变量的target赋值
	* 3,查看run方法,发现run方法中有判断,如果target不为null就会调用Runnable接口子类对象的run方法

### 24.07_多线程(两种方式的区别)(掌握)
* 查看源码的区别:
	* a.继承Thread : 由于子类重写了Thread类的run(), 当调用start()时, 直接找子类的run()方法
	* b.实现Runnable : 构造函数中传入了Runnable的引用, 成员变量记住了它, start()调用run()方法时内部判断成员变量Runnable的引用是否为空, 不为空编译时看的是Runnable的run(),运行时执行的是子类的run()方法
	
* 继承Thread
	* 好处是:可以直接使用Thread类中的方法,代码简单
	* 弊端是:如果已经有了父类,就不能用这种方法
* 实现Runnable接口
	* 好处是:即使自己定义的线程类有了父类也没关系,因为有了父类也可以实现接口,而且接口是可以多实现的
	* 弊端是:不能直接使用Thread中的方法需要先获取到线程对象后,才能得到Thread的方法,代码复杂
### 24.08_多线程(匿名内部类实现线程的两种方式)(掌握)
* 继承Thread类
	 	
		new Thread() {											//1,new 类(){}继承这个类
			public void run() {									//2,重写run方法
				for(int i = 0; i < 3000; i++) {							//3,将要执行的代码,写在run方法中
					System.out.println("aaaaaaaaaaaaaaaaaaaaaaaaaaaa");
				}
			}
		}.start();
* 实现Runnable接口
			
		new Thread(new Runnable(){									//1,new 接口(){}实现这个接口
			public void run() {									//2,重写run方法
				for(int i = 0; i < 3000; i++) {							//3,将要执行的代码,写在run方法中
					System.out.println("bb");
				}
			}
		}).start(); 

### 24.09_多线程(获取名字和设置名字)(掌握)
* 1.获取名字
	* 通过getName()方法获取线程对象的名字
* 2.设置名字
	* 通过构造函数可以传入String类型的名字
	* 
			new Thread("xxx") {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(this.getName() + "....aaaaaaaaaaaaaaaaaaaaaaa");
					}
				}
			}.start();
			
			new Thread("yyy") {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(this.getName() + "....bb");
					}
				}
			}.start(); 
	* 通过setName(String)方法可以设置线程对象的名字
	* 
			Thread t1 = new Thread() {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(this.getName() + "....aaaaaaaaaaaaaaaaaaaaaaa");
					}
				}
			};
			
			Thread t2 = new Thread() {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(this.getName() + "....bb");
					}
				}
			};
			t1.setName("芙蓉姐姐");
			t2.setName("凤姐");
			
			t1.start();
			t2.start();

### 24.10_多线程(获取当前线程的对象)(掌握)
* Thread.currentThread(), 主线程也可以获取
	* 
			new Thread(new Runnable() {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(Thread.currentThread().getName() + "...aaaaaaaaaaaaaaaaaaaaa");
					}
				}
			}).start();
			
			new Thread(new Runnable() {
				public void run() {
					for(int i = 0; i < 1000; i++) {
						System.out.println(Thread.currentThread().getName() + "...bb");
					}
				}
			}).start();
			Thread.currentThread().setName("我是主线程");		//获取主函数线程的引用,并改名字
			System.out.println(Thread.currentThread().getName());		//获取主函数线程的引用,并获取名字
### 24.11_多线程(休眠线程)(掌握)
* Thread.sleep(毫秒,纳秒), 控制当前线程休眠若干毫秒1秒= 1000毫秒 1秒 = 1000 * 1000 * 1000纳秒 1000000000

			new Thread() {
				public void run() {
					for(int i = 0; i < 10; i++) {
						System.out.println(getName() + "...aaaaaaaaaaaaaaaaaaaaaa");
						try {
							Thread.sleep(10);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
					}
				}
			}.start();
			
			new Thread() {
				public void run() {
					for(int i = 0; i < 10; i++) {
						System.out.println(getName() + "...bb");
						try {
							Thread.sleep(10);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
					}
				}
			}.start();
### 24.12_多线程(守护线程)(掌握)
* setDaemon(), 设置一个线程为守护线程, 该线程不会单独执行, 当其他非守护线程都执行结束后, 自动退出
	* 
			Thread t1 = new Thread() {
				public void run() {
					for(int i = 0; i < 50; i++) {
						System.out.println(getName() + "...aaaaaaaaaaaaaaaaaaaaaa");
						try {
							Thread.sleep(10);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
					}
				}
			};
			
			Thread t2 = new Thread() {
				public void run() {
					for(int i = 0; i < 5; i++) {
						System.out.println(getName() + "...bb");
						try {
							Thread.sleep(10);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
					}
				}
			};
			
			t1.setDaemon(true);					//将t1设置为守护线程
			
			t1.start();
			t2.start(); 
### 24.13_多线程(加入线程)(掌握)
* join(), 当前线程暂停, 等待指定的线程执行结束后, 当前线程再继续
* join(int), 可以等待指定的毫秒之后继续
	* 
			final Thread t1 = new Thread() {
				public void run() {
					for(int i = 0; i < 50; i++) {
						System.out.println(getName() + "...aaaaaaaaaaaaaaaaaaaaaa");
						try {
							Thread.sleep(10);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
					}
				}
			};
			
			Thread t2 = new Thread() {
				public void run() {
					for(int i = 0; i < 50; i++) {
						if(i == 2) {
							try {
								//t1.join();					//插队,加入
								t1.join(30);					//加入,有固定的时间,过了固定时间,继续交替执行
								Thread.sleep(10);
							} catch (InterruptedException e) {
								
								e.printStackTrace();
							}
						}
						System.out.println(getName() + "...bb");
					
					}
				}
			};
			
			t1.start();
			t2.start();
### 24.14_多线程(礼让线程)(了解)
* yield让出cpu

### 24.15_多线程(设置线程的优先级)(了解)
* setPriority()设置线程的优先级

### 24.16_多线程(同步代码块)(掌握)
* 1.什么情况下需要同步
	* 当多线程并发, 有多段代码同时执行时, 我们希望某一段代码执行的过程中CPU不要切换到其他线程工作. 这时就需要同步.
	* 如果两段代码是同步的, 那么同一时间只能执行一段, 在一段代码没执行结束之前, 不会执行另外一段代码.
* 2.同步代码块
	* 使用synchronized关键字加上一个锁对象来定义一段代码, 这就叫同步代码块
	* 多个同步代码块如果使用相同的锁对象, 那么他们就是同步的
	* 匿名内部类使用局部变量，这个局部变量必须用final修饰

			class Printer {
				Demo d = new Demo();
				public static void print1() {
					synchronized(d){			//锁对象可以是任意对象,但是被锁的代码需要保证是同一把锁,不能用匿名对象
						System.out.print("黑");
						System.out.print("马");
						System.out.print("程");
						System.out.print("序");
						System.out.print("员");
						System.out.print("\r\n");
					}
				}
	
				public static void print2() {	
					synchronized(d){			//锁对象不能用匿名对象,因为匿名对象不是同一个对象
						System.out.print("传");
						System.out.print("智");
						System.out.print("播");
						System.out.print("客");
						System.out.print("\r\n");
					}
				}
			}
### 24.17_多线程(同步方法)(掌握)
* 使用synchronized关键字修饰一个方法, 该方法中所有的代码都是同步的

		class Printer {
			public static void print1() {
				synchronized(Printer.class){			//锁对象可以是任意对象,但是被锁的代码需要保证是同一把锁,不能用匿名对象
					System.out.print("黑");
					System.out.print("马");
					System.out.print("程");
					System.out.print("序");
					System.out.print("员");
					System.out.print("\r\n");
				}
			}
			/*
			 * 非静态同步函数的锁是:this
			 * 静态的同步函数的锁是:字节码对象
			 */
			public static synchronized void print2() {	
				System.out.print("传");
				System.out.print("智");
				System.out.print("播");
				System.out.print("客");
				System.out.print("\r\n");
			}
		}

### 24.18_多线程(线程安全问题)(掌握)
* 多线程并发操作同一数据时, 就有可能出现线程安全问题
* 使用同步技术可以解决这种问题, 把操作数据的代码进行同步, 不要多个线程一起操作
			
			public class Demo2_Synchronized {

				/**
				 * @param args
				 * 需求:铁路售票,一共100张,通过四个窗口卖完.
				 */
				public static void main(String[] args) {
					TicketsSeller t1 = new TicketsSeller();
					TicketsSeller t2 = new TicketsSeller();
					TicketsSeller t3 = new TicketsSeller();
					TicketsSeller t4 = new TicketsSeller();
					
					t1.setName("窗口1");
					t2.setName("窗口2");
					t3.setName("窗口3");
					t4.setName("窗口4");
					t1.start();
					t2.start();
					t3.start();
					t4.start();
				}
			
			}
			
			class TicketsSeller extends Thread {
				private static int tickets = 100;
				static Object obj = new Object();
				public TicketsSeller() {
					super();
					
				}
				public TicketsSeller(String name) {
					super(name);
				}
				public void run() {
					while(true) {
						synchronized(obj) {
							if(tickets <= 0) 
								break;
							try {
								Thread.sleep(10);//线程1睡,线程2睡,线程3睡,线程4睡
							} catch (InterruptedException e) {
								
								e.printStackTrace();
							}
							System.out.println(getName() + "...这是第" + tickets-- + "号票");
						}
					}
				}
			}

### 24.19_多线程(火车站卖票的例子用实现Runnable接口)(掌握)


### 24.20_多线程(死锁)(了解)
* 多线程同步的时候, 如果同步代码嵌套, 使用相同锁, 就有可能出现死锁
	* 尽量不要嵌套使用
		
			private static String s1 = "筷子左";
			private static String s2 = "筷子右";
			public static void main(String[] args) {
				new Thread() {
					public void run() {
						while(true) {
							synchronized(s1) {
								System.out.println(getName() + "...拿到" + s1 + "等待" + s2);
								synchronized(s2) {
									System.out.println(getName() + "...拿到" + s2 + "开吃");
								}
							}
						}
					}
				}.start();
				
				new Thread() {
					public void run() {
						while(true) {
							synchronized(s2) {
								System.out.println(getName() + "...拿到" + s2 + "等待" + s1);
								synchronized(s1) {
									System.out.println(getName() + "...拿到" + s1 + "开吃");
								}
							}
						}
					}
				}.start();
			}

### 24.21_多线程(以前的线程安全的类回顾)(掌握)
* A:回顾以前说过的线程安全问题
	* 看源码：Vector,StringBuffer,Hashtable,Collections.synchroinzed(xxx)
	* Vector是线程安全的,ArrayList是线程不安全的
	* StringBuffer是线程安全的,StringBuilder是线程不安全的
	* Hashtable是线程安全的,HashMap是线程不安全的
	* 线程安全主要是添加了synchronized.
### 24.22_多线程(总结)	

### 25.01_多线程(单例设计模式)(掌握)
* 单例设计模式：保证类在内存中只有一个对象。

* 如何保证类在内存中只有一个对象呢？
	* (1)控制类的创建，不让其他类来创建本类的对象。private
	* (2)在本类中定义一个本类的对象。Singleton s;
	* (3)提供公共的访问方式。  public static Singleton getInstance(){return s}
* 单例写法两种：
	* (1)饿汉式 开发用这种方式。
	* 
			//饿汉式（上来着急就new对象，就使用了）
			class Singleton {
				//1,私有构造函数
				private Singleton(){}
				//2,创建本类对象
				private static Singleton s = new Singleton();
				//3,对外提供公共的访问方法
				public static Singleton getInstance() {
					return s;
				}
				
				public static void print() {
					System.out.println("11111111111");
				}
			}
	* (2)懒汉式 面试写这种方式。多线程的问题？
	* 
			//懒汉式,单例的延迟加载模式
			class Singleton {
				//1,私有构造函数
				private Singleton(){}
				//2,声明一个本类的引用
				private static Singleton s;
				//3,对外提供公共的访问方法
				public static Singleton getInstance() {
					if(s == null)
						//线程1,线程2。缺点：在多线程访问的时候有可能会创建多个对象
						s = new Singleton();
					return s;
				}
				
				public static void print() {
					System.out.println("11111111111");
				}
			}
			
* 饿汉式和懒汉式的区别：
	* 1,饿汉式是空间换时间,懒汉式是时间换空间
	* 2,在多线程访问时,饿汉式不会创建多个对象,而懒汉式有可能会创建多个对象
 
	* (3)第三种格式（没有名字）
	* 
			class Singleton {
				private Singleton() {}
			
				public static final Singleton s = new Singleton();//final是最终的意思,被final修饰的变量不可以被更改
			}
### 25.02_多线程(Runtime类)
* Runtime类是一个单例类
	* 
			Runtime r = Runtime.getRuntime();
			//r.exec("shutdown -s -t 300");		//300秒后关机
			r.exec("shutdown -a");			//取消关机

### 25.03_多线程(Timer)(掌握)
* Timer类:计时器

			public class Demo5_Timer {
				/**
				 * @param args
				 * 计时器
				 * @throws InterruptedException 
				 */
				public static void main(String[] args) throws InterruptedException {
					Timer t = new Timer();
					//在指定时间安排指定任务
					//第一个参数,是安排的任务,第二个参数是执行的时间,第三个参数是过多长时间再重复执行
					t.schedule(new MyTimerTask(), new Date(114,9,15,10,54,20),3000);
					
					while(true) {
						System.out.println(new Date());
						Thread.sleep(1000);
					}
				}
			}
			class MyTimerTask extends TimerTask {
				@Override
				public void run() {
					System.out.println("起床背英语单词");
				}
				
			}

### 25.04_多线程(两个线程间的通信)(掌握)
* 1.什么时候需要通信
	* 多个线程并发执行时, 在默认情况下CPU是随机切换线程的
	* 如果我们希望他们有规律的执行, 就可以使用通信, 例如每个线程执行一次打印
* 2.怎么通信
	* 如果希望线程等待, 就调用wait()
	* 如果希望唤醒等待的线程, 就调用notify();
	* 这两个方法必须在同步代码中执行, 并且使用同步锁对象来调用

### 25.05_多线程(三个或三个以上间的线程通信)
* 多个线程通信的问题
	* notify()方法是随机唤醒一个线程
	* notifyAll()方法是唤醒所有线程
	* JDK5之前无法唤醒指定的一个线程
	* 如果多个线程之间通信, 需要使用notifyAll()通知所有线程, 用while来反复判断条件
* if语句是在哪里等待,就在哪里起来
* while循环是循环判断,每次都会判断标记
  
```
/*1,在同步代码块中,用哪个对象锁,就用哪个对象调用wait方法
 * 2,为什么wait方法和notify方法定义在Object这类中?
 * 	因为锁对象可以是任意对象,Object是所有的类的基类,所以wait方法和notify方法需要定义在Object这个类中
 * 3,sleep方法和wait方法的区别?
 * a,sleep方法必须传入参数,参数就是时间,时间到了自动醒来
 *   wait方法可以传入参数也可以不传入参数,传入参数就是在参数的时间结束后等待,不传入参数就是直接等待
 * b,sleep方法在同步函数或同步代码块中,不释放锁,睡着了也抱着锁睡
 * 	wait方法在同步函数或者同步代码块中,释放锁
 */ 
```

### 25.06_多线程(JDK1.5的新特性互斥锁)(掌握)
* 1.同步
	* 使用ReentrantLock类的lock()和unlock()方法进行同步
* 2.通信
	* 使用ReentrantLock类的newCondition()方法可以获取Condition对象
	* 需要等待的时候使用Condition的await()方法, 唤醒的时候用signal()方法
	* 不同的线程使用不同的Condition, 这样就能区分唤醒的时候找哪个线程了


### 25.07_多线程(线程组的概述和使用)(了解)
* A:线程组概述
	* Java中使用ThreadGroup来表示线程组，它可以对一批线程进行分类管理，Java允许程序直接对线程组进行控制。
	* 默认情况下，所有的线程都属于主线程组。
		* public final ThreadGroup getThreadGroup()//通过线程对象获取他所属于的组
		* public final String getName()//通过线程组对象获取他组的名字
	* 我们也可以给线程设置分组
		* 1,ThreadGroup(String name) 创建线程组对象并给其赋值名字
		* 2,创建线程对象
		* 3,Thread(ThreadGroup?group, Runnable?target, String?name) 
		* 4,设置整组的优先级或者守护线程
	* B:案例演示
		* 线程组的使用,默认是主线程组
* 
		MyRunnable mr = new MyRunnable();
		Thread t1 = new Thread(mr, "张三");
		Thread t2 = new Thread(mr, "李四");
		//获取线程组
		// 线程类里面的方法：public final ThreadGroup getThreadGroup()
		ThreadGroup tg1 = t1.getThreadGroup();
		ThreadGroup tg2 = t2.getThreadGroup();
		// 线程组里面的方法：public final String getName()
		String name1 = tg1.getName();
		String name2 = tg2.getName();
		System.out.println(name1);
		System.out.println(name2);
		// 通过结果我们知道了：线程默认情况下属于main线程组
		// 通过下面的测试，你应该能够看到，默任情况下，所有的线程都属于同一个组
		System.out.println(Thread.currentThread().getThreadGroup().getName());

	* 自己设定线程组
* 			
		// ThreadGroup(String name)
		ThreadGroup tg = new ThreadGroup("这是一个新的组");

		MyRunnable mr = new MyRunnable();
		// Thread(ThreadGroup group, Runnable target, String name)
		Thread t1 = new Thread(tg, mr, "张三");
		Thread t2 = new Thread(tg, mr, "李四");
		
		System.out.println(t1.getThreadGroup().getName());
		System.out.println(t2.getThreadGroup().getName());
		
		//通过组名称设置后台线程，表示该组的线程都是后台线程
		tg.setDaemon(true);
### 25.08_多线程(线程的五种状态)(掌握)
* 看图说话
* 线程状态图:
![线程状态图](https://github.com/Passion-long/Passion-long.github.io/blob/master/Figure/Thread_state_diagram.png)  
* 新建,就绪,运行,阻塞,死亡

### 25.09_多线程(线程池的概述和使用)(了解)
* A:线程池概述
	* 程序启动一个新线程成本是比较高的，因为它涉及到要与操作系统进行交互。而使用线程池可以很好的提高性能，尤其是当程序中要创建大量生存期很短的线程时，更应该考虑使用线程池。线程池里的每一个线程代码结束后，并不会死亡，而是再次回到线程池中成为空闲状态，等待下一个对象来使用。在JDK5之前，我们必须手动实现自己的线程池，从JDK5开始，Java内置支持线程池
* B:内置线程池的使用概述
	* JDK5新增了一个Executors工厂类来产生线程池，有如下几个方法
		* public static ExecutorService newFixedThreadPool(int nThreads)
		* public static ExecutorService newSingleThreadExecutor()
		* 这些方法的返回值是ExecutorService对象，该对象表示一个线程池，可以执行Runnable对象或者Callable对象代表的线程。它提供了如下方法
		* Future<?> submit(Runnable task)
		* <T> Future<T> submit(Callable<T> task)
	* 使用步骤：
		* 创建线程池对象
		* 创建Runnable实例
		* 提交Runnable实例
		* 关闭线程池
	* C:案例演示
		* 提交的是Runnable
* 
		// public static ExecutorService newFixedThreadPool(int nThreads)
		ExecutorService pool = Executors.newFixedThreadPool(2);

		// 可以执行Runnable对象或者Callable对象代表的线程
		pool.submit(new MyRunnable());
		pool.submit(new MyRunnable());

		//结束线程池
		pool.shutdown();
		
### 25.10_多线程(多线程程序实现的方式3)(了解)
* 提交的是Callable

* 
		// 创建线程池对象
		ExecutorService pool = Executors.newFixedThreadPool(2);

		// 可以执行Runnable对象或者Callable对象代表的线程
		Future<Integer> f1 = pool.submit(new MyCallable(100));
		Future<Integer> f2 = pool.submit(new MyCallable(200));

		// V get()
		Integer i1 = f1.get();
		Integer i2 = f2.get();

		System.out.println(i1);
		System.out.println(i2);

		// 结束
		pool.shutdown();

		public class MyCallable implements Callable<Integer> {

			private int number;
		
			public MyCallable(int number) {
				this.number = number;
			}
		
			@Override
			public Integer call() throws Exception {
				int sum = 0;
				for (int x = 1; x <= number; x++) {
					sum += x;
				}
				return sum;
			}
		
		}
		
* 线程的第三种实现方式：
	* 自定义一个类，实现Callable，然后重写里面的call方法（有返回值，可以抛出异常）
* 多线程程序实现的方式3的好处和弊端
	* 好处：
		* 可以有返回值
		* 可以抛出异常
		
	* 弊端：
		* 代码比较复杂，所以一般不用


### 25.11_设计模式(简单工厂模式概述和使用)(了解)
* A:简单工厂模式概述
	* 又叫静态工厂方法模式，它定义一个具体的工厂类负责创建一些类的实例
* B:优点
	* 客户端不需要在负责对象的创建，从而明确了各个类的职责
* C:缺点
	* 这个静态工厂类负责所有对象的创建，如果有新的对象增加，或者某些对象的创建方式不同，就需要不断的修改工厂类，不利于后期的维护
* D:案例演示
	* 动物抽象类：public abstract Animal { public abstract void eat(); }
	* 具体狗类：public class Dog extends Animal {}
	* 具体猫类：public class Cat extends Animal {}
	* 开始，在测试类中每个具体的内容自己创建对象，但是，创建对象的工作如果比较麻烦，就需要有人专门做这个事情，所以就知道了一个专门的类来创建对象。
* 
		public class AnimalFactory {
			private AnimalFactory(){}
		
			//public static Dog createDog() {return new Dog();}
			//public static Cat createCat() {return new Cat();}
		
			//改进
			public static Animal createAnimal(String animalName) {
				if(“dog”.equals(animalName)) {}
				else if(“cat”.equals(animale)) {
		
				}else {
					return null;
				}
			}
		} 
### 25.12_设计模式(工厂方法模式的概述和使用)(了解)
* A:工厂方法模式概述
	* 工厂方法模式中抽象工厂类负责定义创建对象的接口，具体对象的创建工作由继承抽象工厂的具体类实现。
* B:优点
	* 客户端不需要在负责对象的创建，从而明确了各个类的职责，如果有新的对象增加，只需要增加一个具体的类和具体的工厂类即可，不影响已有的代码，后期维护容易，增强了系统的扩展性
* C:缺点
	* 需要额外的编写代码，增加了工作量
* D:案例演示
* 
		动物抽象类：public abstract Animal { public abstract void eat(); }
		工厂接口：public interface Factory {public abstract Animal createAnimal();}
		具体狗类：public class Dog extends Animal {}
		具体猫类：public class Cat extends Animal {}
		开始，在测试类中每个具体的内容自己创建对象，但是，创建对象的工作如果比较麻烦，就需要有人专门做这个事情，所以就知道了一个专门的类来创建对象。发现每次修改代码太麻烦，用工厂方法改进，针对每一个具体的实现提供一个具体工厂。
		狗工厂：public class DogFactory implements Factory {
			public Animal createAnimal() {…}
		        }
		猫工厂：public class CatFactory implements Factory {
			public Animal createAnimal() {…}
		        }  

### 25.13_GUI(如何创建一个窗口并显示)
* Graphical User Interface(图形用户接口)。
* 
		Frame  f = new Frame(“my window”);
		f.setLayout(new FlowLayout());//设置布局管理器
		f.setSize(500,400);//设置窗体大小
		f.setLocation(300,200);//设置窗体出现在屏幕的位置
		f.setIconImage(Toolkit.getDefaultToolkit().createImage("qq.png"));
		f.setVisible(true);

### 25.14_GUI(布局管理器)
* FlowLayout（流式布局管理器）
	* 从左到右的顺序排列。
	* Panel默认的布局管理器。
* BorderLayout（边界布局管理器）
	* 东，南，西，北，中
	* Frame默认的布局管理器。
* GridLayout（网格布局管理器）
	* 规则的矩阵
* CardLayout（卡片布局管理器）
	* 选项卡
* GridBagLayout（网格包布局管理器）
	* 非规则的矩阵
### 25.15_GUI(窗体监听)
	Frame f = new Frame("我的窗体");
	//事件源是窗体,把监听器注册到事件源上
	//事件对象传递给监听器
	f.addWindowListener(new WindowAdapter() {
	          public void windowClosing(WindowEvent e) {
	                     //退出虚拟机,关闭窗口
			System.exit(0);
		}
	});

### 25.16_GUI(鼠标监听)
### 25.17_GUI(键盘监听和键盘事件)
### 25.18_GUI(动作监听)
### 25.19_设计模式(适配器设计模式)(掌握)
* a.什么是适配器
	* 在使用监听器的时候, 需要定义一个类事件监听器接口.
	* 通常接口中有多个方法, 而程序中不一定所有的都用到, 但又必须重写, 这很繁琐.
	* 适配器简化了这些操作, 我们定义监听器时只要继承适配器, 然后重写需要的方法即可.
* b.适配器原理
	* **适配器就是一个类, 实现了监听器接口, 所有抽象方法都重写了, 但是方法全是空的.**
	* 适配器类需要定义成抽象的,因为创建该类对象,调用空方法是没有意义的
	* 目的就是为了简化程序员的操作, 定义监听器时继承适配器, 只重写需要的方法就可以了.
```
package com.heima.适配器;

public class Demo1_Adapter {

	/**
	 * @param args
	 * 适配器设计模式
	 * 鲁智深
	 */
	public static void main(String[] args) {
		
	}

}

interface 和尚 {
	public void 打坐();
	public void 念经();
	public void 撞钟();
	public void 习武();
}

abstract class 天罡星 implements 和尚 {		//声明成抽象的原因是,不想让其他类创建本类对象,因为创建也没有意义,方法都是空的

	@Override
	public void 打坐() {
	}

	@Override
	public void 念经() {
	}

	@Override
	public void 撞钟() {
	}

	@Override
	public void 习武() {
	}
	
}

class 鲁智深 extends 天罡星 {
	public void 习武() {
		System.out.println("倒拔垂杨柳");
		System.out.println("拳打镇关西");
		System.out.println("大闹野猪林");
		System.out.println("......");
	}
}
```
### 25.20_GUI(需要知道的) 
* 事件处理
	* 事件: 用户的一个操作
	* 事件源: 被操作的组件
	* 监听器: 一个自定义类的对象, 实现了监听器接口, 包含事件处理方法,把监听器添加在事件源上, 当事件发生的时候虚拟机就会自动调用监听器中的事件处理方法
### 25.21_day25总结
	把今天的知识点总结一遍。

### 26.01_网络编程(网络编程概述)(了解)
* A:计算机网络
	* 是指将地理位置不同的具有独立功能的多台计算机及其外部设备，通过通信线路连接起来，在网络操作系统，网络管理软件及网络通信协议的管理和协调下，实现资源共享和信息传递的计算机系统。
* B:网络编程
	* 就是用来实现网络互连的不同计算机上运行的程序间可以进行数据交换。


### 26.02_网络编程(网络编程三要素之IP概述)(掌握)
* 每个设备在网络中的唯一标识
* 每台网络终端在网络中都有一个独立的地址，我们在网络中传输数据就是使用这个地址。 
* ipconfig：查看本机IP192.168.12.42
* ping：测试连接192.168.40.62
* 本地回路地址：127.0.0.1 255.255.255.255是广播地址
* IPv4：4个字节组成，4个0-255。大概42亿，30亿都在北美，亚洲4亿。2011年初已经用尽。 
* IPv6：8组，每组4个16进制数。
* 1a2b:0000:aaaa:0000:0000:0000:aabb:1f2f
* 1a2b::aaaa:0000:0000:0000:aabb:1f2f
* 1a2b:0000:aaaa::aabb:1f2f
* 1a2b:0000:aaaa::0000:aabb:1f2f
* 1a2b:0000:aaaa:0000::aabb:1f2f

### 26.03_网络编程(网络编程三要素之端口号概述)(掌握)
* 每个程序在设备上的唯一标识
* 每个网络程序都需要绑定一个端口号，传输数据的时候除了确定发到哪台机器上，还要明确发到哪个程序。
* 端口号范围从0-65535
* 编写网络应用就需要绑定一个端口号，尽量使用1024以上的，1024以下的基本上都被系统程序占用了。
* 常用端口
	* mysql: 3306
	* oracle: 1521
	* web: 80
	* tomcat: 8080
	* QQ: 4000
	* feiQ: 2425

### 26.04_网络编程(网络编程三要素协议)(掌握)
* 为计算机网络中进行数据交换而建立的规则、标准或约定的集合。
* UDP
	* 面向无连接，数据不安全，速度快。不区分客户端与服务端。
* TCP
　　* 面向连接（三次握手），数据安全，速度略低。分为客户端和服务端。
	* 三次握手: 客户端先向服务端发起请求, 服务端响应请求, 传输数据


### 26.05_网络编程(Socket通信原理图解)(了解)
* A:Socket套接字概述：
	* 网络上具有唯一标识的IP地址和端口号组合在一起才能构成唯一能识别的标识符套接字。
	* 通信的两端都有Socket。
	* 网络通信其实就是Socket间的通信。
	* 数据在两个Socket间通过IO流传输。
	* Socket在应用程序中创建，通过一种绑定机制与驱动程序建立关系，告诉自己所对应的IP和port。

### 26.06_网络编程(UDP传输)(了解)
* 1.发送Send
	* 创建DatagramSocket, 随机端口号
	* 创建DatagramPacket, 指定数据, 长度, 地址, 端口
	* 使用DatagramSocket发送DatagramPacket
	* 关闭DatagramSocket
* 2.接收Receive
	* 创建DatagramSocket, 指定端口号
	* 创建DatagramPacket, 指定数组, 长度
	* 使用DatagramSocket接收DatagramPacket
	* 关闭DatagramSocket
	* 从DatagramPacket中获取数据
* 3.接收方获取ip和端口号
	* String ip = packet.getAddress().getHostAddress();
	* int port = packet.getPort();

### 26.07_网络编程(UDP传输优化)
* 接收端Receive
* 
		DatagramSocket socket = new DatagramSocket(6666);						//创建socket相当于创建码头
		DatagramPacket packet = new DatagramPacket(new byte[1024], 1024);		//创建packet相当于创建集装箱
		
		while(true) {
			socket.receive(packet);												//接收货物
			byte[] arr = packet.getData();
			int len = packet.getLength();
			String ip = packet.getAddress().getHostAddress();
			System.out.println(ip + ":" + new String(arr,0,len));
		}
* 发送端Send

		DatagramSocket socket = new DatagramSocket();		//创建socket相当于创建码头
		Scanner sc = new Scanner(System.in);
		
		while(true) {
			String str = sc.nextLine();
			if("quit".equals(str))
				break;
			DatagramPacket packet = 							//创建packet相当于创建集装箱
					new DatagramPacket(str.getBytes(), str.getBytes().length, InetAddress.getByName("127.0.0.1"), 6666);
			socket.send(packet);			//发货
		}
		socket.close();
### 26.08_网络编程(UDP传输多线程)
* A发送和接收在一个窗口完成

		public class Demo3_MoreThread {

			/**
			 * @param args
			 */
			public static void main(String[] args) {
				new Receive().start();
				
				new Send().start();
			}
		
		}

		class Receive extends Thread {
			public void run() {
				try {
					DatagramSocket socket = new DatagramSocket(6666);					//创建socket相当于创建码头
					DatagramPacket packet = new DatagramPacket(new byte[1024], 1024);	//创建packet相当于创建集装箱
					
					while(true) {
						socket.receive(packet);												//接收货物
						byte[] arr = packet.getData();
						int len = packet.getLength();
						String ip = packet.getAddress().getHostAddress();
						System.out.println(ip + ":" + new String(arr,0,len));
					}
				} catch (IOException e) {
					
					e.printStackTrace();
				}
			}
		}

		class Send extends Thread {
			public void run() {
				try {
					DatagramSocket socket = new DatagramSocket();		//创建socket相当于创建码头
					Scanner sc = new Scanner(System.in);
					
					while(true) {
						String str = sc.nextLine();
						if("quit".equals(str))
							break;
						DatagramPacket packet = 							//创建packet相当于创建集装箱
								new DatagramPacket(str.getBytes(), str.getBytes().length, InetAddress.getByName("127.0.0.1"), 6666);
						socket.send(packet);			//发货
					}
					socket.close();
				}  catch (IOException e) {
					
					e.printStackTrace();
				}
			}
		}


### 26.09_网络编程(UDP聊天图形化界面)
	

### 26.10_网络编程(UDP聊天发送功能)
	
		
### 26.11_网络编程(UDP聊天记录功能)
	
	
### 26.12_网络编程(UDP聊天清屏功能)


### 26.13_网络编程(UDP聊天震动功能)


### 26.14_网络编程(UDP聊天快捷键和代码优化)
	

### 26.15_网络编程(UDP聊天生成jar文件)

### 26.16_网络编程(TCP协议)(掌握)
* 1.客户端
	* 创建Socket连接服务端(指定ip地址,端口号)通过ip地址找对应的服务器
	* 调用Socket的getInputStream()和getOutputStream()方法获取和服务端相连的IO流
	* 输入流可以读取服务端输出流写出的数据
	* 输出流可以写出数据到服务端的输入流
* 2.服务端
	* 创建ServerSocket(需要指定端口号)
	* 调用ServerSocket的accept()方法接收一个客户端请求，得到一个Socket
	* 调用Socket的getInputStream()和getOutputStream()方法获取和客户端相连的IO流
	* 输入流可以读取客户端输出流写出的数据
	* 输出流可以写出数据到客户端的输入流

### 26.17_网络编程(TCP协议代码优化)
* 客户端

		Socket socket = new Socket("127.0.0.1", 9999);		//创建Socket指定ip地址和端口号
		InputStream is = socket.getInputStream();			//获取输入流
		OutputStream os = socket.getOutputStream();			//获取输出流
		BufferedReader br = new BufferedReader(new InputStreamReader(is));
		PrintStream ps = new PrintStream(os);
		
		System.out.println(br.readLine());
		ps.println("我想报名就业班");
		System.out.println(br.readLine());
		ps.println("爷不学了");
		socket.close();
* 服务端

		ServerSocket server = new ServerSocket(9999);	//创建服务器
		Socket socket = server.accept();				//接受客户端的请求
		InputStream is = socket.getInputStream();		//获取输入流
		OutputStream os = socket.getOutputStream();		//获取输出流
		
		BufferedReader br = new BufferedReader(new InputStreamReader(is));
		PrintStream ps = new PrintStream(os);
		
		ps.println("欢迎咨询传智播客");
		System.out.println(br.readLine());
		ps.println("报满了,请报下一期吧");
		System.out.println(br.readLine());
		server.close();
		socket.close();

### 26.18_网络编程(服务端是多线程的)(掌握)
	ServerSocket server = new ServerSocket(9999);	//创建服务器
		while(true) {
			final Socket socket = server.accept();				//接受客户端的请求
			new Thread() {
				public void run() {
					try {
						BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
						PrintStream ps = new PrintStream(socket.getOutputStream());
						ps.println("欢迎咨询传智播客");
						System.out.println(br.readLine());
						ps.println("报满了,请报下一期吧");
						System.out.println(br.readLine());
						socket.close();
					} catch (IOException e) {
						e.printStackTrace();
					}
				}
			}.start();
		}
	}

### 26.19_网络编程(练习)
* 客户端向服务器写字符串(键盘录入),服务器(多线程)将字符串反转后写回,客户端再次读取到是反转后的字符串
### 26.20_网络编程(练习)
* 客户端向服务器上传文件
### 26.21_day26总结
* 把今天的知识点总结一遍。

### 27.01_反射(类的加载概述和加载时机)
* A:类的加载概述
	* 当程序要使用某个类时，如果该类还未被加载到内存中，则系统会通过加载，连接，初始化三步来实现对这个类进行初始化。
	* 加载
		* 就是指将class文件读入内存，并为之创建一个Class对象。任何类被使用时系统都会建立一个Class对象。
	* 连接
		* 验证 是否有正确的内部结构，并和其他类协调一致
		* 准备 负责为类的静态成员分配内存，并设置默认初始化值
		* 解析 将类的二进制数据中的符号引用替换为直接引用
	* 初始化 就是我们以前讲过的初始化步骤

* B:加载时机
	* 创建类的实例
	* 访问类的静态变量，或者为静态变量赋值
	* 调用类的静态方法
	* 使用反射方式来强制创建某个类或接口对应的java.lang.Class对象
	* 初始化某个类的子类
	* 直接使用java.exe命令来运行某个主类
### 27.02_反射(类加载器的概述和分类)
* A:类加载器的概述
	* 负责将.class文件加载到内存中，并为之生成对应的Class对象。虽然我们不需要关心类加载机制，但是了解这个机制我们就能更好的理解程序的运行。
* B:类加载器的分类
	* Bootstrap ClassLoader 根类加载器
	* Extension ClassLoader 扩展类加载器
	* Sysetm ClassLoader 系统类加载器
* C:类加载器的作用
	* Bootstrap ClassLoader 根类加载器
		* 也被称为引导类加载器，负责Java核心类的加载
		* 比如System,String等。在JDK中JRE的lib目录下rt.jar文件中
	* Extension ClassLoader 扩展类加载器
		* 负责JRE的扩展目录中jar包的加载。
		* 在JDK中JRE的lib目录下ext目录
	* Sysetm ClassLoader 系统类加载器
		* 负责在JVM启动时加载来自java命令的class文件，以及classpath环境变量所指定的jar包和类路径

### 27.03_反射(反射概述)
* A:反射概述
	* JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；
	* 对于任意一个对象，都能够调用它的任意一个方法和属性；
	* 这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。
	* 要想解剖一个类,必须先要获取到该类的字节码文件对象。
	* 而解剖使用的就是Class类中的方法，所以先要获取到每一个字节码文件对应的Class类型的对象。
* B:三种方式
	* a:Class类中静态方法forName(),读取配置文件
	* b:静态属性class,锁对象
	* c:Object类的getClass()方法,判断两个对象是否是同一个字节码文件
* C:案例演示
	* 获取class文件对象的三种方式

### 27.04_反射(Class.forName()读取配置文件举例)
榨汁机(Juicer)榨汁的案例
```
分别有水果(Fruit)苹果(Apple)香蕉(Banana)桔子(Orange)榨汁(squeeze)
public class Demo2_Reflect {

    /**
     * 榨汁机(Juicer)榨汁的案例
     * 分别有水果(Fruit)苹果(Apple)香蕉(Banana)桔子(Orange)榨汁(squeeze)
     * @throws Exception
     */
    public static void main(String[] args) throws Exception {
        /*Juicer j = new Juicer();
        //j.run(new Apple());
        j.run(new Orange());*/
        BufferedReader br = new BufferedReader(new FileReader("config.properties"));    //创建输入流对象,关联配置文件
        Class<?> clazz = Class.forName(br.readLine());                                  //读取配置文件一行内容,获取该类的字节码对象
        Fruit f = (Fruit) clazz.newInstance();(被抛弃了)                                         //通过字节码对象创建实例对象
        Juicer j = new Juicer();							//最新的API中java.lang.Class中的newInstance()创建对象的方法被舍弃了，
											//只能通过获取构造器对象的方法来创建对象或者直接通过创建Class对象的方法。
        j.run(f);
    }

}
interface Fruit {
    public void squeeze();
}

class Apple implements Fruit {
    public void squeeze() {
        System.out.println("榨出一杯苹果汁儿");
    }
}

class Orange implements Fruit {
    public void squeeze() {
        System.out.println("榨出一杯桔子汁儿");
    }
}

class Juicer {
    public void run(Fruit f) {
        f.squeeze();
    }

}
```

27.05_反射(通过反射获取带参构造方法并使用)
Constructor
Class类的newInstance()方法是使用该类无参的构造函数创建对象, 如果一个类没有无参的构造函数, 就不能这样创建了,可以调用Class类的getConstructor(String.class,int.class)方法获取一个指定的构造函数然后再调用Constructor类的newInstance("张三",20)方法创建对象

27.06_反射(通过反射获取成员变量并使用)
Field
Class.getField(String)方法可以获取类中的指定字段(可见的), 如果是私有的可以用getDeclaedField("name")方法获取,通过set(obj, "李四")方法可以设置指定对象上该字段的值, 如果是私有的需要先调用setAccessible(true)设置访问权限,用获取的指定的字段调用get(obj)可以获取指定对象中该字段的值

27.07_反射(通过反射获取方法并使用)
Method
Class.getMethod(String, Class...) 和 Class.getDeclaredMethod(String, Class...)方法可以获取类中的指定方法,调用invoke(Object, Object...)可以调用该方法,Class.getMethod("eat") invoke(obj) Class.getMethod("eat",int.class) invoke(obj,10)

27.08_反射(通过反射越过泛型检查)
A:案例演示
ArrayList的一个对象，在这个集合中添加一个字符串数据，如何实现呢？

27.09_反射(通过反射写一个通用的设置某个对象的某个属性为指定的值)
A:案例演示
public void setProperty(Object obj, String propertyName, Object value){}，此方法可将obj对象中名为propertyName的属性的值设置为value。

27.10_反射(练习)
已知一个类，定义如下：
package cn.itcast.heima;
public class DemoClass { public void run() { System.out.println("welcome to heima!"); } }
(1) 写一个Properties格式的配置文件，配置类的完整名称。
(2) 写一个程序，读取这个Properties配置文件，获得类的完整名称并加载这个类，用反射的方式运行run方法。

27.11_反射(动态代理的概述和实现)
A:动态代理概述

代理：本来应该自己做的事情，请了别人来做，被请的人就是代理对象。
举例：春节回家买票让人代买
动态代理：在程序运行过程中产生的这个对象,而程序运行过程中产生对象其实就是我们刚才反射讲解的内容，所以，动态代理其实就是通过反射来生成一个代理
在Java中java.lang.reflect包下提供了一个Proxy类和一个InvocationHandler接口，通过使用这个类和接口就可以生成动态代理对象。JDK提供的代理只能针对接口做代理。我们有更强大的代理cglib，Proxy类中的方法创建动态代理类对象
public static Object newProxyInstance(ClassLoader loader,Class<?>[] interfaces,InvocationHandler h)
最终会调用InvocationHandler的方法
InvocationHandler Object invoke(Object proxy,Method method,Object[] args)

27.12_设计模式(模版(Template)设计模式概述和使用)
A:模版设计模式概述
模版方法模式就是定义一个算法的骨架，而将具体的算法延迟到子类中来实现
B:优点和缺点
a:优点
使用模版方法模式，在定义算法骨架的同时，可以很灵活的实现具体的算法，满足用户灵活多变的需求
b:缺点
如果算法骨架有修改的话，则需要修改抽象类 1,装饰 2,单例 3,简单工厂 4,工厂方法 5,适配器 6,模版

27.13_JDK5新特性(自己实现枚举类)
A:枚举概述
是指将变量的值一一列出来,变量的值只限于列举出来的值的范围内。举例：一周只有7天，一年只有12个月等。
B:回想单例设计模式：单例类是一个类只有一个实例
那么多例类就是一个类有多个实例，但不是无限个数的实例，而是有限个数的实例。这才能是枚举类。
C:案例演示
自己实现枚举类 1,自动拆装箱 2,泛型 3,可变参数 4,静态导入 5,增强for循环 6,互斥锁 7,枚举

27.14_JDK5新特性(通过enum实现枚举类)
A:案例演示
通过enum实现枚举类

27.15_JDK5新特性(枚举的注意事项)
A:案例演示
定义枚举类要用关键字enum
所有枚举类都是Enum的子类
枚举类的第一行上必须是枚举项，最后一个枚举项后的分号是可以省略的，但是如果枚举类有其他的东西，这个分号就不能省略。建议不要省略
枚举类可以有构造器，但必须是private的，它默认的也是private的。
枚举类也可以有抽象方法，但是枚举项必须重写该方法
枚举在switch语句中的使用

27.16_JDK5新特性(枚举类的常见方法)
A:枚举类的常见方法
int ordinal()
int compareTo(E o)
String name()
String toString()
T valueOf(Class type,String name)
values()
此方法虽然在JDK文档中查找不到，但每个枚举类都具有该方法，它遍历枚举类的所有枚举值非常方便
B:案例演示
枚举类的常见方法

27.17_JDK7新特性(JDK7的六个新特性回顾和讲解)
A:二进制字面量
B:数字字面量可以出现下划线
C:switch 语句可以用字符串
D:泛型简化,菱形泛型
E:异常的多个catch合并,每个异常用或|
F:try-with-resources 语句

27.18_JDK8新特性(JDK8的新特性)
接口中可以定义有方法体的方法,如果是非静态,必须用default修饰
如果是静态的就不用了
class Test {
    public void run() {
        final int x = 10;
        class Inner {
            public void method() {
                System.out.println(x);
            }
        }

        Inner i = new Inner();
        i.method();
    }

}

局部内部类在访问他所在方法中的局部变量必须用final修饰,为什么?
因为当调用这个方法时,局部变量如果没有用final修饰,他的生命周期和方法的生命周期是一样的,当方法弹栈,这个局部变量也会消失,那么如果局部内部类对象还没有马上消失想用这个局部变量,就没有了,如果用final修饰会在类加载的时候进入常量池,即使方法弹栈,常量池的常量还在,也可以继续使用
复制代码

27.19_day27总结
把今天的知识点总结一遍。



























































