如果服务在bind了端口服务器后，没有listen，那么就意味着，操作系统把这个socket注册到监听的socket中，所以会连接失败。

在收到SYN报文后，首先查找连接建立状态的socket，没有命中的情况下，才会查找监听socket，
如果又没有命中，内核就会调用 tcp_v4_send_reset 发送 RST 中止这个连接。

> 调用listen会发生什么？

- 创建属于当前socket的半连接和全连接队列
- 将当前socket注册到监听socket中
- 建立属于当前socket的TCB记录连接信息（IP、端口、序列号、窗口、状态等）。

> 客户端调用connect

- 建立属于当前socket的TCB记录连接信息（IP、端口、序列号、窗口、状态等）。

> 不使用 listen ，可以建立 TCP 连接吗？

答案，**是可以的**

客户端是可以自己连自己的形成连接（TCP自连接），也可以两个客户端同时向对方发出请求建立连接（TCP同时打开）

1. 客户端bind自己后直接调用connect。
2. 建立属于当前socket的TCB记录连接信息（IP、端口、序列号、窗口、状态等）。
3. SYN请求经过网络层的ip协议传回传输层。
4. 通过四元组找到指定的TCP控制块。
5. 返回ACK与SYN连接建立。

![[Pasted image 20250906173028.png]]