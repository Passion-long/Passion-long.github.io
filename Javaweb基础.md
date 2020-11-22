# Javaweb基础   

# Xml & Tomcat

## Xml

>eXtendsible  markup language  可扩展的标记语言

### XML 有什么用?

1. 可以用来保存数据

2. 可以用来做配置文件

3. 数据传输载体

### 给Eclipse配置Tomcat


1. 在server里面 右键新建一个服务器， 选择到apache分类， 找到对应的tomcat版本， 接着一步一步配置即可。
2. 配置完毕后， 在server 里面， 右键刚才的服务器，然后open  ， 找到上面的Server Location , 选择中间的 Use Tomcat installation...

3. 创建web工程， 在WebContent下定义html文件， 右键工程， run as server 

## 总结：

	xml

		1. 会定义xml

		2. 会解析xml

			dom4j  基本解析

			Xpath手法


	tomcat

		1. 会安装 ，会启动 ， 会访问。

		2. 会设置虚拟路径

		3. 给eclipse配置tomcat

# Http协议&Servlet

# Http协议

* 什么是协议

> 双方在交互、通讯的时候， 遵守的一种规范、规则。

* http协议

> 针对网络上的客户端 与 服务器端在执行http请求的时候，遵守的一种规范。 其实就是规定了客户端在访问服务器端的时候，要带上哪些东西， 服务器端返回数据的时候，也要带上什么东西。 


### Http响应数据解析

> 请求的数据里面包含三个部分内容 ： 响应行 、 响应头 、响应体


## Get 和  Post请求区别

* get

		1. 会在地址栏后面拼接数据，所以有安全隐患。 一般从服务器获取数据，并且客户端也不用提交上面数据的时候，可以使用GET
	
		2. 能够带的数据有限， 1kb大小
    
* post

		1. 数据是以流的方式写过去，不会在地址栏上面显示。  现在一般提交数据到服务器使用的都是POST
	
		2. 以流的方式写数据，所以数据没有大小限制。

### Web资源

* 在http协议当中，规定了请求和响应双方， 客户端和服务器端。与web相关的资源。 

* 有两种分类

* 静态资源

	html 、 js、 css

* 动态资源

	servlet/jsp

## Servlet


* servlet是什么?

> 其实就是一个java程序，运行在我们的web服务器上，用于接收和响应 客户端的http请求。 

> 更多的是配合动态资源来做。 当然静态资源也需要使用到servlet，只不过是Tomcat里面已经定义好了一个 DefaultServlet
 
## Servlet的生命周期

* 生命周期

> 从创建到销毁的一段时间

* 生命周期方法

> 从创建到销毁，所调用的那些方法。


* init方法

		在创建该servlet的实例时，就执行该方法。
		一个servlet只会初始化一次， init方法只会执行一次
		默认情况下是 ： 初次访问该servlet，才会创建实例。 

* service方法

		只要客户端来了一个请求，那么就执行这个方法了。
	 	 该方法可以被执行很多次。 一次请求，对应一次service方法的调用

* destroy方法

		
		  servlet销毁的时候，就会执行该方法
		
		  	1. 该项目从tomcat的里面移除。
		  	2. 正常关闭tomcat就会执行 shutdown.bat
		 

> doGet 和 doPost不算生命周期方法，所谓的生命周期方法是指，从对象的创建到销毁一定会执行的方法， 但是这两个方法，不一定会执行。

## ServletConfig

>Servlet的配置，通过这个对象，可以获取servlet在配置的时候一些信息

### 为什么需要有这个ServletConfig

1. 未来我们自己开发的一些应用，使用到了一些技术，或者一些代码，我们不会。 但是有人写出来了。它的代码放置在了自己的servlet类里面。 

2. 刚好这个servlet 里面需要一个数字或者叫做变量值。 但是这个值不能是固定了。 所以要求使用到这个servlet的公司，在注册servlet的时候，必须要在web.xml里面，声明init-params


* 在开发当中比较少用。

## HttpServletRequest  和 HttpServletResponse


### Servlet配置方式

* 1. 全路径匹配

> 以 / 开始   /a /aa/bb

> localhost:8080/项目名称/aa/bb 

* 2. 路径匹配 , 前半段匹配

> 以  / 开始 ， 但是以 * 结束  /a/* /*  

> * 其实是一个通配符，匹配任意文字

> localhost:8080/项目名称/aa/bb 

* 3. 以扩展名匹配

> 写法： 没有/  以 * 开始   *.扩展名    *.aa *.bb 


### ServletContext

> Servlet 上下文

> 每个web工程都只有一个ServletContext对象。 说白了也就是不管在哪个servlet里面，获取到的这个类的对象都是同一个。

### 如何得到对象

	//1. 获取对象
		ServletContext context = getServletContext();

### 有什么作用

1. 获取全局配置参数
2. 获取web工程中的资源
3. 存取数据，servlet间共享数据  域对象

### 通过classloader去获取web工程下的资源

### 使用ServletContext存取数据。

### ServletContext 何时创建， 何时销毁?

* 服务器启动的时候，会为托管的每一个web应用程序，创建一个ServletContext对象

* 从服务器移除托管，或者是关闭服务器。 

* ServletContext 的作用范围

> 只要在这个项目里面，都可以取。 只要同一个项目。 A项目 存， 在B项目取，是取不到的？ ServletContext对象不同。


## HttpServletRequest

> 这个对象封装了客户端提交过来的一切数据。 

## HttpServletResponse

> 负责返回数据给客户端。 


## 中文文件下载

> 针对浏览器类型，对文件名字做编码处理 Firefox (Base64) , IE、Chrome ... 使用的是URLEncoder

## 请求转发和重定向

### 重定向

			/*
			之前的写法
			response.setStatus(302);
			response.setHeader("Location", "login_success.html");*/
			
			//重定向写法： 重新定位方向 参数即跳转的位置
		response.sendRedirect("login_success.html");

		1. 地址上显示的是最后的那个资源的路径地址

		2. 请求次数最少有两次， 服务器在第一次请求后，会返回302 以及一个地址， 浏览器在根据这个地址，执行第二次访问。

		3. 可以跳转到任意路径。 不是自己的工程也可以跳。

		4. 效率稍微低一点， 执行两次请求。 

		5. 后续的请求，没法使用上一次的request存储的数据，或者 没法使用上一次的request对象，因为这是两次不同的请求。

### 请求转发

		//请求转发的写法： 参数即跳转的位置
		request.getRequestDispatcher("login_success.html").forward(request, response);

		1. 地址上显示的是请求servlet的地址。  返回200 ok

		2. 请求次数只有一次， 因为是服务器内部帮客户端执行了后续的工作。 

		3. 只能跳转自己项目的资源路径 。  

		4. 效率上稍微高一点，因为只执行一次请求。 

		5. 可以使用上一次的request对象。 


## Cookie

> 饼干. 其实是一份小数据， 是服务器给客户端，并且存储在客户端上的一份小数据

### 应用场景

> 自动登录、浏览记录、购物车。


### 为什么要有这个Cookie

> http的请求是无状态。 客户端与服务器在通讯的时候，是无状态的，其实就是客户端在第二次来访的时候，服务器根本就不知道这个客户端以前有没有来访问过。 为了更好的用户体验，更好的交互 [自动登录]，其实从公司层面讲，就是为了更好的收集用户习惯[大数据]


### Cookie怎么用


#### 简单使用：

* 添加Cookie给客户端

	1. 在响应的时候，添加cookie

		
			Cookie cookie = new Cookie("aa", "bb");
			
			
			//给响应，添加一个cookie
			response.addCookie(cookie);
		

	2. 客户端收到的信息里面，响应头中多了一个字段 Set-Cookie
	3. 

### Jsp 里面使用Java代码

* jsp

> Java Server Pager ---> 最终会翻译成一个类， 就是一个Servlet

* 定义全局变量

	<%! int a = 99; %>

* 定义局部变量

	<% int b = 999; %>
	
* 在jsp页面上，显示 a 和 b的值，
 
	<%=a %> 
	<%=b %>

### 清除浏览记录

> 其实就是清除Cookie， 删除cookie是没有什么delete方法的。只有设置maxAge 为0 。


### Cookie总结

1. 服务器给客户端发送过来的一小份数据，并且存放在客户端上。

2. 获取cookie， 添加cookie

	request.getCookie();

	response.addCookie();

3. Cookie分类

	会话Cookie
		默认情况下，关闭了浏览器，那么cookie就会消失。

	持久Cookie

		在一定时间内，都有效，并且会保存在客户端上。 

		cookie.setMaxAge(0); //设置立即删除

		cookie.setMaxAge(100); //100 秒

4. Cookie的安全问题。

> 由于Cookie会保存在客户端上，所以有安全隐患问题。  还有一个问题， Cookie的大小与个数有限制。 为了解决这个问题 ---> Session .


# Session

> 会话 ， Session是基于Cookie的一种会话机制。 Cookie是服务器返回一小份数据给客户端，并且存放在客户端上。 Session是，数据存放在服务器端。


* 常用API


		//得到会话ID
		String id = session.getId();
		
		//存值
		session.setAttribute(name, value);
		
		//取值
		session.getAttribute(name);
		
		//移除值
		session.removeAttribute(name);

* Session何时创建  ， 何时销毁?

* 创建

> 如果有在servlet里面调用了 request.getSession()

* 销毁

> session 是存放在服务器的内存中的一份数据。 当然可以持久化. Redis . 即使关了浏览器，session也不会销毁。

> 1. 关闭服务器

> 2. session会话时间过期。 有效期过了，默认有效期： 30分钟。

## 移除Session中的元素

		//强制干掉会话，里面存放的任何数据就都没有了。
		session.invalidate();
		
		//从session中移除某一个数据
		//session.removeAttribute("cart");


## 总结：

* 请求转发和重定向（面试经常问。）


* Cookie

	服务器给客户端发送一小份数据， 存放在客户端上。

	基本用法：

		添加cookie

		获取cookie。

	演练例子：

		1. 获取上一次访问时间

		2. 获取商品浏览记录。

* 什么时候有cookie

	response.addCookie(new Cookie())

* Cookie 分类

		会话Cookie

			关闭浏览器，就失效

		持久cookie

			存放在客户端上。 在指定的期限内有效。 

			setMaxAge();


* Session

		也是基于cookie的一种会话技术，  数据存放存放在服务器端
	
		会在cookie里面添加一个字段 JSESSIONID . 是tomcat服务器生成。 

		setAttribute 存数据
 
		getAttribute 取数据

		removeAttribute  移除数据

		getSessionId();  获取会话id

		invalidate() 强制让会话失效。

* 创建和销毁

	，调用request.getSesion创建 
	
	 服务器关闭 ， 会话超时（30分）


setAttribute 存放的值， 在浏览器关闭后，还有没有。  有！，就算客户端把电脑砸了也还有。  

# JSP & EL & JSTL

# jsp

> Java Server Page 

* 什么是jsp

> 从用户角度看待 ，就是是一个网页 ， 从程序员角度看待 ， 其实是一个java类， 它继承了servlet，所以可以直接说jsp 就是一个Servlet.

* 为什么会有jsp?

> html 多数情况下用来显示静态内容 ， 一成不变的。 但是有时候我们需要在网页上显示一些动态数据， 比如： 查询所有的学生信息， 根据姓名去查询具体某个学生。  这些动作都需要去查询数据库，然后在网页上显示。 html是不支持写java代码  ， jsp里面可以写java代码。 

## 怎么用JSP

### 指令写法

<%@ 指令名字 %>

### page指令

* language

> 表明jsp页面中可以写java代码

* contentType

> 其实即使说这个文件是什么类型，告诉浏览器我是什么内容类型，以及使用什么编码

		contentType="text/html; charset=UTF-8"

		text/html  MIMEType 这是一个文本，html网页

* pageEncoding  jsp内容编码

* extends 用于指定jsp翻译成java文件后，继承的父类是谁，一般不用改。

* import 导包使用的，一般不用手写。

* session 

> 值可选的有true or false .

> 用于控制在这个jsp页面里面，能够直接使用session对象。

> 具体的区别是，请看翻译后的java文件   如果该值是true , 那么在代码里面会有getSession（）的调用，如果是false :  那么就不会有该方法调用，也就是没有session对象了。在页面上自然也就不能使用session了。


* errorPage

> 指的是错误的页面， 值需要给错误的页面路径

* isErrorPage

> 上面的errorPage 用于指定错误的时候跑到哪一个页面去。 那么这个isErroPage , 就是声明某一个页面到底是不是错误的页面。


### include 

> 包含另外一个jsp的内容进来。

		<%@ include file="other02.jsp"%>

* 背后细节:

> 把另外一个页面的所有内容拿过来一起输出。 所有的标签元素都包含进来。

### taglib

 	<%@ taglib prefix=""  uri=""%>  

	uri: 标签库路径
	prefix : 标签库的别名  


##JSP 动作标签

	<jsp:include page=""></jsp:include>
	<jsp:param value="" name=""/>
	<jsp:forward page=""></jsp:forward>

* jsp:include

  <jsp:include page="other02.jsp"></jsp:include>

> 包含指定的页面， 这里是动态包含。 也就是不把包含的页面所有元素标签全部拿过来输出，而是把它的运行结果拿过来。 

* jsp:forward

  	<jsp:forward page=""></jsp:forward>

> 前往哪一个页面。  


	<% 
		//请求转发
		request.getRequestDispatcher("other02.jsp").forward(request, response);
	%>	

* jsp:param

> 意思是： 在包含某个页面的时候，或者在跳转某个页面的时候，加入这个参数。


​		
	<jsp:forward page="other02.jsp">
		<jsp:param value="beijing" name="address"/>
	</jsp:forward>
	
	在other02.jsp中获取参数


	<br>收到的参数是：<br>

	<%= request.getParameter("address")%>



## JSP内置对象

> 所谓内置对象，就是我们可以直接在jsp页面中使用这些对象。 不用创建。

- pageContext
- request
- session
- application

以上4个是作用域对象 , 

* 作用域 

> 表示这些对象可以存值，他们的取值范围有限定。  setAttribute   和  getAttribute


		使用作用域来存储数据<br>

		<%
			pageContext.setAttribute("name", "page");
			request.setAttribute("name", "request");
			session.setAttribute("name", "session");
			application.setAttribute("name", "application");
		%>
		
		取出四个作用域中的值<br>
		
		<%=pageContext.getAttribute("name")%>
		<%=request.getAttribute("name")%>
		<%=session.getAttribute("name")%>
		<%=application.getAttribute("name")%>

作用域范围大小：

	pageContext -- request --- session -- application 


### 四个作用域的区别

* pageContext 【PageContext】

> 作用域仅限于当前的页面。  

> 还可以获取到其他八个内置对象。

* request 【HttpServletRequest】

> 作用域仅限于一次请求， 只要服务器对该请求做出了响应。 这个域中存的值就没有了。

* session 【HttpSession】

> 作用域限于一次会话（多次请求与响应） 当中。 

* application 【ServletContext】

> 整个工程都可以访问， 服务器关闭后就不能访问了。 




- out		 【JspWriter】
  - response  【HttpServletResponse】

- exception  【Throwable】
  - page	 【Object】 ---就是这个jsp翻译成的java类的实例对象
    - config 【ServletConfig】

## EL表达式

> 是为了简化咱们的jsp代码，具体一点就是为了简化在jsp里面写的那些java代码。

* 写法格式

${表达式 }

> 如果从作用域中取值，会先从小的作用域开始取，如果没有，就往下一个作用域取。  一直把四个作用域取完都没有， 就没有显示。

## EL表达式 的11个内置对象。 

${ 对象名.成员 }

- pageContext 

作用域相关对象
- pageScope
- requestScope
- sessionScope
- applicationScope

头信息相关对象
- header
- headerValues

参数信息相关对象
- param
- paramValues


- cookie
  全局初始化参数
- initParam

## JSTL

> 全称 ： JSP Standard Tag Library  jsp标准标签库

> 简化jsp的代码编写。 替换 <%%> 写法。 一般与EL表达式配合


### 怎么使用

1. 导入jar文件到工程的WebContent/Web-Inf/lib  jstl.jar standard.jar

2. 在jsp页面上，使用taglib 指令，来引入标签库

3. 注意： 如果想支持 EL表达式，那么引入的标签库必须选择1.1的版本，1.0的版本不支持EL表达式。


	<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>


### 常用标签

<c:set></c:set>  
<c:if test=""></c:if>  
<c:forEach></c:forEach>  


## 学生信息管理系统







### 创建对象的几种方法：  
* 1. 直接new
* 2. 单例模式 | 提供静态方法
* 3. 工厂模式构建 

