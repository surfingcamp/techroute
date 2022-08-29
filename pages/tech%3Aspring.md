title:: tech:spring

- Spring生命周期
	- 自动生成Bean从class文件 -> BeanDefintion ->生成Bean  -->放入到容器里Map里
		- class --> BeanDefinition过程中有扩展点BeanFactoryPostProcessor
		  这个扩展点能干什么？修改BeanDefintion?
			- BeanDefinitionRegistryProcessor
		- BeanDefintion -> Bean 有扩展点BeanPostProcessor接口
		  这个扩展点干什么？修改BeanPostProcessor
			- 重要子接口：SmartInstantiationAwareBeanPostProcessor
- DI:生成Bean，如果有属性怎么设置
	- 构造函数设值
	- 方法设值
- AOP：如果你想调用一个方法之前执行一段其他逻辑，比如加一个日志比如加一个事物
  到时补充怎么解释更充分（比如添加图）
	- 需要增强，增强可以使用修饰者，委托、也可以使用代理。这里增强的逻辑不应该每次都来写而是动态生成如果动态生成那个类，以后调用那个方法之前执行代理类的方法就实现了增强。所有调用这个代理类的都执行了这一段逻辑就相当于在原来调用逻辑上切了一刀，这就是AOP概念
- 使用：
	- 在哪里切（比如在哪里加日志加事物）pointcut
	- advice：你是加日志还是加事物还是加其他的
		- 并且我想加什么就加什么。我想做到解耦不影响原来代码（举例子）
			- 写上上怎么写的，注解形式和Xml那种写法
			  先把逻辑理清楚，代码上实现另外再说
	- 现有哪些组件实现了上面逻辑，我可以定义poincut、advice
	  参考p4
- 源码讲解
  展示两个对比代码，如果有AOP那个Bean就是动态代理，那么我们知道只要配置了AOP那么在IOC DI的时候会生成动态代理对象，把动态代理对象放入到容器里
	- 源码怎么知道你配置了AOP：
		- 扫描注解
			- AnnotationAspect.java @Aspect注解什么时候被处理的，处理后结果放在哪里？
			  AnnotationAspectBootStrap/XMLAspectBootStrap 这两个是触发扫描嘛？
		- `AbstractAutoProxyCreator -> wrapIfNessary`
			- `findAutoAdvisorCandidate`
	- 找到了配置怎么生成动态代理对象
		- `ProxyFactoryBean.getObject()`
			- `getSingletonInstance()-> AopProxy.getProxy()`
			  ProxyFactoryDemo调试 -> DefaultAopProxyFactory.createAopProxy(）有判断是通过JDKDynamic还是CGlib（核心使用ProxyFactory.getProxy来创建动态代理对象的）
	- 调用时候我要拿到advice执行增强的逻辑，比如打印日志比如开启事物
		- `this.adivised.getInterceptorsAndDynamicInterceptionAdvice(method,targetClass)`
		-
		-
	-
	-
	-
	-
	-
	-