title:: p4:Jvm

- Java 一次编译到处运行怎么做到的 {{cards }}
	- java源文件  --> 字节码文件 （通过JVM虚拟机把字节码转换成对应操作系统对应的二进制文件）
		- 为什么要把字节码转换成对应操作系统对应的二进制文件
			- 因为不同操作系统对应指令不一样所以对应二进制不一样
- 写一段代码在计算机 内存中如何存储的
  > 什么变量放栈 什么时候放堆 ，常量池放哪里
	- 变量赋值多个变量会共同指向同一个堆
- 为什么对象放堆里面 #card
	- 对象大小不固定