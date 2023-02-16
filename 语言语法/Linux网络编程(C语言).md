<a name="ImEyj"></a>
# 01-Socket编程
<a name="ZDRGk"></a>
## 01-套接字

- Socket本身有“插座”的意思，在Linux环境下，**用于表示进程间网络通信的特殊文件类型。本质为内核借助缓冲区形成的伪文件。**
- 在TCP/IP协议中，“IP地址+TCP或UDP端口号”唯一标识网络通讯中的一个进程。“IP地址+端口号”就对应一个socket。欲建立连接的两个进程各自有一个socket来标识，那么这两个socket组成的socket pair就唯一标识一个连接。因此可以用Socket来描述网络连接的一对一关系。
- **在网络通信中，套接字一定是成对出现的。**一端的发送缓冲区对应对端的接收缓冲区。我们使用同一个文件描述符索发送缓冲区和接收缓冲区

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671434009447-b70ae98b-22b2-47d0-89a2-ca6c7e08fa9b.png#averageHue=%23f1f1f1&clientId=u72b09786-cfab-4&from=paste&height=204&id=u590e6a7e&name=image.png&originHeight=204&originWidth=675&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25738&status=done&style=none&taskId=ua38e2e57-605f-4881-ba75-08181f5a885&title=&width=675)
<a name="MK1HV"></a>
## ![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671434021821-9e1292f6-d490-4c44-9700-607f33c8fc92.png#averageHue=%23f2f2f2&clientId=u72b09786-cfab-4&from=paste&height=481&id=u7b9b4b55&name=image.png&originHeight=481&originWidth=518&originalType=binary&ratio=1&rotation=0&showTitle=false&size=110769&status=done&style=none&taskId=uab4051ec-8e42-4a10-828b-aad45edb980&title=&width=518)
<a name="JF8t5"></a>
## 02-预备知识
<a name="zJsXb"></a>
### 01-网络字节序
:::info
字节序的概念

- 数据在内存或者网络中的存储方式。
- **高低字节：数据的高低位。**
- 高低地址：内存存储的从小到大排列，是低到高

字节序的分类

- 小端字节序（小端存储）：数据的低位（低字节）存放在低地址，高位存放在高地址	为本地字节序
- **大端字节序（大端存储）：数据的低位（低字节）存放在高地址，高位存放在低地址	为网络字节序**

网络数据流的地址应这样规定<br />先发出低地址的数据，后发出高地址数据。

**总结：**<br />**本机上是低位放低地址，是从小到大。**<br />**网络上是高位放低地址，是从大到小。**<br />发送主机 ->网络->接收主机。要做两次字节序转换
:::
<a name="Ap1BG"></a>
### 02-IP地址转换函数
:::info
**转换函数**<br />#include <arpa/inet.h>

- uint32_t htonl(uint32_t hostlong); 〃长整形主机字节序至!］网络字节序
- uint32_t ntohl(uint32_t netllong); 〃长整形网络字节序到主机字节序
- uintl6_t **htons**(uintl6_t hostshort);//短整形主机字节序到网络字节序
- uintl6_t ntohs(uintl6_t netshort);//短整开彳网络字节序到主机字节序
- in_addr_t inet_addr(char const* ip);
   - 点分十进制字符串地址一》网络字节序形式整数地址
- int inet_aton (char const* ipz struct in_ addr* nip);
   - 点分十进制字符串地址一》网络字节序形式整数地址
- char* inet_ntoa(struct in_addr nip);
   - 网络字节序形式整数地址一》点分十进制字符串地址
:::
<a name="ZExFT"></a>
## 03-套接字地址结构和函数
<a name="JpfJp"></a>
### 01-socket()
:::info
#include <sys/socket.h><br />int socket(int domain, int type, int protocol);

- 功能：创建套接字
- 参数:   
   - domain:	通信域，协议族，可取以下值:
      - **AF_INET**、AF_INET6、AF_LOCAL
      - PF_LOCAL/PF_UNIX		本地套接字,进程间通信
      - PF_INET				基于IPv4的网络通信
      - PF_INET6				基于IPv6的网络通信
      - PF_PACKET			基于底层包的网络通信
   - type:	套接字类型，可取以下值：
      - **SOCK_STREAM	**流式套接字，基于TCP协议 
      - SOCK_DGRAM 	数据报套接字,基于UDP协议 
      - SOCK_RAW 		原始套接字,工作在传输层以下 
   - protocol:	特殊协议，对于流式和数据报套接字而言，只能取0 
- 返回值：成功返回表示套接字对象的文件描述符,失败返回-1。
:::
<a name="YUftj"></a>
### 02-套接字地址结构
套接字接口库通过地址结构定位一个通信主体，可以是一个文件，可以是 台远程主机，也可以是执行者自己
:::info
**基本地址结构**,本身没有实际意义，仅用于泛型化参数<br />struct sockaddr {<br />sa_family_t sa_family; 	// 地址族<br />char sa_data[14]; 		// 地址值<br />}；

**本地地址结构**，用于AF_LOCAL/AF_UNIX域的本地通信<br />struct sockaddr_un {<br />sa_family_t sun_family;	// 地址族(AF_LOCAL/AF_UNIX) <br />char sun_path[]; 		//本地套接字文件的路径<br />}；

**网络地址结构**，用于AF_INET域的IPv4网络通信<br />struct sockaddr_in {<br />sa_family_t sin_family; 	// 地址族(AF_INET)<br />in_port_t sin_port; 		//端口号(0-65535) 	-unsigned short <br />struct in_addr sin_addr;	// IP地址			-unsigned int<br />}；<br />struct in_addr {<br />in_addr_t s_addr; // 常用 INADDR_ANY 任何ip<br />}；<br />typedef uintl6_t in_port_t; 	// 无符号16位整数<br />typedef uint32_t in_addr_t; 	// 无符号32位整数

**创建一个地址结构：**<br />struct sockaddr_in ser;<br />ser.sin_family = AF_INET;<br />ser.sin_port = htons(port);<br />ser.sin_addr.s_addr = INADDR_ANY;
:::
<a name="Zc8PE"></a>
### 03-bind()
:::info
#include ＜sys/socket.h＞<br />int bind(int sockfd, struct sockaddr const* addr, socklen_t addrlen);

- 功能：
   - 将套接字和本机的地址结构绑定在一起
- 参数：
   - sockfd :套接字描述符。
   - addr:自己的地址结构。
   - addrlen :地址结构的字节数
- 返回值：
- 成功返回0 ,失败返回-1。

:::
<a name="K11ck"></a>
### 04-connect()
:::info
#include ＜sys/socket.h＞<br />int bind(int sockfd, struct sockaddr const* addr, socklen_t addrlen);

- 功能：
   - 将套接字和本机的地址结构绑定在一起
- 参数：
   - sockfd :套接字描述符。
   - addr:自己的地址结构。
   - addrlen :地址结构的字节数
- 返回值：
   - 成功返回0 ,失败返回-1。
:::
<a name="TOKXN"></a>
### 05-setsockopt()
:::info
#include ＜sys/socket.h＞<br />int setsockopt(int s, int level, int optname, const void * optval, ,socklen_t optlen);

- 功能：
   - 设置参数s 所指定的socket 状态. 
- 参数：
   - s :		套接字描述符。
   - level:	代表域设置的网络层, 一般设成**SOL_SOCKET**
   - optname :	代表域设置的选项
      - SO_DEBUG 打开或关闭排错模式
      -   ** SO_REUSEADDR 允许在bind ()过程中本地地址可重复使用**
      -    SO_TYPE 返回socket 形态.
      -    SO_ERROR 返回socket 已发生的错误原因
      -    SO_DONTROUTE 送出的数据包不要利用路由设备来传输.
      -    SO_BROADCAST 使用广播方式传送
      -    SO_SNDBUF 设置送出的暂存区大小
      -    SO_RCVBUF 设置接收的暂存区大小
      -    SO_KEEPALIVE 定期确定连线是否已终止.
      -    SO_OOBINLINE 当接收到OOB 数据时会马上送至标准输入设备
      -    SO_LINGER 确保数据安全且可靠的传送出去.
   - optval：域设置的值,
   - optlen：optval的长度
- 返回值：
   - 成功返回0 ,失败返回-1。
- 附加说明：

1、EBADF 参数s 并非合法的socket 处理代码<br />2、ENOTSOCK 参数s 为一文件描述词, 非socket<br />3、ENOPROTOOPT 参数optname 指定的选项不正确.<br />4、EFAULT 参数optval 指针指向无法存取的内存空间.
:::
<a name="zOiUG"></a>
## 04-TCP
<a name="WQuPm"></a>
### 01-常用函数
<a name="TlhQ7"></a>
#### 01-listen()
:::info
#include <sys/socket.h><br />int listen(int sockfd, int backlog)

- 功能：
   - 启动侦听：在指定套接字上启动对连接请求的侦听功能
- 参数：
   - sockfd :套接字描述符,在调用此函数之前是f 主动套接字,是不能感知 连接请求的，在调用此函数并成功返回之后，是一个被动套接字, 具有感知连接请求的能力。
   - backlog :未决连接请求队列的最大长度，一般取不小于1024的值。
- 返回值：
   - 成功返回0 ,失败返回-1。
:::
<a name="Eqftd"></a>
#### 02-accept()
:::info
#inelude <sys/socket.h><br />int accept(int sockfd, struct sockaddr* addr; socklen_t* addrlen);

- 功能：
   - 等待并接受连接请求,在指定套接字上**阻塞**,直到连接建立完成。
- 参数：
   - sockfd :	侦听套接字描述符。
   - addr:	输岀连接请求发起方的地址信息。
   - addrlen :	输岀连接请求发起方的地址信息字节数。
- 返回值：
   - 成功返回可用于后续通信的连接套接字描述符,失败返回
:::
<a name="ZeJju"></a>
#### 03-recv()
:::info
#inelude <sys/socket.h><br />ssize_t recv(int sockfd, void* buf, size_t count, int flags);

- 功能：接收数据
- 参数：若flags取0则与read函数完全等价，另外也可取以下值:
   - MSG.DONTWAIT 	-以非阻塞方式接收数据。
   - MSG.OOB       		-接收带外数据。
   - MSG_WAITALL 	-等待所有数据，即不接收到count字节就不返回。
- 返回值：
- 成功返回实际接收到的字节数，失败返回-1。
:::
<a name="tw82A"></a>
#### 04-send()
:::info
#inelude <sys/socket.h><br />ssize_t send(int sockfd, void const* buf, size_t count, int flags);

- 功能：发送数据
- 参数：若flags取0则与write函数完全等价,另外也可取以下值：
   - MSG.DONTWAIT 	-以非阻塞方式接收数据。
   - MSG.OOB       		-接收带外数据。
   - MSG_DONTROUTE -不查路由表，直接在本地网络中寻找目的主机
- 返回值：
   - 成功返回实际发送的字节数，失败返回-1。
:::
<a name="Vrm36"></a>
### 02-TCP的编程模型
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671438666226-a2067539-84fe-41df-ba19-548101753896.png#averageHue=%23c7d2e4&clientId=u72b09786-cfab-4&from=paste&height=279&id=u76a7c9ad&name=image.png&originHeight=494&originWidth=1062&originalType=binary&ratio=1&rotation=0&showTitle=false&size=283456&status=done&style=none&taskId=u00ea9373-8404-44b0-84c9-c49a2cc3dc7&title=&width=600.0084838867188)

<a name="shGZD"></a>
## 05-UDP
<a name="TlFEV"></a>
### 01-常用函数
<a name="cwLi7"></a>
#### 01-recvfrom()
:::info
#include ＜sys/socket.h＞<br />ssize_t recvfrom(int sockfd, 	void* buf,	size_t count, 	int flags,<br />struct sockaddr* src_addr,  	socklen_t* addrlen);

- 功能：从哪里接收数据
- 参数：前四个参数和函数reev相同
   - src_addr:输出源主机的地址信息 
   - addrlen :输入输出源主机的地址信息的字节数。
- 返回值：成功返回实际接收的字节数，失败返回-1
:::
<a name="xK9t3"></a>
#### 02-sendto()
:::info
#inelude ＜sys/socket.h＞<br />ssize_t sendto(	int sockfd, void con st* buf, size_t count, int flags,<br /> 	struct sockaddr const* dest_addr,	socklen_t addrlen);

- 功能：发送数据到哪里
- 参数：前四个参数和函数send相同
   - dest_addr :目的主机的地址信息。
   - addrlen :目的主机的地址信息的字节数。
- 返回值：成功返回实际发送的字节数，失败返回-1
:::
<a name="Avrrm"></a>
### 02-UDP编程模型
:::info
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671439135385-2ca7fc67-fa69-4aea-a00f-7e8cded36b82.png#averageHue=%23c3cfe2&clientId=u72b09786-cfab-4&from=paste&height=183&id=u63de6591&name=image.png&originHeight=323&originWidth=888&originalType=binary&ratio=1&rotation=0&showTitle=false&size=178614&status=done&style=none&taskId=u76aba5b5-006e-4892-b109-d907f27d3ce&title=&width=503.022705078125)<br />AUDP服务器的阻塞焦点不在accept函数上，而在recvfrom函数上。任何一个UDP客户 机通过sendto函数发送的请求数据都可以被recvfrom函数返回给UDP服务器，其输出的 客户机地址结构src_addr可直接被用于向客户机返回响应时调用sendto函数的输入 dest_addr

![image.png](https://cdn.nlark.com/yuque/0/2022/png/22347830/1671439169790-0ac513bf-0bae-4268-a691-5685dd1ffb13.png#averageHue=%23c3d0e2&clientId=u72b09786-cfab-4&from=paste&height=184&id=u1b529ff4&name=image.png&originHeight=331&originWidth=915&originalType=binary&ratio=1&rotation=0&showTitle=false&size=199914&status=done&style=none&taskId=u5354df67-bde8-46e4-9044-31edf9b1734&title=&width=508.03125)<br />UDP的connect函数与TCP的connect函数完全不同，既无三路握手,亦无虚拟电路, 而仅仅是将传递给该函数的对方地址结构缓存在套接字对象中。此后收发数据时，可不使 用recvfrom/sendto函数，而是使用recv/send或者read/write函数，直接和所连接的对 方主机通信
:::
<a name="YieME"></a>
## 06-DNS
<a name="SfMw8"></a>
### 01-gethostbyname()

- #incluce<netdb.h＞
- struct hostent* gethostbyname(char const* host_name);
- 功能：通过参数所传的主机域名Z获取主机信息
- 参数:host_name主机域名
- 返回值：函数执行成功返回表示主机信息的结构体指针,失败返回NULL
- 注意，该函数需要再联网情况下使用

hostent结构体：
:::info
struct hostent{<br />char *h_name;		//主机官方名 只有一个<br />char **h_aliases;	//主机别名表 有多个	<br />int h_addrtype;		//地址类型<br />int h_length;		//地址长度<br />char **h_addr_list;	//IP地址表<br />}
:::
<a name="suPsm"></a>
# 02-高并发服务器
<a name="uJ9j6"></a>
# 03-Libevent的使用
<a name="xpwEd"></a>
# <br />
