# 查询API版本列表<a name="dds_api_0018"></a>

## 功能介绍<a name="section9793815440"></a>

查询当前支持的API版本信息列表。

## URI<a name="section428804115440"></a>

-   URI格式

    GET /

-   参数说明

    N/A


## 请求消息<a name="section2907369315440"></a>

-   请求头

    ```
    GET https://DDS的Endpoint/
    ```

-   请求体

    N/A


## 响应消息<a name="section5543006115440"></a>

-   要素说明

    **表 1**  要素说明

    <a name="table3575976715440"></a>
    <table><thead align="left"><tr id="row5028223115440"><th class="cellrowborder" valign="top" width="26.772677267726774%" id="mcps1.2.4.1.1"><p id="p4632888215440"><a name="p4632888215440"></a><a name="p4632888215440"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="29.352935293529352%" id="mcps1.2.4.1.2"><p id="p6165196615440"><a name="p6165196615440"></a><a name="p6165196615440"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="43.87438743874388%" id="mcps1.2.4.1.3"><p id="p2775334615440"><a name="p2775334615440"></a><a name="p2775334615440"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row3342858315440"><td class="cellrowborder" valign="top" width="26.772677267726774%" headers="mcps1.2.4.1.1 "><p id="p2336072515440"><a name="p2336072515440"></a><a name="p2336072515440"></a>versions</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.352935293529352%" headers="mcps1.2.4.1.2 "><p id="p94851531275"><a name="p94851531275"></a><a name="p94851531275"></a>Array of objects</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.87438743874388%" headers="mcps1.2.4.1.3 "><p id="p476126915440"><a name="p476126915440"></a><a name="p476126915440"></a>API版本详细信息列表。详情请参见<a href="#table37479565104653">表2</a>。</p>
    </td>
    </tr>
    </tbody>
    </table>

    **表 2**  versions字段数据结构说明

    <a name="table37479565104653"></a>
    <table><thead align="left"><tr id="row65790814104653"><th class="cellrowborder" valign="top" width="26.529999999999998%" id="mcps1.2.4.1.1"><p id="p27455703104653"><a name="p27455703104653"></a><a name="p27455703104653"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="29.7%" id="mcps1.2.4.1.2"><p id="p9319469104653"><a name="p9319469104653"></a><a name="p9319469104653"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="43.769999999999996%" id="mcps1.2.4.1.3"><p id="p1143415283591"><a name="p1143415283591"></a><a name="p1143415283591"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row8861837104653"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p46720233104653"><a name="p46720233104653"></a><a name="p46720233104653"></a>id</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p26242496104653"><a name="p26242496104653"></a><a name="p26242496104653"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p45267452104653"><a name="p45267452104653"></a><a name="p45267452104653"></a>API版本号。</p>
    </td>
    </tr>
    <tr id="row1548795912115"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p26342211121111"><a name="p26342211121111"></a><a name="p26342211121111"></a>links</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p18625313281"><a name="p18625313281"></a><a name="p18625313281"></a>Array of objects</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p31978734121111"><a name="p31978734121111"></a><a name="p31978734121111"></a>对应该API的链接信息。详情请参见<a href="#table630875915440">表3</a>。</p>
    <div class="note" id="note1766615256328"><a name="note1766615256328"></a><a name="note1766615256328"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p566620258325"><a name="p566620258325"></a><a name="p566620258325"></a>v3版本该字段为[]。</p>
    </div></div>
    </td>
    </tr>
    <tr id="row4753892104653"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p49520946104653"><a name="p49520946104653"></a><a name="p49520946104653"></a>status</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p51773656104653"><a name="p51773656104653"></a><a name="p51773656104653"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p32916607104653"><a name="p32916607104653"></a><a name="p32916607104653"></a>版本状态。</p>
    </td>
    </tr>
    <tr id="row1648012414408"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p154811524144020"><a name="p154811524144020"></a><a name="p154811524144020"></a>version</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p10856104114111"><a name="p10856104114111"></a><a name="p10856104114111"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p44820241403"><a name="p44820241403"></a><a name="p44820241403"></a>API版本的子版本信息。</p>
    </td>
    </tr>
    <tr id="row050892716406"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p12508727124012"><a name="p12508727124012"></a><a name="p12508727124012"></a>min_version</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p468916534116"><a name="p468916534116"></a><a name="p468916534116"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p050922734018"><a name="p050922734018"></a><a name="p050922734018"></a>API版本的最小版本号。</p>
    </td>
    </tr>
    <tr id="row27814010104653"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p38342341104653"><a name="p38342341104653"></a><a name="p38342341104653"></a>updated</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.7%" headers="mcps1.2.4.1.2 "><p id="p18721892104653"><a name="p18721892104653"></a><a name="p18721892104653"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.769999999999996%" headers="mcps1.2.4.1.3 "><p id="p40078272104653"><a name="p40078272104653"></a><a name="p40078272104653"></a>版本更新时间。</p>
    <p id="p25160128104653"><a name="p25160128104653"></a><a name="p25160128104653"></a>格式为“yyyy-mm-ddThh:mm:ssZ”。</p>
    <p id="p25114560104653"><a name="p25114560104653"></a><a name="p25114560104653"></a>其中，T指某个时间的开始，Z指UTC时间。</p>
    </td>
    </tr>
    </tbody>
    </table>

    **表 3**  links字段数据结构说明

    <a name="table630875915440"></a>
    <table><thead align="left"><tr id="row4191288815440"><th class="cellrowborder" valign="top" width="26.529999999999998%" id="mcps1.2.4.1.1"><p id="p3950073415440"><a name="p3950073415440"></a><a name="p3950073415440"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="29.459999999999997%" id="mcps1.2.4.1.2"><p id="p4544288515440"><a name="p4544288515440"></a><a name="p4544288515440"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="44.01%" id="mcps1.2.4.1.3"><p id="p2056123485910"><a name="p2056123485910"></a><a name="p2056123485910"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row5319717215440"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p1400369315440"><a name="p1400369315440"></a><a name="p1400369315440"></a>href</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.459999999999997%" headers="mcps1.2.4.1.2 "><p id="p6055731815440"><a name="p6055731815440"></a><a name="p6055731815440"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="44.01%" headers="mcps1.2.4.1.3 "><p id="p619568715440"><a name="p619568715440"></a><a name="p619568715440"></a>对应该API的URL，该字段为""。</p>
    </td>
    </tr>
    <tr id="row5576118615440"><td class="cellrowborder" valign="top" width="26.529999999999998%" headers="mcps1.2.4.1.1 "><p id="p2036224315440"><a name="p2036224315440"></a><a name="p2036224315440"></a>rel</p>
    </td>
    <td class="cellrowborder" valign="top" width="29.459999999999997%" headers="mcps1.2.4.1.2 "><p id="p3872902515440"><a name="p3872902515440"></a><a name="p3872902515440"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="44.01%" headers="mcps1.2.4.1.3 "><p id="p5004333115440"><a name="p5004333115440"></a><a name="p5004333115440"></a>取值为“self”，表示URL为本地链接。</p>
    </td>
    </tr>
    </tbody>
    </table>


-   响应样例

    ```
    {
        "versions": [
            {
                "id": "v3",
                "links": [],
                "status": "CURRENT",
                "version": "",
                "min_version": "",
                "updated": "2017-02-07T17:34:02Z"
            }
        ]
    }
    ```


## 状态码<a name="section17992204432820"></a>

详情请参见[状态码](状态码.md)。

## 错误码<a name="section6522193710339"></a>

详情请参见[错误码](错误码.md)。

