# Summary

* [HashData 数据库管理员指南](README.md)
  * [HashData 数据库概念](hashdata-shu-ju-ku-gai-nian.md)
    * [关于 HashData 架构](hashdata-shu-ju-ku-gai-nian/guan-yu-hashdata-jia-gou.md)
    * [关于管理和监控工具](hashdata-shu-ju-ku-gai-nian/guan-yu-guan-li-he-jian-shi-gong-ju.md)
    * [HashData 数据库的并发控制](hashdata-shu-ju-ku-gai-nian/hashdata-shu-ju-ku-de-bing-fa-kong-zhi.md)
      * 管理事务id的例子
    * 关于平行数据加载
    * HashData 数据库中冗余和故障转移
    * HashData 数据库中关于数据库统计数据
  * [HashData 系统管理](hashdata-xi-tong-guan-li.md)
    * 启动和停止HashData数据库
    * 访问数据库
      * 建立一个数据库会话
      * 支持的客户端应用程序
      * HashData数据库客户端应用程序
      * 使用psql连接
      * 使用PgBouncer连接池
      * 数据库应用程序接口
      * 故障诊断连接问题
    * [配置HashData数据库系统](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong.md)
      * 关于HashData数据库主节点和本地参数
      * [设置配置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu.md)
        * 设置本地配置参数
        * [设置主节点的配置参数](hashdata-xi-tong-guan-li/pei-zhi-hashdata-shu-ju-ku-xi-tong/she-zhi-pei-zhi-can-shu/she-zhi-zhu-jie-dian-de-pei-zhi-can-shu.md)
          * 设置系统级别的参数
          * 在数据库级别设置参数
          * 在角色级别设置参数
          * 在会话级别设置参数
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
    * 启用高可用特性
    * 备份和恢复数据库
    * 扩展HashData系统
    * 使用gptransfer迁移数据
    * HashData系统监控
    * 日常系统维护任务
    * 建议的监控和维护任务
  * HashData 管理数据库访问
  * 工作与数据库
  * 管理绩效

