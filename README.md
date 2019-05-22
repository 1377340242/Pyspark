## Spark定义：

Spark是一个快速通用的集群计算平台

# Spark的核心：

每个spark应用都是由一个**驱动器程序**来发起集群上的各种并行操作，驱动器程序通过SparkContext对象来访问spark，SparkContext是对计算集群的连接，是Spark功能的主要入口。

总结：Spark 编程的核心概念： 通过一个**驱动器程序**创建一个** SparkContext 和一系列 RDD**， 然后进行**并行操作**

## 配置：

**SparkConf\(\)：设置Spark的一些配置的类。**

主要方法：

setAppName\(value\):value&gt;str

set\("spark.ui.showConsoleProgress", "false"\)：不显示Spark执行进度。

**SparkCount\(\):spark应用程序入口**

主要参数：

master：集群的的URL， mesos://host:port, spark://host:port, local\[4\]

conf：配置信息，SparkConf\(\)对象

应用：

```py
def SetLogger( sc ):
    logger = sc._jvm.org.apache.log4j
    logger.LogManager.getLogger("org"). setLevel( logger.Level.ERROR )
    logger.LogManager.getLogger("akka").setLevel( logger.Level.ERROR )
    logger.LogManager.getRootLogger().setLevel(logger.Level.ERROR)    

def SetPath(sc):
    global Path
    if sc.master[0:5]=="local" :
        Path="file:/home/liuzhan/pythonwork/ipynotebook/"
    else:   
        Path="hdfs://master:9000/user/liuzhan/"
#如果要在cluster模式运行(hadoop yarn 或Spark Stand alone)，请按照书上的说明，先把文件上传到HDFS目录

def CreateSparkContext():
    sparkConf = SparkConf()                                                       \
                         .setAppName("RunDecisionTreeBinary")                         \
                         .set("spark.ui.showConsoleProgress", "false") 
    sc = SparkContext(conf = sparkConf)
    print ("master="+sc.master)    
    SetLogger(sc)
    SetPath(sc)
    return (sc)
```







