# Task2 数据读取与数据分析

## 学习目标
- 学习使用Pandas读取赛题数据
- 分析赛题数据的分布规律

## 数据读取
赛题数据储存在csv文件中，可使用pandas中的read_csv函数读取数据
```python
import pandas as pd
train_df = pd.read_csv('./train_set.csv/train_set.csv', sep='\t', nrows=100)
```
