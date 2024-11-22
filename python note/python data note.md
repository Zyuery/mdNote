# python数据分析

# 1、前言

## 1.1 内容概要

主要围绕Python进行**数据控制、处理、整理和分析**的**具体细节和基本要点**。

重点介绍**Python编程、相关库和工具。**

**数据主要指结构化数据**，如*表格型数据、多维数组、通过关键列相互联系的多个表以及间隔平均或不平均的时间序列。*

## 1.2 Python在数据分析中的优势

### 1.2.1 Python的吸引力

- Python是一种受欢迎的*动态编程语言*，具有*广泛应用。*
- 在科学计算领域，Python发展为**数据科学、机器学习和软件开发**的主要语言之一。
- Python作为**胶水语言**，可以轻松集成C、C++和Fortran代码。

> 胶水语言：将不同的编程语言或组件粘合在一起，实现它们之间的交互和协同工作。

### 1.2.2 Python的适用性

- Python适用于**研究、原型构建和构建生产系统**，避免了使用多种语言的问题。
- Python可以替代领域特定的计算语言，提供组织效益。

### 1.2.3 注意事项

- Python是**解释型语言**，相对于**编译型语言**运行速度较慢，但在许多场景中性能足够。
- 在高并发、多线程的应用程序中，Python并非理想的编程语言，因为存在**全局解释器锁（GIL）**。

> ### 解释型语言：
>
> 1. **执行方式：** 解释型语言的代码在运行时逐行被解释器解析和执行。每一行代码都由解释器动态翻译成计算机能够理解的机器码，并立即执行。
> 2. **速度：** 通常相对较慢，因为在执行时需要逐行翻译，无法提前进行优化。
> 3. **跨平台性：** 具有较好的跨平台性，因为解释器通常会在目标机器上直接运行源代码。
> 4. **例子：** Python、JavaScript、Ruby等是解释型语言的例子。
>
> ### 编译型语言：
>
> 1. **执行方式：** 编译型语言的代码在运行之前需要通过编译器进行一次性的翻译，将源代码转换为目标机器的机器码。生成的可执行文件在运行时直接被计算机执行。
> 2. **速度：** 通常较快，因为代码在运行之前已经经过了优化处理。
> 3. **跨平台性：** 编译型语言的可执行文件通常是与特定平台相关的，因此需要在目标平台上重新编译才能运行。
> 4. **例子：** C、C++、Java（Java是一种特殊的编译型语言，但它使用了虚拟机，可以在不同平台上运行相同的字节码）等是编译型语言的例子。

> ### **全局解释器锁（GIL）**
>
>  是一种在解释型语言中用于控制多线程执行的机制。它确保在任一时刻只有一个线程能够执行解释器的字节码，从而限制了多线程并行执行，对于 CPU 密集型任务可能导致性能瓶颈。

### 1.2.4 多语言问题

- Python能够替代领域特定的计算语言，适用于研究和构建生产系统，提供明显的组织效益。

### 1.2.5 不适用的场景

- 在对运行速度要求极高的场景，可能选择更低级的语言。
- 在需要处理高并发、多线程的应用程序中，需要注意全局解释器锁（GIL）的影响。

### 1.3 重要的Python库

#### NumPy

NumPy（Numerical Python）是**Python科学计算的基础包**，

<u>提供快速高效的多维数组对象（ndarray），元素级计算和数学运算函数，以及线性代数运算、傅里叶变换和随机数生成等功能。</u>

在数据分析中，NumPy数组作为数据容器在算法和库之间传递数据，提高了数据处理的效率。

#### pandas

pandas是用于处理结构化数据的库，提供了丰富的数据结构和函数。

其中，<u>DataFrame是一个面向列的二维表结构，而Series是一个一维的标签化数组对象。</u>

pandas结合了NumPy高性能的数组计算功能和灵活的数据处理功能，适用于数据操作、准备、清洗等工作。

#### matplotlib

matplotlib是Python中<u>最流行的用于绘制图表和二维数据可视化的库</u>，适用于创建出版物上使用的图表。

它与其他生态工具配合良好，广泛应用于数据可视化领域。

#### IPython和Jupyter

IPython是用于增强和交互式Python计算的工具，提高了交互计算和软件开发的效率。

Jupyter则是一个更广泛的多语言交互计算工具，支持40种编程语言。

Jupyter notebooks可以编写Markdown和HTML内容，提供了创建代码和文本富文本内容的方式。

#### SciPy

SciPy是解决科学计算中各种标准问题域的包集合，包括数值积分、线性代数、函数优化、信号处理、稀疏矩阵等多个领域的功能。

#### scikit-learn

scikit-learn是通用的Python机器学习工具包，包含分类、回归、聚类、降维、模型选择、预处理等多个模块，成为Python高效数据科学编程的关键组成部分。

#### statsmodels

statsmodels是一个统计分析包，包含经典统计学和经济计量学的算法，如线性回归、方差分析、时间序列分析等。与scikit-learn不同，statsmodels关注统计推断，提供了不确定估计和参数p-值。

# 2. NumPy基础：数组和⽮量计算

## 2.1 NumPy简介

NumPy（Numerical Python的简称）是Python数值计算最重要的基础包。⼤多数提供科学计算的包都是⽤NumPy的数组作为构建基础。

### 2.1.1 NumPy的功能

- **ndarray：** 一个具有⽮量算术运算和复杂⼴播能⼒的快速且节省空间的多维数组。
- **标准数学函数：** 用于对整组数据进⾏快速运算的标准数学函数（⽆需编写循环）。
- **IO工具和内存映射⽂件：** ⽤于读写磁盘数据的⼯具以及⽤于操作内存映射⽂件的⼯具。
- **线性代数、随机数⽣成和傅⾥叶变换：** 提供了这些常用功能。
- **C API：** 用于集成由C、C++、Fortran等语⾔编写的代码。

### 2.1.2 NumPy在数据分析中的作用

NumPy提供了简单易⽤的C API，使得Python成为包装C/C++/Fortran历史代码库的选择，并使被包装库拥有⼀个动态的、易⽤的接⼝。

虽然NumPy本身并没有提供多么⾼级的数据分析功能，但理解NumPy数组以及⾯向数组的计算将有助于更加⾼效地使⽤诸如pandas之类的⼯具.

## 2.2NumPy的ndarray：⼀种多维数组对象

### 2.2.1创建ndarray

<u>创建数组最简单的办法就是使⽤`np.array()`函数。</u>

该函数接受任何序列型的对象作为输入参数，包括列表、元组等，然后将其转换为一个新的NumPy数组。

举个例子，如果有一个Python列表：

```
data1	=	[6,	7.5,	8,	0,	1]
```

你可以使用`np.array()`函数将这个**列表转换为NumPy数组**：

```
import numpy as np
arr1	=	np.array(data1)
```

这样，`my_arr`就成为了一个NumPy数组，你可以利用NumPy提供的各种功能对它进行快速的数组运算，而无需使用显式的循环。这是NumPy数组的一项重要特性，即可以进行矢量化操作，提高了对数组的处理效率。

**嵌套序列**（⽐如由⼀组等⻓列表组成的列表）将会被转换为⼀个 多维数组：

```
In	[22]:	data2	=	[[1,2,3,4],	[5,6,7,8]]
In	[23]:	arr2	=	np.array(data2)
In	[24]:	arr2
Out[24]:	
array([[1,	2,	3,	4],
[5,	6,	7,	8]])
```

除np.array之外，还有⼀些函数也可以新建数组。

**zeros**和 **ones**分别可以创建指定⻓度或形状的全0或全1数组。

in

``` 
np.zeros(10)
```

out

```
	array([0.,0.,0.,0.,0.,0.,0.,0.,0.,0.]
```

in

```
	np.zeros((3,	6))
```

out

```
array([[0.,0.,0.,0.,0.,0.],
	[0.,0.,0.,0.,0.,0.],
	[0.,0.,0.,0.,0.,0.]])
```

**empty**可以 创建⼀个没有任何具体值的数组。

in

```
np.empty((2,3,2))
```

out

```
array([[[	0.,		0.],
		[	0.,		0.],
		[	0.,		0.]],
		[[	0.,		0.],
		[	0.,		0.],
		[	0.,		0.]]])
```

> 注意：认为np.empty会返回全0数组的想法是不安全的。很多 情况下（如前所示），它返回的都是⼀些未初始化的垃圾 值。

### 2.2.2ndarray的数据类型

**dtype**（数据类型）是⼀个特殊的对象，它含有ndarray将⼀块内 存解释为特定数据类型所需的信息：

```
In [33]: arr1 = np.array([1, 2, 3], dtype=np.float64)
In [34]: arr2 = np.array([1, 2, 3], dtype=np.int32)
In [35]: arr1.dtype
Out[35]: dtype('float64')
In [36]: arr2.dtype
Out[36]: dtype('int32')
```

可以通过ndarray的**astype⽅法**明确地将⼀个数组从**⼀个dtype 转换成另⼀个dtype：**

```
In	[37]:	arr	= np.array([1,2,3,4,5])
In	[38]:	arr.dtype
Out [38]:	dtype('int64')
In	[39]:	float_arr=arr.astype(np.float64)
In	[40]:	float_arr.dtype
Out [40]:	dtype('float64')
```

> 在本例中，整数被转换成了浮点数。如果将浮点数转换成整数， 则⼩数部分将会被截取删除：

> 注意：使⽤numpy.string_类型时，⼀定要⼩⼼，因为NumPy 的字符串数据是⼤⼩固定的，发⽣截取时，不会发出警告。 pandas提供了更多⾮数值数据的便利的处理⽅法。

### 2.2.3NumPy数组的运算

数组很重要，因为它使你不⽤编写循环即可对数据执⾏批量运 算。NumPy⽤户称其为⽮量化（vectorization）。

⼤⼩相等的数 组之间的任何算术运算都会将运算应⽤到元素级：

```
# 创建一个2x3的数组
In [51]: arr = np.array([[1., 2., 3.], [4., 5., 6.]])

# 打印数组
In [52]: arr
Out[52]:
array([[1., 2., 3.],
       [4., 5., 6.]])

# 数组元素的平方
In [53]: arr * arr
Out[53]:
array([[ 1.,  4.,  9.],
       [16., 25., 36.]])

# 数组元素的减法
In [54]: arr - arr
Out[54]:
array([[0., 0., 0.],
       [0., 0., 0.]])

```

数组与标量的算术运算会将标量值传播到各个元素：

```
# 标量与数组相除
In [55]: 1 / arr
Out[55]:
array([[1.        , 0.5       , 0.33333333],
       [0.25      , 0.2       , 0.16666667]])

# 数组元素开平方
In [56]: arr ** 0.5
Out[56]:
array([[1.        , 1.41421356, 1.73205081],
       [2.        , 2.23606798, 2.44948974]])

```

⼤⼩相同的数组之间的⽐较会⽣成布尔值数组：

```
# 创建另一个2x3的数组
In [57]: arr2 = np.array([[0., 4., 1.], [7., 2., 12.]])
In [58]: arr2
Out[58]:
array([[ 0.,  4.,  1.],
       [ 7.,  2., 12.]])

# 大小相同的数组之间的比较运算
In [59]: arr2 > arr
Out[59]:
array([[False,  True, False],
       [ True, False,  True]], dtype=bool)

```

> 不同⼤⼩的数组之间的运算叫做⼴播（broadcasting).

### 2.3.3基本的索引和切片

NumPy数组的索引是一个丰富的主题，因为选取数据子集或单个元素的方式有很多。以下是一维数组的基本索引和切片操作，其表现与Python列表相似：

```
# 创建一个长度为10的一维数组
In [60]: arr = np.arange(10)
In [61]: arr
Out[61]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

# 获取索引为5的元素
In [62]: arr[5]
Out[62]: 5

# 获取索引为5到7的子数组
In [63]: arr[5:8]
Out[63]: array([5, 6, 7])

# 将索引为5到7的元素赋值为12
In [64]: arr[5:8] = 12
In [65]: arr
Out[65]: array([ 0,  1,  2,  3,  4, 12, 12, 12,  8,  9])

```

需要注意的是，数组切片是原始数组的**视图**，而不是复制。这意味着对切片的修改将直接反映在原始数组上。

```
# 创建一个切片
In [66]: arr_slice = arr[5:8]
In [67]: arr_slice
Out[67]: array([12, 12, 12])

# 修改切片的值，将反映在原始数组上
In [68]: arr_slice[1] = 12345
In [69]: arr
Out[69]: array([    0,     1,     2,     3,     4,    12, 12345,    12,     8,     9])

```

如果需要得到切片的一份副本而非视图，可以使用 `.copy()` 方法，如 `arr[5:8].copy()`。

对于二维数组，各个元素不再是标量而是一维数组：

```
# 创建一个2x3的二维数组
In [72]: arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
In [73]: arr2d[2]
Out[73]: array([7, 8, 9])
```

可以使用递归访问各个元素，也可以传入以逗号隔开的索引列表：

```
# 等价的两种索引方式
In [74]: arr2d[0][2]
Out[74]: 3
In [75]: arr2d[0, 2]
Out[75]: 3
```

在多维数组中，省略后续索引将返回维度低一点的数组，形成一个切片。例如，对于一个2x2x3的数组 `arr3d`：

```
# 创建一个2x2x3的多维数组
In [76]: arr3d = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
In [77]: arr3d[0]
Out[77]:
array([[1, 2, 3],
       [4, 5, 6]])

```

此外，数组切片支持直接赋值操作：

```
# 赋值给切片
In [70]: arr_slice[:] = 64
In [71]: arr
Out[71]: array([ 0,  1,  2,  3,  4, 64, 64, 64,  8,  9])

```

> 注意：在所有这些示例中，需要注意返回的数组都是视图，而不是副本。

### 2.2.4 切片索引

NumPy数组的切片语法类似于Python列表，尤其是一维数组的切片：

```
# 一维数组的切片
In [88]: arr
Out[88]: array([ 0,  1,  2,  3,  4, 64, 64, 64,  8,  9])

In [89]: arr[1:6]
Out[89]: array([ 1,  2,  3,  4, 64])
```

对于二维数组 `arr2d`，切片方式略有不同，它是沿着第0轴（即第一个轴）切片的。例如，表达式 `arr2d[:2]` 可以理解为“选取 `arr2d` 的前两行”：

```
# 二维数组的切片
In [90]: arr2d
Out[90]:
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])

In [91]: arr2d[:2]
Out[91]:
array([[1, 2, 3],
       [4, 5, 6]])
```

可以一次传入多个切片，就像传入多个索引一样：

```
# 多个切片
In [92]: arr2d[:2, 1:]
Out[92]:
array([[2, 3],
       [5, 6]])
```

通过将整数索引和切片混合使用，可以得到低维度的切片。例如，选择第二行的前两列：

```
# 混合整数索引和切片
In [93]: arr2d[1, :2]
Out[93]: array([4, 5])
```

也可以选择第三列的前两行：

```
# 混合整数索引和切片
In [94]: arr2d[:2, 2]
Out[94]: array([3, 6])
```

对切片表达式的赋值操作会扩散到整个选区：

```
# 赋值给切片
In [96]: arr2d[:2, 1:] = 0

In [97]: arr2d
Out[97]:
array([[1, 0, 0],
       [4, 0, 0],
       [7, 8, 9]])
```

这意味着对切片的修改会直接影响到原始数组。

### 2.2.5 布尔型索引

布尔型索引是通过布尔值来进行数组索引的一种方法。以下是一个例子：

```
# 创建姓名数组和数据数组
In [98]: names = np.array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'])
In [99]: data = np.random.randn(7, 4)

In [100]: names
Out[100]: array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'], dtype='<U4')

In [101]: data
Out[101]:
array([[ 0.0929,  0.2817,  0.769 ,  1.2464],
       [ 1.0072, -1.2962,  0.275 ,  0.2289],
       [ 1.3529,  0.8864, -2.0016, -0.3718],
       [ 1.669 , -0.4386, -0.5397,  0.477 ],
       [ 3.2489, -1.0212, -0.5771,  0.1241],
       [ 0.3026,  0.5238,  0.0009,  1.3438],
       [-0.7135, -0.8312, -2.3702, -1.8608]])

```

我们可以使用布尔运算符进行比较，得到一个布尔型数组：

```
# 使用布尔运算符进行比较
In [102]: names == 'Bob'
Out[102]: array([ True, False, False,  True, False, False, False], dtype=bool)

```

然后，将该布尔型数组用作数组的索引，从而选取满足条件的行：

```
# 通过布尔型数组进行索引
In [103]: data[names == 'Bob']
Out[103]:
array([[ 0.0929,  0.2817,  0.769 ,  1.2464],
       [ 1.669 , -0.4386, -0.5397,  0.477 ]])
```

可以使用多个条件组合进行复杂的布尔型索引：

```
# 多条件组合进行布尔型索引
In [110]: mask = (names == 'Bob') | (names == 'Will')

In [111]: mask
Out[111]: array([ True, False,  True,  True,  True, False, False], dtype=bool)

In [112]: data[mask]
Out[112]:
array([[ 0.0929,  0.2817,  0.769 ,  1.2464],
       [ 1.3529,  0.8864, -2.0016, -0.3718],
       [ 1.669 , -0.4386, -0.5397,  0.477 ]])
```

通过布尔型索引，我们可以灵活地选取数组中满足特定条件的元素。

### 2.2.6  花式索引

花式索引是指通过整数数组进行索引。可以使用整数数组指定所需的行或列。以下是一个简单的例子：

```
# 创建一个8x4的数组
In [117]: arr = np.empty((8, 4))

# 将每一行的值设置为对应的行索引
In [118]: for i in range(8):
   .....:     arr[i] = i

In [119]: arr
Out[119]:
array([[0., 0., 0., 0.],
       [1., 1., 1., 1.],
       [2., 2., 2., 2.],
       [3., 3., 3., 3.],
       [4., 4., 4., 4.],
       [5., 5., 5., 5.],
       [6., 6., 6., 6.],
       [7., 7., 7., 7.]])
```

可以通过传入整数数组来选择特定的行：

```
# 通过整数数组选择特定的行
In [120]: arr[[4, 3, 0, 6]]
Out[120]:
array([[4., 4., 4., 4.],
       [3., 3., 3., 3.],
       [0., 0., 0., 0.],
       [6., 6., 6., 6.]])
```

使用负数索引可以从末尾开始选择行：

```
# 使用负数索引选择行
In [121]: arr[[-3, -5, -7]]
Out[121]:
array([[5., 5., 5., 5.],
       [3., 3., 3., 3.],
       [1., 1., 1., 1.]])
```

可以同时传入多个索引数组，但结果是一维数组：

```
# 通过多个索引数组选择元素
In [124]: arr[[1, 5, 7, 2], [0, 3, 1, 2]]
Out[124]: array([ 4, 23, 29, 10])
```

注意花式索引总是返回一维数组。如果想要获取矩形区域，可以通过组合多个索引数组来实现：

```
# 组合多个索引数组获取矩形区域
In [125]: arr[[1, 5, 7, 2]][:, [0, 3, 1, 2]]
Out[125]:
array([[ 4.,  7.,  5.,  6.],
       [20., 23., 21., 22.],
       [28., 31., 29., 30.],
       [ 8., 11.,  9., 10.]])
```

> 请注意，花式索引与切片不同，它总是返回数据的副本。

### 2.2.7 数组转置和轴对换

转置是数组的一种特殊形式的重塑操作，它返回的是源数据的视图（不进行任何复制操作）。数组可以使用 `transpose` 方法或特殊的 `T` 属性进行转置。

```
# 创建一个3x5的数组
In [126]: arr = np.arange(15).reshape((3, 5))

In [127]: arr
Out[127]:
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14]])

# 使用 T 属性进行转置
In [128]: arr.T
Out[128]:
array([[ 0,  5, 10],
       [ 1,  6, 11],
       [ 2,  7, 12],
       [ 3,  8, 13],
       [ 4,  9, 14]])
```

在矩阵计算中，经常需要进行转置操作，例如使用 `np.dot` 计算矩阵内积：

```
# 创建一个6x3的随机数组
In [129]: arr = np.random.randn(6, 3)

In [130]: arr
Out[130]:
array([[-0.8608,  0.5601, -1.2659],
       [ 0.1198, -1.0635,  0.3329],
       [-2.3594, -0.1995, -1.542 ],
       [-0.9707, -1.307 ,  0.2863],
       [ 0.378 , -0.7539,  0.3313],
       [ 1.3497,  0.0699,  0.2467]])

# 计算矩阵内积
In [131]: np.dot(arr.T, arr)
Out[131]:
array([[ 9.2291,  0.9394,  4.948 ],
       [ 0.9394,  3.7662, -1.3622],
       [ 4.948 , -1.3622,  4.3437]])

```

对于高维数组，`transpose` 方法需要接受一个由轴编号组成的元组来对这些轴进行转置。例如：

```
# 创建一个2x2x4的数组
In [132]: arr = np.arange(16).reshape((2, 2, 4))

# 对轴进行转置
In [134]: arr.transpose((1, 0, 2))
Out[134]:
array([[[ 0,  1,  2,  3],
        [ 8,  9, 10, 11]],
       [[ 4,  5,  6,  7],
        [12, 13, 14, 15]]])
```

这里，第一个轴被换成了第二个，第二个轴被换成了第一个，最后一个轴保持不变。

简单的转置可以使用 `.T`，它实际上就是进行轴对换。`ndarray` 还有一个 `swapaxes` 方法，它需要接受一对轴编号：

```
# 使用 swapaxes 进行轴对换
In [136]: arr.swapaxes(1, 2)
Out[136]:
array([[[ 0,  4],
        [ 1,  5],
        [ 2,  6],
        [ 3,  7]],
       [[ 8, 12],
        [ 9, 13],
        [10, 14],
        [11, 15]]])
```

`swapaxes` 也是返回源数据的视图（不进行任何复制操作）。

## 2.3 通⽤函数：快速的元素级数组函数

通用函数（ufunc）是一种对 ndarray 中的数据执行元素级运算的函数。它们将数组视为数据的向量，并对所有元素执行相同的操作。很多 ufunc 都是简单的元素级变体，如 `sqrt` 和 `exp`。

### 2.3.1 一元 ufunc

一元 ufunc 对单个数组进行操作。例如，`np.sqrt` 计算数组中每个元素的平方根:

```
In [137]: arr = np.arange(10)

In [139]: np.sqrt(arr)
Out[139]:
array([0.        , 1.        , 1.41421356, 1.73205081, 2.        ,
       2.23606798, 2.44948974, 2.64575131, 2.82842712, 3.        ])

```

### 2.3.2 二元 ufunc

二元 ufunc 接受两个数组，并返回一个结果数组。例如，`np.maximum` 计算两个数组中每个元素的最大值：

```
In [141]: x = np.random.randn(8)
In [142]: y = np.random.randn(8)

In [145]: np.maximum(x, y)
Out[145]:
array([ 0.8626,  1.0048,  1.3272,  0.6702,  0.853 ,  0.0222,  0.7584, -0.6605])
```

### 2.3.3 返回多个数组的 ufunc

虽然不太常见，但有些 ufunc 确实可以返回多个数组。例如，`np.modf` 返回浮点数数组的小数和整数部分：

```
In [146]: arr = np.random.randn(7) * 5

In [148]: remainder, whole_part = np.modf(arr)

In [149]: remainder
Out[149]: array([-0.2623, -0.0915, -0.663 ,  0.3731,  0.6182,  0.45  ,  0.0077])

In [150]: whole_part
Out[150]: array([-3., -6., -6.,  5.,  3.,  3.,  5.])
```

### 2.3.4 原地操作

ufunc 可以通过 `out` 选项参数在原地执行操作：

```
In [151]: arr = np.random.randn(8)

In [152]: np.sqrt(arr)
Out[152]: array([       nan,        nan,        nan, 2.318, 1.9022, 1.8574, 2.2378])

In [153]: np.sqrt(arr, arr)
Out[153]: array([       nan,        nan,        nan, 2.318, 1.9022, 1.8574, 2.2378])

In [154]: arr
Out[154]: array([       nan,        nan,        nan, 2.318, 1.9022, 1.8574, 2.2378])
```

表格 4-3 和 4-4 分别列出了一些一元和二元 ufunc。

**表格 4-3: 一元通用函数**

| 函数                                                         | 说明                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| `abs`, `fabs`                                                | 绝对值                                             |
| `sqrt`                                                       | 平方根                                             |
| `square`                                                     | 平方                                               |
| `exp`                                                        | 指数                                               |
| `log`, `log2`, `log10`                                       | 对数                                               |
| `ceil`                                                       | 向上取整                                           |
| `floor`                                                      | 向下取整                                           |
| `rint`                                                       | 四舍五入到最接近的整数，保留dtype                  |
| `modf`                                                       | 将小数和整数部分以两个独立数组返回                 |
| `isnan`                                                      | 返回一个表示“是否为NaN”的布尔型数组                |
| `isfinite`, `isinf`                                          | 分别返回一个表示“是否有限”和“是否无穷”的布尔型数组 |
| `cos`, `cosh`, `sin`, `sinh`, `tan`, `tanh`                  | 普通型和双曲型三角函数                             |
| `arccos`, `arccosh`, `arcsin`, `arcsinh`, `arctan`, `arctanh` | 反三角函数                                         |

**表格 4-4: 二元通用函数**

| 函数                                                         | 说明                                             |
| ------------------------------------------------------------ | ------------------------------------------------ |
| `add`                                                        | 将数组中对应的元素相加                           |
| `subtract`                                                   | 从第一个数组中减去第二个数组中的元素             |
| `multiply`                                                   | 数组元素相乘                                     |
| `divide`, `floor_divide`                                     | 除法，向下圆整除法（丢弃余数）                   |
| `power`                                                      | 第一个数组元素的幂，第二个数组中对应元素为幂指数 |
| `maximum`, `fmax`                                            | 元素级的最大值计算。`fmax` 将 NaN 看作最大值     |
| `minimum`, `fmin`                                            | 元素级的最小值计算。`fmin` 将 NaN 看作最小值     |
| `mod`                                                        | 元素级的求模（除法的余数）                       |
| `copysign`                                                   | 将第一个数组中的值的符号改为第二个数组中的符号   |
| `greater`, `greater_equal`, `less`, `less_equal`, `equal`, `not_equal` | 执行元素级的比较运算，产生布尔型数组             |
| `logical_and`, `logical_or`, `logical_xor`                   | 执行元素级的真                                   |

## 2.4  利⽤数组进⾏数据处理

NumPy 数组允许将许多数据处理任务表达为简洁的数组表达式，这种做法通常称为**矢量化**。矢量化数组运算通常比纯 Python 方式快上一两个数量级（甚至更多），特别是在数值计算方面。

作为一个简单的例子，假设我们想要在一组值（网格型）上计算函数sqrt(x^2 + y^2)。`np.meshgrid` 函数接受两个一维数组，并产生两个二维矩阵，对应于这两个数组中所有的 (x, y) 对：

```
pythonCopy codeIn [155]: points = np.arange(-5, 5, 0.01)  # 1000 equally spaced points
In [156]: xs, ys = np.meshgrid(points, points)

In [157]: ys
Out[157]:
array([[-5.  , -5.  , -5.  , ..., -5.  , -5.  , -5.  ],
       [-4.99, -4.99, -4.99, ..., -4.99, -4.99, -4.99],
       [-4.98, -4.98, -4.98, ..., -4.98, -4.98, -4.98],
       ...,
       [ 4.97,  4.97,  4.97, ...,  4.97,  4.97,  4.97],
       [ 4.98,  4.98,  4.98, ...,  4.98,  4.98,  4.98],
       [ 4.99,  4.99,  4.99, ...,  4.99,  4.99,  4.99]])
```

现在，对该函数的求值运算就容易了，将这两个数组当做两个浮点数那样编写表达式即可：

```
pythonCopy codeIn [158]: z = np.sqrt(xs ** 2 + ys ** 2)

In [159]: z
Out[159]:
array([[7.0711, 7.064 , 7.0569, ..., 7.0499, 7.0569, 7.064 ],
       [7.064 , 7.0569, 7.0499, ..., 7.0428, 7.0499, 7.0569],
       [7.0569, 7.0499, 7.0428, ..., 7.0357, 7.0428, 7.0499],
       ...,
       [7.0499, 7.0428, 7.0357, ..., 7.0286, 7.0357, 7.0428],
       [7.0569, 7.0499, 7.0428, ..., 7.0357, 7.0428, 7.0499],
       [7.064 , 7.0569, 7.0499, ..., 7.0428, 7.0499, 7.0569]])
```

可以使用 `matplotlib` 创建这个二维数组的可视化：

```
In [160]: import matplotlib.pyplot as plt

In [161]: plt.imshow(z, cmap=plt.cm.gray)
          plt.colorbar()
          plt.title("Image plot of $\sqrt{x^2 + y^2}$ for a grid of values")
Out[161]: <matplotlib.colorbar.Colorbar at 0x7f715e3fa630>

```

### 2.4.1 将条件逻辑表述为数组运算

`numpy.where` 函数是三元表达式 x if condition else y 的矢量化版本。假设有一个布尔数组和两个值数组：

```
In [165]: xarr = np.array([1.1, 1.2, 1.3, 1.4, 1.5])
In [166]: yarr = np.array([2.1, 2.2, 2.3, 2.4, 2.5])
In [167]: cond = np.array([True, False, True, True, False])
```

假设我们想要根据 `cond` 中的值选取 `xarr` 和 `yarr` 的值：当 `cond` 中的值为 `True` 时，选取 `xarr` 的值，否则从 `yarr` 中选取。可以使用 `numpy.where` 使得这个操作更简洁：

```
In [170]: result = np.where(cond, xarr, yarr)
In [171]: result
Out[171]: array([1.1, 2.2, 1.3, 1.4, 2.5])
```

`numpy.where` 的第二个和第三个参数不必是数组，它们都可以是标量值。在数据分析工作中，`where` 通常用于根据另一个数组生成一个新的数组。例如，将矩阵中的正值替换为 2，将负值替换为 -2：

```
In [172]: arr = np.random.randn(4, 4)
In [175]: np.where(arr > 0, 2, -2)
Out[175]:
array([[-2, -2, -2, -2],
       [ 2,  2, -2,  2],
       [ 2,  2,  2, -2],
       [ 2, -2,  2,  2]])
```

使用 `numpy.where`，可以将标量和数组结合起来，例如，将数组中所有正的值替换为常数 2：

```
In [176]: np.where(arr > 0, 2, arr)  # set only positive values to 2
Out[176]:
array([[-0.5031, -0.6223, -0.9212, -0.7262],
       [ 2.    ,  2.    , -1.1577,  2.    ],
       [ 2.    ,  2.    ,  2.    , -0.9975],
       [ 2.    , -0.1316,  2.    ,  2.    ]])
```

传递给 `where` 的数组大小可以不相等，甚至可以是标量值。

### 2.4.2 数学和统计⽅法

可以通过数组上的一组数学函数对整个数组或某个轴向的数据进行统计计算。`sum`、`mean` 以及标准差 `std` 等聚合计算（通常叫做约简（reduction））既可以当做数组的实例方法调用，也可以当做顶级 NumPy 函数使用。

以下是一个示例，生成了一些正态分布随机数据，然后进行了统计计算：

```
In [177]: arr = np.random.randn(5, 4)
In [178]: arr
Out[178]:
array([[ 2.1695, -0.1149,  2.0037,  0.0296],
       [ 0.7953,  0.1181, -0.7485,  0.585 ],
       [ 0.1527, -1.5657, -0.5625, -0.0327],
       [-0.929 , -0.4826, -0.0363,  1.0954],
       [ 0.9809, -0.5895,  1.5817, -0.5287]])

In [179]: arr.mean()
Out[179]: 0.19607051119998253

In [180]: np.mean(arr)
Out[180]: 0.19607051119998253

In [181]: arr.sum()
Out[181]: 3.9214102239996507
```

`mean` 和 `sum` 这类的函数可以接受一个 `axis` 选项参数，用于计算该轴向上的统计值，最终结果是一个少一维的数组：

```
In [182]: arr.mean(axis=1)
Out[182]: array([ 1.022 ,  0.1875, -0.502 , -0.0881,  0.3611])

In [183]: arr.sum(axis=0)
Out[183]: array([ 3.1693, -2.6345,  2.2381,  1.1486])
```

这里，`arr.mean(1)` 是“计算行的平均值”，`arr.sum(0)` 是“计算每列的和”。

其他如 `cumsum` 和 `cumprod` 之类的方法则不聚合，而是产生一个由中间结果组成的数组：

```
In [186]: arr = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
In [188]: arr.cumsum(axis=0)
Out[188]:
array([[ 0,  1,  2],
       [ 3,  5,  7],
       [ 9, 12, 15]])

In [189]: arr.cumprod(axis=1)
Out[189]:
array([[ 0,  0,  0],
       [ 3, 12, 60],
       [ 6, 42, 336]])
```

表2.4.2-1列出了全部的基本数组统计方法。后续章节中有很多例子都会用到这些方法。

![image-20231218220159840](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231218220159840.png)

### 2.4.3  ⽤于布尔型数组的⽅法

在上述这些方法中，布尔值会被强制转换为 1（True）和 0（False）。因此，`sum` 经常被用来对布尔型数组中的 `True` 值计数：

```
In [190]: arr = np.random.randn(100)
In [191]: (arr > 0).sum()  # Number of positive values
Out[191]: 42
```

另外还有两个方法 `any` 和 `all`，它们对布尔型数组非常有用。`any` 用于测试数组中是否存在一个或多个 `True`，而 `all` 则检查数组中所有值是否都是 `True`：

```
In [192]: bools = np.array([False, False, True, False])
In [193]: bools.any()
Out[193]: True

In [194]: bools.all()
Out[194]: False
```

这两个方法也能用于非布尔型数组，所有非 0 元素将会被当做 `True`。

### 2.4.4 排序

与 Python 内置的列表类型类似，NumPy 数组也可以通过 `sort` 方法进行就地排序：

```
In [195]: arr = np.random.randn(6)
In [196]: arr
Out[196]: array([ 0.6095, -0.4938, 1.24 , -0.1357, 1.43 , -0.8469])

In [197]: arr.sort()

In [198]: arr
Out[198]: array([-0.8469, -0.4938, -0.1357, 0.6095, 1.24 , 1.43 ])
```

多维数组可以在任何一个轴向上进行排序，只需将轴编号传给 `sort` 即可：

```
In [199]: arr = np.random.randn(5, 3)
In [200]: arr
Out[200]: 
array([[ 0.6033, 1.2636, -0.2555],
       [-0.4457, 0.4684, -0.9616],
       [-1.8245, 0.6254, 1.0229],
       [ 1.1074, 0.0909, -0.3501],
       [ 0.218 , -0.8948, -1.7415]])

In [201]: arr.sort(1)

In [202]: arr
Out[202]: 
array([[-0.2555, 0.6033, 1.2636],
       [-0.9616, -0.4457, 0.4684],
       [-1.8245, 0.6254, 1.0229],
       [-0.3501, 0.0909, 1.1074],
       [-1.7415, -0.8948, 0
```

顶级方法 `np.sort` 返回的是数组的已排序副本，而就地排序则会修改数组本身。计算数组分位数最简单的办法是对其进行排序，然后选取特定位置的值：

```
In [203]: large_arr = np.random.randn(1000)
In [204]: large_arr.sort()

In [205]: large_arr[int(0.05 * len(large_arr))]  # 5% quantile
Out[205]: -1.5311513550102103
```

### 2.4.5 唯⼀化以及其它的集合逻辑

NumPy 提供了一些针对一维 ndarray 的基本集合运算。最常用的可能要数 `np.unique` 了，它用于找出数组中的唯一值并返回已排序的结果：

```
In [206]: names = np.array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'])
In [207]: np.unique(names)
Out[207]: array(['Bob', 'Joe', 'Will'], dtype='<U4')

In [208]: ints = np.array([3, 3, 3, 2, 2, 1, 1, 4, 4])
In [209]: np.unique(ints)
Out[209]: array([1, 2, 3, 4])
```

拿跟 `np.unique` 等价的纯 Python 代码来对比一下：

```
In [210]: sorted(set(names))
Out[210]: ['Bob', 'Joe', 'Will']
```

另一个函数 `np.in1d` 用于测试一个数组中的值在另一个数组中的成员资格，返回一个布尔型数组：

```
In [211]: values = np.array([6, 0, 0, 3, 2, 5, 6])
In [212]: np.in1d(values, [2, 3, 6])
Out[212]: array([True, False, False, True, True, False, True], dtype=bool)
```

NumPy 中的集合函数请参见表4-6。

![image-20231218220559930](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231218220559930.png)

## 2.5 ⽤于数组的⽂件输⼊输出

NumPy 能够读写磁盘上的文本数据或二进制数据。这一小节只讨论 NumPy 的内置二进制格式，因为更多的用户会使用 pandas 或其他工具加载文本或表格数据。

`np.save` 和 `np.load` 是读写磁盘数组数据的两个主要函数。默认情况下，数组是以未压缩的原始二进制格式保存在扩展名为 `.npy` 的文件中的：

```
In [213]: arr = np.arange(10)
In [214]: np.save('some_array', arr)
```

如果文件路径末尾没有扩展名 `.npy`，则该扩展名会被自动加上。然后就可以通过 `np.load` 读取磁盘上的数组：

```
In [215]: np.load('some_array.npy')
Out[215]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

通过 `np.savez` 可以将多个数组保存到一个未压缩文件中，将数组以关键字参数的形式传入即可：

```
In [216]: np.savez('array_archive.npz', a=arr, b=arr)
```

加载 `.npz` 文件时，你会得到一个类似字典的对象，该对象会对各个数组进行延迟加载：

```
In [217]: arch = np.load('array_archive.npz')
In [218]: arch['b']
Out[218]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

如果数据压缩得很好，就可以使用 `numpy.savez_compressed`：

```
In [219]: np.savez_compressed('arrays_compressed.npz', a=arr, b=arr)
```

## 2.6 线性代数

线性代数，如矩阵乘法、矩阵分解、行列式以及其他矩阵数学等，是任何数组库的重要组成部分。不像某些语言（如 MATLAB），通过 `*` 对两个二维数组相乘得到的是一个元素级的积，而不是一个矩阵点积。因此，NumPy 提供了一个用于矩阵乘法的 `dot` 函数（既是一个数组方法也是 NumPy 命名空间中的一个函数）：

```
In [223]: x = np.array([[1., 2., 3.], [4., 5., 6.]])
In [224]: y = np.array([[6., 23.], [-1, 7], [8, 9]])
In [225]: x
Out[225]: 
array([[1., 2., 3.],
       [4., 5., 6.]])
In [226]: y
Out[226]: 
array([[ 6., 23.],
       [-1.,  7.],
       [ 8.,  9.]])
In [227]: x.dot(y)
Out[227]: 
array([[ 28.,  64.],
       [ 67., 181.]])
```

`x.dot(y)` 等价于 `np.dot(x, y)`：

```
In [228]: np.dot(x, y)
Out[228]: 
array([[ 28.,  64.],
       [ 67., 181.]])
```

一个二维数组跟一个大小合适的一维数组的矩阵点积运算之后将会得到一个一维数组：

```
In [229]: np.dot(x, np.ones(3))
Out[229]: array([ 6., 15.])
```

`@` 符号（类似 Python 3.5）也可以用作中缀运算符，进行矩阵乘法：

```
In [230]: x @ np.ones(3)
Out[230]: array([ 6., 15.])
```

`numpy.linalg` 中有一组标准的矩阵分解运算以及诸如求逆和行列式之类的东西。它们跟 MATLAB 和 R 等语言所使用的是相同的行业标准线性代数库，如 BLAS、LAPACK、Intel MKL（Math Kernel Library，可能有，取决于你的 NumPy 版本）等：

```
In [231]: from numpy.linalg import inv, qr
In [232]: X = np.random.randn(5, 5)
In [233]: mat = X.T.dot(X)
In [234]: inv(mat)
Out[234]: 
array([[  933.1189,   871.8258, -1417.6902, -1460.4005,  1782.1391],
       [  871.8258,   815.3929, -1325.9965, -1365.9242,  1666.9347],
       [-1417.6902, -1325.9965,  2158.4424,  2222.0191, -2711.6822],
       [-1460.4005, -1365.9242,  2222.0191,  2289.0575, -2793.422 ],
       [ 1782.1391,  1666.9347, -2711.6822, -2793.422 ,  3409.5128]])
In [235]: mat.dot(inv(mat))
Out[235]: 
array([[ 1.,  0.,  0.,  0.,  0.],
       [ 0.,  1.,  0.,  0.,  0.],
       [ 0.,  0.,  1.,  0.,  0.],
       [ 0.,  0.,  0.,  1.,  0.],
       [ 0.,  0.,  0.,  0.,  1.]])
In [236]: q, r = qr(mat)
In [237]: r
Out[237]: 
array([[-1.6914,  4.38  ,  0.1757,  0.4075, -0.7838],
       [ 0.    , -2.6436,  0.1939, -3.072 , -1.0702],
       [ 0.    ,  0.    , -0.8138,  1.5414,  0.6155],
       [ 0.    ,  0.    ,  0.    , -2.6445, -2.1669],
       [ 0.    ,  0.    ,  0.    ,  0.    ,  0.0002]])
```

表达式 `X.T.dot(X)` 计算 `X` 和它的转置 `X.T` 的点积。

表4-7中列出了一些最常用的线性代数函数。

![image-20231218221029134](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231218221029134.png)

## 2.7 伪随机数⽣成

`numpy.random` 模块对 Python 内置的 `random` 进行了补充，增加了一些用于高效生成多种概率分布的样本值的函数。例如，你可以用 `normal` 来得到一个标准正态分布的 4x4 样本数组：

```
In [238]: samples = np.random.normal(size=(4, 4))
In [239]: samples
Out[239]: 
array([[ 0.5732,  0.1933,  0.4429,  1.2796],
       [ 0.575 ,  0.4339, -0.7658, -1.237 ],
       [-0.5367,  1.8545, -0.92  , -0.1082],
       [ 0.1525,  0.9435, -1.0953, -0.144 ]])
```

而 Python 内置的 `random` 模块则只能一次生成一个样本值。从下面的测试结果中可以看出，如果需要产生大量样本值，`numpy.random` 快了不止一个数量级：

```
In [240]: from random import normalvariate
In [241]: N = 1000000
In [242]: %timeit samples = [normalvariate(0, 1) for _ in range(N)]
1.77 s +- 126 ms per loop (mean +- std. dev. of 7 runs, 1 loop each)
In [243]: %timeit np.random.normal(size=N)
61.7 ms +- 1.32 ms per loop (mean +- std. dev. of 7 runs, 10 loops each)
```

我们说这些都是伪随机数，是因为它们都是通过算法基于随机数生成器种子，在确定性的条件下生成的。你可以用 NumPy 的 `np.random.seed` 更改随机数生成种子：

```
In [244]: np.random.seed(1234)
```

`numpy.random` 的数据生成函数使用了全局的随机种子。要避免全局状态，你可以使用 `numpy.random.RandomState`，创建一个与其他隔离的随机数生成器：

```
In [245]: rng = np.random.RandomState(1234)
In [246]: rng.randn(10)
Out[246]: 
array([ 0.4714, -1.191 ,  1.4327, -0.3127, -0.7206,  0.8872,  0.8596,
       -0.6365,  0.0157, -2.2427])
```

表4-8列出了 `numpy.random` 中的部分函数。在下一节中，我将给出一些利用这些函数一次性生成大量样本值的范例。

![image-20231218221229811](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231218221229811.png)

## 2.8 示例：随机漫步

在这个示例中，我们通过模拟随机漫步来说明如何运用数组运算。首先，我们看一个简单的随机漫步的例子：从0开始，步长1和-1出现的概率相等。下面是一个通过内置的 `random` 模块以纯 Python 的方式实现的 1000 步的随机漫步：

```
import random

position = 0
walk = [position]
steps = 1000

for i in range(steps):
    step = 1 if random.randint(0, 1) else -1
    position += step
    walk.append(position)
```

下面是根据前100个随机漫步值生成的折线图：

```
import matplotlib.pyplot as plt

plt.plot(walk[:100])
plt.show()
```

在这里，我们生成了一个包含1000个步的随机漫步过程，其中每一步的移动方向是向前还是向后都是等概率的。通过累计这些步，我们得到了漫步路径。

接下来，我们使用 NumPy 的数组运算进行漫步模拟。首先，我们通过 `numpy.random` 模块一次性随机产生了1000个“掷硬币”结果，将其分别设置为1或-1，然后计算累计和：

```
import numpy as np

nsteps = 1000
draws = np.random.randint(0, 2, size=nsteps)
steps = np.where(draws > 0, 1, -1)
walk = steps.cumsum()
```

有了这些数据之后，我们可以进行一些统计工作，例如求最大值和最小值：

```
walk.min()  # 最小值
walk.max()  # 最大值
```

接下来，我们可以尝试计算随机漫步的首次穿越时间，即随机漫步过程中第一次到达某个特定值的时间。例如，我们想要知道本次随机漫步需要多久才能距离初始0点至少10步远。我们可以使用 `np.abs(walk) >= 10` 来得到一个布尔型数组，表示是否达到或超过10。然后，我们使用 `argmax` 来找到布尔型数组中第一次最大值（即True）的索引：

```
(np.abs(walk) >= 10).argmax()
```

上述代码中，`argmax` 返回的是布尔型数组中第一次最大值的索引，即第一次穿越时间。

最后，我们进行多个随机漫步过程的模拟。我们可以一次性计算多个随机漫步过程的累计和。例如，假设我们想模拟5000个随机漫步，每个漫步包含1000步：

```
nwalks = 5000
nsteps = 1000
draws = np.random.randint(0, 2, size=(nwalks, nsteps))
steps = np.where(draws > 0, 1, -1)
walks = steps.cumsum(1)
```

现在，我们可以计算所有随机漫步过程的最大值和最小值：

```
walks.max()  # 所有漫步过程的最大值
walks.min()  # 所有漫步过程的最小值
```

也可以计算穿越30或-30的最小穿越时间：

```
hits30 = (np.abs(walks) >= 30).any(1)
hits30.sum()  # 超过30或-30的漫步过程数量
crossing_times = (np.abs(walks[hits30]) >= 30).argmax(1)
crossing_times.mean()  # 平均穿越时间
```

# 3.pandas⼊⻔

pandas 是一个用于数据清洗和分析的强大库，通常与其他工具如 NumPy、SciPy、statsmodels 和 scikit-learn 以及数据可视化库 matplotlib 一同使用。pandas 提供了数据结构和操作工具，使数据处理更加快捷和简单。它构建在 NumPy 数组的基础上，特别适用于处理表格和混杂数据，而 NumPy 更适合处理统一的数值数组数据。

自从 pandas 在2010年开源以来，已经发展成一个非常庞大的库，广泛应用于实际场景。开发者社区有着大约800个独立的贡献者，共同致力于解决日常数据处理问题，并推动项目的发展。

在后续的部分，我们将使用如下的 pandas 引入约定：

```
import pandas as pd
```

这样，在代码中看到 `pd.` 就知道是在使用 pandas。由于 Series 和 DataFrame 的使用频率较高，通常将其引入到本地命名空间中会更加方便：

```
from pandas import Series, DataFrame
```

这使得我们可以直接使用 `Series` 和 `DataFrame` 而无需每次都写 `pd.Series` 和 `pd.DataFrame`。

## 3.1 pandas的数据结构介绍

在使用 pandas 之前，首先要熟悉它的两个主要数据结构：Series 和 DataFrame。这两种数据结构为大多数应用提供了可靠且易于使用的基础。

### 3.1.1 Series

Series 类似于一维数组，由一组数据（各种 NumPy 数据类型）和与之相关的数据标签（即索引）组成。最简单的 Series 只需传入一组数据即可：

```
import pandas as pd

obj = pd.Series([4, 7, -5, 3])
print(obj)
```

输出：

```
0    4
1    7
2   -5
3    3
dtype: int64
```

在 Series 的字符串表现形式中，索引在左边，值在右边。如果没有为数据指定索引，pandas 会自动创建一个从 0 到 N-1（N 为数据长度）的整数型索引。

可以通过 `values` 和 `index` 属性获取其数组表示形式和索引对象：

```
print(obj.values)
# Output: [ 4  7 -5  3]

print(obj.index)
# Output: RangeIndex(start=0, stop=4, step=1)
```

通常，我们希望 Series 带有一个可以对各个数据点进行标记的索引：

```
obj2 = pd.Series([4, 7, -5, 3], index=['d', 'b', 'a', 'c'])
print(obj2)
```

输出：

```
d    4
b    7
a   -5
c    3
dtype: int64
```

索引列表 `['d', 'b', 'a', 'c']` 是由用户指定的，即使它包含字符串而不是整数。

Series 可以看作是一个定长的有序字典，因为它是索引值到数据值的一个映射。与字典类似，我们可以通过索引选取 Series 中的单个或一组值：

```
print(obj2['a'])
# Output: -5

print(obj2[['c', 'a', 'd']])
# Output:
# c    3
# a   -5
# d    4
# dtype: int64
```

与 NumPy 数组一样，可以进行类似的运算，同时保留索引值的链接：

```
print(obj2[obj2 > 0])
# Output:
# d    4
# b    7
# c    3
# dtype: int64

print(obj2 * 2)
# Output:
# d     8
# b    14
# a   -10
# c     6
# dtype: int64

import numpy as np

print(np.exp(obj2))
# Output:
# d      54.598150
# b    1096.633158
# a       0.006738
# c      20.085537
# dtype: float64
```

Series 可以看作是一种类似于 join 操作的数据对齐功能。在数据对齐的情况下，运算会根据索引标签自动对齐数据。

Series 对象本身及其索引都有一个 `name` 属性，该属性与 pandas 的其他关键功能关系密切。同时，Series 的索引可以通过赋值的方式就地修改。

### 3.1.2 DataFrame

DataFrame 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔值等）。DataFrame 既有行索引也有列索引，可以看作是由 Series 组成的字典（共享同一个索引）。DataFrame 中的数据以一个或多个二维块存放，是 pandas 中的核心数据结构之一。

##### 3.1.2-1创建 DataFrame

DataFrame 的创建方法有很多，其中最常用的一种是直接传入一个由等长列表或 NumPy 数组组成的字典：

```
import pandas as pd

data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada', 'Nevada'],
        'year': [2000, 2001, 2002, 2001, 2002, 2003],
        'pop': [1.5, 1.7, 3.6, 2.4, 2.9, 3.2]}

frame = pd.DataFrame(data)
print(frame)
```

输出：

```
    state  year  pop
0    Ohio  2000  1.5
1    Ohio  2001  1.7
2    Ohio  2002  3.6
3  Nevada  2001  2.4
4  Nevada  2002  2.9
5  Nevada  2003  3.2
```

DataFrame 会自动加上索引（类似于 Series），且全部列会被有序排列。在 Jupyter notebook 中，DataFrame 对象会以对浏览器友好的 HTML 表格的方式呈现。

可以使用 `head` 方法选取前五行：

```
print(frame.head())
```

输出：

```
   state  year  pop
0   Ohio  2000  1.5
1   Ohio  2001  1.7
2   Ohio  2002  3.6
3  Nevada  2001  2.4
4  Nevada  2002  2.9
```

如果指定了列序列，DataFrame 的列就会按照指定顺序进行排列：

```
frame = pd.DataFrame(data, columns=['year', 'state', 'pop'])
print(frame)
```

输出：

```
   year   state  pop
0  2000    Ohio  1.5
1  2001    Ohio  1.7
2  2002    Ohio  3.6
3  2001  Nevada  2.4
4  2002  Nevada  2.9
5  2003  Nevada  3.2
```

##### 3.1.2-2获取 DataFrame 的列和行

DataFrame 的列可以通过字典标记的方式或属性的方式获取为一个 Series：

```
print(frame['state'])
print(frame.state)
```

要获取行，可以使用 `loc` 属性：

```
print(frame.loc[2])
```

列可以通过赋值的方式进行修改。例如，给空的 "debt" 列赋上一个标量值或一组值：

```
frame['debt'] = 16.5
print(frame)
```

或者给 "debt" 列赋上一个数组：

```
import numpy as np

frame['debt'] = np.arange(6.)
print(frame)
```

将列表或数组赋值给某个列时，其长度必须跟 DataFrame 的长度相匹配。如果赋值的是一个 Series，就会精确匹配 DataFrame 的索引，所有的空位都将被填上缺失值。

##### 3.1.2-3删除列

关键字 `del` 用于删除列：

```
del frame['eastern']
print(frame.columns)
```

##### 3.1.2-4DataFrame 构造函数可接受的数据类型

表5-1 列出了 DataFrame 构造函数所能接受的各种数据。

| 类型                    | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 二维 ndarray            | 数据矩阵，还可以传入行标和列标                               |
| 数组、列表或元组的字典  | 每个序列会变成 DataFrame 的一列。所有序列的长度必须相同      |
| NumPy 的结构化/记录数组 | 类似于“数组的字典”                                           |
| Series 字典             | 每个 Series 会成为一列。如果没有显示指定索引，则各 Series 的索引会被合并成结果的行索引 |
| 字典的字典              | 同样，每个内层字典会成为一列                                 |
| 字典或 Series 的列表    | 同样，每个元素会成为一行                                     |
| 列表或元组的列表        | 类似于“二维 ndarray”                                         |
| 另一个 DataFrame        | 除非传入 `index` 和 `columns` 参数，否则继承 DataFrame 的索引和列名 |

## 3.2 基本功能

### 3.2.1 重新索引（Reindex）

在 pandas 中，`reindex` 是一个重要的方法，它的作用是创建一个新对象，其数据符合新的索引。这个方法在 Series 和 DataFrame 上都可以使用。

**在 Series 上重新索引**

考虑下面的例子：

```
import pandas as pd

obj = pd.Series([4.5, 7.2, -5.3, 3.6], index=['d', 'b', 'a', 'c'])
print(obj)
```

这个 Series 对象的索引为 `['d', 'b', 'a', 'c']`。使用 `reindex` 方法，可以根据新的索引进行重排。如果某个索引值当前不存在，就引入缺失值：

```
obj2 = obj.reindex(['a', 'b', 'c', 'd', 'e'])
print(obj2)
```

上述代码中，`'e'` 这个索引原先不存在，因此引入了缺失值 `NaN`。

对于有序数据（比如时间序列），在重新索引时可能需要进行一些插值处理。`method` 选项可以实现这个目的。例如，使用 `ffill` 可以实现前向值填充：

```
obj3 = pd.Series(['blue', 'purple', 'yellow'], index=[0, 2, 4])
print(obj3)
obj3.reindex(range(6), method='ffill')
```

在上述代码中，`obj3` 的索引是 `[0, 2, 4]`，通过 `reindex` 和 `ffill` 进行重新索引时，使用前向值填充。这样，新索引 `[1, 3, 5]` 处的值会根据前一个索引处的值填充。

在 DataFrame 上重新索引

在 DataFrame 中，`reindex` 方法可以修改行索引和列。如果只传递一个序列，会重新索引结果的行：

```
import numpy as np

frame = pd.DataFrame(np.arange(9).reshape((3, 3)), index=['a', 'c', 'd'], columns=['Ohio', 'Texas', 'California'])
print(frame)
frame2 = frame.reindex(['a', 'b', 'c', 'd'])
print(frame2)
```

在上述代码中，`frame` 是一个 3x3 的 DataFrame，通过 `reindex` 方法，可以重新索引结果的行，新增的索引 `'b'` 处会引入缺失值。

列可以通过 `columns` 关键字重新索引：

```
states = ['Texas', 'Utah', 'California']
frame.reindex(columns=states)
```

上述代码中，`frame` DataFrame 的列为 `['Ohio', 'Texas', 'California']`，通过 `reindex` 方法重新索引列，新增的列 `'Utah'` 处会引入缺失值。

**reindex函数的各参数及说明。**

![image-20231219193523383](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231219193523383.png)

### 3.2.2 丢弃指定轴上的项

要丢弃某个轴上的一个或多个项，可以使用 `drop` 方法。由于可能需要执行一些数据整理和集合逻辑，`drop` 方法返回的是一个在指定轴上删除了指定值的新对象。

**在 Series 上使用 drop**

考虑以下例子：

```
import pandas as pd
import numpy as np

obj = pd.Series(np.arange(5.), index=['a', 'b', 'c', 'd', 'e'])
print(obj)
```

这是一个带有索引的 Series 对象。使用 `drop` 方法，可以删除指定索引的项：

```
new_obj = obj.drop('c')
print(new_obj)

obj.drop(['d', 'c'])
```

上述代码中，`new_obj` 是删除了索引为 `'c'` 的项后的新 Series 对象。

#### 

在 DataFrame 中，可以删除任意轴上的索引值。首先，创建一个示例 DataFrame：

**在 DataFrame 上使用 drop**

在 DataFrame 中，可以删除任意轴上的索引值。首先，创建一个示例 DataFrame：

```
data = pd.DataFrame(np.arange(16).reshape((4, 4)),
                    index=['Ohio', 'Colorado', 'Utah', 'New York'],
                    columns=['one', 'two', 'three', 'four'])
print(data)
```

使用 `drop` 方法，可以删除指定行标签（axis 0）的行：

```
data.drop(['Colorado', 'Ohio'])
```

通过传递 `axis=1` 或 `axis='columns'` 可以删除列的值：

```
data.drop('two', axis=1)
data.drop(['two', 'four'], axis='columns')
```

**注意事项**

许多函数，如 `drop`，会修改 Series 或 DataFrame 的大小或形状。可以选择是否就地修改对象，通过传递 `inplace=True` 参数可以就地修改对象：

```
obj.drop('c', inplace=True)
```

需要小心使用 `inplace` 参数，因为它会销毁所有被删除的数据。

### 3.2.3 索引、选取和过滤

在 Pandas 中，对 Series 和 DataFrame 进行索引、选取和过滤的方式类似于 NumPy 数组的索引，但是 Series 的索引值可以是非整数。以下是一些例子：

**在 Series 上进行索引和选取**

考虑以下 Series 对象：

```
import pandas as pd
import numpy as np

obj = pd.Series(np.arange(4.), index=['a', 'b', 'c', 'd'])
print(obj['b'])
print(obj[1])
print(obj[2:4])
print(obj[['b', 'a', 'd']])
print(obj[[1, 3]])
print(obj[obj < 2])
```

在 Series 上可以使用标签或整数进行索引，也可以使用切片或布尔条件进行选取。

**在 DataFrame 上进行索引和选取**

对于 DataFrame，可以通过传递一个值或序列来对其进行索引，这实际上是获取一个或多个列：

```
data = pd.DataFrame(np.arange(16).reshape((4, 4)),
                    index=['Ohio', 'Colorado', 'Utah', 'New York'],
                    columns=['one', 'two', 'three', 'four'])
print(data['two'])
print(data[['three', 'one']])
```

这里，`data['two']` 返回的是 DataFrame 中的 `'two'` 列。

**切片和布尔型数组选取数据**

切片操作也适用于 DataFrame：

```
print(data[:2])  # 选取前两行
print(data[data['three'] > 5])  # 选取满足条件的行
```

此外，还可以使用布尔型 DataFrame 进行索引和赋值：

```
print(data < 5)  # 返回布尔型 DataFrame
data[data < 5] = 0  # 将满足条件的元素赋值为 0
print(data)
```

这使得 DataFrame 的语法与 NumPy 二维数组的语法很相似。

### 3.2.4 使用 `loc` 和 `iloc` 进行选取

在 Pandas 中，使用 `loc` 和 `iloc` 可以方便地选择 DataFrame 中的行和列的子集。

- `loc`: 通过标签进行索引，可同时选择行和列。
- `iloc`: 通过整数进行索引，同样可以同时选择行和列。

**通过标签进行选取**

```
data.loc['Colorado', ['two', 'three']]
```

此例中，选择了 'Colorado' 行中 'two' 和 'three' 列的子集。

**通过整数进行选取**

```
data.iloc[2, [3, 0, 1]]
```

此例中，通过整数索引选择了第 2 行中的第 3、0、1 列的子集。

**切片和布尔条件**

```
data.loc[:'Utah', 'two']
data.iloc[:, :3][data.three > 5]
```

`loc` 中可以使用标签进行切片，而 `iloc` 使用整数进行切片。在最后一个例子中，首先选择了前三列，然后使用布尔条件选取满足条件的行。

总的来说，`loc` 和 `iloc` 提供了一种灵活的方式，可以根据标签或整数进行行和列的选择。在实际使用中，它们更安全和清晰，相比于之前的 `ix` 运算符。

 DataFrame的索引选项

![image-20231219194347036](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231219194347036.png)

### 3.2.5 整数索引问题与解决方法

处理整数索引时，可能会遇到一些问题，因为它与 Python 内置的列表和元组的索引语法有所不同。在 Pandas 中，整数索引容易导致一些意外的结果。下面是一个例子：

```
ser = pd.Series(np.arange(3.))
ser
ser[-1]
```

这里，Pandas 可以进行整数索引，但是会导致一些小问题。虽然我们的索引包含了 0、1、2，但是使用 `-1` 作为索引时，很难确定用户想要的是什么。

对于非整数索引，情况就比较清晰：

```
ser2 = pd.Series(np.arange(3.), index=['a', 'b', 'c'])
ser2[-1]
```

为了解决这个问题，如果轴索引包含整数，最好使用标签或位置索引，具体取决于你的需求。可以使用 `loc`（标签）或 `iloc`（整数）来明确你的意图：

```
ser[:1]
ser.loc[:1]
ser.iloc[:1]
```

这样可以避免因整数索引导致的歧义和 bug。

### 3.2.6 算术运算和数据对齐

Pandas 的一个重要特性是它可以对不同索引的对象进行算术运算，并在不重叠的索引处引入缺失值（NaN）。这类似于在索引标签上进行自动外连接。下面是一个简单的例子：

```
s1 = pd.Series([7.3, -2.5, 3.4, 1.5], index=['a', 'c', 'd', 'e'])
s2 = pd.Series([-2.1, 3.6, -1.5, 4, 3.1], index=['a', 'c', 'e', 'f', 'g'])
s1 + s2
```

结果会自动进行数据对齐操作，在不重叠的索引处引入了 NaN 值。

对于 DataFrame，对齐操作会同时发生在行和列上：

```
df1 = pd.DataFrame(np.arange(9.).reshape((3, 3)), columns=list('bcd'), index=['Ohio', 'Texas', 'Colorado'])
df2 = pd.DataFrame(np.arange(12.).reshape((4, 3)), columns=list('bde'), index=['Utah', 'Ohio', 'Texas', 'Oregon'])
df1 + df2
```

这里，将它们相加后将会返回一个新的 DataFrame，其索引和列为原来那两个 DataFrame 的并集。

如果 DataFrame 对象相加，没有共享的列或行标签，结果都会是空：

```
df1 = pd.DataFrame({'A': [1, 2]})
df2 = pd.DataFrame({'B': [3, 4]})
df1 - df2
```

因为 'A' 和 'B' 列均不在两个 DataFrame 对象中，在结果中以缺省值呈现。

### 3.2.7 在算术方法中填充值

在进行算术运算时，如果存在不同索引的位置，我们可以通过填充值的方式处理缺失值。例如：

```
df1 = pd.DataFrame(np.arange(12.).reshape((3, 4)), columns=list('abcd'))
df2 = pd.DataFrame(np.arange(20.).reshape((4, 5)), columns=list('abcde'))
df2.loc[1, 'b'] = np.nan

df1 + df2
```

上述操作会在没有重叠的位置产生 NaN 值。如果想要在没有重叠的位置填充特定值，可以使用 `add` 方法，并传入 `fill_value` 参数：

```
df1.add(df2, fill_value=0)
```

这样，没有重叠的位置会用填充值进行填充。

表格中列出了一些灵活的算术方法：

![image-20231219195037799](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231219195037799.png)



在对Series或DataFrame进行重新索引时，可以使用 `reindex` 方法，并通过 `fill_value` 参数指定填充值。例如：

```
df1.reindex(columns=df2.columns, fill_value=0)
```

上述代码中，`df1` 的列会根据 `df2` 的列进行重新索引，同时使用填充值 0 来填充在 `df1` 中没有的列。这样，没有重叠的位置就会用填充值进行填充。

### 3.2.8 DataFrame和Series之间的运算

跟不同维度的NumPy数组一样，DataFrame和Series之间的算术运算也是有明确规定的。先来看一个具有启发性的例子，计算一个二维数组与其某行之间的差：

```
arr = np.arange(12.).reshape((3, 4))
arr
```

输出：

```
array([[ 0.,  1.,  2.,  3.],
       [ 4.,  5.,  6.,  7.],
       [ 8.,  9., 10., 11.]])
```

当我们从arr减去arr[0]，每一行都会执行这个操作。这就叫做广播（broadcasting），附录A将对此进行详细讲解。DataFrame和Series之间的运算差不多也是如此：

```
frame = pd.DataFrame(np.arange(12.).reshape((4, 3)),
                      columns=list('bde'),
                      index=['Utah', 'Ohio', 'Texas', 'Oregon'])
series = frame.iloc[0]
frame
series
```

输出：

```
                    b     d     e
Utah    0.0  1.0  2.0
Ohio    3.0  4.0  5.0
Texas   6.0  7.0  8.0
Oregon  9.0 10.0 11.0

b    0.0
d    1.0
e    2.0
Name: Utah, dtype: float64
```

默认情况下，DataFrame和Series之间的算术运算会将Series的索引匹配到DataFrame的列，然后沿着行一直向下广播：

```
frame - series
```

输出：

```
                    b    d    e
Utah    0.0 0.0 0.0
Ohio    3.0 3.0 3.0
Texas   6.0 6.0 6.0
Oregon  9.0 9.0 9.0
```

如果某个索引值在DataFrame的列或Series的索引中找不到，则参与运算的两个对象就会被重新索引以形成并集:

```
series2 = pd.Series(range(3), index=['b', 'e', 'f'])
frame + series2
```

输出：

```
                    b   d    e   f
Utah    0.0 NaN 3.0 NaN
Ohio    3.0 NaN 6.0 NaN
Texas   6.0 NaN 9.0 NaN
Oregon  9.0 NaN 12.0 NaN
```

如果你希望匹配行且在列上广播，则必须使用算术运算方法。例如：

```
series3 = frame['d']
frame.sub(series3, axis='index')
```

输出：

```
                    b    d    e
Utah   -1.0  0.0  1.0
Ohio   -1.0  0.0  1.0
Texas  -1.0  0.0  1.0
Oregon -1.0  0.0  1.0
```

传入的轴号就是希望匹配的轴。在本例中，我们的目的是匹配DataFrame的行索引（axis='index' or axis=0）并进行广播。

### 3.2.9 函数应用和映射

NumPy的ufuncs（元素级数组方法）也可以用于操作pandas对象：

```
frame = pd.DataFrame(np.random.randn(4, 3), columns=list('bde'),
                     index=['Utah', 'Ohio', 'Texas', 'Oregon'])
np.abs(frame)
```

输出：

```
               b         d         e
Utah     0.204708  0.478943  0.519439
Ohio     0.555730  1.965781  1.393406
Texas    0.092908  0.281746  0.769023
Oregon   1.246435  1.007189  1.296221
```

另一个常见的操作是，将函数应用到由各列或行所形成的一维数组上。DataFrame的apply方法即可实现此功能：

```
f = lambda x: x.max() - x.min()
frame.apply(f)
```

输出：

```
b    1.802165
d    1.684034
e    2.689627
dtype: float64
```

这里的函数f计算了一个Series的最大和最小的差，在frame的每列都执行了一次。结果是一个Series，使用frame的列作为索引。

如果传递axis='columns'到apply，这个函数会在每行执行：

```
frame.apply(f, axis='columns')
```

输出：

```
Utah      0.998382
Ohio      2.521511
Texas     0.676115
Oregon    2.542656
dtype: float64
```

许多最为常见的数组统计功能都被实现成DataFrame的方法（如sum和mean），因此无需使用apply方法。

传递到apply的函数不是必须返回一个标量，还可以返回由多个值组成的Series：

```
def f(x):
    return pd.Series([x.min(), x.max()], index=['min', 'max'])
frame.apply(f)
```

输出：

```
            b         d         e
min -0.555730  0.281746 -1.296221
max  1.246435  1.965781  1.393406
```

元素级的Python函数也是可以用的。假如你想得到frame中各个浮点值的格式化字符串，使用applymap即可：

```
format = lambda x: '%.2f' % x
frame.applymap(format)
```

输出：

```
            b     d     e
Utah    -0.20  0.48 -0.52
Ohio    -0.56  1.97  1.39
Texas    0.09  0.28  0.77
Oregon   1.25  1.01 -1.30
```

之所以叫做applymap，是因为Series有一个用于应用元素级函数的map方法：

```
frame['e'].map(format)
```

输出：

```
Utah      -0.52
Ohio       1.39
Texas      0.77
Oregon    -1.30
Name: e, dtype: object
```

### 3.2.10 排序和排名

根据条件对数据集排序（sorting）也是一种重要的内置运算。要对行或列索引进行排序（按字典顺序），可以使用`sort_index`方法，它将返回一个已排序的新对象：

```
obj = pd.Series(range(4), index=['d', 'a', 'b', 'c'])
obj.sort_index()
```

输出：

```
a    1
b    2
c    3
d    0
dtype: int64
```

对于DataFrame，则可以根据任意一个轴上的索引进行排序：

```
frame = pd.DataFrame(np.arange(8).reshape((2, 4)),
                     index=['three', 'one'],
                     columns=['d', 'a', 'b', 'c'])
frame.sort_index()
```

输出：

```
          d  a  b  c
one       4  5  6  7
three     0  1  2  3
```

```
frame.sort_index(axis=1)
```

输出：

```
         a  b  c  d
three    1  2  3  0
one      5  6  7  4
```

数据默认是按升序排序的，但也可以降序排序：

```
frame.sort_index(axis=1, ascending=False)
```

输出：

```
         d  c  b  a
three    0  3  2  1
one      4  7  6  5
```

若要按值对Series进行排序，可以使用其`sort_values`方法：

```
obj = pd.Series([7, -5, 7, 4, 2, 0, 4])
obj.sort_values()
```

输出：

```
1   -5
5    0
4    2
0    4
6    4
2    7
3    7
dtype: int64
```

在排序时，任何缺失值默认都会被放到Series的末尾：

```
obj = pd.Series([4, np.nan, 7, np.nan, -3, 2])
obj.sort_values()
```

输出：

```
4   -3.0
5    2.0
0    4.0
2    7.0
1    NaN
3    NaN
dtype: float64
```

当排序一个DataFrame时，你可能希望根据一个或多个列中的值进行排序。将一个或多个列的名字传递给`sort_values`的`by`选项即可达到该目的：

```
frame = pd.DataFrame({'b': [4, 7, -3, 2], 'a': [0, 1, 0, 1]})
frame.sort_values(by='b')
```

输出：

```
   a  b
2  0 -3
3  1  2
0  0  4
1  1  7
```

要根据多个列进行排序，传入名称的列表即可：

```
frame.sort_values(by=['a', 'b'])
```

输出：

```
   a  b
2  0 -3
0  0  4
3  1  2
1  1  7
```

排名会从1开始一直到数组中有效数据的数量。接下来介绍Series和DataFrame的`rank`方法。默认情况下，`rank`是通过“为各组分配一个平均排名”的方式破坏平级关系的：

```
obj = pd.Series([7, -5, 7, 4, 2, 0, 4])
obj.rank()
```

输出：

```
0    6.5
1    1.0
2    6.5
3    4.5
4    3.0
5    2.0
6    4.5
dtype: float64
```

也可以根据值在原数据中出现的顺序给出排名：

```
obj.rank(method='first')
```

输出：

```
0    6.0
1    1.0
2    7.0
3    4.0
4    3.0
5    2.0
6    5.0
dtype: float64
```

这里，条目0和2没有使用平均排名6.5，它们被设成了6和7，因为数据中标签0位于标签2的前面。

你也可以按降序进行排名：

```
# Assign tie values the maximum rank in the group
obj.rank(ascending=False, method='max')
```

输出：

```
0    2.0
1    7.0
2    2.0
3    4.0
4    5.0
5    6.0
6    4.0
dtype: float64
```

在这个例子中，`method='max'`选项将平级的值都分配给了组内的最大排名。

DataFrame可以在行或列上计算排名：

```
frame = pd.DataFrame({'b': [4.3, 7, -3, 2], 'a': [0, 1, 0, 1], 'c': [-2, 5, 8, -2.5]})
frame.rank(axis='columns')
```

输出：

```
    a    b    c
0  2.0  3.0  1.0
1  1.0  3.0  2.0
2  2.0  1.0  3.0
3  2.0  3.0  1.0
```

表格中列出了用于破坏平级关系的`method`选项。

### 3.2.11 带有重复标签的轴索引

- 当轴索引（行或列）具有重复标签时，数据选取的行为会有所不同。以下是带有重复索引值的Series和DataFrame的示例：

  ```
  obj = pd.Series(range(5), index=['a', 'a', 'b', 'b', 'c'])
  ```

  ```
  df = pd.DataFrame(np.random.randn(4, 3), index=['a', 'a', 'b', 'b'])
  ```

- 对于带有重复值的索引，数据选取的行为将根据情况返回不同的结果。如果某个索引对应多个值，则返回一个Series，而对应单个值的索引则返回一个标量值。

  ```
  obj['a']
  # 返回包含多个值的Series
  ```

  ```
  obj['c']
  # 返回标量值
  ```

- 索引的`is_unique`属性可以告诉你它的值是否是唯一的。

  ```
  obj.index.is_unique
  # False
  ```

- 对DataFrame的行进行索引时，也会遇到类似的情况。如果索引对应多个行，则返回一个DataFrame，而对应单个行的索引则返回一个Series。

  ```
  df.loc['b']
  # 返回包含多个行的DataFrame
  ```

这种情况下，由于可能返回多个值，代码可能变得更加复杂，因为输出的类型会根据标签是否有重复而变化。

## 3.3 汇总和计算描述统计

pandas提供了一组用于数学和统计的常用方法，主要属于约简和汇总统计。这些方法用于从Series中提取单个值（如`sum`或`mean`），或从DataFrame的行或列中提取一个Series。这些方法都基于没有缺失数据的假设构建。下面是一个简单的DataFrame示例：

```
df = pd.DataFrame([[1.4, np.nan], [7.1, -4.5], [np.nan, np.nan], [0.75, -1.3]],
                  index=['a', 'b', 'c', 'd'],
                  columns=['one', 'two'])
```

调用DataFrame的`sum`方法将返回一个包含列和的Series：

```
df.sum()
```

传递`axis='columns'`或`axis=1`将按行进行求和运算:

```
df.sum(axis=1)
```

NA值会自动被排除，除非整个切片（行或列）都是NA。通过`skipna`选项可以禁用该功能：

```
df.mean(axis='columns', skipna=False)
```

表5-7列出了这些约简方法的常用选项。

![image-20231219202513556](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231219202513556.png)

有些方法（如`idxmin`和`idxmax`）返回的是间接统计，比如达到最小值或最大值的索引：

```
df.idxmax()
```

另一些方法是累计型的：

```
df.cumsum()
```

还有一种方法既不是约简型也不是累计型，`describe`就是一个例子，它用于一次性产生多个汇总统计：

```
df.describe()
```

对于非数值型数据，`describe`会产生另外一种汇总统计：

```
obj = pd.Series(['a', 'a', 'b', 'c'] * 4)
obj.describe()
```

表5-8列出了所有与描述统计相关的方法。

![image-20231219202526307](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20231219202526307.png)

### 3.3.1 相关系数与协方差

在处理金融数据时，经常需要计算相关系数和协方差。以下是使用pandas处理股票价格和成交量数据的一些示例：

```
import pandas_datareader.data as web

# 使用pandas_datareader下载股票数据（注意：Yahoo! Finance已经不再存在）
all_data = {ticker: web.get_data_yahoo(ticker) for ticker in ['AAPL', 'IBM', 'MSFT', 'GOOG']}
price = pd.DataFrame({ticker: data['Adj Close'] for ticker, data in all_data.items()})
volume = pd.DataFrame({ticker: data['Volume'] for ticker, data in all_data.items()})

# 计算价格的百分数变化
returns = price.pct_change()

# 计算两个Series的相关系数和协方差
returns['MSFT'].corr(returns['IBM'])
returns['MSFT'].cov(returns['IBM'])

# 使用更简洁的语法选择列
returns.MSFT.corr(returns.IBM)

# 计算DataFrame的相关系数和协方差矩阵
returns.corr()
returns.cov()

# 使用corrwith方法计算列或行与另一个Series或DataFrame的相关系数
returns.corrwith(returns.IBM)
returns.corrwith(volume)

# 传入axis='columns'按行计算
returns.corrwith(volume, axis='columns')
```

以上代码演示了如何使用pandas计算相关系数和协方差。相关系数衡量两个变量之间的线性关系，而协方差衡量两个变量的总体趋势。这些统计量对于理解不同资产之间的关联性和波动性非常有用。

### 3.3.2  唯⼀值、值计数以及成员资格

Pandas提供了一些方法来从一维Series中抽取信息，例如查找唯一值、值计数和判断成员资格。

1. `unique()` 方法用于得到Series中的唯一值数组：

   ```
   uniques = obj.unique()
   ```

   返回的唯一值是未排序的。

2. `value_counts()` 方法用于计算Series中各值出现的频率：

   ```
   obj.value_counts()
   ```

   结果Series是按值频率降序排列的。

3. `isin(values)` 方法用于判断向量化集合的成员资格，可以用于过滤Series中或DataFrame列中数据的子集：

   ```
   mask = obj.isin(['b', 'c'])
   obj[mask]
   ```

4. `Index.get_indexer(to_match)` 方法给出一个索引数组，从可能包含重复值的数组到另一个不同值的数组：

   ```
   pd.Index(unique_vals).get_indexer(to_match)
   ```

   返回一个数组，表示to_match中的值在unique_vals中的位置。

5. DataFrame的 `apply(pd.value_counts)` 方法用于得到多个相关列的一张柱状图：

   ```
   result=data.apply(pd.value_counts).fillna(0)
   ```

   结果中的行标签是所有列的唯一值，而这些值是每个列中这些值的相应计数。