> #### 决策树模型：

```py
from pyspark.mllib.tree import DecisionTree,DecisionTreeModel
#使用方法：
model=DecisionTree.trainClassifier(data, numClasses, categoricalFeaturesInfo,
                        impurity="gini", maxDepth=5, maxBins=32, minInstancesPerNode=1,
                        minInfoGain=0.0)
#参数：
data:LabeledPointl类型的RDD训练数据
numClasses：类别个数。
categoricalFeaturesInfo：分类特征字典，主要用于将分类特征转化为数值特征。{“特征1”：0，“特征2”：1}
impurity：决策树计算方法，gini基尼系数，entropy信息熵。
maxDepth：决策胡最大深度
maxBins：每个分支最大节点
minInstancesPerNode：创建子节点的最小实例（样本）数目
minInfoGain：创建拆分所需的最小信息增益。
#返回：
DecisionTreeModel。
```

方  
法：

1.predict\(x\):使用训练模型预测单个数据点或点的RDD的值,如何为单个数据点则输出为int型的类别，否则为RDD类型。

2.numNodes\(\)：返回节点的数量。

3.depth\(\)：决策树的深度。

4.toDebugString\(\)：决策树图。

5.save\( sc, path\)：将模型保存到path（保存的是一个文件夹）

```py
model.save(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/model')
```

6.load\( sc, path\)：类方法载入保存的模型文件夹

```py
from pyspark.mllib.classification import SVMModel
clf=SVMModel.load(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/model')
```



