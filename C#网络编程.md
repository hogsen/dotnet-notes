# 网络架构各层协议

网络架构模型采用自顶向下的的分层结构，上一层需要依赖下一层的服务

1. 应用层协议：用于程序间的沟通交互比如：FTP、HTTP、DNS、Telnet 等
   ====scoket====
2. 传输层：TCP、UDP
3. 网络层：IP

# 端口

识别进程：协议：//ip(域名)/端口号
端口用于识别进程
端口分配

1. 0
2. 1~255：特定服务 如 80、21、22
3. 256~1023：保留给其它服务 443
4. 1024~49999: 用作任意客户端
5. 5000~65535： 用作任意服务端

# 使用套接字进行进程间通信

咋们发送 http 请求，它实际是调用 socket 进行通信
socket 是对 TCP/UDP 抽象，为了方便我们进行网络编程
但在实际开发中我们一般不直接使用 socket,而是使用它的更高层封装比如 http 库。
但是 http 是基于 tcp 的，如果你要使用 udp 进行数据传输，还是得使用 socket,或者使用更高层的封装比如 websocket

## 套接字的类型

套接字有 3 种类型：流套接字、数据报套接字、原始套接字

1. 流套接字用来实现 TCP 通信

- server:创建套接字、用 Bind 方法绑定地址和端口号、用 Listen 监听、用 Accept 方法接收连接并等待 Client 连接、Receive 和 Sends=收发数据、Shutdown 释放连接、Close 关闭连接
- client:创建套接字、Connect 连接服务器、Receive 和 Send 收发数据、Shoutdown 释放连接、Close 关闭连接

2. 数据报套接字用来实现 UDP 通信

- server:创建 socket、用 Bind 绑定地址与端口、ReceiveFrom 和 SendTo 收发数据、Shutdown 释放连接、关闭 socket
- client:创建 socket、用 Bind 绑定地址与端口、ReceiveFrom 和 SendTo 收发数据、Shutdown 释放连接、关闭 socket

3. 原始套接字用来实现 IP 数据包通信，这个更加低层，常用于侦听和分析数据包。

## 数据流

当通过网络传输数据，或对文件数据进行操作时，需要将数据转化为数据流的形式。
数据流分为：文件流、内存流、网络流
**编码与解码**
常见的编码方式有 ASCLL 码和 Unicode 码以及 UTF 码
使用 Encoding 类进行编码解码以及转换
