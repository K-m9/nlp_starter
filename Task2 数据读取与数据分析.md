# <font face="黑体">Task2 数据读取与数据分析</font>

## 学习目标
- 学习使用Pandas读取赛题数据
- 分析赛题数据的分布规律

## 数据读取
赛题数据储存在csv文件中，可使用pandas中的read_csv函数读取数据。<br>
由于训练集共20w数据，全部读入会占用大量内存，会影响之后的代码运行，因此只读入前100条。<br>
./为相对路径，表示在当前文件夹中，而../表示在上一级文件夹中。<br>
代码如下：
```python
import pandas as pd
train_df = pd.read_csv('./train_set.csv/train_set.csv', sep='\t', nrows=100)
train_df.head()
```
| |label|text|
|-|-|-|
|0|2|2967 6758 339 2021 1854 3731 4109 3792 4149 15...|
|1|11|4464 486 6352 5619 2465 4802 1452 3137 5778 54...|
|2|3|7346 4068 5074 3747 5681 6093 1777 2226 7354 6...|
|3|2|7159 948 4866 2109 5520 2490 211 3956 5520 549...|
|4|3|3646 3055 3055 2490 4659 6065 3370 5814 2465 5...|

## 数据分析

### 数据预处理
- 去除指定无用的符号
- 让文本只保留汉字
- 对文本进行jieba分词
- 去除停用词
- 将文本转为tfidf向量并输入到算法中<br>

### 描述性统计
- 1.赛题数据中，新闻文本的长度是多少？
- 2.赛题数据的类别分布是怎么样的，哪些类别比较多？
- 3.赛题数据中，字符分布是怎么样的？

#### 1.句子长度分析
在赛题数据中每行句子的字符使用空格进行隔开，所以可以直接统计单词的个数来得到每个句子的长度。统计并如下：
```python
%pylab inline
train_df['text_len'] = train_df['text'].apply(lambda x: len(x.split(' ')))
print(train_df['text_len'].describe())
```
结果如下：<br>
Populating the interactive namespace from numpy and matplotlib<br>
count    200000.000000<br>
mean        907.207110<br>
std         996.029036<br>
min           2.000000<br>
25%         374.000000<br>
50%         676.000000<br>
75%        1131.000000<br>
max       57921.000000<br>
Name: text_len, dtype: float64<br>
由结果可得出，该20w条新闻平均含907个字符,最短的新闻有2个字符，最长的新闻有57921个字符。<br><br>
绘制直方图分析句子长度分布情况：
```python
_ = plt.hist(train_df['text_len'], bins=200)
plt.xlabel('Text char count')
plt.title("Histogram of char count")
```
![直方图](F:\竞赛\天池\nlp零基础入门\images\直方图.png)

#### 2.新闻类别分布


#### 3.字符分布统计


## 本章作业
- 1.假设字符3750，字符900和字符648是句子的标点符号，请分析赛题每篇新闻平均由多少个句子构成？
- 2.统计每类新闻中出现次数对多的字符

### 1.分析赛题每篇新闻平均由多少个句子构成
```python
all_lines.count('900')+all_lines.count('648')+all_lines.count('3750')
```

### 2.统计每类新闻中出现次数对多的字符
```python
from collections import Counter
for text in train_df.groupby('label').text:
#     print(text)
    all_liness = ''.join(map(str,list(text)))
    word_count = Counter(all_lines.split(" "))
    word_count = sorted(word_count.items(), key=lambda d:d[1], reverse = True) 
    print(word_count[0])
#此代码参考(https://github.com/iooops/Datawhale-NLP-/blob/master/Task2.ipynb)
```
 
