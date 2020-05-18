# Mongo Shell连接实例失败，提示：Authentication failed<a name="dds_03_troubleshoot_0003"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接DDS实例时报错。

**mongo --host 192.168.168.116 --port 8635 -u rwuser -p **_xxxxxxxxx_** --authenticationDatabase admin --ssl --sslCAFile /root/ca.crt --sslAllowInvalidHostnames**

报错信息如下：

```
MongoDB shell version v3.4.17
connecting to: mongodb://192.168.168.116:8635/
2019-09-19T09:39:24.306+0800 W NETWORK  [thread1] The server certificate does not match the host name. Hostname: 192.168.168.116 does not match CN: 172.16.2.65
MongoDB server version: 4.0.3
WARNING: shell and server versions do not match
2019-09-19T09:39:24.329+0800 E QUERY    [thread1] Error: Authentication failed. :
DB.prototype._authOrThrow@src/mongo/shell/db.js:1461:20
@(auth):6:1
@(auth):1:2
exception: login failed
```

## 可能原因<a name="section1118811822513"></a>

连接DDS实例命令中管理员密码错误。

## 处理方法<a name="section19511332122519"></a>

-   请重新输入正确的管理员密码。
-   如果您忘记密码，请参见[重置管理员密码](重置管理员密码.md)重置密码。

