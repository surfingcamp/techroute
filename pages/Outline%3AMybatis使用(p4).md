title:: Outline:Mybatis使用(p4)

- 为什么使用mybatis
  title:: Outline:Mybatis
	- 数据处理层变迁
		- JDBC怎么写的我们可以做哪些优化
		- Mybatis应运而生
		  > 有这么多ORM框架提到就行，重点讲mybatis，后面会讲一下为什么mybatis流行
- 一个例子把mybatis跑起来
	- 经常出现类似 com.tudou.BrandMapper不存在的现象，这个一般是mybtis-config.xml那里配置Mapper方式错误造成
		- 怎么发现是这样错误呢？通过在异常堆栈看到MapperRegistry.getMapper()这里报错发现KnownMappers这个list是
		- 具体应该怎么配置：
		  > 参考：https://blog.csdn.net/fageweiketang/article/details/80835733
			- 可以配置.xml
			- 可以配置接口.java
				- 注意使用`<package name="org/mybatis/'mappers"/>`也是可以跑通的
- mybatis基本和高级使用
  配置不用全部讲呀，后面用到再来讲
- 动态SQL
- 复杂SQL
	- 关联查询
	- 批量操作
	- 分页
	- 分页操作
- 基础支持层
  exceutor statement这些
- 插件缓存
- 事物管理及其与Spring继承
- 手写
  也可以先手写一遍然后呢？在讲到对应源码