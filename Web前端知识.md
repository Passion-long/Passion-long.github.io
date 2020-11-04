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

​	var 变量的名称 = 变量的值

JS声明函数:

​	var 函数的名称 = function(){	

​	}

​	

​	function 函数的名称(){

​	}


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

​	1. 写更少的代码,做更多的事情: write Less ,Do more  
  
	2. 将我们页面的JS代码和HTML页面代码进行分离  

为什么学习JQuery:

​	提高我们的工作效率


















