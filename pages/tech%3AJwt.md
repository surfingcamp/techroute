title:: tech:Jwt

- 还没有搞："有人说JWT不适合用于替换传统的 session+cookies 机制用于Web
  title:: tech:Jwt
  session+cookie机制怎么登录状态维护的呢？后面要去整理一下 comment by
  " https://diigo.com/0oqwr8
- JWT token是网络上都可以看见的，如果另一个人拿到token直接请求是不是也能够登录呢？
	- 解决办法：真实客户端通过js代码拿到浏览器所在的ip地址，然后把这个ip地址设值到payload里去，服务端从request对象里拿到ip地址（这个是请求自带的）然后跟payload里的ip地址比较。如果是另一个用户B截取了payload里的ip地址改不了，而B对应请求的的request对象ip是 ipB那么在服务端匹配的时候肯定通不过。