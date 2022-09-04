[TOC]

## python learning

### 1 运算符 & 字符串 & 列表

#### 1.1 除法(/)、整除(//)、取余(%)、幂乘方(**)

```python
# 通过命令行输入
# 除法会返回一个浮点数
>>> 5/3
1.6666666666666667
>>> 5//3
1
>>> 5%2
1
>>> 5**3
125
# 注意 ** 优先级高于 - 号
>>> -5**4
-625
```

#### 1.2 字符串 & 列表

> **注意：** Python 的字符串不可改变

##### 1.2.1 字符串表示 & 输出

```python
# 字符串可以用单引号 '' 或双引号 "" 标识，特殊字符用 \ 来转义
>>> print('first')
first
>>> print("first\name")
first
ame

# 使用原始字符串，在第一个引号之前加上 r 可以原封不动地输出信息
>>> print(r"first\name")
first\name

# 字符串可以多行显示
>>> print('''
... hello
... wieck
... ''')

hello
wieck

# 可以使用反斜杠 \ 来表示下一行是紧接着上一行
>>> print('''\
... hello
... wieck\
... ''')
hello
wieck

# 使用 + 号连接字符串，用 * 号表示重复
>>> 2 * 'hello, ' + 'wieck'
'hello, hello, wieck'

# 相邻两个字符串会自动连接在一起，在切分很长的字符串时很有用
>>> text = ('Rivers know this: there is no hurry. '
... 'We shall get there some day.')
>>> text
'Rivers know this: there is no hurry. We shall get there some day.'
```

##### 1.2.2 字符串索引 & 切片

```python
# python 中有负索引，从后往前计算
>>> word = 'python'
>>> word[0]
'p'
>>> word[-1]
'n'

# python 中的切片，从 : 前面序号开始，到冒号后面序号为止
>>> word[0:2]
'py'
>>> word[2:6]
'thon'
>>> word[:2]
'py'
>>> word[2:]
'thon'
# len() 为 python 内置函数，可以计算字符串长度
>>> len(word[2:])
4
```

##### 1.2.3 列表

> **注意：**
>
> 1. 列表的索引和切片操作和字符串类似
>
> 2. 列表是可变的

```python
# 列表支持两种连接操作，+ 号和 append() 方法
>>> lists = [1, 4, 9, 16, 25]
>>> lists += [36, 49]
>>> lists
[1, 4, 9, 16, 25, 36, 49]
>>> lists.append(64)
>>> lists
[1, 4, 9, 16, 25, 36, 49, 64]
>>> lists.append(9 ** 2)
>>> lists
[1, 4, 9, 16, 25, 36, 49, 64, 81]

# 列表支持改变尺寸，允许嵌套
>>> lists[4:] = []
>>> lists
[1, 4, 9, 16]
>>> lists = [lists, [25]]
>>> lists
[[1, 4, 9, 16], [25]]
```

##### 1.2.4 斐波那契数列（20以内）

```python
# python 中支持多重赋值
# 在 python3 中 print() 为内置函数
a, b = 0, 1
while b < 20:
	print(b, end = " ")
	a, b = b, a + b
print("\n")
```

#### 1.3 直接赋值 & 浅拷贝 & 深拷贝

> **直接赋值：** 对对象的引用
>
> **浅拷贝：** 拷贝父对象，不会拷贝对象的内部子对象，即只拷贝第一层，其余层引用
>
> **深拷贝：** copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象

```python
>>> import copy
>>> e = [1, [2, 3]]
# 直接赋值，引用
>>> a = e
# 浅拷贝，只拷贝第一层，其余层引用。使用 b = e[:] 也可以达到同样效果
>>> b = e.copy()
# 深拷贝，拷贝一份副本
>>> c = copy.deepcopy(e)
>>> e[1].append(4)
>>> e.append(5)
>>> e
[1, [2, 3, 4], 5]
>>> a
[1, [2, 3, 4], 5]
>>> b
[1, [2, 3, 4]]
>>> c
[1, [2, 3]]
```



### 2 流程控制

> **注意：** 
>
> 1. 其中 break & continue 用法和其他语言类似
> 2. python 中增加了一个 pass ，不执行任何操作

#### 2.1 if 语句

> **使用方法：** `if...elif...else`

```python
# if 语句的两种用法
>>> list = ["hello", "wieck"]
>>> if len(list) < 2:
...     print("list length < 2")
... elif len(list) == 2:
...     print("list length: 2")
... else:
...     print("list length > 2")
...
list length: 2

# if 区别于其他语言
>>> if "wieck" in list:
...     print("true")
...
true
```

#### 2.2 for 语句

> **使用方法：** `for item in list`

```python
# 在 python 中 for 按顺序遍历序列中的元素，类似于 java 中的 foreach
>>> list = ["hello", "wieck"]
>>> for item in list:
...     print(item)
...
hello
wieck

# 使用 range() 函数可以生成从 0 开始的等差序列
# range(5) 为 0, 1, 2, 3, 4, 不包括 5
>>> for i in range(2):
...     print(i, list[i])
...
0 hello
1 wieck
```

### 3 数据结构

#### 3.1 列表(list)

> **常用方法：**
>
> 1. `list.append(x)` ：把一个元素添加到列表的结尾，相当于 list[len(list):] = [x]
> 2. `list.extend(L)` ：将列表 L 中的元素添加到 list 中，相当于 list[len(list):] = L
> 3. `list.insert(i, x)` ：在第 i 个位置上插入 x
> 4. `list.remove(x)` ：移除第一个值为 x 的元素
> 5. `list.count(x)` ：返回 x 出现的次数
> 6. `list.clear()` ：清空列表
> 7. `list.index(x)` ：返回列表中第一个值为 x 的元素下标
> 8. `list.sort()` ：对列表中的元素进行排序
> 9. `list.reverse()` ：将列表中的元素倒序
> 10. `list.copy()` ：返回列表的浅拷贝，相当于 list[:]
> 11. `list.pop([i])` ：删除指定位置的元素并返回。如果没有指定索引 i，将删除并返回最后一个元素

#### 3.2 堆栈（列表实现）

> **注意：** 堆栈“后进先出”

```python
>>> stack = [0, 1, 2, 3, 4]
# 入栈使用 list.append() 方法
>>> stack.append(5)
>>> stack
[0, 1, 2, 3, 4, 5]
# 出栈使用 list.pop() 方法
>>> stack.pop()
5
>>> stack
[0, 1, 2, 3, 4]
```

#### 3.3 队列(deque)

> **注意：**
>
> 1. 在 python 中使用队列需要从 collections 中导入 deque
> 2. 使用 collections.deque 可以实现在队列的首尾两端快速插入和删除
> 3. deque 中有 `appendleft(x)` 和 `popleft()` 方法实现在队列头部插入和删除，也可以使用 `append(x)` 和 `pop()` 方法实现在队列尾部插入和删除

```python
>>> from collections import deque
>>> queue = deque(['one', 'two', 'there'])
>>> queue.append('four')
>>> queue
deque(['one', 'two', 'there', 'four'])
>>> queue.popleft()
'one'
>>> queue
deque(['two', 'there', 'four'])
```

#### 3.4 列表推导式 & del 语句

> **含有 if 和 for 语句**

```python
>>> list = [x for x in range(10) if x % 2 == 0]
>>> list
[0, 2, 4, 6, 8]
>>> del list[0]
>>> list
[2, 4, 6, 8]
```

#### 3.5 元组(tuple)

> **常用方法：**
>
> 索引、切片、连接、复制、遍历、是否存在某元素、返回最大值和最小值
>
> **应用场景：**
>
> 坐标对、数据库中员工记录
>
> **注意：** 元组是不可变的

```python
>>> tuple = ['hello', 'wangzhi']
>>> 'hello' in tuple
True
>>> max(tuple)
'wangzhi'
>>> min(tuple)
'hello'
```

#### 3.6 集合(set)

> **常用方法：**
>
> 1. `set()` ：产生一个空集合
> 2. `add(elem)` ：添加元素到集合中
> 3. `remove()` ：从集合中移除元素
> 4. `pop()` ：将集合中的元素出栈
> 5. `clear()` ：清空集合
>
> **注意：** 集合是无序且不含重复元素的数据结构

```python
>>> orange = set('orange')
>>> apple = set('apple')
# 返回两个集合的交
>>> orange & apple
{'e', 'a'}
# 返回两个集合的并
>>> orange | apple
{'o', 'n', 'g', 'e', 'l', 'p', 'a', 'r'}
# 返回集合 orange 中有但集合 apple 中没有的
>>> orange - apple
{'o', 'n', 'r', 'g'}
# 返回集合 orange 和集合 apple 只有其中某个集合有的
# 相当于 (orange | apple) - (orange & apple)
>>> orange ^ apple
{'o', 'n', 'g', 'l', 'p', 'r'}
# 可以使用 sorted() 内置函数对集合进行排序
>>> sorted(orange)
['a', 'e', 'g', 'n', 'o', 'r']
```

#### 3.7 字典(dict)

> **注意：** 字典是键值对集合

```python
>>> dict = {'1': 'one', '2': 'two', '3': 'three'}
# 添加元素
>>> dict['4'] = 'four'
>>> dict
{'1': 'one', '2': 'two', '3': 'three', '4': 'four'}
# 取出元素 '4'
>>> dict['4']
'four'
# 删除元素 '4'
>>> del dict['4']
>>> dict
{'1': 'one', '2': 'two', '3': 'three'}
# 返回所有键链表
>>> list(dict)
['1', '2', '3']
# 返回所有键链表排序
>>> sorted(dict)
['1', '2', '3']
# 检查键是否在字典中
>>> '2' in dict
True
>>> '3' not in dict
False
```

#### 3.8 循环技巧

> 使用 items() 方法将**字典**中键值对同时取出

```python
>>> dict = {'1': 'one', '2': 'two', '3': 'three'}
# 加上 'f' 或 'F' 可以在 {} 之间写可以引用的变量或字面值的 Python 表达式
>>> for k, v in dict.items():
...     print(f'{k:3}{v:5}')
...
1  one
2  two
3  three
4  four
```

> **序列**中使用 enumerate() 函数可以将索引位置和对应的值输出

```python
>>> list = ['one', 'two', 'there']
>>> for i, item in enumerate(list):
...     print(i, item)
...
0 one
1 two
2 there
```

> 同时遍历**多个序列**时，采用 zip() 函数将其内元素一一匹配

```python
>>> list1 = [1, 2, 3, 4]
>>> list2 = ['I', 'II', 'III']
>>> for l1, l2 in zip(list1, list2):
...     print(l1, l2)
...
1 I
2 II
3 III
```



### 小技巧

1. 对于一个类来说，要让内部属性不能被外部访问，可以在属性的名称前加上两个下划线`__`，相当于一个私有变量，只有内部可以访问

### 常用命令

1. `pip list` ：查看所有已安装的库

2. `pip help` ：显示所有的 pip 命令

### 参考文档

1. [python 文档（菜鸟教程版）](https://www.runoob.com/manual/pythontutorial3/docs/html/appetite.html)
2. [python 3 文档（官网）](https://docs.python.org/3/library/index.html)

3. [python yield 使用浅析](https://www.ibm.com/developerworks/cn/opensource/os-cn-python-yield/index.html)

