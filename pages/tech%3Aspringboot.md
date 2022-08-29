title:: tech:springboot

- 历史故事：在微服务过程中产生了SpringBoot
	- 微服务有很多应用，每个应用依赖外部组件（比如redis过程中）需要做很多事情，能不能把这些步骤简化呢？
		- 借助了Spring在配置上做的努力，就是ImportSelector可以自动导入外部配置不需要你手动写代码
- 为什么要用SpringBoot
	- 去掉了web.xml
		- xml配置哪些配置可以优化？基于SpringMvc
	- 丢掉了外部化配置
-