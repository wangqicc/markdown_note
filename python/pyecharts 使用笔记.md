[TOC]

### 1. pyecharts 安装 & 简介

> **windows 命令行下使用：** `pip install pyecharts`

> **简介：** 百度开源，使用图表使得数据可视化的库，所能绘制的图表参照参考文档所述

### 2. pyecharts 条形图 & 饼图 & 折线图基本使用

```python
# 从 pyecharts.charts 中导入所要绘制的图表类型
from pyecharts.charts import Bar
from pyecharts.charts import Pie
from pyecharts.charts import Line
from pyecharts.render import make_snapshot

# 导入全局配置，其中 as 相当于重命名
from pyecharts import options as opts

# 使用 snapshot_phantomjs 渲染图片，产生无背景图片
from snapshot_phantomjs import snapshot

# 读取 csv 文件
import csv

# 相关的数据信息
difficulty = ["Easy", "Medium", "Hard"]
count = [0, 0, 0]

# 从 csv 文件中读取数据信息
csvFile = open("C:/Users/wangqi/Desktop/leetcode.csv", 'r')
reader = csv.reader(csvFile)

# 使用 flag 去除 csv 文件中的标题行
flag = True
for item in reader:
	if flag == True:
		flag = False
		continue
	if item[2] == "Easy":
		count[0] += 1
	elif item[2] == "Medium":
		count[1] += 1
	elif item[2] == "Hard":
		count[2] += 1
	else:
		pass

# 条形图
bar = (
	Bar()
	.add_xaxis(difficulty)
	# 使用 is_stack = True 可以设置堆叠显示
	.add_yaxis("题目数量", count)
	.reversal_axis()
	# 全局配置项
	.set_global_opts(
		# title_opts = opts.TitleOpts(title = "LeetCode 题目难度分析")
		# 可以直接使用字典参数
		title_opts = {"text": "LeetCode 题目难度分析", "subtext": "条形图"}
	)
	# 系列配置项
	.set_series_opts(
		label_opts = opts.LabelOpts(position = "right")
	)
)

# 饼图
pie = (
	Pie()
	.add("", [list(z) for z in zip(difficulty, count)])
	.set_global_opts(title_opts = opts.TitleOpts(title = "LeetCode 题目难度分析"))
	.set_series_opts(label_opts = opts.LabelOpts(formatter = "{b}: {c}"))
)

# 折线图
line = (
	Line()
	.add_xaxis(difficulty)
	# is_smooth 设置曲线是否光滑
	.add_yaxis("题目数量", count, is_smooth = True)
	.set_global_opts(title_opts = opts.TitleOpts(title = "LeetCode 题目难度分析"))
)

# 使用 render() 函数生成本地的 html 文件，默认在当前文件夹中生成 render.html 文件
# 也可以传入参数，如 pie.render("文件路径")，在指定位置生成 html 文件
# bar.render()
# pie.render()
# line.render()
# make_snapshot() 函数有三个参数，最后一个参数是图片路径，生成无背景图片
make_snapshot(snapshot, pie.render(), "C:/Users/wangqi/Desktop/LeetCode 题目难度分析.png")
```



### 参考文档

1. [A Python Echarts Plotting Library.](https://pyecharts.org/#/)