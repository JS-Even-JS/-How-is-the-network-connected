# -How-is-the-network-connected
# 网络是怎么连接的
## 第一章 浏览器生成消息

## 第二章 用电信号传输TCP/IP 数据 --探索协议栈和网卡
### 2.1 创建套接字
* 2.1.1 协议栈的内部结构<br/>
  **协议栈**是指网络中各层协议的总和，本质是**操作系统内部的网络控制软件**，也叫**协议驱动**或者**TCP/IP驱动**，其形象的反映了一个网络中文件传输的过程：由上层协议到底层协议，再由底层协议到上层协议。<br/>
  协议栈内部主要分为两层：**TCP协议和UDP协议**作为一层，其下面还有**IP协议**作为另一层；<br/>
  整个系统分层结构为:<br/>
  **应用程序**<br/>
  **Socket库(DNS解析器、socket组件、connect组件、write组件、read组件、close组件)**<br/>
  **协议栈(上层的TCP协议和UDP协议，下层的IP协议(ICMP、ARP协议))**<br/>
  **网卡驱动程序(控制网卡)**<br/>
  **网卡(负责对网线中的信号执行发送和接收的操作)**<br/>
  **收发数据的时候，上层会将收发数据的工作委派给下层**<br/>
  **ICMP**:用于告知网络包传送过程中产生的错误以及各种控制消息；<br/>
  **ARP**:用于根据IP地址查询相应的以太网MAC地址；<br/>
* 2.1.2 套接字的实体
  在协议栈的内部有一块**用于存放控制消息的内存空间**，其中控制消息包括，**源IP地址、源端口、目的IP地址、目的端口、连接状态、是否已经收到了响应、发送数据后经过了多长时间**等；<br/>
  所以我们通常把这个**用于存放控制信息的内存空间称为套接字的实体，协议栈会根据这些控制信息进行下一步操作**，这也就是套接字的作用；<br/>
  套接字其实是可以通过命令行的方式来查看的，可以通过**netstat -an -p TCP**命令来查看，-a表示**不仅显示正在通信状态(ESTABLISHED状态)的套接字，还显示处于尚未开始通信状态(LISTENING状态)的套接字**，-n表示**显示IP地址和端口号**<br/>
  ![](https://github.com/JS-Even-JS/-How-is-the-network-connected/blob/master/images/socket.png)

### 2.2 
* 2.2.1 获取微信小程序的AppID <br/>
  开发者开发好的微信小程序必须要有AppID才能进行发布，可以点击以下url地址进行小程序注册并获取AppID，如:

