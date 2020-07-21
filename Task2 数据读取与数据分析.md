# <font face="黑体">Task2 数据读取与数据分析</font>

## 学习目标
- 学习使用Pandas读取赛题数据
- 分析赛题数据的分布规律

## 数据读取
赛题数据储存在csv文件中，可使用pandas中的read_csv函数读取数据
由于训练集共20w数据，全部读入会占用大量内存，会影响之后的代码运行，因此只读入前100条。<br>
./为相对路径，表示在当前文件夹中，而../表示在上一级文件夹中。<br>
代码如下：
```python
import pandas as pd
train_df = pd.read_csv('./train_set.csv/train_set.csv', sep='\t', nrows=100)
```


