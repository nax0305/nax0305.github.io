## 序列构成的数组

- 序列分类
- 列表推导
- 元组
- 切片

### 序列的分类

***1. 根据列表是否含有不同元素分类***

- 容器列表 list、tuple、collection.deque
- 扁平列表 array.array、str、bytes、bytearray、memoryview

***2. 根绝列表元素是否可变***

- 可变，list、bytearray、array.array、collections.deque、memoryview
- 不可变，tuple、str、bytes

### 列表推导

***1. 替代简单的循环赋值***

```py
symbols = '#$@#%^'
codes = []
for symbol in symbols:
    codes.append(ord(symbol))
print(codes)

codes = [ord(symbol) for symbol in symbols]
print(codes)

codes = [ord(symbol) for symbol in symbols if ord(symbol) > 36]
print(codes)

codes = list(filter(lambda c : c > 36, map(ord, symbols)))
print(codes)
```
***2. 笛卡尔积***

多重循环列表推导

```python
colors = ['black', 'white', 'red']
sizes = ['S', 'M', 'L']
tshirts = [(color, size) for color in colors
                            for size in sizes]
print(tshirts)
```

***3. 生成器表达式***

使用列表来初始化其他序列类型
```python
symbols = '@#$%^'
t = tuple(ord(symbol) for symbol in symbols)

a = array.array('I', ord(symbol) for symbol in symbols)
```


### 元组

元组不仅仅只是不可变的列表，他有数据记录的功能，千万不要忽略元组的位置信息

***1. 记录数据***

```python
## 具名元组，并且嵌套了一个地址元组
PI = namedtuple('PI', 'name age address')
pi = PI('qing', 18, ("安徽省", "芜湖市", '南陵县', '稽山镇'))
print(pi)

## 拆包
pname = xie.name
page = xie.age
padd = xie.address
print(pname, page, padd)
```

***2. 不可变列表***

和列表的方法基本一样，除了元组没有_reverse_方法

可以用继承的那个图，看包含之前的方法，Container、Iterable、Size；Sequence（不可变的）；MutableSequence（可变的）

```python
s = range(3)
so = range(5)

# 祖先类
s.__container__()
s.__iter__()
s.__len__()

# 不可变序列
s.__getitem__()
s.__reverse__()
s.index()
s.count()

# 可变序列，直接修改原序列
s.__setitem__()
s.__delitem__()
s.insert(index, ele)  # 在index处插入数据
s.append(ele)  # 在末尾插入ele
s.reverse() # 反转s
s.extend(iter) # 把iter扩展到s后面
s.pop() # 把最后一个元素弹出
s.remove(ele) # 移除元素ele
s.__iadd__(ele) # 就地加入
```

### 切片

***1. 为什么切片的区间会忽略最后一个元素？***

- 当只有一个末尾元素值的话，`range(3); s[:3]`，可以快速看出切片后序列长度是3
- 两个区间的切分，写成`split_left = s[:x]; split_right = s[x:];`，很直观阅读代码

***2. 可以按步长进行切片***

一般形式为`s[start:stop:step]`，注意step可以是负数，这样就可以从后往前进行切片
上述表达式和`s.__getitem__(slice(start, stop, step))`有相同的功能

***3. 对切片进行赋值***

```python
l = range(10)

l[3:6] = [0, 0] # 可以使用较短的数组替代较长的切片
l[3::2] = [1, 1] # 必须使用等长的数组替代对应步长的元素
```


### 排序

`list.sort` 和 `内置sorted`

前者是将原序列直接排序，后者是会返回排序好的序列、原序列不变

二者都将接受三个参数，seq、key、reverse

```python
fruits = ['grape', 'raspberry', 'apple', 'banana']

list.sort(fruits, key=len, reverse=True)
```

### bisect

使用`bisect.bisect(haysect, needle)`先找到needle的位置，然后将needle插入`bisect.bisect(haysect, needle)`返回的index

```python
s = [0, 1, 1, 2, 3, 6, 7, 8, 23, 99, 99, 100]
insert_data = 9
index = bisect.bisect(s, insert_data)
s.insert(insert_data, index)
```

或者使用`bisect.insort(seq, item)`


### 列表不是首选

标准数组和NumPy数组

***2. 队列***

不用list的append方法和pop方法模拟的原因，是append方法耗时并且，不是线程安全的。

collections.deque
queue，Queue、LifoQueue、PriorityQueue
multiprocessing

