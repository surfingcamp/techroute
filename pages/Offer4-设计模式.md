- **工厂模式**
  id:: 628b4837-4526-4bac-92bf-b306bb3f48f1
	- 为什么要用工厂而不是直接new一个对象
		- 隐藏细节
		- 延迟对象初始化：Spring三级缓存那里ObjectFactory有切面的话才会生成动态代理
	- 几种工厂模式
		- 简单工厂
		- 工厂方法factoryMethod
		  解决简单工程里需要有if else判断，给一个工厂模型ICourseFactory后面生成具体的工厂。
		- 抽象工厂
		  关于抽象工厂我觉得重点在于产品族，就是AbstractCourseFactory里面有两个抽象方法，abstract createNote(); abstract createVideo();这样能够创建course写既有note也有video并且Note和Video随时被定制。
- 单例模式
  id:: 628b6c9c-f21c-4d5f-ab05-a4a9a429db69
	- 饿汉式
		- 静态代码
		- 静态成员 static final  xxx = new HungrySingleton();
	- 懒汉式
		- `double check`的方式解决多线程情况会有多个实例
			- volatile解决半对象问题：
			  一般创建一个对象方式：
			  1. 开辟空间
			  2. 初始化
			  3. 赋值
			  指令重排会出现2与3调了个顺序
				- 为什么有指令重排？
					- 指令重排是什么？在单线程情况下不影响执行结果的情况下对执行优化
				- 有指令重排后果：那么当有多线程情况下且有指重排情况可能就会出现这个半对象的问题。
		- 静态懒汉式：类的加载机制，它与饿汉模式不同的是，它是在内部类里面去创建对象实例。这样的话，只要应用中不使用内部类，JVM就不会去加载这个单例类，也就不会创建单例对象，从而实现懒汉式的延迟加载。
	- 注册式单例（有容器管理单例保证对象唯一性）
		- 容器式单例并不能解决反射破坏单例逻辑只是使用容器来存放单例而容器中对象始终只有一个保证是单例模式参考`ContainerSignleton`,只不过别人都是从容器中获取对象获取的都是同一个对象。参考`ReflectDestorySingletonContainerTest`
			- 容器式单例不是ContainerSingleton 单例，而是说Map<String,Object> ioc，相同的key对应的对象只有一个。
			  如果多线程不加锁的情况虽然key对应对象是一个但是可能不是同一个（写代码演示一下）
		- EnumSingleton
			- 序列化不会破坏枚举的单例
				- 为什么？我写了个代码测试了，其中涉及到枚举为什么是线程安全的
	- 破坏单例
		- 反射破坏单例：`ReflectDestorySingletonTest.java`
			- 怎么解决：私有构造函数判断如果对象存在就抛异常，不然你两次都使用发射调用构造方法。
		- 序列化破坏单例：`SeriableSingletonTest`
			- 怎么解决：序列化调用 readResolve() 如果返回是instance实现的返回原来对象那么就是单例(debug可以知道)
- 代理模式
  id:: 628c8942-64bc-4e1f-b820-95bce3a6dd1e
	- 静态代理：写代码的时候代理和增强逻辑就已经确定了
		- 为什么有静态代理
		  staticProxy.Test
		- 场景：
		  客户端A  直接调用 服务端B
		  如果服务端B需要加一些功能不想A改代码
		  特别Spring中@Autowired Iperson可以是代理类（这就是代理类为什么要继承IPerson接口）
	- 动态代理：
		- 那为什么又有动态代理
		  静态数据源DbRouteProxyTest，给订单生成动态数据源给商品添加数据源每个类都要写代理类
		- 实现方式(生成代理类的方式)
			- JDK动态代理：`JdkDynamicProxyTest.testPrintJdkProxyDynamicClass();`
			- CGlib动态代理
			- Assist
		- 每次都生成代理类有性能问题嘛？
		  Spring AOP的Bean就是动态代理类，那么就可以重复利用（打印出ApplicationContext里的Bean就知道了）
		- 透明调用：可以通过Spring注入的那个地方来说明或者拿代码来说明
- 装饰器模式
	- 跟代理模式代码结构是一样的，他们有什么区别呢？从应用场景出发
	- 具体应用：比如Mybatis的CachingExecutor
- 适配器模式
	- 使用场景是什么: `target  --->adaptee`，然后条件不满足就去适配`target--> Adapter --> Adaptee`
	- 适配器有很多种写法
- 桥接模式
	- 使用场景把两个维度结合起来了
		- 通过AbstractMessage把NormalMessage和SmsMessage结合到一块了，一个继承IMessage一个含有IMessage成员
		- 通过AbstractCourse implement Couse{ videoNote}把笔记和课程两个维度结合起来了
	- 实际应用
		- JDBC桥接方式实现：`JdbcTest` 看一下JDBC怎么加载MYSQL驱动的源码
- 委派模式
  可以参考DispatcherServlet，不关心细节我只要发送命令给我反馈结果就可以
- 策略模式
  1. 从PromotionStrategyFacory工厂里拿到具体策略
  2. 有一些就是一个接口，具体策略实现这个接口
- 观察者模式
	- 原生观察者模式：当发生动作时候所有监听者都会被通知到
	- 精准通知：改进参考`MouseEventLisenter`：实现不同事件通知不同监听者
- 总结：
  不要为了设计模式而设计模式，设计模式会增加代码复杂度会增加很多的类阅读起来可能会相对麻烦一些
	-
	-
	-
	-
	-