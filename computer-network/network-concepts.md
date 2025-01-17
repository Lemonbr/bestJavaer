# 计算机网络核心概念

* [计算机网络核心概念](#计算机网络核心概念)
   * [计算机网络基础概念](#计算机网络基础概念)
   * [计算机网络应用层](#计算机网络应用层)
   * [计算机网络传输层](#计算机网络传输层)
   * [计算机网络网络层](#计算机网络网络层)
   * [计算机网络数据链路层和物理层](#计算机网络数据链路层和物理层)
   * [计算机网络安全](#计算机网络安全)
   * [总结](#总结)

上回我整理了一下计算机网络中所有的关键概念，很多小伙伴觉得很有帮助，但是有一个需要优化的点就是这些概念不知道出自哪里，所以理解起来像是在云里穿梭，一会儿在聊应用层的概念，一会儿又跑到网络层协议了。针对这种情况，我重新根据不同的章节来进行整理和汇总，这篇文章理解起来，应该会舒服很多了。

## 计算机网络基础概念

1. `主机`：计算机网络上任何一种能够连接网络的设备都被称为主机或者说是`端系统`，比如手机、平板电脑、电视、游戏机、汽车等，随着 5G 的到来，将会有越来越多的终端设备接入网络。
2. `通信链路`：通信链路是由物理链路（同轴电缆、双绞线、光纤灯）连接到一起组成的一种物理通路。
3. `传输速率`：单位是 bit/s ，用来度量不同链路从一个端系统到另一个端系统传输数据的速率。
4. `分组`：当一台端系统向另外一台端系统发送数据时，通常会将数据进行分片，然后为每段加上首部字节，从而形成计算机网络的专业术语：分组。这些分组通过网络发送到端系统，然后再进行数据处理。
4. `转发表`：路由内部记录报文路径的映射关系的一种记录。
5. `路由器`：英文术语 router，路由器是连接因特网中各局域网、广域网的设备。路由器中维护着路由表，数据发送前路由器会查询路由表，然后根据路由表中记录的信息选择最佳传输路径，它是一种网络层的设备。

6. `交换机`：英文术语 switch，是一种光电信号转发设备，它可以为接入交换机的任意两个网络节点提供独享的电信号通路，它是一种数据链路层设备。
7. `集线器`：英文术语 hub，它是一种能够将多条以太网双绞线或光纤集合连接在同一段物理介质下的设备。它发生在物理层。

![image-20220307085246124](https://tva1.sinaimg.cn/large/e6c9d24ely1h0118nqpjtj21p40jeq58.jpg)

交换机和集线器的功能非常相似，交换机具有记忆功能，它广播之后能够缓存目标 Mac，后续的数据包就会直接通过缓存的路径发送，交换机是一种全双工通信模式。而集线器工作的时候，如果局域网中的一台电脑要发送消息，则局域网内的所有电脑都可以接收到这个消息，安全性较差，而且集线器是一种半双工模式。所以现在大多数都是用交换机，集线器慢慢被淘汰了。

8. `半双工模式`：连接在集线器中的端系统每次只能有数据包一个发送，只有这个发送完毕其他电脑才能再发送，这称为半双工模式。

9. `全双工模式`：连接在交换机中的端系统可以彼此之间相互通信，相互发送消息互不影响。

10. `路径`：一个分组所经历一系列通信链路和分组交换机称为通过这个网络的路径。

11. `因特网服务商`：ISP，不是 lsp（lao se pi）。这个好理解，就是网络运营商，我国的三大运营商：移动、电信、联通。

12. `网络协议`：网络协议是计算机网络中进行数据交换而建立的规则、标准或者约定。

13. `IP`：网际协议，它规定了路由器和端系统之间发送和接收的分组格式。

14. `TCP/IP 协议簇`：不仅仅只有 TCP 协议和 IP 协议，而是以 TCP、IP 协议为主的一系列协议，比如 ICMP 协议、ARP 协议、UDP 协议、DNS 洗衣、SMTP 协议等。

19. `丢包`：在计算机网络中指的是分组出现丢失的现象。

20. `吞吐量`：吞吐量在计算机网络中指的是单位时间内成功传输数据的数量。

21. `报文`：通常指的是应用层的分组。

22. `报文段`：通常把运输层的分组称为报文段。

23. `数据报`：通常将网络层的分组称为数据报。

24. `帧`：一般把链路层的分组称为帧。

25. `电路交换`：是通信网中最早出现的一种交换方式，一般多用于电话网，电路交换的过程中，数据交换是独占信道的，电路交换方式的优点是数据传输可靠、迅速，数据不会丢失，缺点是电路空闲时信道容量容易被浪费。

25. `报文交换`：报文交换是先将整个报文传送到临界点，全部存储下来之后再转发到下一个节点。

26. `分组交换`：分组交换是通信双方以分组为单位、使用存储-转发机制实现数据交互的通信方式，分组交换不会独占信道，从而资源利用率比较高。缺点是时延抖动、开销比较大。

27. `带宽`：带宽指单位时间能通过链路的数据量。通常以 bps 来表示，即每秒可传输的位数。

24. `频分复用`：多用于模拟信号，频分复用的各路信号是并行的。

25. `时分复用`：多用于数字信号，时分复用的各路信号是串行的。

26. `时延`：时延指的是一个报文或者分组从网络的一端传递到另一端所需要的时间，时延分类有发送时延、传播时延、处理时延、排队时延，总时延的计算方式：总时延 = 发送时延 + 传播时延 + 处理时延 + 排队时延。

27. `处理时延`：检查分组首部和决定分组传输路径所需要的时延被称为处理时延。

28. `排队时延`：分组在链路上等待的时间被称为处理时延。

29. `传输时延`：在实际链路中由一端传到网络从开始发送分组到发送完毕所耗费的时间被称为传输时延，可以理解为推出分组所需要的时间。

30. `传播时延`：分组从一台路由器传播到另一台路由器所需要的时间。

31. `单播`：单播最大的特点就是 1 对 1，早期的固定电话就是单播的一个例子

    <img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02lv252m1j21160ma75m.jpg" alt="image-20220308173152944" style="zoom:50%;" />

32. `广播`：我们一般小时候经常会广播体操，这就是广播的一个事例，主机和与他连接的所有端系统相连，主机将信号发送给所有的端系统。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02lvz4jfaj213w0kujse.jpg" alt="image-20220308173245652" style="zoom:50%;" />

34. `多播`：多播与广播很类似，也是将消息发送给多个接收主机，不同之处在于多播需要限定在某一组主机作为接收端。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02lwpr098j211e0oywft.jpg" alt="image-20220308173328256" style="zoom:50%;" />

35. `任播`：任播是在特定的多台主机中选出一个接收端的通信方式。虽然和多播很相似，但是行为与多播不同，任播是从许多目标机群中选出一台最符合网络条件的主机作为目标主机发送消息。然后被选中的特定主机将返回一个单播信号，然后再与目标主机进行通信。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02lx1ydrgj21240owwg4.jpg" alt="image-20220308173347438" style="zoom:50%;" />

## 计算机网络应用层

1. `应用程序体系结构`：其实就是应用层程序的两种组织结构，分为 CS 和 P2P。
2. `客户-服务体系`：它是一种面向网络应用的体系结构。把系统中的不同端系统区分为客户和服务器两类，客户向服务器发出服务请求，由服务器完成所请求的服务，并把处理结果回送给客户。在客户-服务器体系结构中，有一个总是打开的主机称为 `服务器(Server)`，它提供来自于 `客户(client)` 的服务。我们最常见的服务器就是 `Web 服务器`，Web 服务器服务于来自 `浏览器` 的请求。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h01mk4fu9ej20vq0i4abf.jpg" alt="image-20220307211024918" style="zoom:50%;" />

3. `P2P 体系`：对等体系结构，相当于没有服务器了，大家都是客户机，每个客户既能发送请求，也能对请求作出响应。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h01mkch35kj213s0mcabe.jpg" alt="image-20220307211037415" style="zoom: 50%;" />

4. `进程`：进程其实就是运行在端系统的程序，应用程序进行通信的最基本单位就是进程。

5. `分布式应用程序`：多个端系统之间相互交换数据的端系统被称为分布式应用程序。

6. `套接字接口`：指的就是 socket 接口，这个接口规定了端系统之间通过因特网进行数据交换的方式。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h012i93k5qj21590u0te8.jpg" alt="image-20220307093637809" style="zoom:50%;" />

7. `客户端`：在客户-服务器架构中扮演请求方的角色，通常是 PC，智能手机等端系统。

8. `服务器`：在客户-服务器架构中扮演服务方的角色，通常是大型服务器集群扮演服务器的角色。
9. `IP 地址`：IP 地址就是网际协议地址，在互联网中唯一标识主机的一种地址。每一台入网的设备都会有一个 IP 地址，这个 IP 又分为内网 IP 和公网 IP。
10. `端口号`：在同一台主机内，端口号用于标识不同应用程序进程。

11. `URI`：它的全称是（Uniform Resource Identifier），中文名称是统一资源标识符，使用它就能够唯一地标记互联网上资源。

12. `URL`：它的全称是（Uniform Resource Locator），中文名称是统一资源定位符，它实际上是 URI 的一个子集。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h01mjwdk58j20pg0asgly.jpg" alt="image-20220307211009147" style="zoom:50%;" />

13. `HTML`：HTML 称为超文本标记语言，是一种标识性的语言。它包括一系列标签．通过这些标签可以将网络上的文档格式统一，使分散的 Internet 资源连接为一个逻辑整体。HTML 文本是由 HTML 命令组成的描述性文本，HTML 命令可以说明文字，图形、动画、声音、表格、链接等。

14. `Web 页面`：Web 页面也叫做 `Web Page`，它是由对象组成，一个`对象(object)` 简单来说就是一个文件，这个文件可以是 HTML 文件、一个图片、一段 Java 应用程序等，它们都可以通过 URI 来找到。一个 Web 页面包含了很多对象，Web 页面可以说是对象的集合体。

15. `Web 服务器`：Web 服务器的正式名称叫做 `Web Server`，Web 服务器可以向浏览器等 Web 客户端提供文档，也可以放置网站文件，让全世界浏览；可以放置数据文件，让全世界下载。目前最主流的三个 Web 服务器是 Apache、 Nginx 、IIS。

16. `CDN`：CDN 的全称是`Content Delivery Network`，即`内容分发网络`，它应用了 HTTP 协议里的缓存和代理技术，代替源站响应客户端的请求。CDN 是构建在现有网络基础之上的网络，它依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户`就近`获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。
17. `专用 CDN`：由内容提供商特有 CDN 。
18. `第三方 CDN`：它代表多个内容提供商提供服务。
19. `WAF`：WAF 是一种 **应用程序防护系统**，它是一种通过执行一系列针对 HTTP / HTTPS的`安全策略`来专门为 Web 应用提供保护的一款产品，它是应用层面的`防火墙`，专门检测 HTTP 流量，是防护 Web 应用的安全技术。
20. `WebService` ：WebService 是一种 Web 应用程序，**WebService 是一种跨编程语言和跨操作系统平台的远程调用技术**。
21. `HTTP`： TCP/IP 协议簇的一种，它是一个在计算机世界里专门在两点之间传输文字、图片、音频、视频等超文本数据的约定和规范。
22. `Session`：Session 其实就是客户端会话的缓存，主要是为了弥补 HTTP 无状态的特性而设计的。服务器可以利用 Session 存储客户端在同一个会话期间的一些操作记录。当客户端请求服务端时，服务端会为这次请求开辟一块`内存空间`，这个对象便是 Session 对象，存储结构为 `ConcurrentHashMap`。
23. `Cookie`：HTTP 协议中的 Cookie 包括 `Web Cookie` 和`浏览器 Cookie`，它是服务器发送到 Web 浏览器的一小块数据。服务器发送到浏览器的 Cookie，浏览器会进行存储，并与下一个请求一起发送到服务器。通常，它用于判断两个请求是否来自于同一个浏览器，例如用户保持登录状态。
24. `SMTP 协议` ：提供电子邮件服务的协议叫做 SMTP 协议， SMTP 在传输层也使用了 TCP 协议。SMTP 协议主要用于系统之间的邮件信息传递，并提供有关来信的通知。
25. `POP3`：邮件访问协议，协议较为简单，功能有限。
26. `DNS 协议`：由于 IP 地址是计算机能够识别的地址，而我们人类不方便记忆这种地址，所以为了方便人类的记忆，使用 DNS 协议，来把我们容易记忆的网络地址映射称为主机能够识别的 IP 地址。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h01mktq1xhj20p40l2wfl.jpg" alt="image-20220307211105415" style="zoom:50%;" />

27. `根 DNS 服务器`：最顶级的 DNS 服务器，全世界有 400 多台根域名服务器，由 13 个不同的组织管理，根域名服务器提供 TLD 服务器的 IP 地址。
28. `顶级域 DNS 服务器`：这个我们比较熟悉，像是常见的顶级域（如 com、org、net、edu 和 gov）和所有的国家顶级域（uk、fr、ca 和 jp），TLD 服务器提供了权威 DNS 服务器的 IP 地址。
29. `权威 DNS 服务器`：这个服务器就是因特网上具有公共可访问主机的 DNS 记录的服务器。
30. `本地 DNS 服务器`：一般来说，每个 ISP 都有一台本地 DNS 服务器，本地 DNS 服务器会临近主机端。

![image-20220307214941635](https://tva1.sinaimg.cn/large/e6c9d24ely1h01np05u4cj21940g4ju3.jpg)

31. `TELNET 协议`：远程登陆协议，它允许用户(Telnet 客户端)通过一个协商过程来与一个远程设备进行通信，它为用户提供了在本地计算机上完成远程主机工作的能力。

![image-20220309084438274](https://tva1.sinaimg.cn/large/e6c9d24ely1h03c8gkqfdj21840ba754.jpg)

32. `SSH 协议`：SSH 是一种建立在应用层上的安全加密协议。因为 TELNET 有一个非常明显的缺点，那就是在主机和远程主机的发送数据包的过程中是明文传输，未经任何安全加密，这样的后果是容易被互联网上不法分子嗅探到数据包来搞一些坏事，为了数据的安全性，我们一般使用 `SSH` 进行远程登录。

33. `FTP 协议`：文件传输协议，是应用层协议之一。FTP 协议包括两个组成部分，分为 FTP 服务器和 FTP 客户端。其中 FTP 服务器用来存储文件，用户可以使用 FTP 客户端通过 FTP 协议访问位于 FTP 服务器上的资源。FTP 协议传输效率很高，一般用来传输大文件。

![image-20220309084426705](https://tva1.sinaimg.cn/large/e6c9d24ely1h03c8bwixmj215o0c63zg.jpg)

34. `MIME 类型`，它表示的是互联网的资源类型，一般类型有 超文本标记语言文本 .html text/html、xml文档 .xml text/xml、普通文本 .txt text/plain、PNG图像 .png image/png、GIF图形 .gif image/gif、JPEG图形 .jpeg,.jpg image/jpeg、AVI 文件 .avi video/x-msvideo 等。
35. `多路分解`：在接收端，运输层会检查源端口号和目的端口号等字段，然后标识出接收的套接字，从而将运输层报文段的数据交付到正确套接字的过程被称为多路分解。
36. `多路复用`：在发送方，从不同的套接字中收集数据块，然后为数据块封装上首部信息从而生成报文段，然后将报文段传递给网络层的过程被称为多路复用。
37. `周知端口号`：在主机的应用程序中，从 0 - 1023 的端口号是受限制的，被称为周知端口号，这些端口号一般不能占用。

## 计算机网络传输层

1. `可靠数据传输`：确保数据能够从程序的一端准确无误的传递给应用程序的另一端。

2. `容忍丢失的应用`：应用程序在发送数据的过程中可能会存在数据丢失的情况。

3. `非持续连接`：每个请求/响应会对经过不同的连接，每一个连接都会经过建立、保持、销毁这个过程。并且每个请求/响应后都会断开连接。

4. `持续连接`：每个请求/响应都会经过相同的连接，也就是说每个请求/响应都可以复用这个连接，并且在每个请求/响应后不会断开连接。

5. `传输控制协议`：英文名 TCP，通过名称可以大致知道 TCP 协议有控制传输的功能，主要体现在其可控，可靠性。TCP 为应用层提供了一种**可靠的、面向连接**的服务，它能够将分组可靠的传输到其他主机。

6. `用户数据包协议`：英文名 UDP，它为应用层提供了一种无需建立连接就可以直接发送数据报的方法。

7. `三次握手`：TCP 连接的建立需要经过三个报文段的发送，这种连接的建立过程被称为三次握手。

8. `最大报文段长度`：即 MSS，它指的是从缓存中取出并放入报文段中的最大值。

9. `最大传输单元`：即 MTU，它指的是通信双方能够接收有效载荷的大小，MSS 通常会根据 MTU 来设。

10. `冗余 ACK`：就是再次确认某个报文段的 ACK，报文段的丢失会导致冗余 ACK 的出现。

11. `快速重传`：即在报文段定时器过期之前重传丢失的报文段。

12. `选择确认`：在报文段出现丢失的情况下，TCP 能够选择确认失序的报文段，这个机制通常和重传一起使用。

13. `拥塞控制`：拥塞控制说的是，当某一段时间网络中的分组过多，使得接收端来不及处理，从而引起部分甚至整个网络性能下降的现象时采取的一种抑制发送端发送数据，等过一段时间或者网络情况改善后再继续发送报文段的一种方法。

14. `四次挥手`：TCP 断开链接需要经过四个报文段的发送，这种断开过程是四次挥手。

15. `发送缓存`：英文 send buffer，在发送报文时，TCP 不会立刻将报文发送出去，而是存储到内核的发送缓冲区中，等待合适的时机再发送。

16. `接收缓存`：英文 receive buffer，同样在接收报文时，主机不会立刻对报文进行处理，而是存储到内核的接收缓冲区中，等待合适的时机再进行处理。

    ![image-20220308093539652](https://tva1.sinaimg.cn/large/e6c9d24ely1h0283kjkt3j217q0nmwgn.jpg)

17. `SYN`：Synchronize Sequence Numbers，是 TCP/IP 建立连接时发送的数据包，这个数据包就是一个同步序列号，标识客户端发送的是哪个请求。

18. `ACK`：Acknowledge character，ACK 是对请求进行响应的数据包。

19. `FIN`：Finish ，带有 FIN 标志位的数据包表示客户端希望断开连接。

20. 三次握手中的状态变化

    * `LISTEN`: 表示等待任何来自远程 TCP 和端口的连接请求。
    * `SYN-SEND`: 表示发送连接请求后等待匹配的连接请求。
    * `SYN-RECEIVED`: 表示已接收并发送连接请求后等待连接确认，也就是 TCP 三次握手中第二步后服务端的状态
    * `ESTABLISHED`: 表示已经连接已经建立，可以将应用数据发送给其他主机

    <img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02bbzwt9ij210d0u0jv2.jpg" alt="image-20220308112733731" style="zoom:50%;" />

21. 四次挥手中的状态变化

    * `FIN-WAIT-1`: 表示等待来自远程 TCP 的连接终止请求，或者等待先前发送的连接终止请求的确认。
    * `FIN-WAIT-2`: 表示等待来自远程 TCP 的连接终止请求。
    * `CLOSE-WAIT`: 表示等待本地用户的连接终止请求。
    * `CLOSING`: 表示等待来自远程 TCP 的连接终止请求确认。
    * `LAST-ACK`: 表示等待先前发送给远程 TCP 的连接终止请求的确认（包括对它的连接终止请求的确认）。
    * `TIME-WAIT`: 表示等待足够的时间以确保远程 TCP 收到其连接终止请求的确认。
    * `CLOSED`: 表示连接已经关闭，无连接状态。

    <img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h02bc91dp1j20vt0u0jvl.jpg" alt="image-20220308112749030" style="zoom:67%;" />

22. `滑动窗口`：英文 sliding window，它是一种流量控制技术，在互联网早期，通信双方通常不会考虑网络情况，一般都会直接进行通信，同时发送数据，很容易导致阻塞，谁也发不了数据，针对这种现象，提出了滑动窗口，通过滑动窗口，接收方会告诉发送方自己能够接收多少数据。

23. `窗口长度`：窗口长度指的是已发送但还未确认的分组范围，如下图中的发送窗口结构就是窗口长度。

    ![image-20220308135839897](https://tva1.sinaimg.cn/large/e6c9d24ely1h02fp7qgevj213a0miq76.jpg)

24. `累积确认`：TCP 规定在一段时间内发送方只要收到最后一条接收方返回的确认 ACK ，而不用重传报文段。

25. `冗余ACK`：由于 TCP 采用的是累计确认机制，即当接收端收到比期望序号大的报文段时，便会重复发送最近一次确认的报文段的确认信号，我们称之为冗余 ACK。

26. `选择确认`：可选择性的确认失序报文段，而不是重传最后一个报文段。

## 计算机网络网络层

1. `路由选择算法`：网络层中决定分组发送路径的一种算法。

2. `转发`：它指的是将分组从一个输入链路转移到合适的输出链路的动作。

3. `路由选择`：指确定分组从一端发送到另一端所选择路径的处理过程。

4. `三种路由交换技术`：内存交换、总线交换、互联网络交换。

5. `分组调度`：分组调度讨论的是分组如何经输出链路传输的问题，主要有三种调度方式：先进先出、优先级排队和"循环和加权公平排队"。

6. `先入先出`：FIFO，或者称为 FCFS，先到达的分组优先进行处理。

   <img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h03eir0s1fj213k0ca74y.jpg" alt="image-20220309100343211" style="zoom:50%;" />

7. `优先权排队`：priority queue，到达输出链路的分组会被放入优先级队列里面。

   ![image-20220309100404137](https://tva1.sinaimg.cn/large/e6c9d24ely1h03ej40tfpj217y0cat9w.jpg)

8. `循环排队规则`：round robin queuing discipline，这种就是循环调度器会在队列进行轮流提供服务。

   ![image-20220309100432639](https://tva1.sinaimg.cn/large/e6c9d24ely1h03ejmr6h4j216k0fkq48.jpg)

9. `IPv4`：网际协议的第四个版本，也是被广泛使用的一个版本。IPv4 是一种无连接的协议，无连接不保证数据的可靠性交付。使用 32 位的地址。

10. `IPv6`：网际协议的第六个版本，IPv6 的地址长度是 128 位，由于 IPv4 最大的问题在于网络地址资源不足，严重制约了互联网的应用和发展。IPv6 的使用，不仅能解决网络地址资源数量的问题，而且也解决了多种接入设备连入互联网的障碍。

11. `接口`：主机和物理链路之间的边界。

12. `ARP 协议`：ARP 是一种解决地址问题的协议，通过 IP 位线索，可以定位下一个用来接收数据的网络设备的 MAC 地址。如果目标主机与主机不在同一个链路上时，可以通过 ARP 查找下一跳路由的地址。不过 ARP 只适用于 IPv4 ，不适用于 IPv6。

13. `RARP`：RARP 就是将 ARP 协议反过来，通过 MAC 地址定位 IP 地址的一种协议。

![image-20220309084454610](https://tva1.sinaimg.cn/large/e6c9d24ely1h03c8qw789j218u08wt9f.jpg)

14. `代理 ARP`：用于解决 ARP 包被路由器隔离的情况，通过代理 ARP 可以实现将 ARP 请求转发给临近的网段。
15. `ICMP 协议`：Internet 报文控制协议，如果在 IP 通信过程中由于某个 IP 包由于某种原因未能到达目标主机，那么将会发送 ICMP 消息，ICMP 实际上是 IP 的一部分。

![image-20220309084505703](https://tva1.sinaimg.cn/large/e6c9d24ely1h03c8zx3wdj218m0quq60.jpg)

16. `DHCP 协议`：DHCP 是一种动态主机配置协议，又被称为即插即用协议或者零配置协议，使用 DHCP 就能实现自动设置 IP 地址、统一管理 IP 地址分配，实现即插即用。
17. `NAT 协议`：网络地址转换协议，它指的是所有本地地址的主机在接入网络时，都会要在 NAT 路由器上讲其转换成为全球 IP 地址，才能和其他主机进行通信。
18. `NAT 转换表`：和路由表类似，NAT 转换表记录了私有 IP 地址和公共 IP 地址的转换记录。
19. `NAT 穿越`：NAT 穿越用来解决处于使用了 NAT 设备的私有 TCP/IP 网络中主机之间建立连接的问题。
20. `IP 隧道`：IP 隧道技术说的是由路由器把网络层协议封装到另一个协议中从而跨过网络传输到另外一个路由器的过程。
21. `OSPF`：是根据 OSI 的 IS-IS 协议提出的一种链路状态型协议。这种协议还能够有效的解决网络环路问题。
22. `BGP`：边界网关协议，这个协议将因特网中数以千计的 ISP 连接起来。
23. `IGP`：内部网关协议，一般用于企业内部自己搭建的路由自治系统。
24. `EGP`：外部网关协议，EGP 通常用于在网络主机之间相互交换路由信息。
25. `RIP` ：一种距离向量型路由协议，广泛应用于 LAN 网。

## 计算机网络数据链路层和物理层

1. `节点`：一般指链路层协议中的设备。
2. `链路`：一般把沿着通信路径连接相邻节点的通信信道称为链路。
3. `MAC 协议`：媒体访问控制协议，它规定了帧在链路上传输的规则。
4. `奇偶校验位`：一种差错检测方式，多用于计算机硬件的错误检测中，奇偶校验通常用在数据通信中来保证数据的有效性。
5. `向前纠错`：接收方检测和纠正差错的能力被称为向前纠错。
6. `以太网`：以太网是一种当今最普遍的局域网技术，它规定了物理层的连线、电子信号和 MAC 协议的内容。
7. `VLAN`：虚拟局域网（VLAN）是一组逻辑上的设备和用户，这些设备和用户并不受物理位置的限制，可以根据功能、部门及应用等因素将它们组织起来，相互之间的通信就好像它们在同一个网段中一样，所以称为虚拟局域网。
8. `基站`：无线网络的基础设施。
9. `奇偶校验位`：一种进行差错检测的方式。
10. `向前纠错`：接收方检测和纠正差错的能力被称为向前纠错，也就是 FEC。
11. `校验和`：checksum，在数据处理和数据通信领域中，用于校验目的地一组数据项的和。
12. `循环冗余检测`：CRC ，一种现如今正在使用的差错检测技术，使用多项式来进行差错检测。
13. `CSMA/CD`：具有碰撞的载波侦听多路访问，CSMA/CD 会要求每个介质提前检查一下链路上是否有可能产生冲突的现象，一旦发生冲突，那么尽可能早地释放信道。
14. `共享介质型网络`：故名思义就是多个设备共同使用同一个通信介质的网络。
15. `非共享介质型网络`：与共享介质型网络相对，这种网络不会使用相同的通信介质。
16. `令牌环`：一种共享介质型网络传输方式。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h03n9t7kpsj210e0u076i.jpg" alt="image-20220309150627463" style="zoom:50%;" />

17. `过滤`：在链路层是决定一个帧应该转发到某个接口还是应当将其丢弃的交换机的一种功能。
18. `转发`：转发决定一个帧应该导向那个接口，并把帧移动到那些接口的交换机的一种功能。
19. `交换机表`：交换机的过滤和转发功能都依靠交换机表来完成。
20. `MPLS`：它是一种标记交换技术，标记交换会对每个 IP 数据包都设定一个标记，然后根据这个标记进行转发。

## 计算机网络安全

1. 安全通信的四大要素：机密性、保温完整性、端点鉴别和运行安全性。
2. `机密性`：报文需要在一定程度上进行加密，用来防止窃听者截取报文。
3. `报文完整性`：在报文传输过程中，需要确保报文的内容不会发生改变。
4. `端点鉴别`：发送方和接收方都应该证实通信过程中所对方的身份。
5. `运行安全性`：设施保护报文防止被攻击的能力。
6. `明文`：没有被加密过的内容都被称为明文。
7. `加密算法`：对原来明文的文件或数据按照某种算法进行处理，这种算法就是加密算法。
8. `密文`：对明文进行加密生成后的报文称为密文。
9. `解密算法`：对密文进行解密的算法。
10. `密钥`：解密算法对密文进行解密的工具叫做密钥。
11. `对称加密`：采用单钥密码系统的加密方法，同一个密钥可以同时用作信息的加密和解密，这种加密方法称为对称加密，也称为单密钥加密。
12. `块密码`：块密码也叫做分组密码，顾名思义，它把加密和解密序列分成了一个个分组，最后把每一块序列合并到一起，形成明文或者密文。
13. `流密码`：流密码也叫做序列密码，每次加密都通过密钥生成一个密钥流，解密也是使用同一个密钥流，明文与同样长度的密钥流进行异或运算得到密文，密文与同样的密钥流进行异或运算得到明文。
14. `公钥`：公钥是与私钥算法一起使用的密钥对的非秘密一半。公钥通常用于加密会话密钥、验证数字签名，或加密可以用相应的私钥解密的数据
15. `私钥`：私钥通常是公钥的另一半，私钥只有自己知道，可以用来加密或解密。
16. `CA` 认证中心，CA 的职责就是使识别和发行证书合法化。
17. `防火墙`：一种软硬件结合体，将机构的内部网络和整个因特网隔离，允许一些分组通过，阻止一些分组通过。
18. 防火墙一般分为三种：分组过滤器、状态过滤器和应用程序网关。
19. `分组过滤器`：机构将内部网络与外部网络进行隔离，所有离开和进入内部网络的分组都会经过这个路由器，这个路由器会检查每个分组的信息。
20. `状态分组过滤器`：根据分组中的 TCP 连接状态进行过滤。
21. `应用程序网关`：一个应用程序网关是一个特定的应用程序，所有应用程序的数据都会经过它。
22. `入侵检测系统`：观察到潜在恶意流量时能够产生警告的设备称为入侵检测系统
23. `入侵防止系统`：过滤恶意流量的设备称为入侵防止系统。

## 总结

计算机网络范围内重点概念非常多，这篇文章我总结了一部分我认为应该重点了解的概念，也许有一些概念解释的没那么清晰，你可以作为一个参考或者说索引，等遇到相关概念时，能够大致理解其意思，那么这篇文章的目的就达到了，如果文章对你有帮助，欢迎大家点赞、再看、分享，你的每一份支持是我更文最大的动力！
