# Computer_Network
2018年秋季哈工大计算机网络实验

## 课程总结
关于计算机网络课程，总的来说难度不大，主要是内容细碎，不易完整记忆。课程的讲授方式也比较奇怪，传统课堂中所强调的面对面授课，改为MOOC形式；课堂时间主要用于解决在MOOC上的一些问题，(即所谓翻转课堂模式)，这种模式在平时需要极大的时间来看MOOC和做相应的PPT(而且在于每次每个人都需要做)，这种方式个人觉得可能作用不大。

另外说一些关于复习的事情，这个课程在2018年秋季的工大开设，在考试之前有2周的时间充分复习，所以将所有的内容复习一遍之后，还做完了全部的王道考研对应的部分。私以为，这种复习方式需要大量的时间，但最终效果还可以，可以参考。

关于实验部分，希望能够改进实验3的设置，主要在于实验平台过于老旧以及实验内容过于单调。

于2018年秋季期末后
## Lab1 HTTP代理服务器的设计与实现
### 实验目的
熟悉并掌握Socket网络变成的过程与技术；深入理解HTTP协议，掌握HTTP代理服务器的基本工作原理；掌握HTTP代理服务器设计用于变成实现的基本技能。
### 实验内容
- [x] 设计并实验一个基本HTTP代理服务器。要求在制定端口(例如8080)接收来自客户的HTTP请求并且根据其中的URL地址访问该地址所指向的HTTP服务器(原服务器)，接收HTTP服务器的相应报文，并将相应报文转发给对应的客户进行浏览。
- [x] 设计并实现一个支持Cache功能的HTTP代理服务器。要求能缓存原服务器相应的对象，并能够通过修改请求报文(添加`if-modified-since`头部行)，向原服务器确认缓存对象是否是最新版本。
- [x] 扩展HTTP代理服务器，支持网站过滤，允许/不允许访问某些网站。
- [x] 扩展HTTP代理服务器，支持用户过滤，支持/不支持某些用户访问外部网站。
- [x] 扩展HTTP代理服务器，支持网站引导，将用户对某个网站的访问引导至一个模拟网站(钓鱼)。
### 写在实验之后
对于HTTP代理服务器的设计与实现，使用`Python`相较其他同学使用`Java/C/C++`，可能代码长度比较少，封装程度偏高。另外，只实现了对于HTTP协议的代理，对于HTTPS的相关代理问题可能需要在之后，利用`requests`包实现相应的功能。

## Lab2 可靠数据传输协议-GBN协议的设计与实现
### 实验目的
理解滑动窗口协议的基本原理；掌握GBN的工作原理；掌握基于UDP设计并实现一个GBN协议的过程与技术。
### 实验内容
- [x] 基于UDP设计一个简单的GBN协议，实现单项可靠数据传输(服务器到客户的数据传输)
- [x] 模拟引入数据包的丢失，验证所设计协议的有效性
- [x] 改进所设计的GBN协议，支持双向数据传输
- [x] 将所设计的GBN协议改进为SR协议

### 写在实验后
- 对于这次实验，代码实现的有些问题，冗余代码太多，本质上在sr.py和gbn.py中，无需区分Server和CLient，只需有个可以初始化IP和端口号的对象即可；但由于时间问题，不再进行优化。
- 此外，在模拟丢包的时候，有两种方式，一是在实验指导书上提示的是模拟ACK丢失，这种方式不够明显，本次实验使用这种方式进行模拟；二是模拟发送端数据包的丢失，这种方式更加直观，做法与模拟ACK丢失很像，可以参考模拟ACK丢失实现，同样由于时间问题不再进行优化。
**此次实验报告见doc文件**

## Lab3 IPV4分组收发实验与IPV4分组转发实验

### 实验目的与实验内容
**见**[实验指导书](https://github.com/1160300314/Computer_Network/blob/master/lab/%E3%80%8A%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C%E3%80%8B%E5%AE%9E%E9%AA%8C%E6%8C%87%E5%AF%BC%E4%B9%A6(2018).pdf)，此处不再赘述。

### 写在实验之前(有关环境配置)
~~致敬在8102年，仍然需要在Win7 32位机上才能运行的实验环境。~~

在实验指导书中提到的Netriver环境，实际中被以压缩包的形式给出。在压缩包中可能有
- SimplePAD客户端v3.1
- 安装工具
- readme.txt
- SimplePAD客户端安装手册.pdf
- 安装工具.zip

其中，SimplePAD客户端v3.1中为客户端主体，如果电脑是Windows10系统，可以先尝试直接从`SimplePAD客户端v3.1/expsys/bin/INEP.exe`中打开程序，应该可以打开(注意保存路径里不要包含空格)。

但是，打开了之后，配置好实验服务器的ip地址，新建看见模板之后，进行编译，会有400多个errors，这一点在Win 7电脑上是没有的(对，模板直接编译就有400多个errors)。所以，**此时最好不要犹豫，直接去下载VMware，安装win7 32位虚拟机，免得浪费时间。**

在安装Win7 虚拟机时，**不要尝试使用各种奇怪的Ghost，一定要使用官方ISO**。主要是有保证，下载的时候最后可以使用本校的镜像站，如[哈工大正版软件管理平台](http://ms.hit.edu.cn/)等，这样可以保证下载速度。

### IPV4分组收发实验
- [x] 实现`stud_ip_recv()`函数，实现IPV4分组接收处理功能
- [x] 实现`stud_ip_Upsend()`函数，实现IPV4分组封装发送功能

### IPV4分组转发实验
- [x] 实现`stud_fwd_deal()`函数，系统处理收到的IP分组的函数
- [x] 实现`stud_Route_Init()`函数，路由表初始化函数
- [x] 实现`stud_route_add()`函数，向路由表添加路由的函数

### 写在实验之后
~~这次实验难度在于环境配置~~，总的来说实验难度不大，但是思路比较固定，实验指导书写的比较详细，仔细看就可以写，网上代码的思路和自己写的思路十分相似。实验环境中，在运行时不能修改文件，断点不能一起删除，希望改进吧。

## Lab4 利用Wireshark进行协议分析
### 实验目的
熟悉并掌握Wireshark的基本操作，了解网络协议实体间进行交互以及报文交换的情况。

### 实验内容

- [x] 学习Wireshark的使用
- [x] 利用Wireshark分析HTTP协议
- [x] 利用Wireshark分析TCP协议
- [x] 利用Wireshark分析IP协议
- [x] 利用Wireshark分析Ethernet数据帧

**选做内容**

- [x] 利用Wireshark分析DNS协议
- [x] 利用Wireshark分析UDP协议
- [x] 利用Wireshark分析ARP协议

### 写在实验后
Wireshark是个相当强大的工具，学会使用不仅仅在本次实验中有用，在以后的学习工作生活中，同样有很大的帮助。~~(但是本次实验还是相当繁琐的)~~