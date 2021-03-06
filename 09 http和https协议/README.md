### http和https的区别
- http是超文本传输协议，信息是明文传输，https则是由SSL+Http协议构建的具有安全性的ssl加密传输协议。
- 在 OSI 网络模型中，HTTP 工作于应用层，而 HTTPS 工作在传输层
- HTTP 标准端口是 80 ，而 HTTPS 的标准端口是 443

### 简单说说https是如何保证安全传输的
- 应用层需要将数据先传给 SSL/TLS 进行加密，然后再传给 TCP

### https是不是绝对安全的？有没有办法被破解？
- 不是绝对安全的，如果本地信任了不可信任的证书，就有可能会导致加密证书被破解

### http无状态协议，怎么理解无状态协议。如何实现有状态的请求
- 无状态协议是指同一个会话的连续两个请求互相不了解；当浏览器发送请求给server的时候，server响应，可是同一个浏览器再发送请求给server的时候，他会响应，可是他不知道你就是刚才那个浏览器，简单地说，就是server不会去记得你，所以是无状态协议。
- 可以在客户端使用cookie，在服务端使用session。


### 说说http协议中的302状态码的作用
- 302 代表暂时性转移，表示重定向，就是说浏览器在拿到服务器返回的这个状态码后会自动跳转到一个新的URL地址，这个地址可以从响应的Location首部中获取（用户看到的效果就是他输入的地址A瞬间变成了另一个地址B）
- 302表示旧地址A的资源还在（仍然可以访问），这个重定向只是临时地从旧地址A跳转到地址B，搜索引擎会抓取新的内容而保存旧的网址。


### 304缓存原理
- 客户端请求一个页面（A）。 服务器返回页面A，并在给A加上一个ETag。 客户端展现该页面，并将页面连同ETag一起缓存。 客户再次请求页面A，并将上次请求时服务器返回的ETag一起传递给服务器。 服务器检查该ETag，并判断出该页面自上次客户端请求之后还未被修改，直接返回响应304（未修改——Not Modified）和一个空的响应体
### http协议1.0和http协议1.1的区别
- http1.0是一个短连接,无状态,且单向通信的应用层协议
- HTTP 1.1支持长连接，多个请求和响应可以重叠，多个请求和响应可以同时进行

### 如何保证基于http协议的接口的安全性
- 选择拦截过滤器，对请求方法进行一次拦截处理
- 数据加密，对客户端和服务端都对数据传输的时候进行一个加密处理
- 签名，身份认证

### http协议上传文件，数据如何传输？
- HTTP请求报文分为三部分：请求行、请求头、请求正文
- 数据发送采用标准HTTP MIME封装格式的扩展Content-Type为multipart/form-data；boundary=%boundaryid%，其中boundaryid值用于标识上传任务，客户端需通过算法生成任务标识保证其唯一性。

### 说说http协议的优缺点

- 缺点：通信双方互相不认识，容易遭到冒充；通信过程使用明文，容易被第三方窃听；无法确定报文完整性，有可能会遭到篡改；
- 优点：简单快速，客户向服务器请求服务时，只需传送请求方法和路径；通信速度很快；灵活，可以传输任意类型的数据对象


### 一次http请求的完整交互流程
1. 建立TCP连接，在HTTP工作开始之前，Web浏览器首先要通过网络与Web服务器建立连接，该连接是通过TCP来完成的，该协议与IP协议共同构建Internet
2.  Web浏览器向Web服务器发送请求命令 
3.  Web浏览器发送请求头信息，浏览器发送其请求命令之后，还要以头信息的形式向Web服务器发送一些别的信息，之后浏览器发送了一空白行来通知服务器，它已经结束了该头信息的发送。
4.  Web服务器应答，应答的第一部分是协议的版本号和应答状态码
5.  Web服务器发送应答头信息 
6.  Web服务器向浏览器发送数据，Web服务器向浏览器发送头信息后，它会发送一个空白行来表示头信息的发送到此为结束，接着，它就以Content-Type应答头信息所描述的格式发送用户所请求的实际数据。
7.  Web服务器关闭TCP连接，如果是短连接，那么久关闭TCP连接，如果设置了keep-alive，TCP连接在发送后将仍然保持打开状态，于是，浏览器可以继续通过相同的连接发送请求。

