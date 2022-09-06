title:: Outline:SpringAOP源码

- SpringaAOP源码讲解  
  展示两个对比代码（一个没有AOP 一个有AOP），如果有AOP那个Bean就是动态代理，那么我们知道只要配置了AOP那么在IOC DI的时候会生成动态代理对象，把动态代理对象放入到容器里
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