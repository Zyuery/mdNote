### 命令模式

##### 1.1 命令行模式

在命令行模式下，Python 可以通过终端执行脚本文件或者输入交互式命令。

- 执行脚本文件：`python script.py`
- 进入交互式命令行：`python`

##### 1.2 交互模式

交互模式是一种逐行输入和执行 Python 代码的方式，可用于测试简单程序和查看结果。

### 方法与函数

**1、方法**

使用格式：**对象.方法名(...)**

如  s="Hello"          print(s.uppper())

**2、函数**

使用格式：**函数名(对象)**

导入函数库：import math

​           调用 ：math.函数名(...)

例   math.sin(x)返回x的正弦值

### 常用函数：

#### 1. **输入与输出：**

- **input()：** 从用户获取输入。
  ```python
  age = input("Enter your age: ")
  ```

- **print()：** 打印输出到控制台。
  ```python
  print("Hello, World!")
  ```

#### 2. **字符串操作：**

- **str.upper() / str.lower()：** 将字符串转为大写/小写。
  ```python
  text = "Hello"
  uppercase_text = text.upper()
  ```

- **str.strip()：** 去除字符串两端的空白字符。
  ```python
  sentence = "   This is a sentence.   "
  trimmed_sentence = sentence.strip()
  ```

- **str.split()：** 使用指定的分隔符拆分字符串。
  ```python
  words = "Hello, World".split(", ")
  ```

- **str.join()：** 将字符串列表连接为一个字符串。
  ```python
  words = ["Hello", "World", "Python"]
  joined_string = " ".join(words)
  ```

- **str.capitalize() / str.title()：** 将字符串的第一个字母大写/每个单词的首字母大写。
  ```python
  text = "hello world"
  capitalized_text = text.capitalize()
  title_case_text = text.title()
  ```

- **str.find() / str.index()：** 查找子字符串并返回索引。
  ```python
  sentence = "Python is powerful"
  index1 = sentence.find("is")
  index2 = sentence.index("powerful")
  ```

- **str.count()：** 统计子字符串在原字符串中出现的次数。
  ```python
  sentence = "Python is powerful. Python is easy to learn."
  count_python = sentence.count("Python")
  ```

#### 3. **文件处理：**

- **open()：** 打开文件。
  ```python
  file = open("example.txt", "r")
  ```

- **file.read() / file.readline() / file.readlines()：** 读取文件内容。
  ```python
  content = file.read()
  line = file.readline()
  lines = file.readlines()
  ```

- **file.write()：** 向文件写入内容。
  ```python
  file = open("example.txt", "w")
  file.write("Hello, World!")
  ```

- **file.close()：** 关闭文件。
  ```python
  file.close()
  ```

#### 4. **数学函数：**

- **abs()：** 返回数值的绝对值。
  ```python
  absolute_value = abs(-10)
  ```

- **round()：** 四舍五入到指定的小数位数。
  ```python
  rounded_number = round(3.14159, 2)
  ```

- **math.sqrt()：** 返回数值的平方根（需要导入 `math` 模块）。
  ```python
  import math
  square_root = math.sqrt(25)
  ```

- **math.sin() / math.cos() / math.tan()：** 计算数值的正弦/余弦/正切值（需要导入 `math` 模块）。
  ```python
  import math
  sine_value = math.sin(math.radians(30))  # 注意将角度转换为弧度
  ```

#### 5. **时间和日期：**

- **datetime.datetime.now()：** 获取当前日期和时间。
  ```python
  from datetime import datetime
  current_time = datetime.now()
  ```

- **datetime.timedelta：** 表示时间差异。
  ```python
  from datetime import timedelta
  one_day = timedelta(days=1)
  tomorrow = datetime.now() + one_day
  ```

- **strftime()：** 将日期时间对象格式化为字符串。
  ```python
  formatted_time = current_time.strftime("%Y-%m-%d %H:%M:%S")
  ```

### 常用字符串方法：

#### 1. **str.join()：** 将字符串列表连接为一个字符串。
```python
words = ["Hello", "World", "Python"]
joined_string = " ".join(words)
```

#### 2. **str.capitalize() / str.title()：** 将字符串的第一个字母大写/每个单词的首字母大写。
```python
text = "hello world"
capitalized_text = text.capitalize()
title_case_text = text.title()
```

#### 3. **str.find() / str.index()：** 查找子字符串并返回索引。
```python
sentence = "Python is powerful"
index1 = sentence.find("is")
index2 = sentence.index("powerful")
```

#### 4. **str.count()：** 统计子字符串在原字符串中出现的次数。
```python
sentence = "Python is powerful. Python is easy to learn."
count_python = sentence.count("Python")
```

#### 5. **str.startswith() / str.endswith()：** 检查字符串是否以指定的前缀/后缀开头。
```python
filename = "document.txt"
starts_with_doc = filename.startswith("doc")
ends_with_txt = filename.endswith(".txt")
```

#### 6. **str.isalpha() / str.isdigit() / str.isalnum()：** 检查字符串是否只包含字母/数字/字母和数字的组合。
```python
alpha_check = "abc".isalpha()
digit_check = "123".isdigit()
alphanumeric_check = "abc123".isalnum()
```

### 注释

python中的注释用**#**标注

也可以使用快捷键，光标选中目标，**control+/**

# 一、数据类型

### 元组 tuple

##### 1、创

- 使用圆括号 () 创建一个空元组：`my_tuple = ()`
- 使用 tuple() 函数将其他数据类型转换为元组：`my_tuple = tuple([1, 2, 3, 4])`

##### 2、访

- 使用索引访问元组元素：`first_element = my_tuple[0]`
- 使用负数索引从元组末尾开始访问元素：`last_element = my_tuple[-1]`

##### 3、合

- 使用加号运算符或者直接创建新的元组进行合并：`new_tuple = my_tuple + (5, 6)`

##### 4、切

- 使用切片操作获取部分元组：`sub_tuple = my_tuple[1:3]`

##### 5、其他常用函数及方法

- 使用 len() 函数获取元组长度：`length = len(my_tuple)`
- 使用 index() 方法查找元素的索引：`index = my_tuple.index(3)`
- 使用 count() 方法统计指定值在元组中出现的次数：`count = my_tuple.count(3)`

##### 6、性质总结

- 不可变性：元组是不可变的数据结构，一旦创建后，就不能修改其内容。**因此元组可以作字典的键**！
- 有序性：元组中的元素是按照插入顺序依次排列的，可以通过索引访问其中的元素。
- 元素类型多样性：元组中的元素可以是不同类型的对象，就像列表一样。
- 元组长度：可以使用内置函数 len() 来获取元组的长度，即其中包含的元素个数。
- 元组操作：可以对元组进行合并、重复、切片等操作，但不能修改元组中的元素。

### 列表 list

##### 1、创：

- 使用方括号 [] 创建一个空列表：`my_list = []`
- 使用 list() 函数将其他数据类型转换为列表：`my_list = list((1, 2, 3, 4))`

##### 2、访

- 使用索引访问列表元素：`first_element = my_list[0]`
- 使用负数索引从列表末尾开始访问元素：`last_element = my_list[-1]`

##### 3、改

- 直接赋值：`my_list[0] = 'new value'`
- 切片赋值：`my_list[1:3] = [5, 6]`

##### 4、增

- 使用 append() 方法在列表末尾添加元素：`my_list.append(5)`
- 使用 insert() 方法在指定位置插入元素：`my_list.insert(2, 'new element')`

##### 5、删

- 使用 del 语句删除指定位置的元素：`del my_list[0]`

- 使用 remove() 方法删除指定值的元素：`my_list.remove('new element')`

##### 6、其他常用函数及方法

- 使用 len() 函数获取列表长度：`length = len(my_list)`
- 使用 sort() 方法对列表元素进行排序：`my_list.sort()`
- 使用 reverse() 方法反转列表元素的顺序：`my_list.reverse()`
- 使用 index() 方法查找元素的索引：`index = my_list.index('new element')`
- 使用max()  min()可以返回列表里的最大值与最小值。

##### 7、性质总结

- 有序性：列表中的元素是按照插入顺序依次排列的，可以通过索引访问和修改其中的元素。
- 可变性：列表中的元素可以被修改，可以添加新的元素，也可以删除已有的元素。
- 元素类型多样性：列表中的**元素可以是不同类型的对象，甚至可以是其他列表。**
- 列表长度：可以使用内置函数len()来获取列表的长度，即其中包含的元素个数。
- 列表操作：可以对列表进行合并、重复、切片等操作，也可以使用各种方法对列表进行排序、反转、插入和删除等操作。

### 字典 disc

​                            **键 ：值**

​                          **key : value**

键与值之间用**引号**表示**对应**

键值对之间用**逗号**表示**分隔**

##### 1、创

- 使用花括号 {} 来创建一个空字典：`my_dict = {}`
- 使用 dict() 构造函数：`my_dict = dict(key1=value1, key2=value2)`

##### 2、访

- 使用键来访问对应的值：`value = my_dict[key]`
- 使用 get() 方法以及默认值来访问值：`value = my_dict.get(key, default_value)`
- 键 in 字典  会返回一个布尔值

##### 3、增或改

- 直接赋值：`my_dict[key] = value`

##### 4、删

- 使用 del 语句删除指定键值对：`del my_dict[key]`
- 使用 pop() 方法删除指定键，并返回相应的值：`value = my_dict.pop(key)`

##### 5、其他函数及方法

- 使用 keys() 方法获取所有键的视图：`keys_view = my_dict.keys()`
- 使用 values() 方法获取所有值的视图：`values_view = my_dict.values()`
- 使用 items() 方法获取所有键值对的视图：`items_view = my_dict.items()`
- 使用 update() 方法合并另一个字典到当前字典：`my_dict.update(another_dict)`

##### 6、性质总结

- 键值对：字典由键和对应的值组成，每个键值对之间使用冒号“:”分隔，整个字典包裹在花括号 {} 中。
- 键的唯一性：字典中的键必须是唯一的，每个键只能对应一个值。
- 可变性：字典中的值可以修改，也可以动态地添加或删除键值对。
- 无序性：字典中的键值对没有固定的顺序，即使按照特定顺序添加键值对，遍历时也不会按照这个顺序输出。
- 异构性：字典中的值可以是任意数据类型，包括数字、字符串、列表、元组、甚至是另一个字典。
- 长度可变性：字典可以根据需要动态地增加或减少键值对。

### 字符串 str

- **字符串连接**

  **print（“Hello"+"world"+"i")  与print（“Helloworldi")效果完全一样**

  <img src="file:///C:\Users\zengyue\Documents\Tencent Files\3229587344\nt_qq\nt_data\Pic\2023-11\Ori\7c934ae0aa338a1115036111d73a9250.jpg" alt="img" style="zoom: 25%;" />

- **单双引号转义**

  **在通常情况下，单引号与双引号没有太大区别，但当需要打印的字符串里存在双引号，就得仔细甄别引号类型的选择。**

  如：print"He said "Hi".") 这时python会动把前面两个引号配对识别成应字符串。

  为了避免这种情况，

  1、我们可以把外层的**双引号改成单引号**。

  print‘He said "Hi".’) 这样就可以输出正确的结果。

  2、我们还可以使用反斜杠

  print"He said \"Hi\".") 这样即便外层使用的是双引号，也可以正确打印整个字符串。

  

- **换行**

  print("Hello!\nWorld!")与c语言同理

- **三引号跨行字符串**

  **三引号可以是由三个双引号组成，也可是由三个单引号组成。**

  如  我想打印《将进酒》

  <img src="file:///C:\Users\zengyue\Documents\Tencent Files\3229587344\nt_qq\nt_data\Pic\2023-11\Ori\11923c26c0be2c5e173ff329d9b74c75.jpeg" alt="img" style="zoom:25%;" />

  如图，这样可以避免写过多的print和\n，极度简洁明了。

### 整型 int 

   与c语言的整形无太大差别，代表整数。

### 浮点型 float

与c语言的整形无太大差别，代表小数。

### 布尔类型 bool

- Ture 真
- False 假

### 空值类型 None Type

-   只有一个值  None   其含义为完全无值

# 二、变量

- python中的变量可以直接使用，它的类型与其接收的数据类型相同，不需要像C语言一样提前声明或初始化才可使用

- 变量的命名规范

  ​                  1、最好使用英文单词，不要用拼音或a,b这种简单字母。

  ​                  2、最好常用下划线

  ​                                       如 my _love

  ​                  3、不能有空格

  ​                                       如 my love 

  ​                  4、不能以数字开头

  ​                                       如 1 my_love

  ​                  5、 注意区分大小写

  

- 变量的输入

  #### 输入

  我们常用的函数是**input函数**              

  **age=input("请输入您的年龄：")**

  上面这行代码，会先打印”请输入您的年龄“然后读取用户在控制台上输入的**字符串。**

  **注意**：input函数只能返回字符串，如果你想输入变成Int,float类型，可以使用a=int(input())，这样input函数返回的字符串就会被强制转换成整数类型赋值给变量a。

  

  扩展：

  **1、split函数**

  - split()`函数用于将字符串根据指定的分隔符分割成多个子字符串，并返回一个包含分割后的子字符串的列表。

  - 语法：

    ```
    str.split(sep=None, maxsplit=-1)
    ```

    - `sep`（可选）：指定分隔符，默认为None，表示使用空格作为分隔符。
    - `maxsplit`（可选）：指定分割的次数，默认为-1，表示对整个字符串进行分割。

  示例

  sentence = "Hello, world! How are you?"
  words = sentence.split()  # 默认使用空格分割
  print(words)  # ['Hello,', 'world!', 'How', 'are', 'you?']

  numbers = "1,2,3,4,5"
  num_list = numbers.split(',')  # 使用逗号分割
  print(num_list)  # ['1', '2', '3', '4', '5']

  **2、map函数**

  - `map()`函数用于将一个函数应用于迭代器的每个元素，并返回一个包含结果的迭代器对象。

  - 语法：

    ```
    map(function, iterable, ...)
    ```

    - `function`：要应用的函数。
    - `iterable`：一个或多个可迭代对象，如列表、元组等。

​      示例

       user_input = input("请输入一些数字，用空格分隔：")
​               numbers = user_input.split()  # 使用空格分割用户输入的数字
​               numbers = list(map(int, numbers))  # 将用户输入的字符串转换为整数列表
​               print(numbers)

 **3、eval函数**

`eval()`函数是Python中的一个内置函数，用于将字符串当作表达式来求值，并返回表达式的结果。下面是关于`eval()`函数的一些知识点：

1. 语法： `eval(expression, globals=None, locals=None)`

   - `expression`：要求值的字符串表达式。
   - `globals`（可选）：全局命名空间，如果提供，则在求值时使用该命名空间。
   - `locals`（可选）：局部命名空间，如果提供，则在求值时使用该命名空间。

2. 功能：

   - `eval()`函数可以动态地执行字符串表示的代码，并返回表达式的结果。
   - 它可以处理算术运算、逻辑运算、变量赋值等多种操作。

3. 示例用法：

   x = 5
   y = eval('x + 1')  # 求值表达式'x + 1'，相当于执行了 5 + 1
   print(y)  # 输出：6

   math_expr = "2 * (3 + 4)"
   result = eval(math_expr)  # 求值数学表达式，相当于执行了 2 * (3 + 4)
   print(result)  # 输出：14

4. `eval()`函数与`input()`函数搭配使用：

   - `eval()`函数可以与`input()`函数搭配使用，以便求值用户输入的表达式或运算。

   - 示例：

     ```
     math_expr = input("请输入一个数学表达式：")
     result = eval(math_expr)  # 求值用户输入的数学表达式
     print("计算结果为:", result)
     ```

# 三、顺序、分支与循环

### 1、分支

####   if 语句 

​     if [条件]  :

​           [执行语句]#注意执行语句前面必须有”缩进“，一般建议缩进为四个空格。

​           [执行语句]#if下方的前面有缩进的语句，都会被看成条件为真时需要执行的内容

条件可以是布尔值Ture or  False，也可以是表达式（比较、赋值、逻辑。

elif[条件1]：

​    [执行语句A]

elif[条件2]：

​    [执行语句B]

elif[条件3]：

​    [执行语句C]

 else:
     [执行语句D]

<img src="file:///C:\Users\zengyue\Documents\Tencent Files\3229587344\nt_qq\nt_data\Pic\2023-11\Ori\f8b691930d13f3b702d761781f8d9ceb.png" alt="img" style="zoom:25%;" />

#### 逻辑运算

**and 与**

全真则真，一假具假

**or 或**

全假则假，一真具真

**not 非**

取反



注意：逻辑运算符是可以混用的，但混用时需要注意计算优先级。

优先级： not>and>or

当然我们可以用括号改变优先级

### 2、循环

#for循环与while循环的大体区别在于循环次数是否是已知的。

#### 2.1for循环

for循环可以对列表、字典、字符串等进行迭代。

对列表迭代:对元素做一些事情。

对字典迭代：对各个键或各个值做一些事情。

对字符串迭代：对各个字符做事情

for循环也经常与range函数搭配使用

###### 2.1-1 格式

for 变量名 in 可迭代对象：

**注意缩进！！！！！！！！！**

注意 ：for key,value in list.items()这个循环成立，循环会遍历列表里的键和值分别给到key和value。

###### 2.1-2嵌套

例  for i in range(3):  *# 外层循环*    

​          for j in range(2):  *# 内层循环*      

​                 print(i, j)

#补充：**range函数**

`range()` 函数是 Python 中常用的一个函数，用于生成一个整数序列，通常结合循环语句使用。以下是关于 `range()` 函数的一些知识点：

1. 基本语法：`range()` 函数的基本语法为 `range(start, stop, step)`，其中 `start` 表示起始值（默认为0），`stop` 表示结束值（不包含在序列中），`step` 表示步长（默认为1）。
2. 生成整数序列：`range()` 函数可以生成一个整数序列，包括起始值但不包括结束值，步长为指定的值。例如，`range(0, 5, 1)` 生成的序列为 0, 1, 2, 3, 4。
3. 默认参数：`range(stop)` 可以用来生成从0开始到 `stop-1` 结束的整数序列，步长默认为1。
4. 应用：`range()` 函数通常与循环结构（如 `for` 循环）一起使用，用于迭代执行固定次数的代码块。

```
for i in range(5):
    print(i)
```

4.1转换为列表：`range()` 函数生成的是一个 range 对象，如果需要将其转换为列表，可以使用 `list()` 函数进行转换。

```
my_list = list(range(5))
print(my_list)  # 输出：[0, 1, 2, 3, 4]
```

4.2注意事项：Python 2.x 中的 `range()` 函数返回的是一个实际的列表，而在 Python 3.x 中，`range()` 返回的是一个类似于生成器的对象，因此在需要列表的场景中，要注意是否需要进行列表转换。



###### 2.2-1基本语法

`while` 循环通过检查一个条件来决定是否继续执行循环体内的代码。只要条件为真，循环就会一直执行下去。

```
while condition:
    # 执行循环体的代码
```

###### 2.2-2 避免无限循环：

如果循环条件始终为真，循环将会无限执行下去，这将导致程序陷入无限循环状态。为了避免这种情况，你可以在循环体内使用 `break` 语句来提前结束循环，或者确保循环条件在某个时刻变为假。

```
while True:
    # 执行循环体的代码
    if some_condition:
        break  # 提前结束循环
```

###### 2.2-3continue

在循环中，可以使用 `continue` 关键字来跳过当前循环的剩余代码，直接进入下一轮循环。这在某些情况下可能会很有用。

```
while condition:
    if some_condition:
        continue  # 跳过剩余代码，直接进入下一轮循环
    # 其他循环体的代码
```