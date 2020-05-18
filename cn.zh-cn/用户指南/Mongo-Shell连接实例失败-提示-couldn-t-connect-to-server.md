# Mongo Shell连接实例失败，提示：couldn't connect to server<a name="dds_03_troubleshoot_0004"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接DDS实例时报错。

**mongo --host 192.168.64.201 --port 8635 -u rwuser -p **_xxxxxxxxx_ ** --authenticationDatabase admin --ssl --sslCAFile /root/ca.crt --sslAllowInvalidHostnames**

报错信息如下：

```
MongoDB shell version v3.4.17
connecting to: mongodb://192.168.64.201:8635/
2019-09-19T09:45:48.168+0800 W NETWORK  [thread1] Failed to connect to 192.168.64.201:8635 after 5000ms milliseconds, giving up.
2019-09-19T09:45:48.168+0800 E QUERY    [thread1] Error: couldn't connect to server 192.168.64.201:8635, connection attempt failed :
connect@src/mongo/shell/mongo.js:240:13
@(connect):1:6
exception: connect failed
```

## 可能原因<a name="section1118811822513"></a>

未设置正确的安全组策略，导致从安全组外访问安全组内的DDS实例失败。

## 处理方法<a name="section19511332122519"></a>

请设置正确的安全组策略，请参见[设置安全组](https://support.huaweicloud.com/qs-dds/dds_02_0022.html)。

