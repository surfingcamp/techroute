title:: Outline:多线程基础知识

- 什么是线程
- 创建线程方式
- 线程状态
	- new 初始化状态
	- runnable 运行状态
	  > 分为start()就绪状态和运行running()状态
	- 等待
		- 限期等待：time_waiting  `Thread.sleep(long)`/ obj.wait(long) /LockSupport.parkUnit(Long)
			- Thread.sleep()与obj.wait
		- 无限期等待
	- block：阻塞状态，在用synchronize锁的情况下没有获取锁的状态
	- terminated：终止状态，执行完run()方法之后就是terminated状态
	  > 参考threadPool里怎么不让线程terminated
- 线程怎么终止
	- run()方法执行完自动终止
	- Thread.stop()线程
-