# DDS实例节点故障处理机制<a name="dds_03_troubleshoot_node"></a>

## 集群实例<a name="section1839410613140"></a>

集群实例的shard节点和config节点均采用三节点副本集架构。当其中的某个节点发生故障后，系统会使用另一个正常节点替换故障节点继续提供服务，并对故障节点进行检查与修复。该过程对用户完全透明，可能会产生1次30秒内的连接闪断，建议您的应用程序添加自动重连机制。

**图 1**  集群实例拓扑图<a name="fig121519272438"></a>  
![](figures/集群实例拓扑图.png "集群实例拓扑图")

集群实例的mongos节点采用单节点架构，当某个mongos节点发生故障，该节点相关服务将不可用。推荐您使用Connection String URI连接所有mongos节点，请勿连接单个mongos节点。当使用Connection String URI连接所有mongos节点时，如果某个mongos节点发生故障，客户端能自动进行故障切换，将请求分散到状态正常的mongos节点上。连接命令示例：

**mongo "mongodb://rwuser:xxxxxxxx@192.168.95.167:8635,192.168.92.43:8635/test?authSource=admin"**

>![](public_sys-resources/icon-notice.gif) **须知：**   
>使用Connection String URI连接兼容MongoDB 3.4版本的集群实例时，建议使用4.0以上的MongoDB客户端，否则会出现报错。  

**图 2**  报错信息<a name="fig2165053610"></a>  
![](figures/报错信息.png "报错信息")

## 副本集实例<a name="section162168712214"></a>

**图 3**  副本集实例拓扑图<a name="fig13864133115216"></a>  
![](figures/副本集实例拓扑图.png "副本集实例拓扑图")

副本集实例提供两个节点供用户访问，当其中的某个节点发生故障后，系统会使用另一个正常节点替换故障节点继续提供服务，并对故障节点进行检查与修复。该过程对用户完全透明，可能会产生1次30秒内的连接闪断，建议您的应用程序添加自动重连机制。

推荐您使用Connection String URI进行连接，请勿直接连接副本集的Primary节点。当使用Connection String URI进行连接时，如果某个节点出现故障，不会因为节点的切换而影响应用的读写操作。连接命令示例：

**mongo "mongodb://rwuser:xxxxxxxx@192.168.168.116:8635,192.168.200.147:8635/test?authSource=admin&replicaSet=replica"**

连接副本集实例的最佳实践，请参见[如何连接副本集实例以实现读写分离和高可用](https://support.huaweicloud.com/bestpractice-dds/dds_0003.html)。

## 单节点实例<a name="section295116121313"></a>

**图 4**  单节点实例拓扑图<a name="fig146721637111320"></a>  
![](figures/单节点实例拓扑图.png "单节点实例拓扑图")

由于单节点实例架构的特殊性，仅提供一个节点供用户访问。当节点发生故障后，系统会对故障节点进行检查与重建。节点故障期间，该节点相关服务将不可用。

单节点实例适用于测试、培训、非核心业务等场景，生产环境建议您使用集群实例或副本集实例，以保障服务的高可用性。

