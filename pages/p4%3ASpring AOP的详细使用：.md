title:: p4:Spring AOP的详细使用：

- 为了更好组件化使用提供了pointCut Advice这些注解
- pointCut：在哪里切（比如在哪里加日志加事物）pointcut
- advice：你是加日志还是加事物还是加其他的
	- 并且我想加什么就加什么。我想做到解耦不影响原来代码（举例子）
		- 写上上怎么写的，注解形式和Xml那种写法
		  先把逻辑理清楚，代码上实现另外再说
- 现有哪些组件实现了上面逻辑，我可以定义pointcut、advice
  参考p4