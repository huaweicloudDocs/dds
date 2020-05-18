# Java驱动连接实例失败，提示：Timeout while receiving message<a name="dds_03_troubleshoot_0007"></a>

## 问题描述<a name="section10861151113245"></a>

使用Java驱动连接DDS实例时报错。

报错信息如下：

```
org.springframework.data.mongodb.UncategorizedMongoDbException: Timeout while receiving message; nested exception is com.mongodb.MongoSocketReadTimeoutException: Timeout while receiving message
```

## 可能原因<a name="section1118811822513"></a>

-   异常的慢查询占用实例资源，导致CPU使用率激增甚至到达峰值。
-   应用端连接池的配置错误导致，如超时时间的设置等。

## 处理方法<a name="section19511332122519"></a>

-   检查是否有[慢查询](慢日志.md)，建议添加索引进行优化。
-   检查应用端连接池的配置是否正确，具体请参见[如何查询及限制连接数](https://support.huaweicloud.com/dds_faq/dds_faq_0040.html)。

