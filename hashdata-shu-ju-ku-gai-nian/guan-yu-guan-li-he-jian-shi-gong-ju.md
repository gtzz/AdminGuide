# 关于管理和监控工具

HashData数据库为日常监控和管理任务提供了命令行工具。

HashData 命令行工具在 $GPHOME/bin 目录下面，在master主机上面执行。HashData 命令行工具可以用来完成以下管理任务：

* 安装HashData数据库
* 初始化HashData数据库系统
* 启动和停止HashData数据库
* 添加或删除一个主机
* 扩展集群节点并重新分配表数据
* 管理恢复故障的segment实例
* 执行故障转移和恢复故障的master实例
* 备份和转储数据库\(并行\)
* 并行加载数据
* HashData数据库之间的数据传输
* 系统状态报告

HashData数据库包含一个gpperfmon\_install管理工具, 创造了gpperfmon数据库并支持数据收集代理。 用户可以查询gpperfmon数据库来查看查询和系统指标。

![](http://greenplum.org/docs/admin_guide/graphics/cc_arch_gpdb.png)

**父主题:**[HashData数据库概念](/hashdata-shu-ju-ku-gai-nian.md)

