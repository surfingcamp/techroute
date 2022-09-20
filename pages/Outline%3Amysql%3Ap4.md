title:: Outline:mysql:p4

- 没有设置时区导致必须timezone不对
	- 解决办法：
	- 为什么要关注时区 #card
		- 因为数据库字段类型 timestamp在存储上是包含时区的 
		  > 可以参考：https://juejin.cn/post/7007044908250824741
- mysql 驱动的问题,包名mysql-connector-java：
  > mysql-connector-java如果是5.1.46 那么使用的JDBC驱动是`com.mysql.jdbc.Driver`，如果是1.8那么使用的是`com.mysql.cj.jdbc.Driver`并且启动时候会提示`com.mysql.jdbc.Driver` 已经被deprecated。