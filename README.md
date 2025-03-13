# openwrt-缩身大法
首先感谢网络，感谢自由的网络！
在使用留学软件学习之后，对openwrt在硬路由器中的使用，个人遇到了存储空间不足，无法安装插件的问题，通过提问，搜索，测试等行动，找到了给路由器存储空间缩身的一点方法，集中贴在此处，以防将来万一不小心老年痴呆了找不到人问。
1. 第一的缩身大法是重复文件的删除。
使用留学技术的家人们，很多都希望路由器实现分流管理。也基本上采取了相关插件分流的功能。 具体方案如 ： mosdns+ adguard home+openclash(或 nikki ，或hometproxy等等)
不同的插件采用相似的方法做数据分流，底层都需要一个GEOIP的基础数据库，这个文件很大，相对于路由器来说，20M的数据已经超过老旧路由器的8M，16M FLASH空间了。 重复利用这些空间，删除路由器中的重复项非常有效，还只需要维护一个版本的升级即可以保证插件对流量的分流保持同步，防止出现不同插件因采用不同数据把网络数据分流到不同通道的不和谐问题。
为了实现流量分流，保证GFW内的网络速度，也节省出口流量，很多采用MOSDNS + ADGUARD HOME + 留学 三剑客的类似方案。如：
 a) https://github.com/nikkinikki-org/OpenWrt-nikki/discussions/197
 b) https://github.com/vernesong/OpenClash/discussions/2995
在这类方案中，MOSDNS依赖GEOIP数据库对IP分流，留学软件也同样依赖此数据库。 在安装好路由器，各插件正常工作之后，采用 WINSCP工具软件连接到路由器，在插件的安装目录中搜索GEOIP数据库文件。MOSDNS依赖的GEOIP安装在：  /usr/share/v2ray/目录下，  openclash 依赖的GEOIP库安装在：/etc/openclash/下。 
 首先，在系统启动项中停止openclash，
![image](https://github.com/user-attachments/assets/16cc878c-627c-4c2b-a5c6-cd1381610a85)

删除openclash中的IP库， 再用如下两个命令创建一个软连接：

ln -s /usr/share/v2ray/geosite.dat   /etc/openclash/GeoSite.dat

ln -s /usr/share/v2ray/geoip.dat     /etc/openclash/GeoIP.dat

这样即可以实现GEOIP数据库的共享，保证两个插件采用相同的数据源分流。 若openclash中设置的是采用小IP库模式，需要修改设置项。
openclash中的输出面板非常漂亮，也很方便使用，但是几种面板采用了相同的字库文件，每个文件占用有1.5M左右。  WINSCP 找到这些字库文件后，同样方式创建软连接，同样可节省出空间。

2.第二位的缩身大法是执行文件的压缩。 




https://zh.wikipedia.org/wiki/%E6%97%B6%E7%A9%BA%E6%9D%83%E8%A1%A1
