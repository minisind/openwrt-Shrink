# openwrt-缩身大法
首先感谢网络，感谢自由的网络！
在使用留学软件学习之后，对openwrt在硬路由器中的使用，个人遇到了存储空间不足，无法安装插件的问题，通过提问，搜索，测试等行动，找到了给路由器存储空间缩身的一点方法，集中贴在此处，以防将来万一不小心老年痴呆了找不到人问。
1. 第一的缩身大法是重复文件的删除。
使用留学技术的家人们，很多都希望路由器实现分流管理。也基本上采取了相关插件分流的功能。 具体方案如 ： mosdns+ adguard home+openclash(或 nikki ，或hometproxy等等)
不同的插件采用相似的方法做数据分流，底层都需要一个GEOIP的基础数据库，这个文件很大，相对于路由器来说，20M的数据已经超过老旧路由器的8M，16M FLASH空间了。 重复利用这些数据，删除路由器中的重复项非常有效，还只需要维护一个版本的升级即可以保证插件对流量的分流保持同步，防止出现不同插件因采用不同数据把网络数据分流到不同通道的不和谐问题。

https://github.com/nikkinikki-org/OpenWrt-nikki/discussions/197


https://github.com/vernesong/OpenClash/discussions/2995



2.第二位的缩身大法是执行文件的压缩。 




https://zh.wikipedia.org/wiki/%E6%97%B6%E7%A9%BA%E6%9D%83%E8%A1%A1
