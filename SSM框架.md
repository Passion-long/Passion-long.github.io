# Spring
  
### JavaBean的概念  
* JavaBean的书写规范  
a. 必须是public的  
b. 提供默认的构造方法  
c. 字段都是私有的: private String usename;  
d. 提供公有的getter和setter方法: 属性  
例如: getUsername() 读属性, 属性名: username   
e. 一般需要实现java.io.Serializable接口  
  
  
### IOC和DI  
* IOC: 控制反转, 将对象的创建权反转给了Spring  
* DI: 依赖注入, 前提必须有IOC的环境, Spring管理这个类的时候将类的依赖的属性注入(设置)进来  
  
### 面向对象的时候  
* 依赖  
```
Class A{

}

Class B{
  public void xxx(A a){
  
  }
}
B依赖A
```
* 继承  
```
Class A{

}

Class B extends A{

}
```
* 聚合: has a  
  
## Spring底层的AOP实现原理  
### 动态代理  
* JDK动态代理: 只能对实现了接口的类产生代理.  
* Cglib动态代理: 对没有实现接口的类产生代理对象,生成子类对象.  
  
在Java中java.lang.reflect包下提供了一个Proxy类和一个InvocationHandler接口，通过使用这个类和接口就可以生成动态代理对象。JDK提供的代理只能针对接口做代理。我们有更强大的代理cglib，Proxy类中的方法创建动态代理类对象  
  
```
//JDK动态代理:

package com.ithaima.spring;

import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

public class JdkProxy implements InvocationHandler {

	//将被增强的对象传递到代理中
	private UserDao userDao;
	public JdkProxy (UserDao userDao) {
		this.userDao = userDao;
	}
	
	public UserDao createProxy() {
		UserDao userDaoProxy = (UserDao) Proxy.newProxyInstance(userDao.getClass().getClassLoader(),
				userDao.getClass().getInterfaces(), this);
		return userDaoProxy;
	}
	
	@Override
	public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
		
		//判断方法名是不是delete,在原有方法上执行权限校验
		if ("delete".equals(method.getName())) {
			//增强
			System.out.println("权限校验===========================");
			return method.invoke(userDao, args);
		}
		return method.invoke(userDao, args);
	}

}
```

```

```
* 什么是事务?  

        * 事务: 逻辑上的一组操作,组成这组操作的各个单元,要么全部成功,要么全部失败.  
  
* 事务的特性?  
  
        * 原子性:事务不可分割.
        * 一致性:事务执行前后数据完整性保持一致.
        * 隔离性:一个事务的执行不应该受到其他事物的干扰.
        * 持久性:一旦事务结束,数据就持久化到数据库.
  
  
# mybatis  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  


























