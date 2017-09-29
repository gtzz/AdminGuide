# Summary

* [HashData 数据库管理员指南](README.md)
  * [HashData 数据库概念](hashdata-shu-ju-ku-gai-nian.md)
    * [HashData 数据库架构](hashdata-shu-ju-ku-gai-nian/guan-yu-hashdata-jia-gou.md)
    * [管理和监控应用程序](hashdata-shu-ju-ku-gai-nian/guan-yu-guan-li-he-jian-shi-gong-ju.md)
    * [HashData 数据库的并发控制](hashdata-shu-ju-ku-gai-nian/hashdata-shu-ju-ku-de-bing-fa-kong-zhi.md)
      * [管理事务id的例子](hashdata-shu-ju-ku-gai-nian/hashdata-shu-ju-ku-de-bing-fa-kong-zhi/guan-li-shi-wu-id-de-li-zi.md)
    * [平行数据加载](hashdata-shu-ju-ku-gai-nian/guan-yu-ping-xing-shu-ju-jia-zai.md)
    * [HashData 数据库冗余和容错](hashdata-shu-ju-ku-gai-nian/hashdata-shu-ju-ku-zhong-rong-yu-he-gu-zhang-zhuan-yi.md)
    * [HashData 数据库统计信息](hashdata-shu-ju-ku-gai-nian/hashdata-shu-ju-ku-zhong-guan-yu-shu-ju-ku-tong-ji-shu-ju.md)
  * [HashData 数据库系统管理](hashdata-xi-tong-guan-li.md)
    * [启动和停止 HashData 数据库](hashdata-xi-tong-guan-li/qi-dong-he-ting-zhi-hashdata-shu-ju-ku.md)
    * [访问 HashData 数据库](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku.md)
      * [创建数据库会话](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/jian-li-yi-ge-shu-ju-ku-hui-hua.md)
      * 支持的客户端应用程序
      * [HashData 数据库客户端应用程序](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/hashdatashu-ju-ku-ke-hu-duan-ying-yong-cheng-xu.md)
      * 使用 psql 连接 HashData 数据库
      * [HashData 数据库的 pgAdmin III](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/hashdata-shu-ju-ku-de-pgadmin-iii.md)
        * [安装 pgAdmin III](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/hashdata-shu-ju-ku-de-pgadmin-iii/an-zhuang-pgadmin-iii.md)
        * [pgAdmin III 使用文档](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/hashdata-shu-ju-ku-de-pgadmin-iii/pgadmin-iii-wen-dang.md)
        * [使用 pgAdmin III 管理 HashData 数据库](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/hashdata-shu-ju-ku-de-pgadmin-iii/shi-yong-pgadmin-iii-guan-li-hashdata-shu-ju-ku.md)
          * 编辑服务器配置
          * 查看图形化查询计划
      * [使用PgBouncer连接池](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/shi-yong-pgbouncer-lian-jie-chi.md)
      * 数据库应用程序接口
      * 第三方客户端工具
      * [故障诊断连接问题](hashdata-xi-tong-guan-li/fang-wen-shu-ju-ku/gu-zhang-zhen-duan-lian-jie-wen-ti.md)
    * [配置 HashData 数据库系统](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong.md)
      * 关于HashData数据库主节点和本地参数
      * [设置配置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu.md)
        * 设置本地配置参数
        * [设置主节点的配置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu.md)
          * [设置系统级别的参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu/she-zhi-xi-tong-ji-bie-de-can-shu.md)
          * [在数据库级别设置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu/zai-shu-ju-ku-ji-bie-she-zhi-can-shu.md)
          * [在角色级别设置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu/zai-jiao-se-ji-bie-she-zhi-can-shu.md)
          * [在会话级别设置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu/zai-hui-hua-ji-bie-she-zhi-can-shu.md)
      * [查看服务器配置参数设置](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/cha-kan-fu-wu-qi-pei-zhi-can-shu-she-zhi.md)
      * [配置参数种类](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/pei-zhi-can-shu-zhong-lei.md)
        * [连接和授权参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/pei-zhi-can-shu-zhong-lei/lian-jie-he-shou-quan-can-shu.md)
          * 连接参数
          * 安全认证参数
        * [系统资源配置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/pei-zhi-can-shu-zhong-lei/xi-tong-zi-yuan-pei-zhi-can-shu.md)
          * 内存分配参数
          * 空闲空间分布参数
          * OS资源参数
          * 基于代价的Vacuum延迟参数
          * 事务ID管理参数
        * [查询优化参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/pei-zhi-can-shu-zhong-lei/cha-xun-you-hua-can-shu.md)
        * 错误报告及日志参数
        * 系统监控参数
        * 运行统计信息收集参数
        * 自动统计信息收集参数
        * 客户端连接默认参数
        * 锁管理参数
        * 工作负载管理参数
        * 外部表参数
        * 数据库表参数
        * 数据库及表空间/文件空间参数
        * 老PostgreSQL版本兼容参数
        * HashData集群配置参数
        * HashData主节点和计算节点镜像参数
        * HashData数据库扩展参数
    * [启用高可用特性](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing.md)
      * [HashData 数据库高可用特性概述](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/hashdata-shu-ju-ku-gao-ke-yong-te-xing-gai-shu.md)
        * 计算节点镜像概述
        * 主节点镜像概述
        * 错误检测和恢复概述
      * [启用 HashData 数据库镜像](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/qi-yong-hashdata-shu-ju-ku-jing-xiang.md)
        * 启用计算节点镜像
        * 启用主节点镜像
      * [检测失败节点](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/jian-ce-shi-bai-jie-dian.md)
        * 启用警报和通知
        * [检查失败节点](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/jian-ce-shi-bai-jie-dian/jian-cha-shi-bai-de-ji-suan-jie-dian.md)
        * 检查失败节点的日志文件
      * [恢复失败节点](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/hui-fu-shi-bai-jie-dian.md)
        * [从失败节点恢复](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/hui-fu-shi-bai-jie-dian/cong-shi-bai-jie-dian-hui-fu.md)
          * 当一个计算节点主机不可恢复
          * 计算节点恢复进程
      * [恢复失败的主节点](hashdata-xi-tong-guan-li/qi-yong-gao-ke-yong-te-xing/hui-fu-shi-bai-de-zhu-jie-dian.md)
        * 在恢复之后恢复主节点镜像
    * [备份和恢复数据库](hashdata-xi-tong-guan-li/bei-fen-he-hui-fu-shu-ju-ku.md)
      * 备份恢复概述
      * 使用 gpcrondump 备份
      * 备份一组表
      * 创建增量备份
      * 备份进程和锁
      * 使用直接读写
      * 使用命名的管道
      * 用数据域增强备份数据库
      * Veritas NetBackup 备份数据库
      * 恢复 HashData 数据库
      * 使用 gpdbrestore 恢复数据库
      * 恢复到不同的 HashData 系统配置
    * [扩展 HashData 数据库系统](hashdata-xi-tong-guan-li/kuo-zhan-hashdata-shu-ju-ku-xi-tong.md)
      * 系统扩展概述
      * 规划 HashData 数据库系统扩展
      * 准备和添加节点
      * [初始化新的计算节点](hashdata-xi-tong-guan-li/kuo-zhan-hashdata-shu-ju-ku-xi-tong/chu-shi-hua-xin-de-ji-suan-jie-dian.md)
      * [重分布表](hashdata-xi-tong-guan-li/kuo-zhan-hashdata-shu-ju-ku-xi-tong/zhong-fen-bu-biao.md)
      * [移除扩展模式](hashdata-xi-tong-guan-li/kuo-zhan-hashdata-shu-ju-ku-xi-tong/yi-chu-kuo-zhan-mo-shi.md)
    * 使用 gptransfer 迁移数据
    * 监控 HashData 数据库系统
    * [日常系统维护任务](hashdata-xi-tong-guan-li/ri-chang-xi-tong-wei-hu-ren-wu.md)
    * [建议的监控和维护任务](hashdata-xi-tong-guan-li/jian-yi-de-jian-kong-he-wei-hu-ren-wu.md)
  * [HashData 数据库访问管理](hashdata-guan-li-shu-ju-ku-fang-wen.md)
    * [配置客户端认证](hashdata-guan-li-shu-ju-ku-fang-wen/pei-zhi-ke-hu-duan-ren-zheng.md)
      * 通过 TLS/SSL 使用 LDAP 认证
      * 使用 Kerberos 认证
      * 为 Windows  客户端配置 Kerberos
    * 管理角色和权限
    * 为 HashData 数据库配置 IPsec
  * [使用 HashData 数据库](gong-zuo-yu-shu-ju-ku.md)
    * [定义数据库对象](gong-zuo-yu-shu-ju-ku/ding-yi-shu-ju-ku-dui-xiang.md)
      * 创建和管理数据库
      * 创建和管理表空间
      * 创建和管理用户模式
      * 创建和管理表
      * 选择表存储模式
      * 分区大表
      * 创建和使用序列
      * 在 HashData 数据库中使用索引
      * 创建和管理视图
    * 管理数据
    * [加载卸载数据](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju.md)
      * [使用基于文件的外部表](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/shi-yong-ji-yu-wen-jian-de-wai-bu-biao.md)
        * 访问基于文件的外部表
        * file:// 协议
        * gpfdist:// 协议
        * gpfdists:// 协议
        * gphdfs:// 协议
        * s3:// 协议
        * 使用用户协议
        * 处理外部表数据错误
      * [使用 HashData 并行文件服务（gpfdist）](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/shi-yong-hashdata-bing-xing-wen-jian-fu-wu-ff08-gpfdist.md)
        * gpfdist 启动和性能优化
        * 控制节点并行
        * 安装 gpfdist
        * 启动停止 gpfdist
        * 分析 gpfdist 的问题
      * [使用 Hadoop Distributed File System \(HDFS\) 表](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/shi-yong-hadoop-distributed-filesystem-hdfs-biao.md)
        * 一次安装 HDFS 协议
          * 给 HDFS 协议分配权限
          * [在外部表定义中指定 HDFS 数据](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/shi-yong-hadoop-distributed-filesystem-hdfs-biao/zai-wai-bu-biao-ding-yi-zhong-zhi-ding-hdfs-shu-ju.md)
            * 给 Hadoop 可写外部表设置压缩选项
          * HDFS 可读写外部表示例
          * 读写客户化 HDFS 数据
          * MapReduce 代码样例
            * 运行 CREATE EXTERNAL TABLE
          * 从 HashData 数据库读取数据客户化写入 HDFS
          * MapReduce 样例代码
        * gphdfs JVM 内存
        * 通过在 AWS 上安装 HashData 数据库使用 Amazon EMR
        * Avro 文件支持
        * Parquet 文件支持
      * [创建和使用 Web 外部表](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/chuang-jian-he-shi-yong-web-wai-bu-biao.md)
        * 基于指令的 Web 外部表
        * 基于 URL 的 Web 外部表
      * 使用外部表加载数据
      * [加载和写入 Non-HDFS 用户数据](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/jia-zai-he-xie-ru-non-hdfs-yong-hu-shu-ju.md)
        * [使用客户化格式](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/jia-zai-he-xie-ru-non-hdfs-yong-hu-shu-ju/shi-yong-ke-hu-hua-ge-shi.md)
          * 导入导出固定宽度数据
          * 示例：读取固定宽度数据
        * 使用客户化协议
      * [创建外部表 - 示例](gong-zuo-yu-shu-ju-ku/jia-zai-xie-zai-shu-ju/chuang-jian-wai-bu-biao-shi-li.md)
        * 示例一：单网卡机器单 gpfdist 实例
        * 示例二：多 gpfdist 实例
      * 处理加载错误
      * 使用 gpload 加载数据
      * 使用 COPY 加载数据
      * 在单行模式隔离模式下运行 COPY
      * 优化数据加载和查询性能
      * 从 HashData 卸载数据
      * 转换 XML 数据
      * 格式化数据文件
      * 示例自定义数据访问协议
    * 查询数据
  * [HashData 数据库性能管理](guan-li-ji-xiao.md)

