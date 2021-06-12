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



# 4 .	Data Link Layer 



# 5 .	Physical Layer



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

  



