---
title: pandas_readcsv_tocsv
date: 2019-11-27 23:58:25
tags:
- python
- pandas
- 数据处理
categories:
- Python
mathjax:false
---

简单记录以下使用python处理空气质量数据的摸索过程。

## 获取研究区所有地面监测站点信息

这个步需要 解决：

1. 对csv文本文件的读取；
2. 对csv文本文件特定的行数据进行筛选；
3. 对筛选出来的数据进行合并；

其实合并这一步可以使用更合适的筛选条件来完成

- 此例表示使用`read_csv`和`to_csv`对文本文件进行读写

```python
#!/usr/bin/env python3
import sys
import pandas as pd

input_file = "D:/PycharmProjects/DataProcess/testdata.csv"
output_file = "D:/PycharmProjects/DataProcess/testdata_out.csv"
data_frame = pd.read_csv(input_file)
print(data_frame)
data_frame.to_csv(output_file, index=False)
```
- 此例表示使用`loc`对某列满足一定条件的所有行进行抽取

```python
#!/usr/bin/env python3
import sys
import pandas as pd

input_file = "D:/PycharmProjects/DataProcess/testdata.csv"
output_file = "D:/PycharmProjects/DataProcess/testdata_out.csv"
data_frame = pd.read_csv(input_file)
data_frame_value_meet_condition = data_frame.loc[(data_frame['城市'].str.contains('北京')), :]
print(data_frame_value_meet_condition)
data_frame_value_meet_condition.to_csv(output_file, index=False)
```
- 此例表示利用`??`对`loc`抽取过单独保存的各个`.csv`文件进行合并
  - 可以参考以下文章：<https://blog.csdn.net/weixin_42338058/article/details/83869146> 
  - os.path.join(path1, path2, ...) 
  - glob.glob(pathname) 用法

```python
#!/usr/bin/env python3
import sys
import pandas as pd
import glob
import os

input_file = "D:/PycharmProjects/DataProcess/testdata.csv"
output_file1 = "D:/PycharmProjects/DataProcess/beijingsite_out.csv"
output_file2 = "D:/PycharmProjects/DataProcess/tianjinsite_out.csv"
output_file3 = "D:/PycharmProjects/DataProcess/mergeofsite_out.csv"
data_frame = pd.read_csv(input_file)
#data_frame['Cost'] = data_frame['Cost'].str.strip('$').astype(float)
#data_frame_value_meets_condition = data_frame.log[data_frame['supplier Name'].str.contains('Z')|(data_frame['Cost'] > 600.0), :]
data_frame_value_meet_condition1 = data_frame.loc[(data_frame['城市'].str.contains('北京')), :]
data_frame_value_meet_condition2 = data_frame.loc[(data_frame['城市'].str.contains('天津')), :]
print(data_frame_value_meet_condition1)
data_frame_value_meet_condition1.to_csv(output_file1, index=False)
data_frame_value_meet_condition2.to_csv(output_file2, index=False)

#all_files = glob.glob(os.path.join(input_file, 'sales_*'）
all_files = glob.glob(os.path.join(input_file))
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file3, index=False)
```


```python
#!/usr/bin/env python3
import sys
import pandas as pd
import glob
import os

input_file = "D:/PycharmProjects/DataProcess/站点列表-2018.11.08起.csv"
output_file1 = "D:/PycharmProjects/DataProcess/河南site/郑州site_out.csv"
output_file2 = "D:/PycharmProjects/DataProcess/河南site/开封site_out.csv"
output_file3 = "D:/PycharmProjects/DataProcess/河南site/洛阳site_out.csv"
output_file4 = "D:/PycharmProjects/DataProcess/河南site/平顶山site_out.csv"
output_file5 = "D:/PycharmProjects/DataProcess/河南site/安阳site_out.csv"
output_file6 = "D:/PycharmProjects/DataProcess/河南site/鹤壁site_out.csv"
output_file7 = "D:/PycharmProjects/DataProcess/河南site/新乡site_out.csv"
output_file8 = "D:/PycharmProjects/DataProcess/河南site/焦作site_out.csv"
output_file9 = "D:/PycharmProjects/DataProcess/河南site/濮阳site_out.csv"
output_file10 = "D:/PycharmProjects/DataProcess/河南site/许昌site_out.csv"
output_file11 = "D:/PycharmProjects/DataProcess/河南site/漯河site_out.csv"
output_file12 = "D:/PycharmProjects/DataProcess/河南site/三门峡site_out.csv"
output_file13 = "D:/PycharmProjects/DataProcess/河南site/南阳site_out.csv"
output_file14 = "D:/PycharmProjects/DataProcess/河南site/商丘site_out.csv"
output_file15 = "D:/PycharmProjects/DataProcess/河南site/信阳site_out.csv"
output_file16 = "D:/PycharmProjects/DataProcess/河南site/周口site_out.csv"
output_file17 = "D:/PycharmProjects/DataProcess/河南site/驻马店site_out.csv"
output_file18 = "D:/PycharmProjects/DataProcess/河南site/济源site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/巩义site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/兰考site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/汝州site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/滑县site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/长垣site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/邓州site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/永城site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/固始site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/鹿邑site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/新蔡site_out.csv"
output_file19 = "D:/PycharmProjects/DataProcess/河南site/mergeofsite_out.csv"
data_frame = pd.read_csv(input_file)
#data_frame['Cost'] = data_frame['Cost'].str.strip('$').astype(float)
#data_frame_value_meets_condition = data_frame.log[data_frame['supplier Name'].str.contains('Z')|(data_frame['Cost'] > 600.0), :]
data_frame_value_meet_condition1 = data_frame.loc[(data_frame['城市'].str.contains('郑州')), :]
data_frame_value_meet_condition2 = data_frame.loc[(data_frame['城市'].str.contains('开封')), :]
data_frame_value_meet_condition3 = data_frame.loc[(data_frame['城市'].str.contains('洛阳')), :]
data_frame_value_meet_condition4 = data_frame.loc[(data_frame['城市'].str.contains('平顶山')), :]
data_frame_value_meet_condition5 = data_frame.loc[(data_frame['城市'].str.contains('安阳')), :]
data_frame_value_meet_condition6 = data_frame.loc[(data_frame['城市'].str.contains('鹤壁')), :]
data_frame_value_meet_condition7 = data_frame.loc[(data_frame['城市'].str.contains('新乡')), :]
data_frame_value_meet_condition8 = data_frame.loc[(data_frame['城市'].str.contains('焦作')), :]
data_frame_value_meet_condition9 = data_frame.loc[(data_frame['城市'].str.contains('濮阳')), :]
data_frame_value_meet_condition10 = data_frame.loc[(data_frame['城市'].str.contains('许昌')), :]
data_frame_value_meet_condition11 = data_frame.loc[(data_frame['城市'].str.contains('漯河')), :]
data_frame_value_meet_condition12 = data_frame.loc[(data_frame['城市'].str.contains('三门峡')), :]
data_frame_value_meet_condition13 = data_frame.loc[(data_frame['城市'].str.contains('南阳')), :]
data_frame_value_meet_condition14 = data_frame.loc[(data_frame['城市'].str.contains('商丘')), :]
data_frame_value_meet_condition15 = data_frame.loc[(data_frame['城市'].str.contains('信阳')), :]
data_frame_value_meet_condition16 = data_frame.loc[(data_frame['城市'].str.contains('周口')), :]
data_frame_value_meet_condition17 = data_frame.loc[(data_frame['城市'].str.contains('驻马店')), :]
data_frame_value_meet_condition18 = data_frame.loc[(data_frame['城市'].str.contains('济源')), :]
print(data_frame_value_meet_condition1)
data_frame_value_meet_condition1.to_csv(output_file1, index=False)
data_frame_value_meet_condition2.to_csv(output_file2, index=False)
data_frame_value_meet_condition3.to_csv(output_file3, index=False)
data_frame_value_meet_condition4.to_csv(output_file4, index=False)
data_frame_value_meet_condition5.to_csv(output_file5, index=False)
data_frame_value_meet_condition6.to_csv(output_file6, index=False)
data_frame_value_meet_condition7.to_csv(output_file7, index=False)
data_frame_value_meet_condition8.to_csv(output_file8, index=False)
data_frame_value_meet_condition9.to_csv(output_file9, index=False)
data_frame_value_meet_condition10.to_csv(output_file10, index=False)
data_frame_value_meet_condition11.to_csv(output_file11, index=False)
data_frame_value_meet_condition12.to_csv(output_file12, index=False)
data_frame_value_meet_condition13.to_csv(output_file13, index=False)
data_frame_value_meet_condition14.to_csv(output_file14, index=False)
data_frame_value_meet_condition15.to_csv(output_file15, index=False)
data_frame_value_meet_condition16.to_csv(output_file16, index=False)
data_frame_value_meet_condition17.to_csv(output_file17, index=False)
data_frame_value_meet_condition18.to_csv(output_file18, index=False)

#all_files = glob.glob(os.path.join(input_file, 'sales_*'）
all_files = glob.glob(os.path.join(input_file，))
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file19, index=False)
```
前面两个程序合并失败了，主要是这个语句：`all_files = glob.glob(os.path.join(input_file，))`用错了正确的如下：

```python
#!/usr/bin/env python3
import sys
import pandas as pd
import glob
import os

input_file = "D:/PycharmProjects/DataProcess/testdata.csv"
output_file1 = "D:/PycharmProjects/DataProcess/beitian/beijingsite_out.csv"
output_file2 = "D:/PycharmProjects/DataProcess/beitian/tianjinsite_out.csv"
output_file3 = "D:/PycharmProjects/DataProcess/beitian/mergeofsite_out.csv"
data_frame = pd.read_csv(input_file)
#data_frame['Cost'] = data_frame['Cost'].str.strip('$').astype(float)
#data_frame_value_meets_condition = data_frame.log[data_frame['supplier Name'].str.contains('Z')|(data_frame['Cost'] > 600.0), :]
data_frame_value_meet_condition1 = data_frame.loc[(data_frame['城市'].str.contains('北京')), :]
data_frame_value_meet_condition2 = data_frame.loc[(data_frame['城市'].str.contains('天津')), :]
print(data_frame_value_meet_condition1)
data_frame_value_meet_condition1.to_csv(output_file1, index=False)
data_frame_value_meet_condition2.to_csv(output_file2, index=False)

#all_files = glob.glob(os.path.join(input_file, 'sales_*'）
input_path = "D:/PycharmProjects/DataProcess/beitian"
all_files = glob.glob(os.path.join(input_path, '*.csv'))
print(all_files)
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file3, index=False)
```



```python
#!/usr/bin/env python3
import sys
import pandas as pd
import glob
import os

input_file = "D:/PycharmProjects/DataProcess/站点列表-2018.11.08起.csv"
output_file1 = "D:/PycharmProjects/DataProcess/河南site/郑州site_out.csv"
output_file2 = "D:/PycharmProjects/DataProcess/河南site/开封site_out.csv"
output_file3 = "D:/PycharmProjects/DataProcess/河南site/洛阳site_out.csv"
output_file4 = "D:/PycharmProjects/DataProcess/河南site/平顶山site_out.csv"
output_file5 = "D:/PycharmProjects/DataProcess/河南site/安阳site_out.csv"
output_file6 = "D:/PycharmProjects/DataProcess/河南site/鹤壁site_out.csv"
output_file7 = "D:/PycharmProjects/DataProcess/河南site/新乡site_out.csv"
output_file8 = "D:/PycharmProjects/DataProcess/河南site/焦作site_out.csv"
output_file9 = "D:/PycharmProjects/DataProcess/河南site/濮阳site_out.csv"
output_file10 = "D:/PycharmProjects/DataProcess/河南site/许昌site_out.csv"
output_file11 = "D:/PycharmProjects/DataProcess/河南site/漯河site_out.csv"
output_file12 = "D:/PycharmProjects/DataProcess/河南site/三门峡site_out.csv"
output_file13 = "D:/PycharmProjects/DataProcess/河南site/南阳site_out.csv"
output_file14 = "D:/PycharmProjects/DataProcess/河南site/商丘site_out.csv"
output_file15 = "D:/PycharmProjects/DataProcess/河南site/信阳site_out.csv"
output_file16 = "D:/PycharmProjects/DataProcess/河南site/周口site_out.csv"
output_file17 = "D:/PycharmProjects/DataProcess/河南site/驻马店site_out.csv"
output_file18 = "D:/PycharmProjects/DataProcess/河南site/济源site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/巩义site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/兰考site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/汝州site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/滑县site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/长垣site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/邓州site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/永城site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/固始site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/鹿邑site_out.csv"
# output_file2 = "D:/PycharmProjects/DataProcess/河南site/新蔡site_out.csv"
output_file19 = "D:/PycharmProjects/DataProcess/河南site/mergeofsite_out.csv"
data_frame = pd.read_csv(input_file)
#data_frame['Cost'] = data_frame['Cost'].str.strip('$').astype(float)
#data_frame_value_meets_condition = data_frame.log[data_frame['supplier Name'].str.contains('Z')|(data_frame['Cost'] > 600.0), :]
data_frame_value_meet_condition1 = data_frame.loc[(data_frame['城市'].str.contains('郑州')), :]
data_frame_value_meet_condition2 = data_frame.loc[(data_frame['城市'].str.contains('开封')), :]
data_frame_value_meet_condition3 = data_frame.loc[(data_frame['城市'].str.contains('洛阳')), :]
data_frame_value_meet_condition4 = data_frame.loc[(data_frame['城市'].str.contains('平顶山')), :]
data_frame_value_meet_condition5 = data_frame.loc[(data_frame['城市'].str.contains('安阳')), :]
data_frame_value_meet_condition6 = data_frame.loc[(data_frame['城市'].str.contains('鹤壁')), :]
data_frame_value_meet_condition7 = data_frame.loc[(data_frame['城市'].str.contains('新乡')), :]
data_frame_value_meet_condition8 = data_frame.loc[(data_frame['城市'].str.contains('焦作')), :]
data_frame_value_meet_condition9 = data_frame.loc[(data_frame['城市'].str.contains('濮阳')), :]
data_frame_value_meet_condition10 = data_frame.loc[(data_frame['城市'].str.contains('许昌')), :]
data_frame_value_meet_condition11 = data_frame.loc[(data_frame['城市'].str.contains('漯河')), :]
data_frame_value_meet_condition12 = data_frame.loc[(data_frame['城市'].str.contains('三门峡')), :]
data_frame_value_meet_condition13 = data_frame.loc[(data_frame['城市'].str.contains('南阳')), :]
data_frame_value_meet_condition14 = data_frame.loc[(data_frame['城市'].str.contains('商丘')), :]
data_frame_value_meet_condition15 = data_frame.loc[(data_frame['城市'].str.contains('信阳')), :]
data_frame_value_meet_condition16 = data_frame.loc[(data_frame['城市'].str.contains('周口')), :]
data_frame_value_meet_condition17 = data_frame.loc[(data_frame['城市'].str.contains('驻马店')), :]
data_frame_value_meet_condition18 = data_frame.loc[(data_frame['城市'].str.contains('济源')), :]
print(data_frame_value_meet_condition1)
data_frame_value_meet_condition1.to_csv(output_file1, index=False)
data_frame_value_meet_condition2.to_csv(output_file2, index=False)
data_frame_value_meet_condition3.to_csv(output_file3, index=False)
data_frame_value_meet_condition4.to_csv(output_file4, index=False)
data_frame_value_meet_condition5.to_csv(output_file5, index=False)
data_frame_value_meet_condition6.to_csv(output_file6, index=False)
data_frame_value_meet_condition7.to_csv(output_file7, index=False)
data_frame_value_meet_condition8.to_csv(output_file8, index=False)
data_frame_value_meet_condition9.to_csv(output_file9, index=False)
data_frame_value_meet_condition10.to_csv(output_file10, index=False)
data_frame_value_meet_condition11.to_csv(output_file11, index=False)
data_frame_value_meet_condition12.to_csv(output_file12, index=False)
data_frame_value_meet_condition13.to_csv(output_file13, index=False)
data_frame_value_meet_condition14.to_csv(output_file14, index=False)
data_frame_value_meet_condition15.to_csv(output_file15, index=False)
data_frame_value_meet_condition16.to_csv(output_file16, index=False)
data_frame_value_meet_condition17.to_csv(output_file17, index=False)
data_frame_value_meet_condition18.to_csv(output_file18, index=False)

#all_files = glob.glob(os.path.join(input_file, 'sales_*'）
input_path = "D:/PycharmProjects/DataProcess/河南site"
all_files = glob.glob(os.path.join(input_path, '*site_out.csv'))
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file19, index=True)
```

## 根据监测站点编号获取对应的空气质量指标数据

这一步需要解决的问题是：

1. 对csv文件中指定列进行抽取
2. 遍历所有csv文件抽取所需数据并分别保存
3. 对抽取的数据文件进行合并

- 此例表示使用`loc`对某列的所有行数据进行抽取

```python
  #!/usr/bin/env python3
  import sys
  import pandas as pd
  
  input_file = "D:/PycharmProjects/DataProcess/站点_20180101-20181231/china_sites_20181108.csv"
  output_file = "D:/PycharmProjects/DataProcess/河南air/安阳_20181108_out.csv"
  data_frame = pd.read_csv(input_file)
  data_frame_column_by_name = data_frame.loc[:, ['date', 'hour', 'type', '1818A', '1819A','1820A', '1821A', '1822A', '3141A']]
  data_frame_column_by_name.to_csv(output_file, index=False)
```
-  python 中的`for`循环
```python
print('my name is')
for i in range(5):
    print('Jimmy five times(' + str(i) + ')')
```
输出是
```
my name is
Jimmy five times(0)
Jimmy five times(1)
Jimmy five times(2)
Jimmy five times(3)
Jimmy five times(4)
```
报错：
`KeyError: "None of [Index([...],\n dtype='object')] are in the [columns]"`

- 安阳：
```python
#!/usr/bin/env python3
import sys
import pandas as pd
import os

path1 = "D:/PycharmProjects/DataProcess/站点_20180101-20181231/"
# for i in os.walk(path1):
#     PathArr = i
#     print(PathArr)
files = os.listdir(path1)
for file in files:
    # print(file)
    input_file = "D:/PycharmProjects/DataProcess/站点_20180101-20181231/" + file
    output_file = "D:/PycharmProjects/DataProcess/河南air/安阳/安阳_" + file + "_out.csv"
    data_frame = pd.read_csv(input_file)
    data_frame_column_by_name = data_frame.loc[:, ['date', 'hour', 'type', '1818A', '1819A','1820A', '1821A', '1822A', '3141A']]
    data_frame_column_by_name.to_csv(output_file, index=False)
```

- 最后再根据把安阳市的所有站点的2018年所有数据整合到一起
```python
#!/usr/bin/env python3
import sys
import pandas as pd
import os
import glob

output_file = "D:/PycharmProjects/DataProcess/河南air/河南air_20180101-20181231/安阳/merge2018.csv"
input_path = "D:/PycharmProjects/DataProcess/河南air/河南air_20180101-20181231/安阳"
all_files = glob.glob(os.path.join(input_path, '*_out.csv'))
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file, index=False)
```
- 然后在整合的数据中在抽取，只取出PM2.5的小时变化数据

```
#!/usr/bin/env python3
import sys
import pandas as pd
import os
import glob

# Part0：循环读取2018年365天的安阳的站点数据并按天保存为365个文件
path = "D:/PycharmProjects/DataProcess/site_20180101-20181231/"
# for i in os.walk(path1):
#     PathArr = i
#     print(PathArr)
files = os.listdir(path)
for file in files:
    # print(file)
    input_file = "D:/PycharmProjects/DataProcess/site_20180101-20181231/" + file
    output_file = "D:/PycharmProjects/DataProcess/HNair/HNair_20180101-20181231/AnYang/AnYang_" + file
    data_frame = pd.read_csv(input_file)
    data_frame_column_by_name = data_frame.loc[:, ['date', 'hour', 'type', '1818A', '1819A','1820A', '1821A', '1822A', '3141A']]
    data_frame_column_by_name.to_csv(output_file, index=False)

# Part1：把安阳市的所有站点的2018年所有数据整合到一起
output_file1 = "D:/PycharmProjects/DataProcess/HNair/HNair_20180101-20181231/AnYang/merge2018.csv"
input_path = "D:/PycharmProjects/DataProcess/HNair/HNair_20180101-20181231/AnYang"
all_files = glob.glob(os.path.join(input_path, '*.csv'))
all_data_frames = []
for file in all_files:
    data_frame = pd.read_csv(file, index_col=None)
    all_data_frames.append(data_frame)
data_frame_concat = pd.concat(all_data_frames, axis=0, ignore_index=True)
data_frame_concat.to_csv(output_file1, index=False)

# Part2：从安阳所有站点2018年数据中抽取PM2.5的数据
input_file1 = output_file1
output_file2 = "D:/PycharmProjects/DataProcess/HNair/HNair_20180101-20181231/AnYang/merge2018_PM2.5.csv"
data_frame = pd.read_csv(input_file1)
data_frame_value_meet_condition = data_frame.loc[data_frame['type'] == 'PM2.5', :]
print(data_frame_value_meet_condition)
data_frame_value_meet_condition.to_csv(output_file2, index=False)
```