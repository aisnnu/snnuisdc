目录
# 公共技能
## 安装和使用KaliLinux
## 熟悉Nmap的基本操作
## 熟悉Metasploit
## 密码学基础知识
## Owasp TOP10漏洞原理和修补方法
## Burpsuit的使用
# 公共技能
  这是一个大家都需要共同学习和掌握的基本技能
  
##   安装和使用KaliLinux
   Linux的安装有两种方式，一种是物理机直接安装，一种是虚拟机里安装。建议新手使用虚拟机
   安装，虚拟机（Virtual Machine）就是通过软件方法利用一台物理电脑的硬盘和内存可虚拟出
   若干台机器。它是电脑中的电脑，是利用软件虚拟出来的计算机，是在现有的操作系统上虚拟出来
   的一个完全隔离环境中的完整计算机系统。运行虚拟机的电脑分为Host（主系统）和Guest OS（子系统），
   Host就是用户的计算机，直接控制操作系统和硬件，称为宿主机，Guest OS则是利用软件在主系统中虚拟
   出来一个硬件环境，称为虚拟机或客户机。由宿主机创建的虚拟机，与真实的计算机几乎一模一样，不但有独
   立的CPU、内存、硬盘网卡等各种硬件，还有自己的BIOS。用户也可以在虚拟机上安装Linux、Windows等真实的
   操作系统及各种应用软件。
### KaliLinux在虚拟机里的安装
    1、首先你需要查看一下你的电脑CPU支持不支持虚拟化，一般来说，现在的CPU只要不是那种老古董处理器，都支持
    虚拟化，所以你要是购买电脑的话，CPU最低型号也应该是Intel i5以上的五代处理器。这是最低的型号，再低的话
    可以安装是可以安装，但是不保证能流畅运行。
    2、下载Vmware（一款支持物理机虚拟化安装操作系统的软件）
       下载链接：https://pan.baidu.com/s/1Lnu5n445_LQ_qm3Zy_L77g
    3、下载KaliLinux
        http://cdimage.kali.org/kali-2018.2/kali-linux-2018.2-amd64.iso    
    4、安装Kali
       这个操作自行百度获取操作方法。
### 安装完KaliLinux后需要做的几件事
#### 将Kali Linux的源换到国内
     鼠标单击右键打开终端，输入
    sudo vim /etc/apt/sources.list
    这个时候你就进入了sources.list这个文件的源码界面，相当于你打开了一个Word文档
    这个时候你还不能进入编辑界面，这是由于你没有打开编辑模式的缘故。此时按一下i，你就
    会进入编辑模式。复制以下两行内容到sources.list
    deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
    deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
    完成以上操作后你需要退出编辑模式，此时按一下“ESC”键，这个键通常在你键盘的左上角。
    退出编辑模式后，按一下： 并输入wq，回车。这个操作的作用是：保存并退出sources.list
    
#### Install VMware Tools
    依次点击虚拟机->安装vmware-tools，找到压缩包，并拷贝到home文件夹下，文件名后缀是
    tar.gz
    Copy VNware Tools Desk
    tar -zxvf Filename
    cd vmware-tools-distrib
    ./vmware-install.pl
    Update KaliLinux
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install linux-source
#### Install SouGouPinYin
    sudo apt-get install fcitx
    sudo apt-get install fcitx-libs-qt
    下载搜狗拼音 For Linux
    dpkg -i File.deb
    sudo apt-get --fix-broken install
## 熟悉Nmap的基本操作
### 简介
nmap是一个网络连接端扫描软件，用来扫描网上电脑开放的网络连接端。确定哪些服务运行在哪些连接端，并且推断计算机运行哪个操作系统（这是亦称 fingerprinting）。它是网络管理员必用的软件之一，以及用以评估网络系统保安。
正如大多数被用于网络安全的工具，nmap 也是不少黑客及骇客（又称脚本小孩）爱用的工具 。系统管理员可以利用nmap来探测工作环境中未经批准使用
的服务器，但是黑客会利用nmap来搜集目标电脑的网络设定，从而计划攻击的方法。
Nmap 常被跟评估系统漏洞软件Nessus 混为一谈。Nmap 以隐秘的手法，避开闯入检测系统的监视，并尽可能不影响目标系统的日常操作。
### 功能
其基本功能有三个
    一是探测一组主机是否在线；
    其次是扫描 主机端口，嗅探所提供的网络服务；
    还可以推断主机所用的操作系统 。
Nmap可用于扫描仅有两个节点的LAN，直至500个节点以上的网络。Nmap 还允许用户定制扫描技巧。通常，一个简单的使用ICMP协议的ping操作可以满足一般需求；
也可以深入探测UDP或者TCP端口，直至主机所 使用的操作系统；还可以将所有探测结果记录到各种格式的日志中， 供进一步分析操作。
进行ping扫描，打印出对扫描做出响应的主机,不做进一步测试(如端口扫描或者操作系统探测)：
        nmap -sP 192.168.1.0/24
仅列出指定网络上的每台主机，不发送任何报文到目标主机：
        nmap -sL 192.168.1.0/24
探测目标主机开放的端口，可以指定一个以逗号分隔的端口列表(如-PS22，23，25，80)：
        nmap -PS 192.168.1.234
使用UDP ping探测主机：
        nmap -PU 192.168.1.0/24
使用频率最高的扫描选项：SYN扫描,又称为半开放扫描，它不打开一个完全的TCP连接，执行得很快：
        nmap -sS 192.168.1.0/24
当SYN扫描不能用时，TCP Connect()扫描就是默认的TCP扫描：
        nmap -sT 192.168.1.0/24
UDP扫描用-sU选项,UDP扫描发送空的(没有数据)UDP报头到每个目标端口:
        nmap -sU 192.168.1.0/24
确定目标机支持哪些IP协议 (TCP，ICMP，IGMP等):
        nmap -sO 192.168.1.19
探测目标主机的操作系统：
        nmap -O 192.168.1.19
        nmap -A 192.168.1.19
另外，nmap官方文档中的例子：
        nmap -v scanme.
这个选项扫描主机scanme中 所有的保留TCP端口。选项-v启用细节模式。
        nmap -sS -O scanme./24
进行秘密SYN扫描，对象为主机Saznme所在的“C类”网段 的255台主机。同时尝试确定每台工作主机的操作系统类型。因为进行SYN扫描 和操作系统检测，这个扫描需要有根权限。
        nmap -sV -p 22，53，110，143，4564 198.116.0-255.1-127
进行主机列举和TCP扫描，对象为B类188.116网段中255个8位子网。这 个测试用于确定系统是否运行了sshd、DNS、imapd或4564端口。如果这些端口 打开，将使用版本检测来确定哪种应用在运行。
        nmap -v -iR 100000 -P0 -p 80
随机选择100000台主机扫描是否运行Web服务器(80端口)。由起始阶段 发送探测报文来确定主机是否工作非常浪费时间，而且只需探测主机的一个端口，因 此使用-P0禁止对主机列表。
        nmap -P0 -p80 -oX logs/pb-port80scan.xml -oG logs/pb-port80scan.gnmap 216.163.128.20/20
扫描4096个IP地址，查找Web服务器(不ping)，将结果以Grep和XML格式保存。
        host -l | cut -d -f 4 | nmap -v -iL -
进行DNS区域传输，以发现中的主机，然后将IP地址提供给 Nmap。上述命令用于GNU/Linux -- 其它系统进行区域传输时有不同的命令。
其他选项：
-p (只扫描指定的端口)
单个端口和用连字符表示的端口范 围(如 1-1023)都可以。当既扫描TCP端口又扫描UDP端口时，可以通过在端口号前加上T: 或者U:指定协议。 协议限定符一直有效直到指定另一个。 例如，参数 -p U:53，111，137，T:21-25，80，139，8080 将扫描UDP 端口53，111，和137，同时扫描列出的TCP端口。
-F (快速 (有限的端口) 扫描)
### 使用
#### 安装Nmap
Nmap要用到一个称为“Windows包捕获库”的驱动程序WinPcap——如果你经常从网上下载流媒体电影，可能已经熟悉这个驱动程序——某些流媒体电影的地址是加密的，侦测这些电影的真实地址就要用到WinPcap。WinPcap的作用是帮助调用程序（即这里的Nmap）捕获通过网卡传输的原始数据。WinPcap支持XP/2K/Me/9x全系列操作系统，下载得到的是一个执行文件，双击安装，一路确认使用默认设置就可以了，安装好之后需要重新启动。
接下来下载Nmap（国内各大软件网站也有，但一般版本更新略有滞后）。下载好之后解开压缩，不需要安装。除了执行文件nmap.exe之外，它还有下列参考文档：
    nmap-os-fingerprints：列出了500多种网络设备和操作系统的堆栈标识信息。
    nmap-protocols：Nmap执行协议扫描的协议清单。
    nmap-rpc：远程过程调用（RPC）服务清单，Nmap用它来确定在特定端口上监听的应用类型。
    nmap-services：一个TCP/UDP服务的清单，Nmap用它来匹配服务名称和端口号。除了命令行版本之外，还提供了一个带GUI的Nmap版本。和其他常见的Windows软件一样，GUI版本需要安装，图一就是GUI版Nmap的运行界面
#### 常用扫描类型
解开Nmap命令行版的压缩包之后，进入Windows的命令控制台，再转到安装Nmap的目录（如果经常要用Nmap，最好把它的路径加入到PATH环境变量）。不带任何命令行参数
。GUI版的功能基本上和命令行版本一样，鉴于许多人更喜欢用命令行版本，本文后面的说明就以命令行版本为主。 下面是Nmap支持的四种最基本的扫描方式：
⑴ TCP connect()端口扫描（-sT参数）。
⑵ TCP同步（SYN）端口扫描（-sS参数）。
⑶ UDP端口扫描（-sU参数）。
⑷ Ping扫描（-sP参数）。
如果要勾画一个网络的整体情况，Ping扫描和TCP SYN扫描最为实用。Ping扫描通过发送ICMP （Internet Control Message Protocol，Internet控制消息协议）回应请求数据包和TCP应答（Acknowledge，简写ACK）数据包，确定主机的状态，非常适合于检测指定网段内正在运行的主机数量。
TCP SYN扫描一下子不太好理解，但如果将它与TCP connect()扫描比较，就很容易看出这种扫描方式的特点。在TCP connect()扫描中，扫描器利用操作系统本身的系统调用打开一个完整的TCP连接——也就是说，扫描器打开了两个主机之间的完整握手过程（SYN，SYN-ACK，和ACK）。一次完整执行的握手过程表明远程主机端口是打开的。
TCP SYN扫描创建的是半打开的连接，它与TCP connect()扫描的不同之处在于，TCP SYN扫描发送的是复位（RST）标记而不是结束ACK标记（即，SYN，SYN-ACK，或RST）：如果远程主机正在监听且端口是打开的，远程主机用SYN-ACK应答，Nmap发送一个RST；如果远程主机的端口是关闭的，它的应答将是RST，此时Nmap转入下一个端口。
Nmap支持丰富、灵活的命令行参数。例如，如果要扫描192.168.7网络，可以用 192.168.7.x/24或192.168.7.0-255的形式指定IP地址范围。指定端口范围使用-p参数，如果不指定要扫描的端口，Nmap默认扫描从1到1024再加上nmap-services列出的端口。如果要查看Nmap运行的详细过程，只要启用verbose模式，即加上-v参数，或者加上-vv参数获得更加详细的信息。例如，nmap -sS 192.168.7.1-255 -p 20,21,53-110,30000- -v命令，表示执行一次TCP SYN扫描，启用verbose模式，要扫描的网络是192.168.7，检测20、21、53到110以及30000以上的端口（指定端口清单时中间不要插入空格）。再举一个例子，nmap -sS 192.168.7.1/24 -p 80扫描192.168.0子网，查找在 80端口监听的服务器（通常是Web服务器）。
有些网络设备，例如路由器和网络打印机，可能禁用或过滤某些端口，禁止对该设备或跨越该设备的扫描。初步侦测网络情况时，-host_timeout参数很有用，它表示超时时间，例如 nmap sS host_timeout 10000 192.168.0.1命令规定超时时间是10000毫秒。
## 熟悉Metasploit
Metasploit是一款开源的安全漏洞检测工具，可以帮助安全和IT专业人士识别安全性问题，验证漏洞的缓解措施，并管理专家驱动的安全性进行评估，提供真正的安全风险情报。这些功能包括智能开发，代码审计，Web应用程序扫描，社会工程。团队合作，在Metasploit和综合报告提出了他们的发现。
操作实例：
    http://www.hetianlab.com/expc.do?ec=ECID172.19.104.182014122211281900001
## 密码学基础知识
   https://zhuanlan.zhihu.com/cryptography
## Owasp Top10漏洞原理和修补方法
  http://www.owasp.org.cn/owasp-project/download/2010_OWASP_Top_10
  http://www.owasp.org.cn/owasp-project/download/mobile-top-10-2013-2
  http://www.owasp.org.cn/owasp-project/OWASPTop102017v1.1.pdf
## burpsuit的使用
  https://legacy.gitbook.com/book/t0data/burpsuite/details
