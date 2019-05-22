#### 1.支持向量机分类模型

```py
from pyspark.mllib.classification import SVMWithSGD
#构建模型的方法
svm=SVMWithSGD.train(data, iterations=100, step=1.0, regParam=0.01,
              miniBatchFraction=1.0, initialWeights=None, regType="l2",
              intercept=False, validateData=True, convergenceTol=0.001)
#参数：
data:LabeledPointl类型的RDD训练数据
iterations:迭代次数
step：SGD迭代步长（应该是学习率）
regParam：正则化系数
miniBathFraction:批量大小(0,1]
initialWeights:初始化的权重
regType:正则化类型（l1,l2，None）
intercept：是否使用偏置特征，bool类型，默认False
validationData：布尔参数，指示算法是否应在训练前验证数据
convergenceTol - 决定迭代终止的条件
#返回：
pyspark.mllib.classification.SVMModel
```

方法：

1.predict\(x\):使用训练模型预测单个数据点或点的RDD的值,如何为单个数据点则输出为int型的类别，否则为RDD类型。

2.save\( sc, path\)：将模型保存到path（保存的是一个文件夹）

```py
svm.save(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/svm.h5')
```

3.load\( sc, path\)：类方法载入保存的模型文件夹

```py
from pyspark.mllib.classification import SVMModel
clf=SVMModel.load(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/svm.h5')
```



