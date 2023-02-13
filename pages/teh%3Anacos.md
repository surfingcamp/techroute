title:: teh:nacos

- 与Spring底层相关：
	- TODO spring boot 中使用的是nacos自己的注解而spring cloud中使用的是spring的注解@Value，spring cloud 中nacos怎么用到@value这个注解的呢？
- 与Springcloud gateway结合起来
	- TODO 讲springcloud gateway的时候，动态路由的时候 修改了数据会走到监听那里。 这个想起了nacos源码，我们可以对应上来
- TODO pringcloud gateway 动态路由时候sc-gateway-server  写了监听，这个监听跟配置中心那个自动监听有什么不一样呢？
- Nacos2.0版本相比1.X:
	- 新增了gRPC的通信方式，因此需要增加2个端口。新增端口是在配置的主端口(server.port)基础上，进行一定偏移量自动生成，用到了protobuf序列化方式