# Spark定义：

Spark是一个快速通用的集群计算平台

# Spark的核心：

每个spark应用都是由一个**驱动器程序**来发起集群上的各种并行操作，驱动器程序通过SparkContext对象来访问spark，SparkContext是对计算集群的连接，是Spark功能的主要入口。

总结：Spark 编程的核心概念： 通过一个**驱动器程序**创建一个** SparkContext 和一系列 RDD**， 然后进行**并行操作**



