title:: p4:工具类:object和hashcode

- Object方法
	- hashcode方法 是native的方法底层已经实现了
		- hashcode代表了：一定程度上代表了这个对象的地址
		- 你可以通过比较hashcode判断这两个变量指向的是不是同一个地址。`写个代码测试一下` 
		  > 这是个问题让学习者验证
		- 两个对象比较（工作中一般比较内容）：参考[[$blue]]==【video:20211007常用工具类:1h9min==】
	- 面试题：Hash为什么重写equals方法必须重写HashCode方法 #turing-interview
		- 实际工作中一般比较的是内容：
			- 登录时候：用户传了一个User(zs,123) 要跟数据库里的比较，比对密码user.getname().equals() && user.getPwd()
				- 当然你也可以user1.equals(user2)  要重写equals方法，重写的比对name和password
				-
		- [[draws/2022-09-25-10-52-29.excalidraw]]
	- 克隆 clone()
		- 使用注意：如果你要调用clone()方法，这个对象必须继承Cloneable接口不然会报`NotSupportedException`
		  > 你可以不继承clone编译不报错但是运行起来报错
			- 原理：clone方法是native方法，c++写的底层会判断是否继承了Cloneable接口
			- 继承Cloneable就是告诉外面的人我具有克隆能力，这从实际应用感受接口作用参考 ((63212040-e982-47f3-84bb-a3d759a89b1e))
		- TODO 怎么使用的 (p4的代码整好)
		  > 先解释浅克隆在看看浅克隆有什么问题 然后说深克隆
			- 浅克隆：对于包含引用类型的对象，浅克隆前后引用类型属性指向同一块内存，也就是说虽然克隆产生一个全新的对象，但它的引用属性还指向被克隆对象引用属性指向的对象
			- 深克隆：重写当前类的 clone() 方法，在方法中手动克隆引用类型属性并赋值
	- Object.finalize()方法
		- 用完之后对象会自动回收在垃圾回收器质性垃圾回收之前会执行这个方法
	- 锁相关方法
		- wait /wai(long)
		- notify/notifyAll
		- TODO 怎么使用，在并发编程会解释这几个锁怎么使用
	- 反射相关方法
		- getClass()从一个对象获取这个对象类信息
- 比较内容：重写equals方法
	- 应用场景：你登录验证从前端传过来跟数据库select出来的对象肯定是不一样但我们只要比对内容，比对username和pwd方法是否一样就可以。
- 字符串比较：
	- 参考[[$blue]]== 【video:20211007常用工具类:1h:41min】==
	- String和StringBuffer StringBuild
		- 为什么多次给一个String赋值性能不好要使用StringBuffer呢？
			- 可以写一个代码 for循环strVar += “i”；每次strVar这个hashcode应该不一样，而对于StringBuffer应该是一样的
- Integer Long
- 面试题：
	- 为什么重写equals方法一定要重写hashcode方法 #card #100-turin
	  id:: 63abf594-eb60-4a9a-b4e2-c2935883f4fb