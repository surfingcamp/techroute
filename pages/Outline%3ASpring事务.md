title:: Outline:Spring事务

- required_new传播属性下事务如何走的：
	- 外层事务：主要的2个切面，1个是数据源重写了order接口给了排序号是1，先走数据源切面设置数据源，再走事务切面启动事务，事务会先获取连接，就调用getConnection，最终会走我们重写的
		- TODO 事务的排序是在哪决定的
	- determineCurrentLookupKey方法，拿到ThreadLocal里的数据源，创建事务，然后执行完成外层事务
	- 走内层事务，同样的也是2个切面，就不说了，区别在于是required_new会新建一个事务，然后是newTransaction，自己能独自提交，最后外层事务也提交了