# Mongo Shell连接实例失败，提示：isMaster<a name="dds_03_troubleshoot_0001"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接DDS实例时报错。

**./mongo --host 192.168.168.182 --port 8635 -u rwuser -p **_xxxxxxxxxx_** --authenticationDatabase admin**

**图 1**  连接失败<a name="fig13321428351"></a>  
![](figures/连接失败.png "连接失败")

## 可能原因<a name="section1118811822513"></a>

该命令为非SSL方式下连接实例的命令，若实例已开通SSL连接，执行此命令会报错。

## 处理方法<a name="section19511332122519"></a>

-   关闭SSL连接，使用非SSL方式下的命令连接实例。
-   下载SSL证书，将证书上传到ECS目录下（示例：/root/ca.crt），使用SSL方式下的命令连接实例。

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >您可以在DDS控制台界面，单击实例名称，在“连接管理“页签的“SSL“处，单击![](figures/download.png)，下载SSL证书。  

    **./mongo --host 192.168.168.182 --port 8635 -u rwuser -p **_xxxxxxxxxx_** --authenticationDatabase admin --ssl --sslCAFile /root/ca.crt --sslAllowInvalidHostnames**

    **图 2**  连接成功<a name="fig8396185415373"></a>  
    ![](figures/连接成功.png "连接成功")


