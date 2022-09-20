title:: Outline:mysql:p4

- 没有设置时区导致必须timezone不对
	- 解决办法：
	- 为什么要关注时区 #card
		- 因为数据库字段类型 timestamp在存储上是包含时区的 
		  > 可以参考：https://juejin.cn/post/7007044908250824741
- mysql 驱动的问题：mysql-connector-java如果是5.1.46 那么