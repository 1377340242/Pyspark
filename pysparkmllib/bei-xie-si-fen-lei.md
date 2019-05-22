> ### 贝叶斯模型

```py
from pyspark.mllib.classification import NaiveBayes,NaiveBayesModel
model = NaiveBayes.train(data, lambda_=1.0)
#参数：
data：LabeledPointl类型的RDD训练数据
lambda_:平滑系数，值越小过拟合较厉害，值越大，欠拟合越厉害。
```

方法：

1.predict\(x\):使用训练模型预测单个数据点或点的RDD的值,如何为单个数据点则输出为int型的类别，否则为RDD类型。

2.save\( sc, path\)：将模型保存到path（保存的是一个文件夹）

```py
model.save(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/model')
```

3.load\( sc, path\)：类方法载入保存的模型文件夹

```py
from pyspark.mllib.classification import SVMModel
clf=SVMModel.load(sc,path='file:/home/liuzhan/pythonwork/ipynotebook/model')
```



