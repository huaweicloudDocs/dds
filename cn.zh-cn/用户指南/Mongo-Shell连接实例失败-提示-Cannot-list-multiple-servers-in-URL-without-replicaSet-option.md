# Mongo Shell连接实例失败，提示：Cannot list multiple servers in URL without 'replicaSet' option<a name="dds_03_troubleshoot_0005"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接兼容MongoDB 3.4版本的DDS实例时报错。

**mongo "mongodb://rwuser:**_xxxxxxxxx_**@192.168.95.167:8635,192.168.92.43:8635/test?authSource=admin"**

报错信息如下：

```
FailedToParse: Cannot list multiple servers in URL without 'replicaSet' option
try 'mongo --help' for more information.
```

## 可能原因<a name="section1118811822513"></a>

MongoDB客户端版本太低。

## 处理方法<a name="section19511332122519"></a>

使用4.0版本以上的MongoDB客户端连接实例。

**图 1**  连接成功<a name="fig33714114459"></a>  
![](figures/连接成功-25.png "连接成功-25")

