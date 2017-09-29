# HashData 架构

HashData 数据库是一个大规模并行处理（MPP）数据库服务器，具有特别设计用于管理大型分析数据仓库和商业智能工作负载的体系结构。

MPP（也称为无共享架构）是指具有两个或多个处理器的系统，其协作来执行操作，每个处理器具有其自己的存储器，操作系统和磁盘。 HashData 使用这种高性能系统架构来分配 TB 级数据仓库的负载，并且可以并行地使用系统的所有资源来处理查询。

HashData 数据库基于 PostgreSQL 开源技术。 它本质上是几个 PostgreSQL 数据库实例一起作为一个连贯的数据库管理系统（DBMS）。 它基于 PostgreSQL 8.2.15 ，在大多数情况下与 PostgreSQL 非常相似，涉及 SQL 支持，功能，配置选项和最终用户功能。 数据库用户与 HashData 数据库进行交互，就像常规的 PostgreSQL DBMS 一样。

PostgreSQL 的内部部件已被修改或补充，以支持 HashData 数据库的并行结构。 例如，系统目录，优化程序，查询执行程序和事务管理器组件已被修改和增强，以便能够同时跨所有并行 PostgreSQL 数据库实例执行查询。 HashData 互连（网络层）可实现不同 PostgreSQL 实例之间的通信，并允许系统作为一个逻辑数据库。

HashData 数据库还包括旨在优化 PostgreSQL 以实现商业智能（BI）工作负载的功能。 例如，HashData 已经在标准 PostgreSQL 中添加了并行数据加载（外部表），资源管理，查询优化和存储增强功能。 HashData 开发的许多功能和优化进入了 PostgreSQL 社区。 例如，表分区是 HashData 首先开发的一个功能，它现在在标准的 PostgreSQL 中。

HashData Database 通过在多个服务器或主机之间分配数据和处理工作负载来存储和处理大量数据。HashData 数据库是基于PostgreSQL 8.2 的单独数据库数组，共同提供单个数据库映像。 主节点是 HashData 数据库系统的入口点。 它是客户端连接和提交SQL语句的数据库实例。 主节点与系统中的其他数据库实例协调工作，称为计算节点，计算节点用来存储和处理数据。

图1所示。 HashData 数据库架构

![](http://greenplum.org/docs/admin_guide/graphics/highlevel_arch.jpg)

以下主题描述组成 HashData 数据库系统的组件以及它们如何协同工作。

* 关于 HashData 主节点
* 关于 HashData 计算节点
* 关于 HashData 内部互连

**父主题: **[HashData 数据库概念](/hashdata-shu-ju-ku-gai-nian.md)

## 关于 HashData 主节点

HashData 数据库主节点是 HashData 数据库系统的入口，接受客户端连接和 SQL 查询，并将工作分配到计算节点实例。

HashData 数据库最终用户与 HashData 数据库（通过主节点）进行交互，就像使用典型的 PostgreSQL 数据库一样。 它们使用客户端程序如 psql ，或者应用程序接口诸如 JDBC ，ODBC 或 [libpq](https://www.postgresql.org/docs/8.2/static/libpq.html) （PostgreSQL C API）连接到数据库。

主节点是全局系统目录所在的位置。 全局系统目录是一组系统表，其中包含有关 HashData 数据库系统本身的元数据。 主节点不包含任何用户数据; 数据仅保存在计算节点上。 主节点服务器验证客户端连接，处理传入的 SQL 命令，在计算节点之间分配工作负载，协调每个计算节点返回的结果，并将最终结果呈现给客户端程序。

## 关于 HashData 计算节点

HashData 数据库计算节点实例是独立的 PostgreSQL 数据库，每个数据库都存储一部分数据并执行查询处理的大部分。

当用户通过 HashData 主节点连接到数据库并发出查询时，会在每个计算节点数据库中创建进程以处理该查询的工作。 有关查询过程的更多信息，请参阅关于 HashData 查询处理。

用户定义的表及其索引分布在 HashData 数据库系统中的可用计算节点; 每个节点包含不同部分的数据。 在相应的计算节点实例下运行节点数据的数据库服务器进程。 用户通过主节点与 HashData 数据库系统中的计算节点进行交互。

## 关于 HashData 互连

interconect是 HashData 数据库网络层的体系结构。

interconect 是指在计算节点之间的进程通信以及通信所依赖的网络基础设施。 HashData内部通信使用标准以太网交换结构。 由于性能原因,建议使用10-Gigabit网卡,或者更快的网卡。

默认情况下,内部互连使用用户数据报协议流控制\(UDPIFC\) 通过网络互连流量发送消息。HashData 软件会在执行 UDP 时提供额外的数据包验证。 这意味着可靠性是与传输控制协议\(TCP\)是等价的,性能和可伸缩性超过TCP。 如果内部互联改为TCP,HashData 数据库的可伸缩性限制为1000 个 segment 实例。 UDPIFC 作为默认协议互连,没有这个上限限制。更多关于 HashData 数据库支持的内部连接的类型，可以查看《Greenplum Database Reference Guide》中的服务器配置参数 gp\_interconnect\_type 。

.

