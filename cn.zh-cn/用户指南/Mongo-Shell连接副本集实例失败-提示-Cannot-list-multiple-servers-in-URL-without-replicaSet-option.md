# Mongo Shell连接副本集实例失败，提示：Cannot list multiple servers in URL without 'replicaSet' option<a name="dds_03_troubleshoot_0006"></a>

## 问题描述<a name="section10861151113245"></a>

使用如下命令连接DDS副本集实例时报错。

**mongo mongodb://rwuser:**_xxxxxxxxxxx_**@192.168.168.116:8635,192.168.200.147:8635/test?authSource=admin&replicaSet=replica**

报错信息如下：

```
[1] 8302
[root@serverceddea23-0d5f-49e6-8a8c-94259dcf09cb ycsb]# FailedToParse: Cannot list multiple servers in URL without 'replicaSet' option
try 'mongo --help' for more information
```

## 可能原因<a name="section1118811822513"></a>

使用Connection String URI连接副本集实例时，URI命令行没有加双引号。

## 处理方法<a name="section19511332122519"></a>

将命令行添加双引号，再连接副本集实例。

**mongo "mongodb://rwuser:**_xxxxxxxxx_**@192.168.168.116:8635,192.168.200.147:8635/test?authSource=admin&replicaSet=replica"**

