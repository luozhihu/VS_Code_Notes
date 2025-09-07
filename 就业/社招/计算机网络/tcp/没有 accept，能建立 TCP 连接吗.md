没有accept是可以建立TCP连接的，在accept方法之前执行了listen方法，该方法会将socket注册到监听socket里面，并且建立半连接和全连接队列。在收到SYN请求后可以正常的三次握手建立连接。

> 全连接队列满了会发生什么

- 丢弃第三次握手的ACK（`tcp_abort_on_overflow`设置为0）
- 收到第三次握手的ACK后，回复RST报文（`tcp_abort_on_overflow`设置为1）

> 半连接队列满了会发生什么

- 丢弃第一次握手的SYN（`tcp_syncookies`关闭）
- 返回一个特殊的ACK+SYN（`tcp_syncookies`打开）
	- seq由ip、端口、时间戳等信息组成，等收到ACK验证ack确认号是否对的上

> cookies方案为什么不直接取代半连接队列？

编码解码`cookies`，都是比较**耗CPU**的利用这一点，如果此时攻击者构造大量的第三次握手包（ACK包）同时带上各种瞎编的`cookies`信息服务端收到`ACK包`后**以为是正经cookies**，憨憨地跑去解码（**耗CPU**），最后发现不是正经数据包后才丢弃。