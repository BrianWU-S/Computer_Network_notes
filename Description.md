# Computer Network

计算机网络中涉及许多重要的知识和思想，在详细阅读了 James F.Kurose 的《Computer Networking-- A top-down approach》sixth edition和它对应的中文版本：《计算机网络--自顶向下方法》第七版之后，我对此领域有了基本的了解。我于2020年9月-2021年1月上了SJTU的计算机网络课程，孔令和教授的讲授令某些原本复杂的知识、理论变得通俗易懂。上述的几篇notes记录了我计算机网络中某些内容的理解，这里列出了notes中讲诉的主要内容，希望能对你有所帮助。

​																																																	-- Brian Wu

# 1 .	Application Layer

#### Basic concepts 

- OSI protocal (七层模型)， TCP/IP protocal(四层模型)，5 layer protocal （五层模型，为了方便讲述，大部分情况下使用的标准，虽然真正的标准的OSI七层模型，不过由于过于繁琐，很少人使用）
- 常见的应用层协议： HTTP （Hyper Text Transporation Protocal，超文本传输协议）, SMTP（Simple Mail Transporation Protocal，邮件传输协议）, FTP（File Transporation Protocal，文件传输协议）, TFTP（Trivial File Transfer Protocol，简单文件传输协议）
- DNS （Domain Name System）
- SEO（Seach Engine Optimization）
- Professional Terms：计算机网络领域常用的术语
- Core of computer network:
  1. 分组交换
     1. 排队时延
     2. 吞吐量
  2. 电路交换
     1. 频分复用
     2. 时分复用
  3. 网路的结构

#### HTTP

- 作用，特征，建立HTTP连接的过程（三次握手）
- HTTP请求报文
- Cookies
- Web cache, Proxy server

#### SMTP

- 协议框架
- 与HTTP的对比

# 2 .	Transportation Layer

#### Basic concepts 

- Functions of transportation layer
- Features of transportation layer
- Services of transportation layer
- Multiplexing && Demultiplexing

#### UDP

- 原理
- 适用情景

#### TCP

- 可靠数据传输的实现
  - 非流水线：停止等待协议
    1. rdt 1.0
    2. rdt 2.0
    3. rdt 2.1
    4. rdt 2.2
    5. rdt 3.0
  - 流水线：
    1. GBN（Go Back N）
    2. 选择重传
- TCP 
  - 特性
  - RTT估计与超时设置管理，超时情况处理和超时间隔加倍实现原理
  - TCP的流水线差错回复与GBN，选择重传对比
  - 流量控制
  - 死锁，发送方糊涂窗口问题，接收方糊涂窗口问题
  - TCP连接的建立（三次握手）和断开（四次挥手）
  - 拥塞控制
    1. 拥塞代价
    2. 拥塞控制方法
    3. TCP拥塞控制算法：慢启动，拥塞避免，快重传，快速恢复
  - TCP的公平性
    1. 实现原理
    2. 与UDP对比

# 3 .	Network Layer

#### Basic concepts:

- 网络层提供的两种服务
  - 虚电路服务
  - 数据报服务
- IP地址分类，特殊的IP地址，IP地址与硬件地址（MAC）对比
- IP数据报格式
- 子网划分与子网掩码
- 路由器转发算法

#### IP

- ICMP (Internet Control Message Protocol, 网际控制报文协议)

  允许**主机、路由器**报告差错信息（时间超时，终点不可达等）和异常情况，使得IP协议更有效的转发数据报和提高数据报交付成功的机会。

  - 应用

    PING: 使用ICMP的require, request 报文，测试两个host之间是否连通

    Traceroute: 使用ICMP的**时间超过**差错报告报文，跟踪一个分组从源点到终点的路径

- IGMP (Internet Group Management Protocol, 网际组管理协议)

  使得多播路由器知道多播组成员信息，多播组的组成员之间知道彼此的信息（成员加入，退出信息）

- ARP (Address Resolution Protocol, 地址解析协议)

  解析目的IP地址到目的MAC地址，并将其加入IP数据报发送

#### 路由选择协议

- IGP  (Internal Gate Protocol, 内部网关协议)

  自治系统内部使用的协议。

  - RIP  (Router Information Protocol, 路由信息协议)
  - OSPF (Open Shortest Path First, 开放最短路径优先)

- EGP (External Gate Protocol, 外部网关协议)

  源站、目的站处于不同的自治系统中，需要EGP协议将路由选择信息传递到另一个自治系统中。

  - BGP

- 多播路由选择协议

  - Flooding and Cut
  - Tunneling
  - 基于核心发现技术

#### IPV4, IPV6

- IPV4对比IPV6
  1. 32 --> 128
  2. IPV6即插即用，无需DHCP
  3. IPV6支持资源预分配
  4. 零压缩表示形式
- IPV4到IPV6过渡
  - 双协议栈
  - 隧道技术

#### 多播, VPN, NAT

# 4 .	Data Link Layer 

#### Basic concepts

- 什么是Data Link:

  Link + Protocol。Link 为点到点的物理链路；Protocol为通信协议，通过软硬件配合实现

  Data Link: 时效性； Link: 长期性

- 数据链路层的作用

  将数据**可靠的传输**到**相邻的结点**。

  （网络层作用：实现两个**端系统**之间的**逻辑通信**；运输层作用：实现两个**端系统的应用程序**之间的逻辑通信）

- 数据链路层协议

  - PPP：一对一的通信方式
  - 广播信道：一对多的通信方式

- 数据链路层三个基本问题

  - 封装成帧

    将来自网络层的IP数据报加上数据链路层头部（SOH）、尾部（EOT）封装成数据链路层帧发送

  - 透明传输

    封装成帧的步骤**不能破坏原始的数据**（原始数据中出现SOH,EOH则错误的找到帧边界，造成数据不完整）。通常采用字节填充法往SOH,EOH前填充ESC解决。

  - 差错检测

    CRC  (Cyclic Redundancy Check, 循环校验检测)

- CSMA/CD
- 集线器与星型拓扑

#### 以太网MAC 帧

- MAC地址

  局域网通信设备、端口唯一的标识符，有48位，前24位是序列号（生产厂商自行分配），后24位是供应商代码（IEEE管理）

- MAC帧类型

  1. unicast (单播)
  2. multi-cast (多播)
  3. broadcast (广播)

- MAC帧格式

Note: 以太网MAC帧不必有结束符，而PPP帧要有，因为以太网的sender每次发送完一个MAC帧都需要delay 一个 $t$的时间（使得发送者与未发送者重新处于公平竞争状态），这段时间可以作为MAC帧结束符。

#### 以太网的扩展

- Physical layer

  使用Huber (集线器)进行星形扩展

- Data Link layer

  使用 L2 switch (以太网交换机) 进行扩展 

- VLAN (Virtual LAN)

  VLAN是一些具有某些共同需求的LAN网段构成的逻辑组（Virtual Group），它提供了一种资源整合、按需提取的服务，有效避免了广播风暴。

# 5 .	Physical Layer

#### Basic concepts

- 速率
- 带宽
- 时延
- 吞吐量

#### 常用编码方式

- 不归零制
- 归零制
- 曼彻斯特
- 差分曼彻斯特

#### 信噪比、香农公式

# 6 .	Advanced Topics



- Internet of things (物联网): 万物互联，将互联网扩展到互联物品网

- 5G : 

  - 容量：相比4G，提高1000 倍
  - 传输速率：相比4G，提高10-100倍
  - 可接入设备量：相比4G，提高10-100倍

- 网络安全：

  - 常见的网络攻击：

    - 主动：

      1. 报文篡改
      2. 拒绝服务攻击
      3. 重放攻击
      4. 恶意程序

      i 使用加密技术防范，ii,iii,iv使用鉴别技术防范

    - 被动：

      报文截获，使用加密技术防范

  - 对称加密体制，公钥私钥体制概念以及区别

  - 数字签名与鉴别（报文鉴别、实体鉴别）

  - 防火墙与入侵检测

  - 密钥分配与互联网安全协议

  - 区块链与比特币

- SDN (Software Defined Network):

  - 概念：将数据转发平台和网络控制平台分离，使用软件平台集中控制
  - 优势：底层硬件可编程化，实现网络资源按需分配
  - 核心协议：OpenFlow，用于规定底层设备的转发控制方式

  



