TCP KeepAlive与HTTP Keep-Alive是两个完全不同的东西，他们的功能也完全不同。
- TCP KeepAlive是传输层（内核态）为了探测对方是否存活的**保活机制**。
-  HTTP Keep-Alive是应用层（应用态）的**HTTP长连接**。

## TCP KeepAlive

TCP KeepAlive是为了探测长时间没有交互的TCP连接的状态的。

TCP KeepAlive的默认是关闭的，下面是开启状态下的默认设置

| 参数 | 内核参数 | 默认值 | 描述 |
| --- | --- | --- | --- |
|空闲时间|`net.ipv4.tcp_keepalive_time`|7200s(2h)|TCP在连接状态超过7200s没有数据交互就开始探测|
|探测时间|`net.ipv4.tcp_keepalive_intvl`|75s|每隔75s探测一次|
|探测次数|`net.ipv4.tcp_keepalive_probes`|9|超过9次探测就断开连接|


![[Pasted image 20250905211154.png]]

## HTTP Keep-Alive

HTTP Keep-Alive是为了减少交互次数，提高性能的一个功能。一般的HTTP协议是一个请求响应的交互方式（**HTTP 短连接**），如果短时间内有大量的请求需要发送，那么就会频繁的建立断开连接、这会大大的降低交互的效率。如果打开了HTTP Keep-Alive，可以实现在一个连接下进行多次请求响应，甚至可以通过HTTP流水线来进一步提高性能。

> HTTP 1.1的默认配置

|服务|启用状态|超时时间|
|---|---|---|
|nginx|启用|65s|
|Apache http server|启用|5s|
|浏览器|启用|5s-15s|

> HTTP 流水线

客户端可以先一次性发送多个请求，而在发送过程中不需先等待服务器的回应，可以减少整体的响应时间。但是**服务器还是按照顺序响应**，先回应 A 请求，完成后再回应 B 请求。

![[Pasted image 20250905212444.png]]