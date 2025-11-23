# 植物幼苗分类

本仓库包含一个用于将植物幼苗分类为12个类别的卷积神经网络实现。
有效地进行分类意味着更好的作物产量和更好的环境管理。

<div align=center><img src="./img/plants.png"/></div>

## 数据集

本项目使用来自Kaggle上[植物幼苗分类](https://www.kaggle.com/c/plant-seedlings-classification)竞赛的数据。
<br>
奥胡斯大学信号处理小组与南丹麦大学合作，发布了一个数据集，
包含约960株独特植物的图像，这些植物属于12个物种，处于不同的生长阶段。
数据集包括带注释的RGB图像，物理分辨率约为每毫米10像素。
总共有4750张图像。

## 技术栈

本项目使用的技术：
- Python 3.5+
- [Pytorch](http://pytorch.org/)
- [Imbalanced-learn](https://imbalanced-learn.readthedocs.io/en/stable/api.html)

## 类别不平衡问题

<div align=center><img src="./img/imb.png"/></div>

从上图可以看出，图像的分布不均匀，类别分布从最多654张图像到最少221张图像不等。
这清楚地表明数据是不平衡的，需要平衡数据才能获得最佳结果。

## SMOTE：合成少数类过采样技术

为了获得平衡的数据集，使用了[SMOTE](https://jair.org/index.php/jair/article/view/10302/24590)技术。
这涉及对少数类进行过采样和对多数类进行欠采样，以获得最佳结果。
使用该技术生成了2487张合成图像，使训练集的图像总数达到7237张。

## 结果

- 未使用过采样的基础模型在验证集上达到了94.19%的准确率，在Kaggle公开排行榜上的平均F分数为0.89420。
  - 运行 `base_model.ipynb`

- 使用过采样来平衡数据集的模型在验证集上达到了97.15%的准确率，在Kaggle公开排行榜上的平均F分数为0.97732。
  - 运行 `model_balanced.ipynb`
