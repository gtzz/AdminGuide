# 关于 HashData 架构

HashData 数据库是一个大规模并行处理\(MPP\)数据库服务器架构，特别设计来管理用来做业务分析的大型数据仓库以及商业智能的工作负载。

MPP\(有时也称为一个_无共享_架构\)是指系统两个或两个以上的处理器,配合执行一个操作,每个处理器有自己的内存,操作系统和磁盘。 HashData 使用这种高性能的系统架构分发负载tb级数据仓库,可以使用系统的所有资源并行处理一个查询。

HashData 数据库基于PostgreSQL开源技术。 它本质上是几个 PostgreSQL数据库实例紧密结合在一起协作，作为一个数据库管理系统\(DBMS\)。 它是基于PostgreSQL 8.3.23,在大多数情况下与 PostgreSQL关于SQL支持、功能、配置选项和终端用户功能是非常相似的。 数据库用户可以像使用 PostgreSQL数据库管理系统一样使用 HashData。

HashData 数据库可以使用append-optimized\(AO\)存储格式批量加载和读取数据,并通过堆表提供性能优势。 Append-optimized 存储为数据保护、压缩和行/列定向，提供校验。 行向或者列向的append-optimized表都可以被压缩。

HashData 数据库和PostgreSQL之间的主要区别如下:

* GPORCA是用于查询计划,除了传统的查询计划, 基于Postgres查询计划。
* HashData 数据库可以使用append-optimized存储。
* HashData 数据库可以使用列存储,数据在逻辑上组织为一个表,行和列在物理存储模式上面采用列向格式，而非行向格式。列存储只能使用 append-optimized表。 列存储是可压缩的。 它还可以提供性能提升，当你只需要返回你感兴趣的列时。 所有的压缩算法可用于行向或列向的表,但Run-Length Encoded \(RLE\)压缩只能使用用于列向表。 HashData 数据库为使用列存储的所有Append-Optimized表提供压缩。

PostgreSQL的内部已修改或补充支持并行 HashData 数据库的结构。 例如,系统目录、优化器、查询执行器, 和事务管理器组件已经被修改和增强，使能够同时查询所有的平行PostgreSQL数据库实例。 HashData 的_互连_\(网络层\)支持不同的PostgreSQL实例之间的通信 和并使得系统像一个逻辑数据库一样。

HashData 数据库也可以使用声明性分区和子分区隐式地生成分区约束。

HashData 数据库还包括为PostgreSQL 智能\(BI\)工作负载做的功能设计优化。 例如,HashData 增加了并行数据加载\(外部表\)、资源管理、查询优化和存储增强，这些在标准PostgreSQL中是没有的。 HashData 开发了许多新特性并对数据库做了很多优化。

HashData 数据库查询使用Volcano-style查询引擎模型,执行引擎获取一个执行计划,并使用它生成一个物理操作树,通过物理操作评估表,提供查询反馈结果。

HashData 通过分发数据和工作负载进程到多个服务器或者主机上面，来存储和处理大量的数据。 HashData 数据库是一系列的基于PostgreSQL 8.3的独立的数据库一起协作提供服务，好像一台数据库服务器一样。 master 是 HashData 数据库系统的入口_。 客户端通过数据库的master 实例连接和提交SQL语句。 master 与系统中其它存储和处理数据的 segments 数据库实例协同工作。_

图1所示。 HashData 数据库架构

![](http://greenplum.org/docs/admin_guide/graphics/highlevel_arch.jpg)

以下主题描述了构成 HashData 数据库系统的组件以及如何他们一起工作。

* 关于 HashData Master节点
* 关于 HashData Segments 节点
* 关于 HashData 内部互连

**父主题: **[HashData 数据库概念](/hashdata-shu-ju-ku-gai-nian.md)

## 关于 HashData Master 节点（主节点）

Master 节点是 HashData 数据库系统的入口, 接受客户端连接和SQL查询,并且分发工作给segment 节点的实例。

HashData 的用户通过主节点与 HashData 数据库交互就与普通的 PostgreSQL 数据库一样。 他们使用客户程序连接到数据库,比如psql或应用程序编程接口\(api\),例如JDBC、 ODBC或libpq\(PostgreSQL C API\)。

主节点包含所有的系统目录。系统目录是包含 HashData 数据库系统的元数据的系统表的集合。 主节点不包含任何用户数据;用户数据仅仅存在于segments节点上面。Master 节点授权客户端连接，处理接受的SQL指令，分发工作负载到segments节点上面，整合每个segment节点的返回结果，展示最终结果给客户端程序。

HashData 数据库在master/standby master mirroring使用Write-Ahead Logging \(WAL\)。 所有的修改在被应用之前会被写入日志，以确保在操作进程中的数据完整性。

注意: Write-Ahead Logging 在segment 镜像中还没有实现。

## 关于 HashData segments 节点（计算节点）

HashData 数据库的计算节点实例是独立的PostgreSQL数据库，存储有一部分的数据，并且执行大部分的查询进程。

当用户通过 HashData 主节点连接到数据库执行一个查询操作时，在每一个结算节点数据库都会创建进程来处理这个查询的工作。

用户定义的表及其索引分布在HashData数据库系统中的可用的segment节点上面,每个计算节点包含一部分不重复的数据（是指所有计算节点的数据不会重复）。 数据库服务在相应的segment实例下面处理相应的数据服务请求。用户通过HashData中的主节点与计算节点交互。

segments节点运行在segment主机上面。 一个segment主机通常会有2-8个HashData计算节点，根据CPU核心,内存,存储,网络 接口和工作负载来设计。 所有的segments主机最好采用相同的配置。 通过分配数据和工作负载到大量的相同性能的计算节点上面，能够获得最佳性能的关键因素在于所有计算节点同时开始和结束同一个任务。

## 关于 HashData 互连

interconect是 HashData 数据库网络层的体系结构。

interconect 是指在计算节点之间的进程通信以及通信所依赖的网络基础设施。 HashData内部通信使用标准以太网交换结构。 由于性能原因,建议使用10-Gigabit网卡,或者更快的网卡。

默认情况下,内部互连使用用户数据报协议流控制\(UDPIFC\) 通过网络互连流量发送消息。HashData 软件会在执行 UDP 时提供额外的数据包验证。 这意味着可靠性是与传输控制协议\(TCP\)是等价的,性能和可伸缩性超过TCP。 如果内部互联改为TCP,HashData 数据库的可伸缩性限制为1000 个 segment 实例。 UDPIFC 作为默认协议互连,没有这个上限限制。更多关于 HashData 数据库支持的内部连接的类型，可以查看《Greenplum Database Reference Guide》中的服务器配置参数 gp\_interconnect\_type 。

.

