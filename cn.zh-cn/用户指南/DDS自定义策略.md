# DDS自定义策略<a name="dds_03_0061"></a>

如果系统预置的DDS权限，不满足您的授权要求，可以创建自定义策略。自定义策略中可以添加的授权项（Action）请参见[文档数据库服务授权项说明](https://support.huaweicloud.com/api-dds/dds_api_0037.html)。

目前华为云支持以下两种方式创建自定义策略：

-   可视化视图创建自定义策略：无需了解策略语法，按可视化视图导航栏选择云服务、操作、资源、条件等策略内容，可自动生成策略。
-   JSON视图创建自定义策略：可以在选择策略模板后，根据具体需求编辑策略内容；也可以直接在编辑框内编写JSON格式的策略内容。

具体创建步骤请参见：[创建自定义策略](https://support.huaweicloud.com/usermanual-iam/iam_01_0605.html)。本章为您介绍常用的DDS自定义策略样例。

## DDS自定义策略样例<a name="section11187162918515"></a>

-   示例1：授权用户创建文档数据库实例

    ```
    {
        "Version": "1.1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "dds:instance:create"
                ]
            }
        ]
    }
    ```

-   示例2：拒绝用户删除文档数据库实例

    拒绝策略需要同时配合其他策略使用，否则没有实际作用。用户被授予的策略中，一个授权项的作用如果同时存在Allow和Deny，则遵循**Deny优先原则**。

    如果您给用户授予DDS Admin的系统策略，但不希望用户拥有DDS Admin中定义的删除文档数据库实例权限，您可以创建一条拒绝删除文档数据库实例的自定义策略，然后同时将DDS Admin和拒绝策略授予用户，根据Deny优先原则，则用户可以对DDS执行除了删除文档数据库实例外的所有操作。拒绝策略示例如下：

    ```
    {
        "Version": "1.1",
        "Statement": [
            {
              "Effect": "Deny"
              "Action": [
                    "dds:instance:deleteInstance"
                ],
              }
        ]
    }
    ```

-   示例3：多个授权项策略

    一个自定义策略中可以包含多个授权项，且除了可以包含本服务的授权项外，还可以包含其他服务的授权项，可以包含的其他服务必须跟本服务同属性，即都是项目级服务或都是全局级服务。多个授权语句策略描述如下：

    ```
    {  
            "Version": "1.1",  
            "Statement": [  
                    {  
                            "Action": [  
                                    "dds:instance:create",  
                                    "dds:instance:modify",  
                                    "dds:instance:deleteInstance",  
                     "vpc:publicIps:list",  
                     "vpc:publicIps:update"  
                            ],  
                            "Effect": "Allow"  
                    }  
            ]  
    }
    ```


