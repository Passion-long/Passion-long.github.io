# html（决定了页面的框架）   
<h>标题  
<br/>换行  
<p>段落包裹，可以用css修改，段落前后都增加一个换行符。   
<b>加粗   
<i>斜体   
<hr/>水平分割线    
<strong>加粗，可以加重语气读出来    
<em>斜体，可以加重语气读出来    
<font>改变字体，包括color，face    
  
图片：
<img src="">  
width，height宽，高  
./代表当前路径  
../代表上一级的路径  
../../代表上上一级的路径    
    
列表： 
无序列表：  
<ul type="square">
  <li>百度</li>
  <li>阿里</li>
  <li>腾讯</li>
</ul>
<hr/>
有序列表：  
<ol type="a" start="2">
  <li>百度</li>
  <li>阿里</li>
  <li>腾讯</li>
</ol>
  
链接：  
_self：当前页面打开  
_blank:新标签页打开页面  
  
表格：  
<table>  
<tr>行  
<td>列  
<table border="1px" width="400px" bgcolor="yellow" align="center">  
依次是：表格框宽度、表格宽度、背景颜色、对齐方式  
colspan:跨列合并  
rowspan:跨行合并  
  
# css（Cascading Style Sheets）：（层叠样式表，用来美化html页面）  
div:默认占一行，自动换行  
span:内容显示在同一行  
CSS选择器：帮助我们找到我们要修饰的标签或者元素  
元素的名称{  
  属性名称：属性的值；
  属性名称：属性的值；
}
ID选择器：  
以#号开头  
#ID的名称{
  属性名称：属性的值；
  属性名称：属性的值；
}

# javaScript（提供用户的交互）  
脚本语言：直接解释执行的语言。  
##### JS的数据类型:

- 基本类型  
  - string  
  - number  
  - boolean  
  - undefine  
  - null  

##### JS的运算符和语句:

- 运算符和java 一样
  - "===" 全等号: 值和类型都必须相等
  - == 值相等就可以了
- 语句和java 一样


##### JS的输出

- alert()  直接弹框
- document.write()  向页面输出
- console.log() 向控制台输出
- innerHTML:  向页面输出

JS声明变量:

var 变量的名称 = 变量的值

JS声明函数:

var 函数的名称 = function(){	

}



function 函数的名称(){

}


#### JS的开发步骤

```html
1. 确定事件
2. 通常事件都会出发一个函数
3. 函数里面通常都会去操作页面元素,做一些交互动作

```

JS的文档从上到下加载，有一个文档加载顺序。  


# JQuery  
JavaScript的库。  
JQuery的作用:

1. 写更少的代码,做更多的事情: write Less ,Do more  
  
2. 将我们页面的JS代码和HTML页面代码进行分离  

为什么学习JQuery:

提高我们的工作效率

基本选择器:

​	ID选择器: #ID名称

​	类选择器: .类名

​	元素选择器: 元素的名称

​	通配符选择器:  *  找出页面上所有元素

​	选择器分组: 选择器1,选择器2     [选择器1 , 选择器2]  

层级选择器:

​	后代选择器: 选择器1 选择器2  找出来的选择器1 下面的所有选择器2  子孙

​	子元素选择器: 选择器1 > 选择器2   找出来的是所有的子节点  儿子

​	相邻兄弟选择器: 选择器1+选择器2    找出来的紧挨着自己的弟弟

​	兄弟选择器:   选择器1~选择器2    找出所有的弟弟

​		(找出所有兄弟:   $("div").siblings()    )

属性选择器:

```html
选择器 div
选择器[title]
选择器[title='test']
选择器[title='test'][style]
```



基本的过滤器:    选择器:过滤器   $("div:first")

​	:first : 找出第一个元素

​	:last  找出最后一个元素

​	:even   找出偶数索引

​	:odd   找出奇数

​	:gt(index)   greater-than大于

​	:lt(index)    小于

​	:eq(index)  等于

表单选择器:

​	:input  找出所有的输入项,  textarea select button

​	:password

​	:text

​	:radio

表单对象属性的过滤器

​	:selected

​	:checked



常用函数:

​	属性prop()    properties

​		如果传入一个参数  就是获取

​	prop("src","../img/1.jpg");  

​		设置图片路径

​	attr : 操作一些自定义的属性  <img  abc='123' />

​	prop: 通常是用来操作元素固有属性的 ,建议大家使用prop来操作属性



​	css() ; 修改css样式

​	addClass()  : 添加一个class样式

​	removeClass() : 移除

​	

​	blur : 绑定失去焦点

​	focus: 绑定获得焦点事件

​	click:

​	dblclick

​	change

​	

​	append    :  给自己添加儿子

​	appendTo :  把自己添加到别人家

​	prepend :  在自己子节点最前面添加子节点

​	after  : 在自己后面添加一个兄弟

​	before: 在自己前面添加一个兄弟

​	

​	$("数组对象").each(function(index,data))

​	$.each(arr,function(index,data))

几个经常忘记的东西：  
​	form 标签: 表单标签,主要是用来向服务器提交数据

HTML的块标签:

​	div标签: 默认占一行,自动换行

​	span标签:  内容显示在同一行

## JSON格式

  ​	JSON对象

  ```json
  { key1:value}   
  {"username":"zhangsan","password":"123"}
  ```

  ​	JSON数组

  ```json
  [{ key1:value},{   key1:value},{ key1:value}]
  ```

  

# BootStrap  



- BootStrap有什么作用

  - 复制粘贴, 能够提高开发人员的工作效率



- 什么是响应式页面


  - 适应不同的分辨率显示不同样式,提高用户的体验


- BootStrap的中文网
  - http://www.bootcss.com
  










