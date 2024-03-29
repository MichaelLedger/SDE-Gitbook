## 信息安全

### 试题放置
题目编号大致为：7-11

### 知识点
#### 常见的加密算法

- **常见非对称密钥加密算法（公开密钥加密技术）：**

RSA（Author: Ron Rivest、Adi Shamir、Leonard Adleman，公开密钥密码体制）

**原理：根据数论，寻求两个大素数比较简单，而将它们的乘积进行因式分解却极其困难，因此可以将乘积公开作为加密密钥。**

ECC（Elliptic Curves Cryptography，椭圆曲线加密算法）

DSA：既 Digital Signature Algorithm，数字签名算法，他是由美国国家标准与技术研究所（NIST）与1991年提出。和 RSA 不同的是 DSA 仅能用于数字签名，不能进行数据加密解密，其安全性和RSA相当，但其性能要比RSA快。

ECDSA：Elliptic Curve Digital Signature Algorithm，椭圆曲线签名算法，是ECC（Elliptic curve cryptography，椭圆曲线密码学）和 DSA 的结合

- **常见对称密钥加密算法（共享密钥加密技术）：**

DES（Data Encryption Standard，数据加密标准）

3DES（ Triple DES，三重数据加密算法 ）

RC5（分组密码算法）

IDEA（International Data Encryption Algorithm，国际数据加密算法）

AES（Advanced Encryption Standard，高级加密标准，分组加密算法）算法。 

- **常见的摘要算法：**

MD5(128位)（Message-Digest Algorithm 5，信息-摘要算法5）

SHA(160位)（Secure Hash Algorithm，安全散列算法）

#### 加密技术的应用

数字信封：用接收方公钥加密使用的对称密钥。

数字签名：用发送方私钥签名，保证发送方身份真实性，发送者不可抵赖，与信息摘要结合，可防篡改。对用户的身份进行认证。

信息摘要：单向散列值函数，防篡改，保证消息完整性。

数字证书（确保消息不可否认）

数字证书的内容包括：CA签名、用户信息（用户名称）、用户公钥等。

证书中的CA签名验证数字证书的可靠性、验证网站真伪。

用户公钥：客户端利用证书中的公钥加密，服务器利用自己的私钥解密。

#### 网络安全协议分层

- IPSec工作于网络层，为IP数据报文进行加密。

- PP2P工作于数据链路层，用于链路加密。

- 超文本传输安全协议 (Hypertext Transfer Protocol Secure, HTTPS)

协议是HTTP协议与SSL协议的结合，**为传输层以上层次数据加密**，默认端口号443。

- 安全传输层协议（Transport Layer Security, TLS）

用于在两个**通信应用程序之间**提供保密性和数据完整性。
该协议由两层组成： TLS 记录协议（TLS Record）和 TLS 握手协议（TLS Handshake）。

- PGP协议是邮件安全协议。

- SET协议是电子商务安全协议，涉及电子交易安全。

- SSH (Secure Shell )：为建立在应用层基础上的安全协议。SSH是较可靠，专为远程登录会话和其他网络服务提供安全性的协议。

- 文件传输协议（File Transfer Protocol, FTP） 

TCP/IP 协议组中的协议之一。FTP协议包括两个组成部分，其一为FTP服务器，其二为FTP客户端。其中FTP服务器用来存储文件，用户可以使用FTP客户端通过FTP协议访问位于FTP服务器上的资源。在开发网站的时候，通常利用FTP协议把网页或程序传到Web服务器上。此外，由于FTP传输效率非常高，在网络上传输大的文件时，一般也采用该协议。
**默认情况下FTP协议使用TCP端口中的 20和21这两个端口，其中20用于传输数据，21用于传输控制信息。** 但是，是否使用20作为传输数据的端口与FTP使用的传输模式有关，如果采用主动模式，那么数据传输端口就是20；如果采用被动模式，则具体最终使用哪个端口要服务器端和客户端协商决定。

- 安全文件传送协议（SSH File Transfer Protocol, SFTP）

可以为传输文件提供一种安全的网络的加密方法。SFTP 与 FTP 有着几乎一样的语法和功能。SFTP 为 SSH的其中一部分，是一种传输档案至 Blogger 伺服器的安全方式。其实在SSH软件包中，已经包含了一个叫作SFTP(Secure File Transfer Protocol)的安全文件信息传输子系统，SFTP本身没有单独的守护进程，它必须使用sshd守护进程(**端口号默认是22**)来完成相应的连接和答复操作，所以从某种意义上来说，SFTP并不像一个服务器程序，而更像是一个客户端程序。**SFTP同样是使用加密传输认证信息和传输的数据，所以，使用SFTP是非常安全的。** 但是，由于这种传输方式使用了加密/解密技术，所以传输效率比普通的FTP要低得多。

- 简单文件传输协议（Trivial File Transfer Protocol, TFTP）
TCP/IP协议族中的一个用来在客户机与服务器之间进行简单文件传输的协议，提供不复杂、开销不大的文件传输服务。**端口号为69**。

- Internet控制报文协议（Internet Control Message Protocol, ICMP）
TCP/IP协议族的一个子协议，用于在IP主机、路由器之间传递控制消息。控制消息是指网络通不通、主机是否可达、路由是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用。

#### 远程登录或控制协议
- SSH：SSH 为建立在应用层基础上的安全协议。SSH 是较可靠，专为**远程登录会话**和其他网络服务提供安全性的协议。

- Telnet：Telnet协议是TCP/IP协议族中的一员，是Internet**远程登录服务**的标准协议和主要方式。它为用户提供了在本地计算机上完成远程主机工作的能力。在终端使用者的电脑上使用telnet程序，用它连接到服务器。

- RFB：RFB （ Remote Frame Buffer 远程帧缓冲） 协议是一个用于**远程访问图形用户界面**的简单协议。由于 RFB 协议工作在帧缓冲层，因此它适用于所有的窗口系统和应用程序。

#### 其他协议
- 传输控制协议（Transmission Control Protocol, TCP）

一种**面向连接的、可靠的、基于字节流的传输层通信协议**，为了在不可靠的互联网络上提供可靠的端到端字节流而专门设计的一个传输协议。

- Internet 组管理协议(Internet Group Management Protocol, IGMP)：

属于**网络的组播协议**，不能实现相关应用层的远程登录。

#### 隔离区(demilitarized zone, DMZ )

DMZ是英文“demilitarized zone”的缩写，中文名称为“隔离区”，也称“非军事化区”。

它是为了解决安装防火墙后外部网络不能访问内部网络服务器的问题，而设立的一个非安全系统与安全系统之间的缓冲区。

**一个黑客必须通过三个独立的区域(外部防火墙、内部防火墙和堡垒主机)才能够到达局域网。**

#### 网络地址转换(Network Address Translation, NAT)
将IP数据包头中的IP地址转换为另一个IP地址的过程。在实际的应用中，NAT主要用于实现私有网络访问公共网络的功能。这种通过使用少量的公网IP地址代表较多的私有IP地址的方式，将有助于减缓可用IP地址空间的枯竭。

#### 网络安全控制技术
- 防火墙：过滤路由器和代理服务器组成。
 - 包过滤防火墙
 
 拦截和检查所有出站和进站的数据；包过滤通常被包含在路由器数据包中；不能防范黑客攻击；不支持应用层协议，访问控制粒度太粗糙。
 
 - 应用代理网关
 
 内网与外网的所有通信必须经应用层代理软件转发，访问者不能与服务器建立之间的TCP连接；优点是可以检查应用层、传输层和网络层的协议特征，对数据包的检测能力比较强；缺点是难以配置、处理速度非常慢。
 
 - 状态检测技术
 
 结合前两者的优点，在防火墙的核心部分建立状态连接表，跟踪每个会话（进出网络的数据）状态。
 
- 加密

- 用户识别

- 访问控制：

**访问控制列表 (Access Control Lists, ACL)** 是一种基于包过滤的访问控制技术，它可以根据设定的条件对接口上的数据包进行过滤，允许其通过或丢弃。
访问控制列表被广泛地应用于路由器和三层交换机，借助于访问控制列表，可以有效地控制用户对网络的访问，从而最大程度地保障网络安全。**通过在出口防火墙上配置ACL功能可以组织外部未授权用户访问内部网络。**

- 网络反病毒

- 网络安全漏洞扫描
- 入侵检测（Intrusion Detection System, IDS）

防火墙后的第二道安全屏障，通过从计算机系统或网络中的若干关键点收集网络的安全日志、用户的行为、网络数据包和审计记录等信息并对其进行分析，检查是否入侵并自动做出响应。

- 入侵防御系统（Intrusion Prevention System, IPS）
不仅能检测到网络攻击，同时主动对攻击行为进行响应。IPS与IDS在网络中的部署位置不同；IPS作为网络设备串联在网络中，而IDS一般是旁路挂接的方式；入侵响应能力不同。

#### 网络攻击
- 跨站脚本（cross-site scripting，XSS）

- SQL注入攻击

通过把SQL命令插入到 Web表单提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。

其首要目的是**获取数据库访问权限**。

会导致的数据库安全风险包括：**刷库、拖库、撞库**。

危害很大，而且防火墙很难对攻击行为进行拦截，主要的**SQL注入攻击防范方法**，具体有以下几个方面。

1、分级管理 2、参数传值 3、基础过滤与二次过滤 4、使用安全参数 5、漏洞扫描 6、多层验证 7、数据库信息加密

- **分布式拒绝服务攻击(DDos, Distributed denial of service attack)**

可以使很多的计算机在同一时间遭受到攻击，使攻击的目标无法正常使用，分布式拒绝服务攻击已经出现了很多次，导致很多的大型网站都出现了无法进行操作的情况，这样不仅仅会影响用户的正常使用，同时造成的经济损失也是非常巨大的。分布式拒绝服务攻击方式在进行攻击的时候，可以对源IP地址进行伪造，这样就使得这种攻击在发生的时候隐蔽性是非常好的，同时要对攻击进行检测也是非常困难的，因此这种攻击方式也成为了非常难以防范的攻击。

- 跨站脚本（cross-site scripting，XSS）

一种安全攻击，其中，攻击者在看上去来源可靠的链接中恶意嵌入译码。它允许恶意用户将代码注入到网页上，其他用户在观看网页时就会受到影响。不影响服务的提供。

- 拒绝服务

对信息或其它资源的合法访问被无条件地阻止，会让服务器拒绝提供服务。

- 信息篡改

指主动攻击者将窃听到的信息进行修改(如删除和/或替代部分或者全部信息)之后再将信息传送给原本的接受者。

- 口令猜测

攻击者攻击目标时常常把破译用户的口令作为攻击的开始。只要攻击者能猜测或者确定用户的口令，他就能获得机器或者网络的访问权，并能访问到用户能访问到的任何资源。

#### DDoS的防范

- 主机上的设置

几乎所有的主机平台都有抵御DoS的设置，总结一下，基本的有几种：

关闭不必要的服务、限制同时打开的Syn半连接数目、缩短Syn半连接的time out 时间、及时更新系统补丁

- 网络设备上的设置

企业网的网络设备可以从防火墙与路由器上考虑。这两个设备是到外界的接口设备，在进行防DDoS设置的同时，要注意一下这是以多大的效率牺牲为代价的，对你来说是否值得。

１.防火墙

禁止对主机的非开放服务的访问、限制同时打开的SYN最大连接数、限制特定IP地址的访问、启用防火墙的防DDoS的属性、严格限制对外开放的服务器的向外访问、第五项主要是防止自己的服务器被当做工具去害人。

２.路由器 (以Cisco路由器为例)

Cisco Express Forwarding（CEF）、使用 unicast reverse-path、访问控制列表（ACL）过滤、设置SYN数据包流量速率、升级版本过低的ISO、为路由器建立log server

