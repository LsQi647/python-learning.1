Python学习

# 变量、运算符、数据类型

## 1、注释

“#” 注释整行

” “ ”    ” “ ” 或者 ‘ ’ ‘    ’ ‘ ’ 注释段落

## 2、运算符

不同于c：

“/”    表示除        eg : 3/4=0.75

“// ”  表示整除    eg : 3 // 4=0

“**” 表示幂        eg : 2 * * 3= 2 ³

"and" 表示与     eg：（3>2) and (3<5) #true

"or"表示或         eg：（1>3)or(9<2) #false

"not"表示非       eg：not（2>1) #false

![image-20220927204934991](D:\typora\Python学习\位运算符)

???↑

 **三元运算符**

small=x if x<y else y ; 

--->if(x<y) small=x; else small=y;

**其他运算符**

| 操作符   | 名称   | 示例                        |
| -------- | ------ | --------------------------- |
| `in`     | 存在   | `'A' in ['A', 'B', 'C']`    |
| `not in` | 不存在 | `'h' not in ['A', 'B', 'C'] |

eg：判断是否存在

letters = ['A', 'B', 'C']
if 'A' in letters:
    print('A' + ' exists')     #A exists
if 'h' not in letters:
    print('h' + ' not exists')      #h not exists

| 操作符   | 名称 | 示例                     |
| -------- | ---- | ------------------------ |
| `is`     | 是   | `"hello" is "hello"`     |
| `is not` | 不是 | `"hello" is not "hello"` |

eg：比较

a、b指向不可变类型

a = "hello"
b = "hello"
print(a is b, a == b)   # True True
print(a is not b, a != b)   # False False

a、b指向可变类型

a = ["hello"]
b = ["hello"]
print(a is b, a == b)  # **False** True
print(a is not b, a != b)  # **True** False

[ps] is和is not对比的是两个变量的<u>*内存地址*</u>

​        ==，!=对比的是两个变量的<u>*值*</u>

若两个变量指向的都是地址不可变的类型（str等 ），is和==是等价的；若两个变量指向的是地址可变的类型（list，dict，tuple等），is和==是有区别的。

**运算符的优先级**

| 符                | 描述                     |
| ----------------- | ------------------------ |
| **                | 指数（最高优先级）       |
| ~+-               | 按位翻转，一元加号和减号 |
| * / % //          | 乘，除，取模和取整除）   |
| + -               | 加法减法                 |
| >> <<             | 右移，左移运算符         |
| &                 | 位‘AND’                  |
| ^\|               | 位运算符                 |
| <=<>>=            | 比较运算符               |
| <>==!=            | 等于运算符               |
| =%=/=//=-=+=*=**= | 赋值运算符               |
| is is not         | 身份运算符               |
| in not in         | 成员运算符               |
| not and or        | 逻辑运算符               |

## 3、变量和赋值

1、字符型变量可以直接相加

myTeacher = "老马的程序人生"
yourTeacher = "小马的程序人生"
ourTeacher = myTeacher **+** ',' **+** yourTeacher
print(ourTeacher)  # 老马的程序人生,小马的程序人生

[ps]**集合**。集合用来保存不重复的元素，即集合中的元素都是唯一的，元素只能是不可变的数据类型（包括整形、浮点型、字符串、元组），无法存储可变的数据类型（列表、字典、集合）。

1、使用{}创建

set_name = {1, 1.2, "字符串", (1,2)}    //可包含不同的数据类型变量

print("set_name:", set_name)   //直接输出

set_name.pop()  //当集合是由列表和元组组成时,set.pop()是从左边删除元素的如下；对于是字典和字符转换的集合是随机删除元素的.

2、set（）函数

set_name1 = set("帅气的读者")

//访问数据元素  返回集合是**无序的**

for  index, item in enumerate(set_name):

print(index, item)

## 4、数据类型与转换

 格式：`<class 'int'>`

eg: a=1031

print(a,**type(a**))    #1031 <class 'int'>

万物皆对象（object），整型也不例外，只要是对象，就有相应的属性 （attributes） 和方法（methods）。

eg:a=1031

print(**bin(a)**)   #0b10000000111     //二进制表示

print(**a.bit_length()**)   #11     //并返回二进制的长度

【扩展】有时候我们想保留浮点型的小数点后 `n` 位。可以用 `decimal` 包里的 `Decimal` 对象和 `getcontext()` 方法来实现；getcontext().prec来调整精度

import decimal

from decimal import Decimal

a = decimal.getcontext()

print(a)

**布尔型**

- 对于数值变量，`0`, `0.0` 都可认为是空的。
- 对于容器变量，里面没元素就是空的。

**获取类型信息**

- `type()` 不会认为子类是一种父类类型，不考虑继承关系。
- `isinstance()` 会认为子类是一种父类类型，考虑继承关系。//判断两个类型是否相同   eg：print(isinstance(1, int))  # True

## 5、print（）函数

**sep**  分隔符，多个参数输出时想要输出中间的分割字符

**end**  输出结束时的字符     默认为\n

eg：

没有参数时，每次输出都会换行

shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed without 'end'and 'sep'.")
for item in shoplist:   //循环
  print(***item***)

[输出]

This is printed without 'end'and 'sep'.

apple

mango

carrot

banana



输出结果用end设置的参数&结尾，并没有默认换行

shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed with 'end='&''.")
for item in shoplist:
  print(***item, end='&'***)
print('hello world')

[输出]

This is printed with 'end='&''.

apple&mango&carrot&banana&hello world



`item`值与`'another string'`两个值之间用`sep`设置的参数`&`分割。

shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed with 'sep='&''.")
for item in shoplist:
    print(item, 'another string', sep='&')

[输出]

This is printed with 'sep='&''.

apple&another string

mango&another string

carrot&another string

banana&another string

# 位运算

## 1、原码、反码和补码

计算机内部用补码表示

**原码**：就是其二进制表示（注意，有一位符号位）。  //最高位为符号位

```python
00 00 00 11 -> 3
10 00 00 11 -> -3
```

**反码**：正数的反码就是原码，负数的反码是符号位不变，其余位取反（对应正数按位取反）。

```python
00 00 00 11 -> 3
11 11 11 00 -> -3
```

**补码**：正数的补码就是原码，负数的补码是反码+1。

```
00 00 00 11 -> 3
11 11 11 01 -> -3
```

## 2、按位运算

**非操作    ~**     //把num的<u>补码</u>中的0和1全部取反，符号位也取反。

~ 1 = 0        ~ 0 = 1

**与操作**    **& **    //只有两个对应位都为1时才为1

1&1=1   1&0=0   0&1=0   0&0=0

```python
00 00 01 01 -> 5
&
00 00 01 10 -> 6
---
00 00 01 00 -> 4
```

**或操作   |**    //只要两个对应位中有一个为1就为1

**异或操作   ^**   //只有两个对应位不同时才为1

满足交换律和结合律

**左移操作    <<**   //num<<i 将二进制表示向左移动i位所得的值    整体向左移动

```python
00 00 10 11 -> 11
11 << 3
---
01 01 10 00 -> 88 
```

**右移操作   >>**   //num>>i 向有移动

## 3、利用位运算符实现快速计算

**通过 `<<`，`>>` 快速计算2的倍数问题。**

```python
n << 1 -> 计算 n*2
n >> 1 -> 计算 n/2，负奇数的运算不可用
n << m -> 计算 n*(2^m)，即乘以 2 的 m 次方
n >> m -> 计算 n/(2^m)，即除以 2 的 m 次方
1 << n -> 2^n
```

通过 `^` 快速交换两个整数。 通过 `^` 快速交换两个整数。

两个数相同为0，不同为1 ，且当一个数异或上2次相同的数后，原数不变，就是说4^5^5其结果还是4        //a ^ a = 0 和 a ^ 0 = a.

```python
a ^= b
b ^= a
a ^= b
```

通过 `a & (-a)` 快速获取`a`的最后为 1 位置的整数。

## 4、利用位运算实现整数集合

比如集合 `{1, 3, 4, 8}`，可以表示成 `01 00 01 10 10` 而对应的位运算也就可以看作是对集合进行的操作。

0100011010

9876543210

元素与集合的操作：

```python
a | (1<<i)  -> 把 i 插入到集合中
a & ~(1<<i) -> 把 i 从集合中删除
a & (1<<i)  -> 判断 i 是否属于该集合（零不属于，非零属于）
```

集合之间的操作：

```python
a 补   -> ~a
a 交 b -> a & b
a 并 b -> a | b
a 差 b -> a & (~b)
```

# 条件语句

## 1、if和else

if 2 > 1 and not 2 > 3**:**
    print('Correct Judgement!')     // Correct Judgement!

【与c不同】

1、没有括号，每个条件语句后有**：**

2、用布尔操作符and，or和not实现

3、Python 使用缩进而不是大括号来标记代码块边界，因此要特别注意`else`的悬挂问题

4、elif 语句即为 else if

## 2、assert

`assert`这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出`AssertionError`的异常。

# 循环语句

## 1、while循环

```python
while 布尔表达式:
    代码块
```

与条件语句一样无括号，靠缩进判断代码关系

## 2、while - else循环

```python
while 布尔表达式:
    代码块
else:
    代码块
```

当`while`循环<u>正常执行完</u>的情况下，执行`else`输出，如果`while`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容。

## 3、for循环

```python
for 迭代变量 in 可迭代对象:
    代码块
```

每次循环，迭代变量被设置为可迭代对象的当前元素，提供给代码块使用。

eg：

for i in 'ILoveLSGO':
    print(i, end=' ')  # 不换行输出  //I L o v e L S G O

eg：

dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for <u>key</u>, <u>value</u> in dic.<u>items()</u>:
    print(key, value, sep=':', end=' ')    //a:1 b:2 c:3 d:4



dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for key in dic.<u>keys()</u>:
    print(key, end=' ')   //a b c d



dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for value in dic.<u>values()</u>:
    print(value, end=' ')  //1 2 3 4

## 4、for - else 循环

```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```

## 5、range() 函数

```python
range([start,] stop[, step=1])
```

- `step=1` 表示第三个参数的默认值是1。step表示生成的数中间间隔几位。
- `range` 这个BIF的作用是生成一个从`start`参数的值开始到`stop`参数的值结束的数字序列，该序列包含`start`的值但不包含`stop`的值。

eg：

for i in range(2, 9):  # 不包含9
    print(i，end=' ')    //2 3 4 5 6 7 8

for i in range(1, 10, 2):
    print(i，end=' ')  //1 3 5 7 9

## 6、enumerate()函数

```python
enumerate(sequence, [start=0])
```

- sequence：一个序列、迭代器或其他支持迭代对象。
- start：下标起始位置。
- 返回 enumerate(枚举) 对象

seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)

//[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]

lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)

//[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]

- for和enumerate()结合使用

  ```python
  for i, a in enumerate(A)
      do something with a  
  ```

i表示该元素的索引值，a表示A中的元素

eg:

languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)

//I love Python

I love R

I love Matlab

I love C++


for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')

//2 I love Python

3 I love R

4  I love Matlab

5  I love C++

## 7、break

`break`语句可以跳出当前所在层的循环。

## 8、continue

`continue`终止本轮循环并开始下一轮循环。

## 9、pass

`pass`是空语句，不做任何操作，只起到占位的作用，其作用是为了保持程序结构的完整性。尽管`pass`语句不做任何操作，但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个`pass`语句，让代码可以正常运行。

```python
def a_func():
    pass
```

## 10、推导式

**列表推导式**

```python
[ expr for value in collection [if condition] ]
```

Eg: x = [-4, -2, 0, 2, 4]
y = [a * 2 for a in x]
print(y)         //[-8, -4, 0, 4, 8]

把x中的每个元素a都×2

[ps] i*2=i×2    i**2=i的二次方

Eg: x = [i for i in range(100) <u>if</u> (i % 2) != 0 and (i % 3) == 0]
print(x)            //[3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99]

if用于条件判断

Eg：a = [(i, j) <u>for</u> i in range(0, 3) <u>for</u> j in range(0, 3)]
print(a)             // [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]

for可多次分别进行

**元祖推导式**

```python
( expr for value in collection [if condition] )
```

a = (x for x in range(10))
print(a)        //<generator object <genexpr> at 0x0000025BE511CC48>

print(tuple(a))       //(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

运用tuple()函数现实数据

**字典推导式**

```python
{ key_expr: value_expr for value in collection [if condition] }
```

b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)     //{0: True, 3: False, 6: True, 9: False}

在1-10中找出3的倍数后判断是否为2的倍数

**集合推导式**

```
{ expr for value in collection [if condition] }
```

Eg：c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)        //{1, 2, 3, 4, 5, 6}

在集合中逐个输出不重复的元素

**其他**

- `next(iterator[, default])`

Eg：e = (i for i in range(10))
print(e)          //<generator object <genexpr> at 0x0000007A0B8D01B0>

print(next(e))      # 0
print(next(e))      # 1

for each in e:
    print(each, end=' ')          // 2 3 4 5 6 7 8 9

next() 把元素输出并移向下一个

- sum（） 求和

s = sum([i for i in range(101)])
print(s)   # 5050
s = sum((i for i in range(101)))
print(s)   # 5050

# 异常处理

## 1、警告总结

- Warning：警告的基类
- DeprecationWarning：关于被弃用的特征的警告
- FutureWarning：关于构造将来语义会有改变的警告
- UserWarning：用户代码生成的警告
- PendingDeprecationWarning：关于特性将会被废弃的警告
- RuntimeWarning：可疑的运行时行为(runtime behavior)的警告
- SyntaxWarning：可疑语法的警告
- ImportWarning：用于在导入模块过程中触发的警告
- UnicodeWarning：与Unicode相关的警告
- BytesWarning：与字节或字节码相关的警告
- ResourceWarning：与资源使用相关的警告

## 2、try-except 语句

```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
```

- 首先，执行`try`子句（在关键字`try`和关键字`except`之间的语句）
- 如果没有异常发生，忽略`except`子句，`try`子句执行后结束。
- 如果在执行`try`子句的过程中发生了异常，那么`try`子句余下的部分将被忽略。如果异常的类型和`except`之后的名称相符，那么对应的`except`子句将被执行。最后执行`try - except`语句之后的代码。
- 如果一个异常没有与任何的`except`匹配，那么这个异常将会传递给上层的`try`中。

【例子】

try:
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError as error:
    print('打开文件出错\n原因是：' + str(error))

//打开文件出错

//原因是：[Errno 2] No such file or directory: 'test.txt'

一个`try`语句可能包含多个`except`子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

Eg：

dict1 = {'a': 1, 'b': 2, 'v': 22}
try:
    x = dict1['y']
except LookupError:
    print('查询错误')
except KeyError:
    print('键错误')
else:
    print(x)

//查询错误

由于`KeyError`是`LookupError`的子类，且将`LookupError`置于`KeyError`之前，因此程序优先执行该`except`代码块。所以，使用多个`except`代码块时，必须坚持对其规范排序，要从最具针对性的异常到最通用的异常。

## 3、try-except-finally语句

try: 检测范围 except Exception[as reason]: 出现异常后的处理代码 finally: 无论如何都会被执行的代码

不管`try`子句里面有没有发生异常，`finally`子句都会执行。

## 4、try-except-else语句

如果在`try`子句执行时没有发生异常，Python将执行`else`语句后的语句。

```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
```

注意：`else`语句的存在必须以`except`语句的存在为前提，在没有`except`语句的`try`语句中使用`else`语句，会引发语法错误。

## 5、raise语句

Python 使用`raise`语句抛出一个指定的异常。

try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')

//An exception flew by!
