title:: Outline:Mysql

- 什么是幻读
	-
- 4个隔离级别
	- Serializable：不需要写for update，执行select * from user where id = ‘6’，默认就是自动加锁
		- 一个事务 select  * from user where id = ‘6’ 另外一个insert user（6，‘张三’）这个插入语句是插入不进来的
		- TODO 业务上：幻读记录是20%  (这个待确认)，幻读是什么呢？
-