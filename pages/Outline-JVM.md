title:: Outline:JVM

- 从一个Java例子引出什么是JVM
  编译成一个class，一个Java代码在linux和Windows上都可以跑（从具体例子引出人会感知得到一点dd）
- 我们为什么要学习JVM呢？
	- 以后工作中需要JVM调优需要配置参数
	- 出现异常知道是什么原因
	  举出几个例子，堆溢出
	- 有助于我们写出性能更好的代码，理解一些框架源码设计
	  比如从软引用、弱引用中理解的
- 怎么学习JVM呢？整个课程按照这样的思路来讲
	- JVM虚拟机，虚拟机规范
	- 怎么定义垃圾
	- 如何找到垃圾
		- 算法 -->引出垃圾收集器
	-