# JAVA
* **Error**和**Exception**的区别？  
首先，所有的异常都是由Throwable继承而来，但在下一层立即分解为两个分支：Error和Exception  
**Error**  
1．总是不可控制的(unchecked)  
2．经常用来用于表示系统错误或低层资源的错误  
3．如何可能的话，应该在系统级被捕捉  
**Exception**  
1．可以是可被控制(checked)或不可控制的(unchecked)  
2．表示一个由程序员导致的错误  
3．应该在应用程序级被处理  
