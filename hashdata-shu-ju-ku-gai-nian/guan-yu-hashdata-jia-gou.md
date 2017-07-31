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

* [关于Greenplum主](http://greenplum.org/docs/admin_guide/intro/arch_overview.html#arch_master)
* [关于Greenplum段](http://greenplum.org/docs/admin_guide/intro/arch_overview.html#arch_segments)
* [关于Greenplum互连](http://greenplum.org/docs/admin_guide/intro/arch_overview.html#arch_interconnect)

**父主题:**

[Greenplum数据库概念](http://greenplum.org/docs/admin_guide/intro/partI.html)

## 关于Greenplum主

Greenplum数据库的主入口Greenplum数据库系统, 接受客户端连接和SQL查询,和分发工作段的实例。

Greenplum数据库最终用户与Greenplum数据库交互\(通过主\)他们 会与一个典型的PostgreSQL数据库。 他们使用客户程序连接到数据库 如psql或应用程序编程接口\(api\),例如JDBC、 ODBC或[libpq](https://www.postgresql.org/docs/8.3/static/libpq.html)\(PostgreSQL C API\)。

主的_全球系统目录_驻留。 全球系统目录 系统表的集合包含关于Greenplum数据库系统本身的元数据。 主不包含任何用户数据;数据驻留在_段_。 的 大师认证客户端连接,过程输入的SQL命令,分发 工作负载在段,每段坐标返回的结果,介绍了 最终结果给客户端程序。

Greenplum数据库使用写前日志记录\(细胞膜\)主/备用主镜像。 在 WAL-based日志,所有修改都写入到日志被应用之前,确保 数据完整性的任何进程内操作。

注意:

WAL日志尚未获得 段镜像。

## 关于Greenplum段

Greenplum独立PostgreSQL数据库,每个数据库部分实例 存储的数据并执行查询处理的大部分。

当用户连接到数据库通过Greenplum大师和问题查询,流程 在每一部分中创建数据库查询处理的工作。 的更多信息 关于查询流程,明白了[关于Greenplum查询处理](http://greenplum.org/docs/admin_guide/query/topics/parallel-proc.html#topic1)。

用户定义的表及其索引分布在可用的部分中 Greenplum数据库系统,每个部分包含一个独特的部分数据。 数据库 服务器进程服务段数据下运行相应的段实例。 用户与段Greenplum通过主数据库系统。

段运行在一个服务器_部分主机_。 部分主机通常执行 从2到8个Greenplum段,根据CPU核心,内存,存储,网络 接口和工作负载。 部分主机预计将完全相同的配置。 的关键 从Greenplum数据库获得最佳性能和分发数据 工作负载_均匀_在大量的同样段,这样所有的能力 段开始工作在一个任务同时完成他们的工作在同一时间。

## 关于Greenplum互连

Greenplum interconect是网络层的数据库 体系结构。

的_互连_是指部分和之间的进程间通信 这个通信网络基础设施。 Greenplum互连使用 标准以太网交换结构。 由于性能原因,10 g系统,或者更快, 建议。

默认情况下,互连使用用户数据报协议流控制\(UDPIFC\) 通过网络互连流量发送消息。 Greenplum软件执行 UDP数据包提供验证超出。 这意味着可靠性是等价的 传输控制协议\(TCP\),性能和可伸缩性超过TCP。 如果 互连改为TCP,Greenplum数据库的可伸缩性限制为1000 段的实例。 UDPIFC作为默认协议互连,这个极限 不适用。

