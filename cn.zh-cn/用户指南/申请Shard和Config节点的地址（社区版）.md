# 申请Shard和Config节点的地址（社区版）<a name="dds_02_0100"></a>

社区版集群实例由Mongos、Shard和Config节点共同组成，普通业务在读写数据时只需要连接至Mongos节点即可。在某些特定的场景（例如：集群间的数据迁移和同步）下，需要读取Shard节点或者Config节点的数据信息，为了满足业务的正常运行，您可以申请相应节点的地址。

本章节将分别介绍获取shard和config节点地址的方法。

## 使用须知<a name="section12401231171410"></a>

-   支持版本为3.4和4.0的社区版集群实例。
-   申请连接地址后，系统将为每个GROUP组创建两个连接地址，分别对应该GROUP组中的Primary节点和Secondary节点。

    申请的连接地址的网络类型将与当前Mongos节点的网络类型保持一致。

-   申请Shard节点或Config节点的连接地址后，暂不支持修改和删除。
-   申请的连接地址仅支持通过内网访问。

## 申请Shard节点的地址<a name="section1748562461319"></a>

1.  [登录文档数据库服务](zh-cn_topic_0160390880.md)。
2.  单击左侧导航栏的“实例管理“，从实例列表中选择指定实例，单击实例名称，进入基本信息页面。
3.  在基本信息页面，单击右侧“节点信息“模块下的“shard“页签。

    **图 1**  shard节点<a name="fig9475722155618"></a>  
    ![](figures/shard节点.png "shard节点")

4.  单击“shard IP显示“，填写并确认帐户密码。

    **图 2**  申请Shard节点地址<a name="fig65514200020"></a>  
    ![](figures/申请Shard节点地址.png "申请Shard节点地址")

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   shard IP显示开启后，需要重启对应shard节点才能生效。  
    >-   shard IP显示按钮仅支持开启，暂不支持关闭和修改，并且帐户密码也不支持修改。  
    >-   shard节点IP开启后，对于新增的shard节点不会默认申请连接地址，需要在节点“更多”操作中开启shard IP显示。  
    >-   shard IP显示按钮开启后，当前所有shard类型节点都会申请连接地址。  

5.  <a name="li79582518253"></a>获取shard节点的内网IP。

    Shard节点连接地址申请成功后，您可以在当前页面或者单击左侧导航栏中的“连接管理“，展开对应节点的下拉列表，获取对应的内网IP。

    **图 3**  查看shard节点内网IP<a name="fig32731653164613"></a>  
    ![](figures/查看shard节点内网IP.png "查看shard节点内网IP")

6.  获取shard节点的连接地址。

    示例：

    根据[5](#li79582518253)中获取到的内网IP地址，当前shard节点连接地址为：

    mongodb://_**sharduser:\*\*\*\*@192.168.237.15:8637,192.168.255.217:8637**_/test?authSource=admin&replicaSet=shard\_?

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   “sharduser“为当前shard节点的用户名。  
    >-   “\*\*\*\*“为当前节点的密码。  
    >-   “192.168.237.15“和“192.168.255.217“为当前节点的内网IP。  
    >-   “8637“为当前节点的实际端口。  
    >-   “shard\_? “为指定连接的shard节点名称， 比如 shard\_1。  


## 申请config节点的地址<a name="section88951332134016"></a>

1.  登录文档数据库服务。
2.  单击左侧导航栏的“实例管理“，从实例列表中选择指定实例，单击实例名称，进入基本信息页面。
3.  在基本信息页面，单击右侧“节点信息“模块下的“config“页签。

    **图 4**  config节点<a name="fig824358134214"></a>  
    ![](figures/config节点.png "config节点")

4.  单击“config IP显示“，填写并确认帐户密码。

    **图 5**  申请Config节点地址<a name="fig424155820427"></a>  
    ![](figures/申请Config节点地址.png "申请Config节点地址")

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   config IP显示开启后，需要重启对应config节点才能生效。  
    >-   config IP显示按钮仅支持开启，暂不支持关闭和修改，并且帐户密码也不支持修改。  
    >-   config IP显示按钮开启后，当前所有config类型节点都会申请连接地址。  

5.  <a name="li1225175894219"></a>获取config节点的内网IP。

    config节点连接地址申请成功后，您可以在当前页面或者单击左侧导航栏中的“连接管理“，展开指定节点的下拉列表，获取对应的内网IP。

    **图 6**  查看config节点内网IP<a name="fig0894103163316"></a>  
    ![](figures/查看config节点内网IP.png "查看config节点内网IP")

6.  获取config节点的连接地址。

    示例：

    根据[5](#li1225175894219)中获取到的内网IP地址，当前config节点连接地址为：

    mongodb://_**csuser:\*\*\*\*@192.168.154.71:8636,192.168.143.227:8636**_/test?authSource=admin&replicaSet=config

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   “csuser“为当前config节点的用户名。  
    >-   “\*\*\*\*“为当前config节点的密码。  
    >-   “192.168.154.71“和“192.168.143.227“为当前节点的内网IP。  
    >-   “8636“为当前节点的实际端口。  


