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
  
  
  
  
  
  
  
  
  
  
Spring的工厂类  
* sadf
> asd




























