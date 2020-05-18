# 变更集群实例的CPU和内存规格（社区增强版）<a name="dds_03_0049"></a>

## 操作场景<a name="section38106127132942"></a>

当用户购买的增强版集群实例的CPU和内存规格无法满足业务需求时，可以在控制台进行CPU和内存规格变更。

>![](public_sys-resources/icon-note.gif) **说明：**   
>-   账户余额大于或等于0元，才可以变更规格。  
>-   当实例进行CPU和内存规格变更时，该实例不可被删除。  
>-   目前，社区增强版实例仅支持扩大规格。  
>-   变更CPU/内存规格，需要5\~10分钟的中断重启，建议业务空闲时变更。重启后实例会自动释放内存中的缓存，请注意对业务进行预热，避免业务高峰期出现阻塞。  

## 注意事项<a name="section1752311674715"></a>

-   对于按需计费的实例，变更规格后，依旧按使用时长实时计费。

-   对于包年/包月的实例，需结合已使用的时间周期，补交差价费用。
-   增强版实例各节点规格的对应关系如下表所示。

    示例：将原规格“1核 | 4GB”变更为“4核 | 16GB”，变更后可查看到shard规格为“4核 | 16GB”、mongos规格为“4核 | 16GB”、config规格为“1核 | 4GB”。

    **表 1**  节点规格对应关系

    <a name="table12243532412"></a>
    <table><thead align="left"><tr id="row20241934418"><th class="cellrowborder" valign="top" width="32.269999999999996%" id="mcps1.2.4.1.1"><p id="p202408314116"><a name="p202408314116"></a><a name="p202408314116"></a>shard</p>
    </th>
    <th class="cellrowborder" valign="top" width="34.27%" id="mcps1.2.4.1.2"><p id="p424113124118"><a name="p424113124118"></a><a name="p424113124118"></a>mongos</p>
    </th>
    <th class="cellrowborder" valign="top" width="33.46%" id="mcps1.2.4.1.3"><p id="p1324113194117"><a name="p1324113194117"></a><a name="p1324113194117"></a>config</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row8241134412"><td class="cellrowborder" valign="top" width="32.269999999999996%" headers="mcps1.2.4.1.1 "><p id="p72419318414"><a name="p72419318414"></a><a name="p72419318414"></a>1核 | 4GB</p>
    </td>
    <td class="cellrowborder" valign="top" width="34.27%" headers="mcps1.2.4.1.2 "><p id="p1324193104113"><a name="p1324193104113"></a><a name="p1324193104113"></a>1核 | 4GB</p>
    </td>
    <td class="cellrowborder" rowspan="3" valign="top" width="33.46%" headers="mcps1.2.4.1.3 "><p id="p324115314411"><a name="p324115314411"></a><a name="p324115314411"></a>1核 | 4GB</p>
    </td>
    </tr>
    <tr id="row1424214310419"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p62428374112"><a name="p62428374112"></a><a name="p62428374112"></a>2核 | 8GB</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.4.1.2 "><p id="p22426319416"><a name="p22426319416"></a><a name="p22426319416"></a>2核 | 8GB</p>
    </td>
    </tr>
    <tr id="row11242173184117"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p724273184114"><a name="p724273184114"></a><a name="p724273184114"></a>4核 | 16GB</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.4.1.2 "><p id="p82421331415"><a name="p82421331415"></a><a name="p82421331415"></a>4核 | 16GB</p>
    </td>
    </tr>
    <tr id="row324203134117"><td class="cellrowborder" valign="top" width="32.269999999999996%" headers="mcps1.2.4.1.1 "><p id="p4242103114119"><a name="p4242103114119"></a><a name="p4242103114119"></a>8核 | 32GB</p>
    </td>
    <td class="cellrowborder" valign="top" width="34.27%" headers="mcps1.2.4.1.2 "><p id="p162421637417"><a name="p162421637417"></a><a name="p162421637417"></a>8核 | 32GB</p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="33.46%" headers="mcps1.2.4.1.3 "><p id="p424215384116"><a name="p424215384116"></a><a name="p424215384116"></a>2核 | 8GB</p>
    </td>
    </tr>
    <tr id="row424343164117"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p32431314119"><a name="p32431314119"></a><a name="p32431314119"></a>16核 | 64GB</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.4.1.2 "><p id="p202436374114"><a name="p202436374114"></a><a name="p202436374114"></a>16核 | 64GB</p>
    </td>
    </tr>
    <tr id="row8243173114115"><td class="cellrowborder" valign="top" width="32.269999999999996%" headers="mcps1.2.4.1.1 "><p id="p11243103114120"><a name="p11243103114120"></a><a name="p11243103114120"></a>32核 | 128GB</p>
    </td>
    <td class="cellrowborder" valign="top" width="34.27%" headers="mcps1.2.4.1.2 "><p id="p924314317415"><a name="p924314317415"></a><a name="p924314317415"></a>16核 | 64GB</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.46%" headers="mcps1.2.4.1.3 "><p id="p16243430417"><a name="p16243430417"></a><a name="p16243430417"></a>4核 | 16GB</p>
    </td>
    </tr>
    </tbody>
    </table>


## 操作步骤<a name="section79281543052"></a>

1.  [登录文档数据库服务](https://support.huaweicloud.com/qs-dds/dds_02_0043.html)。
2.  在“实例管理“页面，选择指定的增强版实例，单击实例名称。
3.  在“基本信息“页面“数据库信息“区域的“性能规格“处，单击“规格变更“，进入“变更增强版实例规格”页面。
4.  在“变更增强版实例规格”页面，选择所需修改到的性能规格，单击“下一步“。

    **图 1**  变更增强版实例规格<a name="fig590517210398"></a>  
    ![](figures/变更增强版实例规格.png "变更增强版实例规格")

5.  在规格确认页面，确认性能规格。
    -   包年/包月
        -   如需重新选择，单击“上一步”，修改性能规格。
        -   核对无误后，单击“提交订单”，进入付款页面，选择支付方式，完成支付。

    -   按需计费
        -   如需重新选择，单击“上一步”，修改性能规格。
        -   核对无误后，单击“提交“，开始变更规格。

6.  查看变更结果。
    -   CPU和内存变更过程中，实例运行状态显示为“规格变更中”，变更耗时如下：
        -   对于变更后config规格未发生改变的场景，变更过程约10\~15分钟。
        -   对于变更后config规格发生改变的场景，变更过程约20分钟。

    -   在实例列表的右上角，单击![](figures/kwx318612-GAUSS-DBaaS-image-dbe6bb50-e0f5-42a9-91be-08aab27832dc-11.png)刷新列表，可看到规格变更完成的实例的运行状态显示为“正常”。
    -   在集群实例“基本信息”页面的“节点信息”区域，结合[表1](#table12243532412)，查看变更后的规格。


