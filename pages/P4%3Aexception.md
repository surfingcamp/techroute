title:: P4:exception

- 从写代码层面解释为什么要使用异常：[[$blue]]==【video:20211012异常:10min】==
	- 没有一场就在有问题时不能直接把链路都返回，出现异常就中断流程
- 怎么使用，参考[[$blue]]==【video:20211012异常:40min】==
  > 总体上错误尽可能细 便于知道哪里出错了
	- 我们可能会有很多错误种类这个怎么表示呢？
	- 出现异常要不要中断是你自己决定，如果是while循环获取可能一个有错还想继续执行
	- 使用的时候不要把异常扩大了- 声明异常：告诉别人这里可能会抛出这样异常你要进行处理[[$blue]]^^【video:20211012异常:1h:12min】^^
- 声明异常：告诉别人这里可能会抛出这样异常你要进行处理[[$blue]]==【video:20211012异常:1h】==
- finally使用场景：参考 [[$blue]]==【video:20211012异常:1h:18min】==
	- try catch finally，finally改变不了要return的结果【code:ExceptionDemo11.java】
		- 设计初衷是，所有业务逻辑放在try 和catch里finally只做清理，业务操作比如++x放在finally不起作用
- Exception和RuntimeException的区别
	- RuntimeException是运行的时候才知道写代码的时候不知道
	- 写一个代码，题目：写一个代码批量进行学生注册如果一个失败了会怎么办？
-