# Mongo Shell连接实例失败，提示No route to host以及connection attempt failed<a name="dds_03_troubleshoot_0002"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接DDS实例时报错。

**mongo --host 192.168.1.6 --port 8635 -u rwuser -p **_xxxxxxxxx_** --authenticationDatabase admin --ssl --sslCAFile /root/ca.crt --sslAllowInvalidHostnames**

报错信息如下：

```
MongoDB shell version v3.4.17
connecting to: mongodb://192.168.1.6:8635/
2019-09-19T09:38:36.954+0800 W NETWORK  [thread1] Failed to connect to 192.168.1.6:8635, in(checking socket for error after poll), reason: No route to host
2019-09-19T09:38:36.954+0800 E QUERY    [thread1] Error: couldn't connect to server 192.168.1.6:8635, connection attempt failed :
connect@src/mongo/shell/mongo.js:240:13
@(connect):1:6
exception: connect failed
```

## 可能原因<a name="section1118811822513"></a>

-   DDS实例的端口错误。
-   DDS实例与ECS不在同一个区域。
-   DDS实例与ECS不在同一个子网。

通过内网连接DDS实例的最佳实践，请参见[通过ECS内网连接DDS实例](https://support.huaweicloud.com/bestpractice-dds/dds_0009.html)。

## 处理方法<a name="section19511332122519"></a>

可以通过**curl**命令确认到达DDS实例的网络是否畅通，示例：

**curl 192.168.1.6:8635**

提示“It looks like you are trying to access MongoDB over HTTP on the native driver port.”表示可以正常连接该IP地址，且8635端口可以正常通信。

**图 1**  回显信息<a name="fig3180101818525"></a>  
![](figures/回显信息.png "回显信息")

