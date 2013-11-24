start
=====

开始写点东西

twinkle twinkle little star, how i wander what you are

13.11.16

软件版本和网速的原因，今天没有啥实质的收获可以写的，就写个计划吧。

1.每天都写点东西，无论多少

2.尽可能的写，可以与工作有关，也可以无关。

暂时先这样吧

13.11.17


竟然就这么睡过去了，万万不应该啊，还有好多事情没有做，R的东西没有看，avayaVPN的问题还没处理，该聊的东西也完全错过去了，哎，怎么会这样子。
13.11.19 02：02

又是崩溃的一天，肿么办，想报个课来着，咨询群都加满了，崩溃啊。
13.11.20 0：23

今天搞tcpdump，好麻烦啊
13.11.21

还是弄tcpdump，终于搞清楚抓包分析是个啥东西。
抓包，只能抓通过当前设备的网卡的数据包，所以，是没法直接抓通过别的网卡信息的包的，要是可以安全性就太低了。
所以，抓包分析需要在交换机上座流量镜像，然后抓镜像流量做分析。

另外，voip是走rtp协议，rtp会封装到udp协议里传输，并且不会重传，所以一旦丢包就完全没法用了

最近比特币很火，或者是不是都火过了，要不要挖个矿试试啊。
13.11.22

centos的桥接，网上的教程各种坑爹，一重启网卡起不来了，悲催啊
网卡设置，直接发结果吧

[root@localhost network-scripts]# cat ifcfg-eth0
# Intel Corporation 82545EM Gigabit Ethernet Controller (Copper)
DEVICE=eth0
#BOOTPROTO=status
ONBOOT=yes
HWADDR=00:0c:29:6a:27:2e
#TYPE=Ethernet
#IPADDR=192.168.50.181
#NETMASK=255.255.255.0
#GATEWAY=192.168.50.1
BRIDGE=br0
[root@localhost network-scripts]# cat ifcfg-br0
# Intel Corporation 82545EM Gigabit Ethernet Controller (Copper)
DEVICE=br0
BOOTPROTO=static
ONBOOT=yes
TYPE=Bridge
IPADDR=192.168.50.181
NETMASK=255.255.255.0
GATEWAY=192.168.50.1

再补充下KVM安装的几个出错点
安装 xorg-x11-xauth
这两项改成yes
vim /etc/ssh/sshd_config
AllowTcpForwarding yes
X11Forwarding yes

Xming启动被拒绝时 快捷方式后面加一个 -ac

virt-install --name coffee --ram=2048 --vcpus=2 --os-type=linux--accelerate \
--hvm --disk path=/home/tangchengji/coffee.img,size=6,bus=virtio \
--cdrom=/root/ubuntu-12.04.2-desktop-amd64.iso --network bridge=br0,model=virtio

另外，服务器bios要开启虚拟化支持，要不没法创建全虚拟化的虚拟机
