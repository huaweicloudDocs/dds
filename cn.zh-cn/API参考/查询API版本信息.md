# 查询API版本信息<a name="dds_api_0019"></a>

## 功能介绍<a name="section50404481154838"></a>

查询指定API版本信息。

## URI<a name="section36318247154838"></a>

URI格式

GET /v3

## 请求消息<a name="section47398739154838"></a>

-   请求头

    ```
    GET https://DDS的Endpoint/v3
    ```

-   请求体

    N/A


## 响应消息<a name="section59724852154838"></a>

-   要素说明

    **表 1**  要素说明

    <a name="table62971306105515"></a>
    <table><thead align="left"><tr id="row21185732105515"><th class="cellrowborder" valign="top" width="25.962596259625965%" id="mcps1.2.4.1.1"><p id="p19221610105536"><a name="p19221610105536"></a><a name="p19221610105536"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.273027302730277%" id="mcps1.2.4.1.2"><p id="p13446610105536"><a name="p13446610105536"></a><a name="p13446610105536"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="43.76437643764376%" id="mcps1.2.4.1.3"><p id="p2775334615440"><a name="p2775334615440"></a><a name="p2775334615440"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row3452848511416"><td class="cellrowborder" valign="top" width="25.962596259625965%" headers="mcps1.2.4.1.1 "><p id="p4534392511416"><a name="p4534392511416"></a><a name="p4534392511416"></a>version</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.273027302730277%" headers="mcps1.2.4.1.2 "><p id="p146911450319"><a name="p146911450319"></a><a name="p146911450319"></a>Object</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.76437643764376%" headers="mcps1.2.4.1.3 "><p id="p790243911416"><a name="p790243911416"></a><a name="p790243911416"></a>API版本详细信息列表。详情请参见<a href="#table57914909154838">表2</a>。</p>
    </td>
    </tr>
    </tbody>
    </table>

    **表 2**  version字段数据结构说明

    <a name="table57914909154838"></a>
    <table><thead align="left"><tr id="row17905664154838"><th class="cellrowborder" valign="top" width="26.202620262026205%" id="mcps1.2.4.1.1"><p id="p41072674154838"><a name="p41072674154838"></a><a name="p41072674154838"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.193019301930192%" id="mcps1.2.4.1.2"><p id="p38552284154838"><a name="p38552284154838"></a><a name="p38552284154838"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="43.604360436043606%" id="mcps1.2.4.1.3"><p id="p35727319154838"><a name="p35727319154838"></a><a name="p35727319154838"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row8231739154838"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p62791086154838"><a name="p62791086154838"></a><a name="p62791086154838"></a>id</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p52913243154838"><a name="p52913243154838"></a><a name="p52913243154838"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p58114280154838"><a name="p58114280154838"></a><a name="p58114280154838"></a>API版本号。</p>
    </td>
    </tr>
    <tr id="row83118291298"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p2684540212911"><a name="p2684540212911"></a><a name="p2684540212911"></a>links</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p121791290324"><a name="p121791290324"></a><a name="p121791290324"></a>Array of objects</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p16707192915253"><a name="p16707192915253"></a><a name="p16707192915253"></a>对应该API版本的链接信息。详情请参见<a href="#table630875915440">表3</a>。</p>
    <div class="note" id="note1766615256328"><a name="note1766615256328"></a><a name="note1766615256328"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p566620258325"><a name="p566620258325"></a><a name="p566620258325"></a>v3版本该字段为[]。</p>
    </div></div>
    </td>
    </tr>
    <tr id="row53266474154838"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p19617131154838"><a name="p19617131154838"></a><a name="p19617131154838"></a>status</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p45483744154838"><a name="p45483744154838"></a><a name="p45483744154838"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p60304625154838"><a name="p60304625154838"></a><a name="p60304625154838"></a>版本状态。取值为“CURRENT”，表示该版本目前已对外公布。</p>
    </td>
    </tr>
    <tr id="row1144294017433"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p154811524144020"><a name="p154811524144020"></a><a name="p154811524144020"></a>version</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p10856104114111"><a name="p10856104114111"></a><a name="p10856104114111"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p44820241403"><a name="p44820241403"></a><a name="p44820241403"></a>API版本的子版本信息。</p>
    </td>
    </tr>
    <tr id="row17567134264316"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p12508727124012"><a name="p12508727124012"></a><a name="p12508727124012"></a>min_version</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p468916534116"><a name="p468916534116"></a><a name="p468916534116"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p050922734018"><a name="p050922734018"></a><a name="p050922734018"></a>API版本的最小版本号。</p>
    </td>
    </tr>
    <tr id="row5870720154838"><td class="cellrowborder" valign="top" width="26.202620262026205%" headers="mcps1.2.4.1.1 "><p id="p5766344154838"><a name="p5766344154838"></a><a name="p5766344154838"></a>updated</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.193019301930192%" headers="mcps1.2.4.1.2 "><p id="p64420704154838"><a name="p64420704154838"></a><a name="p64420704154838"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.604360436043606%" headers="mcps1.2.4.1.3 "><p id="p50694512154838"><a name="p50694512154838"></a><a name="p50694512154838"></a>版本更新时间。</p>
    <p id="p53597429154838"><a name="p53597429154838"></a><a name="p53597429154838"></a>格式为“yyyy-mm-ddThh:mm:ssZ”。</p>
    <p id="p12614817154838"><a name="p12614817154838"></a><a name="p12614817154838"></a>其中，T指某个时间的开始，Z指UTC时间。</p>
    </td>
    </tr>
    </tbody>
    </table>

    **表 3**  links字段数据结构说明

    <a name="table630875915440"></a>
    <table><thead align="left"><tr id="row4191288815440"><th class="cellrowborder" valign="top" width="26.040000000000003%" id="mcps1.2.4.1.1"><p id="p3950073415440"><a name="p3950073415440"></a><a name="p3950073415440"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.509999999999998%" id="mcps1.2.4.1.2"><p id="p4544288515440"><a name="p4544288515440"></a><a name="p4544288515440"></a>参数类型</p>
    </th>
    <th class="cellrowborder" valign="top" width="43.45%" id="mcps1.2.4.1.3"><p id="p5699506015440"><a name="p5699506015440"></a><a name="p5699506015440"></a>描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row5319717215440"><td class="cellrowborder" valign="top" width="26.040000000000003%" headers="mcps1.2.4.1.1 "><p id="p1400369315440"><a name="p1400369315440"></a><a name="p1400369315440"></a>href</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.509999999999998%" headers="mcps1.2.4.1.2 "><p id="p6055731815440"><a name="p6055731815440"></a><a name="p6055731815440"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.45%" headers="mcps1.2.4.1.3 "><p id="p619568715440"><a name="p619568715440"></a><a name="p619568715440"></a>对应该API的URL，该字段为""。</p>
    </td>
    </tr>
    <tr id="row5576118615440"><td class="cellrowborder" valign="top" width="26.040000000000003%" headers="mcps1.2.4.1.1 "><p id="p2036224315440"><a name="p2036224315440"></a><a name="p2036224315440"></a>rel</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.509999999999998%" headers="mcps1.2.4.1.2 "><p id="p3872902515440"><a name="p3872902515440"></a><a name="p3872902515440"></a>String</p>
    </td>
    <td class="cellrowborder" valign="top" width="43.45%" headers="mcps1.2.4.1.3 "><p id="p5004333115440"><a name="p5004333115440"></a><a name="p5004333115440"></a>取值为“self”，表示URL为本地链接。</p>
    </td>
    </tr>
    </tbody>
    </table>


-   响应样例

    ```
    {
        "version": {
            "id": "v3",
            "links": [],
            "status": "CURRENT",
            "version": "",
            "min_version": "",
            "updated": "2017-02-07T17:34:02Z"
        }
    }
    ```


## 状态码<a name="section5382712154838"></a>

详情请参见[状态码](状态码.md)。

## 错误码<a name="section6522193710339"></a>

详情请参见[错误码](错误码.md)。

