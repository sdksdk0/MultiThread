## 1、HTTP协议、WebSocket协议、Socket协议之间的区别
答：

- HTTP、WebSocket 等应用层协议，都是基于 TCP 协议来传输数据的。我们可以把这些高级协议理解成对 TCP 的封装。Socket是应用层与TCP/IP协议族通信的中间软件抽象层，它是一组接口。
- HTTP: 通信只能由客户端发起，做不到服务器主动向客户端推送信息。
- WebSocket: 可以实现双向通信,服务器可以主动向客户端推送信息，客户端也可以主动向服务器发送信息，是真正的双向平等对话
- Socket:本身不是一种协议，而是对传输层中的TCP/UDP协议进行了封装，对用户隐藏了内部TCP/UDP是如何传输的，只提供一套接口（API）给程序员调用，从而完成socket编程。通过socket接口，我们才能使用TCP/UDP协议。


## 2、自定义报文协议应用在什么场景下？
答：可以在一些通信要求比较高的情况下，或者传统的机器设备的通信中


## 3、如果实现单人聊天，改如何改造？
答： 当客户端连接的时候，记录一个唯一标识，服务端根据这个客户端的channel对象，进行channel.writeAndFlush操作
