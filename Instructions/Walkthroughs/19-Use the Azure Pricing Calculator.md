﻿---
wts:
    title: '19 - 使用 Azure 定价计算器'
    module: '模块 04 - Azure 定价和支持'
---
# 19 - 使用定价计算器

在本演练中，我们将使用 Azure 定价计算器生成 Azure 虚拟机和相关网络资源的成本估算。

预计用时：30 分钟

# 任务 1：配置定价计算器

在此任务中，我们将在 Azure 定价计算器中配置一个简单的基础结构。 

**注意**：为创建 Azure Pricing Calculator 估算，本次演示提供了 VM 和相关资源的示例配置。使用示例配置或在 Azure Pricing Calculator 提供你 *实际* 资源要求的详细信息。

1. 在浏览器中，导航至 [Azure 定价计算器](https://azure.microsoft.com/zh-cn/pricing/calculator/) 网页。

2. 要添加 VM 配置的详细信息，请选择 **产品** 选项卡的 **虚拟机**。向下滚动以查看虚拟机的详细信息。 

3. 输入 Azure Pricing Calculator 估算的名称以及 VM 配置的名称。本次演示示例使用 **我的定价计算器估算** 进行估算，**Windows VM** 进行 VM 配置。

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的 VM 配置区域。突出显示的估算名称和 VM 配置名称指示了如何将估算名称和 VM 配置名称添加到 Azure 定价计算器估算中。](../images/1901.png)

4. 修改默认的 VM 配置。

    |区域|操作系统|类型|
    |------|----------------|----|
    |北欧|Windows|（仅限 OS）|
    | | |

    |层|实例|
    |----|--------|
    |标准|A2：2 个核心，3.5 GB RAM，135 GB 临时存储|
    | | |

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的 VM 配置区域。突出显示的用户输入 VM 配置属性值示例指示了如何在 Azure 定价计算器估算中指定 VM 配置。](../images/1902.png)

    **注意**：VM 实例规范和定价可能与此示例中的不同。通过选择与示例尽可能匹配的实例来完成本次演示。要查看有关不同 VM 产品选项的详细信息，请在右侧 **更多信息** 菜单中选择 **产品** 详情。

5. 设置 **结算选项** 为 **现收现付**。

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的 VM 计费选项区域。突出显示的“即付即用”计费选项指示了如何在 Azure 定价计算器估算中指定 VM 计费选项。](../images/1903.png)

6. 在 Azure 中，一个月定义为 730 小时。如果你每月 100％的时间需要使用 VM，则将每月的小时数设置为“730”。本次演示示例要求每个月有 50％的时间需要用到 VM。

    将 VM 的数量设置为`1`，并将每月小时数值更改为`365`。

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的 VM 计费选项区域。突出显示的 VM 实例数和每月小时数选项指示了如何在 Azure 定价计算器估算中指定 VM 的实例数和每月小时数。](../images/1904.png)

7. 在 **托管的 OS 磁盘** 窗格中，修改默认的 VM 存储配置。

    |层|磁盘大小|磁盘数量|快照|存储交易|
    |----|---------|---------------|--------|--------------------|
    |标准 HDD|S30：1024 GiB|1|关闭|10,000|

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的托管 OS 磁盘选项区域。突出显示的层级类型、磁盘大小、磁盘数和存储交易数选项指示了如何在 Azure 定价计算器估算中指定 VM 存储配置。](../images/1905.png)

8. 要为估算添加网络带宽，请转到 Azure 定价计算器网页的顶部。在左侧 **产品** 菜单中选择 **联网** ，然后选择 **带宽** 图块。在带宽里增加消息对话框，选择 **查看**。

   ![此屏幕截图显示了 Azure 定价计算器网页中的网络产品区域。突出显示的“网络”、“添加带宽”和“查看带宽”图块指示了如何在 Azure 定价计算器估算中添加和查看网络带宽配置的详细信息。](../images/1906.png)

9. 添加 VM 带宽配置名称。本次演示示例使用名称 **带宽：Windows VM**。通过添加以下详细信息来修改默认带宽配置。

    |区域|1 区出站数据传输量|
    |------|--------------------------------------|
    |北欧|50 GB|

   ![此屏幕截图显示了 Azure 定价计算器估算网页中的网络带宽配置区域。突出显示的用户输入带宽属性值示例指示了如何在 Azure 定价计算器估算中指定 VM 带宽配置。](../images/1907.png)

10. 要添加应用程序网关，请返回 Azure 定价计算器网页的顶部。在 **联网** 产品菜单内选择 **Application Gateway** 图块。在 **Application Gateway** 的消息对话框内选择 **查看**。

    ![此屏幕截图显示了 Azure 定价计算器网页中的网络产品区域。突出显示的“网络”、“添加应用程序网关”和“查看应用程序网关”图块指示了如何在 Azure 定价计算器估算中添加和查看应用程序网关配置的详细信息。](../images/1908.png)

11. 添加 Application Gateway 配置名称。本次演示使用名称 **App Gateway： Windows VM**。通过添加以下详细信息来修改默认 Application Gateway 配置。

    |区域|层|大小|
    |------|----|----|
    |北欧|基础|小|
    | | |

    |实例|小时|
    |-------|-------|
    |1|365|
    | | |

    |数据处理|
    |--------------|
    |50 GB|
    | | |

    |1 区：北美，欧洲|
    |-----------------------------|
    |50 GB|
    | | |

    ![此屏幕截图显示了 Azure 定价计算器估算网页中的应用程序网关配置区域。](../images/1909.png)


# 任务 2：查看定价估算

在此任务中，我们将查看 Azure 定价计算器的结果。 

1. 滚动到 Azure 定价计算器网页底部，查看 **每月估算总成本**。

    **注意**：浏览 Azure Pricing Calculator 中提供的各种选项。例如，本次演示要求你将货币更新为欧元。

2. 将货币更改为欧元，然后选择 **导出** 下载 Microsoft Excel（`.xlsx`）格式的离线查看估计的副本。

    ![此屏幕截图显示了 Azure 定价计算器估算网页中的每月估算总成本。突出显示的欧元货币选项指示如何修改 Azure 定价计算器估算中使用的货币。突出显示的导出选项说明了如何下载估算副本以供离线查看。](../images/1910.png)

    ![此屏幕截图显示了 Microsoft Excel 中的示例 Azure 定价计算器估算。](../images/1911.png)

恭喜！你从 Azure Pricing Calculator 下载了估算。