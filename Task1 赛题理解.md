# Task1 赛题理解 

## 学习目标
- 理解赛题背景与赛题数据
- 完成赛题报名和数据下载，理解赛题的解题思路

## 赛题背景
[天池大赛：零基础入门NLP - 新闻文本分类闻文本分类](https://tianchi.aliyun.com/competition/entrance/531810/introduction?spm=5176.12281973.1005.1.3dd51f54YfiseM) </br>
- 根据匿名处理后的新闻数据(text)对新闻进行分类(label)，共14种类别
- 了解各种特征工程和评测标准(F1)
- 了解各种NLP数据科学库、Baseline方案和从0到1打比赛通用流程

## 赛题数据
- 训练集共20w条数据，测试集A共5w条数据，测试集B共5w条数据
- 训练集共两个变量：label和text </br>
  1. label：共有14个取值，分别为14个分类类别：
  ``` c++
  {'科技': 0, '股票': 1, '体育': 2, '娱乐': 3, '时政': 4, '社会': 5, '教育': 6, '财经': 7, '家居': 8, '游戏': 9, '房产': 10, '时尚': 11, '彩票': 12, '星座': 13}
  ```
  2. text：通过收集并字符级别匿名处理得到互联网上的新闻</br>

## 数据读取
``` python3
train_df=pd.read_csv('./train_set.csv/train_set.csv',sep='\t')
train_df.head()
```

## 评价指标
  f1_score：[原理](https://blog.csdn.net/qq_14997473/article/details/82684300)、[sklearn中的使用方法](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html#sklearn.metrics.f1_score)


## 解题思路
赛题思路分析：对匿名字符进行建模，进而完成文本分类的过程。由于文本数据是一种典型的非结构化数据，因此可能涉及到特征提取和分类模型两个部分。</br>
- 1.思路一：TF-IDF+机器学习分类器 </br>
    TF-IDF：[TF-IDF原理及使用](https://blog.csdn.net/zrc199021/article/details/53728499) </br>
    机器学习分类器：[SVM](https://www.jb51.net/article/131580.htm)、[LR](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html#sklearn.linear_model.LogisticRegression)或者[XGBoost](https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/)

- 2.思路二：FastText</br>
    [fastText原理](https://zhuanlan.zhihu.com/p/32965521)、[fastText实战](https://zhuanlan.zhihu.com/p/32965521)

- 3.思路三：WordVec+深度学习分类器</br>
    WordVec:</br>
    [word2vec 中的数学原理详解](https://www.cnblogs.com/peghoty/p/3857839.html)、[word2vec的安装与使用](https://www.jianshu.com/p/4714b46f207c)、[word2vec在python中的使用](https://nbviewer.jupyter.org/github/danielfrg/word2vec/blob/master/examples/word2vec.ipynb)</br>
    深度学习分类的网络结构：</br>
    TextCNN：[文本分类算法TextCNN原理详解(一)](https://www.cnblogs.com/ModifyRong/p/11319301.html)、[pytorch实现textCNN](https://blog.csdn.net/qq_25037903/article/details/85058217)、[基于tensorflow的代码实现](https://blog.csdn.net/John_xyz/article/details/79210088)</br>
    TextRNN:[TextRNN用于文本分类](https://www.jianshu.com/p/19fd7206f070)</br>
    BiLSTM:[BiLSTM介绍及代码实现](https://www.jiqizhixin.com/articles/2018-10-24-13)

- 4.思路四：Bert词向量</br>
    [BERT中的词向量指南](https://blog.csdn.net/u011984148/article/details/99921480)
