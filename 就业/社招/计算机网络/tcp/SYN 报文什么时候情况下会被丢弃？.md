> 半连接队列满了，会造成SYN报文被丢弃

当服务器造成syn攻击，就有可能导致 TCP 半连接队列满了，这时后面来的 syn 包都会被丢弃。

但是，如果开启了syncookies 功能，即使半连接队列满了，也不会丢弃syn 包。

![alt text](image-58.png)

防御SYN攻击的方式

- 方式一：增大半连接队列
要想增大半连接队列，我们得知不能只单纯增大tcp_max_syn_backlog 的值，还需一同增大 somaxconn 和 backlog，也就是增大全连接队列。
- 方式二：开启 tcp_syncookies 功能
- 方式三：减少 SYN+ACK 重传次数