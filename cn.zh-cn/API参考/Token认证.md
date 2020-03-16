# Token认证<a name="dds_api_0010"></a>

## 应用场景<a name="zh-cn_topic_0110967262_section50237402"></a>

当您使用Token认证方式完成认证鉴权时，需要获取用户Token并在调用接口时增加“X-Auth-Token”到业务接口请求消息头中。

本节介绍如何调用接口完成Token认证。

## 调用接口步骤<a name="zh-cn_topic_0110967262_section49483440"></a>

1.  <a name="zh-cn_topic_0110967262_li14280177102918"></a>获取相关信息。
    1.  获取IAM的Endpoint以及消息体中的区域名称，请参见[地区和终端节点](http://developer.huaweicloud.com/endpoint)。
    2.  获取项目ID，具体请参见[获取项目ID](获取项目ID.md)。

2.  <a name="zh-cn_topic_0110967262_li109381224173013"></a>发送“POST https://_IAM__\_Endpoint_/v3/auth/tokens”请求，获取用户Token。

    **表 1**  Header说明

    <a name="zh-cn_topic_0110967262_table18389930"></a>
    <table><thead align="left"><tr id="zh-cn_topic_0110967262_row24749807"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0110967262_p58577354"><a name="zh-cn_topic_0110967262_p58577354"></a><a name="zh-cn_topic_0110967262_p58577354"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="28.98%" id="mcps1.2.5.1.2"><p id="zh-cn_topic_0110967262_p47145209"><a name="zh-cn_topic_0110967262_p47145209"></a><a name="zh-cn_topic_0110967262_p47145209"></a>描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="21.02%" id="mcps1.2.5.1.3"><p id="zh-cn_topic_0110967262_p60665573"><a name="zh-cn_topic_0110967262_p60665573"></a><a name="zh-cn_topic_0110967262_p60665573"></a>是否必选</p>
    </th>
    <th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0110967262_p14964341"><a name="zh-cn_topic_0110967262_p14964341"></a><a name="zh-cn_topic_0110967262_p14964341"></a>示例</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="zh-cn_topic_0110967262_row4152081"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0110967262_p774306"><a name="zh-cn_topic_0110967262_p774306"></a><a name="zh-cn_topic_0110967262_p774306"></a>Content-Type</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.98%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0110967262_p62718864"><a name="zh-cn_topic_0110967262_p62718864"></a><a name="zh-cn_topic_0110967262_p62718864"></a>发送的实体的MIME类型。</p>
    </td>
    <td class="cellrowborder" valign="top" width="21.02%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0110967262_p47063234"><a name="zh-cn_topic_0110967262_p47063234"></a><a name="zh-cn_topic_0110967262_p47063234"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0110967262_p54025633"><a name="zh-cn_topic_0110967262_p54025633"></a><a name="zh-cn_topic_0110967262_p54025633"></a>application/json</p>
    </td>
    </tr>
    </tbody>
    </table>

    请求内容示例如下：

    ```
    {
        "auth": {
            "identity": {
                "methods": [
                    "password"
                ],
                "password": {
                    "user": {
                        "name": "username",
                        "password": "password",
                        "domain": {
                            "name": "domainname"
                        }
                    }
                }
            },
            "scope": {
                "project": {
                   "id": "project_id"
                 }
            }
        }
    }
    ```

    上述命令中，部分参数值（斜体字）请参见以下说明替换为实际内容，具体请参考《统一身份认证服务API参考》的“[获取用户Token](https://support.huaweicloud.com/api-iam/iam_30_0001.html)”章节：

    1.  _IAM__\_Endpoint_替换为[步骤1](#zh-cn_topic_0110967262_li14280177102918)中获取的IAM的Endpoint。
    2.  _username_和_password_分别替换为连接IAM服务器的用户名和密码。
    3.  _project\_id_替换为[步骤1](#zh-cn_topic_0110967262_li14280177102918)中获取的项目ID。

    请求响应成功后，在响应Header中的“X-Subject-Token”的值即为Token值。

    ```
    X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...
    ```

3.  使用如下命令将Token设置为环境变量，方便后续事项。

    **export Token=_\{_**_X-Subject-Token_**_\}_**

    _X-Subject-Token_即为[步骤2](#zh-cn_topic_0110967262_li109381224173013)获取到的token，命令示例如下。

    **export Token=MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...**


