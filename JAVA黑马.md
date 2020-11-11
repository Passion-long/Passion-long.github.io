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
* -128到127是byte的取值范围,如果在这个取值范围内,自动装箱就不会新创建对象,而是从常量池中获取
		 * 如果超过了byte取值范围就会再新创建对象








