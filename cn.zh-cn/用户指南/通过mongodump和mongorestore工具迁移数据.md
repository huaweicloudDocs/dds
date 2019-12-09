# 通过mongodump和mongorestore工具迁移数据<a name="dds_03_0055"></a>

## 操作场景<a name="section25341248175518"></a>

文档数据库服务支持开启公网访问功能，通过EIP进行访问。通过弹性云服务器访问，迁移前需要创建一台弹性云服务器，并安装mongodump和mongorestore工具。

关于迁移增强版实例数据的注意事项，请参见《文档数据库服务最佳实践》中“[DDS增强版使用须知](https://support.huaweicloud.com/bestpractice-dds/dds_0001.html)”的内容。

## 注意事项<a name="section16837122418917"></a>

-   建议您尽量选择在业务低峰期迁移数据，避免在迁移过程中对业务造成影响。
-   不支持迁移系统库admin和local。
-   确保源库中系统库admin和local没有创建业务集合，如果已经有业务集合，必须在迁移前将这些业务集合从admin和local库中迁移出来。
-   导入数据之前，确保源端有必要的索引，即在迁移前删除不需要的索引，创建好必要的索引。
-   如果选择迁移分片集群，必须在目标库创建好要分片的集合，并配置数据分片。同时，迁移前必须要创建好索引。
-   如果使用mongodump工具备份失败（示例：备份进度至97%时报错），建议您尝试增大虚拟机磁盘空间，预留部分冗余空间，再重新执行备份。

## 前提条件<a name="section690371271217"></a>

1.  准备弹性云服务器或可访问文档数据库的设备。
    -   通过内网连接文档数据库实例，需要创建并登录弹性云服务器，请参见[购买弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0021831611.html)和[登录弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0092494193.html)。
    -   通过公网地址连接文档数据库实例，需具备以下条件。
        1.  为实例中的节点绑定公网地址，如何绑定公网地址，请参见《文档数据库服务快速入门》各实例类型下“绑定和解绑弹性IP”的内容。
        2.  保证本地设备可以访问文档数据库绑定的公网地址。

2.  在已准备的弹性云服务器或可访问文档数据库的设备上，安装数据迁移工具。

    安装数据迁移工具，请参见[如何安装MongoDB客户端](http://support.huaweicloud.com/dds_faq/dds_faq_0018.html)。

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >MongoDB客户端会自带mongoexport和mongoimport工具。  


## 备份数据<a name="section6217671136"></a>

1.  <a name="li5891409715403"></a>登录到已准备的弹性云服务器或可访问文档数据库的设备。
2.  使用mongodump工具，备份源数据库中的数据。

    此处以SSL连接方式为例进行说明，如果选择普通连接方式，去掉命令中对应的“**--ssl --sslCAFile** <_FILE\_PATH_\>  **--sslAllowInvalidCertificates**”即可。

    **mongodump --host **_<__DB\_HOST\>_** --port **_<DB\_PORT\>_** -u **_<DB\_USER\>_** --authenticationDatabase **_<AUTH\_DB\>_ **--ssl --sslCAFile** <_FILE\_PATH_\>  **--sslAllowInvalidCertificates**

    -   DB\_HOST为数据库地址。
    -   DB\_PORT为数据库端口号。
    -   DB\_USER为数据库用户名。
    -   AUTH\_DB为存储DB\_USER信息的数据库，一般为admin。
    -   FILE\_PATH是存放根证书的路径。

    出现如下提示时，输入数据库管理员对应的密码：

    ```
    Enter password:
    ```

    示例如下，命令执行后，源数据库中的数据将备份至当前目录下的“dump”文件夹中。

    **./mongodump --host 192.168.6.39 --port 8635 -u rwuser --authenticationDatabase admin --ssl --sslCAFile /tmp/ca.crt --sslAllowInvalidCertificates**

    ```
    2019-03-04T18:42:10.687+0800    writing admin.system.users to
    2019-03-04T18:42:10.688+0800    done dumping admin.system.users (1 document)
    2019-03-04T18:42:10.688+0800    writing admin.system.roles to
    2019-03-04T18:42:10.690+0800    done dumping admin.system.roles (0 documents)
    2019-03-04T18:42:10.690+0800    writing admin.system.version to
    2019-03-04T18:42:10.691+0800    done dumping admin.system.version (2 documents)
    2019-03-04T18:42:10.691+0800    writing test.test_collection to
    2019-03-04T18:42:10.691+0800    writing admin.system.profile to
    2019-03-04T18:42:10.692+0800    done dumping admin.system.profile (4 documents)
    2019-03-04T18:42:10.695+0800    done dumping test.test_collection (198 documents)
    ```


## 导入数据<a name="section517713551614"></a>

1.  登录到已准备的弹性云服务器或可访问文档数据库的设备。
2.  将要导入的数据上传到弹性云服务器或可访问文档数据库的设备。

    根据不同的平台选择相应的上传方法。Linux下可参考命令：

    scp -r  _<__IDENTITY\_DIR\>_ _<REMOTE\_USER\>_@_<REMOTE\_ADDRESS\>_:_<REMOTE\_DIR\>_

    -   IDENTITY\_DIR为备份文件夹所在的目录。
    -   REMOTE\_USER为[1](#li5891409715403)中的弹性云服务器的操作系统用户。
    -   REMOTE\_ADDRESS为[1](#li5891409715403)中的弹性云服务器的主机地址。
    -   REMOTE\_DIR为待导入的目标弹性云服务器的文件目录。

    Windows平台下，请使用传输工具上传备份目录至弹性云服务器。

3.  将备份的数据导入到文档数据库。

    此处以SSL连接方式为例进行说明，如果选择普通连接方式，去掉命令中对应的“**--ssl --sslCAFile** <_FILE\_PATH_\>  **--sslAllowInvalidCertificates**”即可。

    **./mongorestore --host **_<__DB\_HOST\>_** **--port ****_<DB\_PORT\>_** -u **_<DB\_USER\>_** --authenticationDatabase **_<AUTH\_DB\>_**_ _**_<Backup directory\>_** --ssl --sslCAFile** <_FILE\_PATH_\>  **--sslAllowInvalidCertificates**

    -   DB\_HOST为数据库地址。
    -   DB\_PORT为数据库端口号。
    -   DB\_USER为数据库管理员帐号名，默认为rwuser。
    -   AUTH\_DB为DB\_USER进行权限验证的数据库，一般为admin。
    -   Backup directory：备份文件存储目录，默认为“dump”。
    -   FILE\_PATH是存放根证书的路径。

    出现如下提示时，输入数据库管理员对应的密码：

    ```
    Enter password:
    ```

    示例如下：

    **./mongorestore --host 192.168.6.187 --port 8635 -u rwuser --authenticationDatabase admin dump --ssl --sslCAFile** **/tmp/ca.crt** **--sslAllowInvalidCertificates**

    ```
    2019-03-05T14:19:43.240+0800    preparing collections to restore from
    2019-03-05T14:19:43.243+0800    reading metadata for test.test_collection from dump/test/test_collection.metadata.json
    2019-03-05T14:19:43.263+0800    restoring test.test_collection from dump/test/test_collection.bson
    2019-03-05T14:19:43.271+0800    restoring indexes for collection test.test_collection from metadata
    2019-03-05T14:19:43.273+0800    finished restoring test.test_collection (198 documents)
    2019-03-05T14:19:43.273+0800    restoring users from dump/admin/system.users.bson
    2019-03-05T14:19:43.305+0800    roles file 'dump/admin/system.roles.bson' is empty; skipping roles restoration
    2019-03-05T14:19:43.305+0800    restoring roles from dump/admin/system.roles.bson
    2019-03-05T14:19:43.333+0800    done
    ```


