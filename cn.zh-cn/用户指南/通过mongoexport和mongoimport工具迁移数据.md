# 通过mongoexport和mongoimport工具迁移数据<a name="dds_03_0054"></a>

## 操作场景<a name="zh-cn_topic_0085335428_section25341248175518"></a>

要将已有的MongoDB数据库迁移到文档数据库，需要先使用mongoexport工具对它做转储。再通过弹性云服务器或可访问文档数据库的设备，使用mongoimport工具将转储文件导入到文档数据库服务。

## 注意事项<a name="zh-cn_topic_0085335428_section16837122418917"></a>

-   建议您尽量选择在业务低峰期迁移数据，避免在迁移过程中对业务造成影响。
-   不支持迁移系统库admin和local。
-   确保源库中系统库admin和local没有创建业务集合，如果已经有业务集合，必须在迁移前将这些业务集合从admin和local库中迁移出来。
-   导入数据之前，确保源端有必要的索引，即在迁移前删除不需要的索引，创建好必要的索引。
-   如果选择迁移分片集群，必须在目标库创建好要分片的集合，并配置数据分片。同时，迁移前必须要创建好索引。

## 前提条件<a name="zh-cn_topic_0085335428_section8361919133059"></a>

1.  准备弹性云服务器或可访问文档数据库的设备。
    -   通过内网连接文档数据库实例，需要创建并登录弹性云服务器，请参见[购买弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0021831611.html)和[登录弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0092494193.html)。
    -   通过公网地址连接文档数据库实例，需具备以下条件。
        1.  为实例中的节点绑定公网地址，如何绑定公网地址，请参见《文档数据库服务快速入门》各实例类型下“绑定和解绑弹性IP”的内容。
        2.  保证本地设备可以访问文档数据库绑定的公网地址。

2.  在已准备的弹性云服务器或可访问文档数据库的设备上，安装数据迁移工具。

    安装数据迁移工具，请参见[如何安装MongoDB客户端](http://support.huaweicloud.com/dds_faq/dds_faq_0018.html)。

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >MongoDB客户端会自带mongoexport和mongoimport工具。  


## 导出数据<a name="zh-cn_topic_0085335428_section990018367329"></a>

1.  登录到已准备的弹性云服务器或可访问文档数据库的设备。
2.  使用mongoexport，将源数据库转储至JSON文件。

    此处以SSL连接方式为例进行说明，如果选择普通连接方式，去掉命令中对应的“--ssl --sslAllowInvalidCertificates“即可。

    ./**mongoexport** **--host** _<__DB\_ADDRESS\>_ **_--_port** _<DB\_PORT\>_ **_--_ssl** **--sslAllowInvalidCertificates** **--type json** **--authenticationDatabase** _<AUTH\_DB_\> **-u** _<DB\_USER\>_ **--db** <_DB\_NAME_\> **--collection** <_DB\_COLLECTION_\> **--out** <_DB\_PATH_\>

    -   DB\_ADDRESS为数据库地址。
    -   DB\_PORT为数据库端口。
    -   AUTH\_DB为存储DB\_USER信息的数据库，一般为admin。
    -   DB\_USER为数据库用户。
    -   DB\_NAME为要迁移的数据库名称。
    -   DB\_COLLECTION为要迁移的数据库集合。
    -   DB\_PATH为存储数据JSON文件所在的路径。

    出现如下提示时，输入数据库管理员对应的密码：

    ```
    Enter password:
    ```

    示例如下，命令执行完会生成“exportfile.json“文件：

    **./mongoexport --host 192.168.1.21 --port 8635 --ssl --sslAllowInvalidCertificates  --type json  --authenticationDatabase admin -u rwuser --db test02 --collection Test --out /tmp/mongodb/export/exportfile.json**

3.  查看迁移结果。

    输出内容显示如下，说明迁移成功。其中，“x”表示转储数据的记录条数。

    ```
    exported x records
    ```

4.  压缩导出的JSON文件。

    **gzip exportfile.json**

    压缩是为了方便网络传输，压缩后生成“exportfile.json.gz“文件。


## 导入数据<a name="zh-cn_topic_0085335428_section5895195683218"></a>

1.  登录到已准备的弹性云服务器或可访问文档数据库的设备。
2.  将要导入的数据上传到弹性云服务器或可访问文档数据库的设备。

    根据不同的平台选择相应的上传方法。Linux下可参考命令：

    scp  _<__IDENTITY\_FILE\>_ _<REMOTE\_USER\>_@_<REMOTE\_ADDRESS\>_:_<REMOTE\_DIR\>_

    -   IDENTITY\_FILE为存储“exportfile.json.gz”的文件目录，该文件目录权限为600。
    -   REMOTE\_USER为弹性云服务器的操作系统用户。
    -   REMOTE\_ADDRESS为弹性云服务器的主机地址。
    -   REMOTE\_DIR为将“exportfile.json.gz”上传到弹性云服务器的文件目录。

    Windows平台下，请使用传输工具上传“exportfile.json.gz”至弹性云服务器。

3.  解压数据包。

    **gzip** **-d** _exportfile.json.gz_

4.  将转储文件导入到文档数据库。

    此处以SSL连接方式为例进行说明，如果选择普通连接方式，去掉命令中对应的“--ssl --sslAllowInvalidCertificates“即可。

    ./**mongoimport --host** <_DB\_ADDRESS_\> **--port** <_DB\_PORT_\> **--ssl --sslAllowInvalidCertificates --type json --authenticationDatabase** <_AUTH\_DB_\> **-u** <_DB\_USER_\> **--db** <_DB\_NAME_\> **--collection**  <_DB\_COLLECTION_\> **--file** <_DB\_PATH_\>

    -   DB\_ADDRESS为数据库实例的IP地址。
    -   DB\_PORT为数据库端口。
    -   AUTH\_DB为DB\_USER进行权限验证的数据库，一般为admin。
    -   DB\_USER为数据库管理员帐号名。
    -   DB\_NAME为要导入的数据库。
    -   DB\_COLLECTION为要导入的数据库中的集合。
    -   DB\_PATH为转储数据JSON文件所在的路径。

    出现如下提示时，输入数据库管理员对应的密码：

    ```
    Enter password:
    ```

    示例如下：

    **./mongoimport --host 192.168.1.21 --port 8635 --ssl --sslAllowInvalidCertificates   --type json  --authenticationDatabase admin -u rwuser --db test02 --collection Test --file /tmp/mongodb/export/exportfile.json**

5.  查看迁移结果。

    输出内容显示如下，说明迁移成功。其中，“x“表示转储数据的记录条数。

    ```
    imported x records
    ```


