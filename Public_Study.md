# 公共技能
  说明：这是一个大家都需要共同学习和掌握的基本技能，首先，我们应该熟悉一下中国在法律层面对网络安全领域的一些规定
  http://www.npc.gov.cn/npc/xinwen/2016-11/07/content_2001605.htm
  
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
    
        https://pan.baidu.com/s/1Lnu5n445_LQ_qm3Zy_L77g
       
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
### 使用
  http://www.nmap.com.cn/doc/manual.shtm
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
  
## CTF相关
### 入门（推荐资源）：
  www.ichunqiu.com 有线下决赛题目复现
  
  http://oj.xctf.org.cn/xctf 题库网站
  
  www.wechall.net/challs 入门ctf题库
  
  http://prompt.ml/0 国外的xss测试
  
  http://redtiger.labs.overthewire.org/ sql注入挑战网站
