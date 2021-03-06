# UDP网络通信协议
---
+ 要认识UDP，就得从最基础的OSI七层网络模型说起，虽然这个模型是学术模型，未在企业或实际场合中应用
+ 但是却掀起了腥风血雨的网络时代，要知道，实际的网络通信就是通信链路+设备，但是通信链路上传输的是
+ 高低电平，也就是0-1数据流，如果没有人为的干预，这些数据流是没有任何意义的，为了赋予这些数据有意义
+ 人们为它定义了一套规则，就像自然语言中的中文或者是英语，这套规则就是前面提到的OSI七层网络模型，
+ 这套模型从下至上分别是物理层、数据链路层、网络层、传输层、应用层、会话层、表示层
+ 物理层就是前面提到的通信链路，这个是实际的概念，除了这一层以外，其它都是虚拟的上层概念，
+ 数据链层收集物理层的电平信号，同时向网络层提供接口服务，其他层也是如此，
+ 但是在实际的应用中应用层、会话层、表示层的功能合到一起最方便，所以又诞生出TCP/IP五层模型
+ UDP协议就是TCP/IP五层模型中传输层的数据通信规则，它的上层是应用层，也就是编写应用程序的地方
+ 由于分层结构的存在，所以编写应用程序只需要关注应用层和传输层即可，
+ 讲完了UDP的起源，下面就延申UDP的传输方式，想要与互联网中的某个节点中的某个应用程序通信，就得知道这个节点的地址
+ 也就是IP地址，节点中存在大量的应用程序，所以通过端口号去定位想要通信的应用程序，
+ 所以，UDP的传输方式就是指定目标的IP地址和端口号，不需要建立连接，直接把数据扔过去。
+ 即发送方只管发送数据，接收方只管接收数据，这是属于异步通信的一种方式，就像写完一封邮件，直接扔到邮箱里，经过漫长的运输后
+ 信封才到达收信人的手中。
+ 虽然数据在传输中可能会丢失，但是只要不断的“扔信封”，收信人是能够明白送信人所要传达的意思。

---
# Socket
---
+ 在C++中提供了Socket套接字去实现UDP通信，Socket套接字将UDP协议的具体内容封装起来，对外提供接口
+ 只需要调用这些接口，就能间接的调用UDP协议，从而封装要传输的数据，然后从应用层扔到传输层
