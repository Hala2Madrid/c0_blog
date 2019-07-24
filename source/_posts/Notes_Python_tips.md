# Notes: Python 小技巧

### **1. enumerate()**



enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。



```seasons = ['Spring', 'Summer', 'Fall', 'Winter']```

```list(enumerate(seasons))```

[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]



```list(enumerate(seasons, start=1)) # 下标从1开始```

[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]



for循环中使用enumerate()

```seq = ['one', 'two', 'three']
for i, element in enumerate(seasons):
    print(i, element)
```

(0, 'Spring')

(1, 'Summer') 

(2, 'Fall')

(3, 'Winter')



**2. 组合两个可迭代的元组或pivot嵌套的iterables**



\# Combining two iterables

\>>> a = [1, 2, 3]

\>>> b = ['a', 'b', 'c']

\>>> z = zip(a, b)

\>>> z

[(1, 'a'), (2, 'b'), (3, 'c')]



\# Pivoting list of tuples

\>>> zip(*z)

[(1, 2, 3), ('a', 'b', 'c')]



**▍10、可迭代排序（可以通过“compare”函数排序）**



\>>> a = [1, 2, -3]

\>>> sorted(a)

[-3, 1, 2]



\>>> sorted(a,key=abs)

[1, 2, -3]





**▍12、初始化一个包含重复数字的列表**



\>> [1]* 10

[1, 1, 1, 1, 1, 1, 1, 1, 1, 1]





**▍14、命名和保存iterables切片**



\# Naming slices (slice(start, end, step))

\>>> a = [0, 1, 2, 3, 4, 5]

\>>> LASTTHREE = slice(-3, None)

\>>> LASTTHREE

slice(-3, None, None)

\>>> a[LASTTHREE]

[3, 4, 5]



**▍15、在列表中查找项的索引**



\>>> a = ["foo", "bar", "baz"]

\>>> a.index("bar")

1



**▍16、在iterables**中查找最小/最大项的索引



\>>> a = [2, 3, 1]

\>>> min(enumerate(a),key=lambda x: x[1])[0]

2



**▍17、旋转iterables**的k个元素



\>>> a = [1, 2, 3, 4]

\>>> k = 2

\>>> a[-2:] + a[:-2]

[3, 4, 1, 2]



**▍18、删除字符串末尾/开始/两端无用的字符**



\>>> name = "//George//"

\>>> name.strip("/")

'George'

\>>> name.rstrip("/")

'//George'

\>>> name.lstrip("/")

'George//'



**▍19、倒序iterables的顺序（字符串、列表等）**



\# Reversing string

\>>> s = "abc"

\>>> s[::-1]

"cba"



\# Reversing list

\>>> l = ["a", "b", "c"]

\>>> l[::-1]

["c", "b", "a"]



**branching技巧**



**▍20、多个short-cut**



\>>> n = 10

\>>> 1 < n < 20

True



**▍21、For-else结构在搜索某些东西并找到它时很有用**



for i in mylist:

​    if i == theflag:

​        break

​     process(i)

else:

​    raise ValueError("List argument missing terminal flag.")



**▍22、Trenary operator**



\>>> "Python ROCK"ifTrueelse" I AM GRUMPY"

"Python ROCK"



**▍23、Try-catch-else结构**



try:

​     foo()

except Exception:

​     print("Exception occured")

else:

​     print("Exception didnt occur")

finally:

​     print("Always gets here")



**▍24、While-else结构**



i = 5



while i > 1:

​     print("Whil-ing away!")

​     i -= 1

​    if i == 3:

​        break

else:

​    print("Finished up!")



**comprehensions（推导式）技巧**



**▍25、List推导式**



\>>> m = [x ** 2for x in range(5)]

\>>> m

[0, 1, 4, 9, 16]



**▍26、Set推导式**



\>>> m = {x ** 2for x in range(5)}

\>>> m

{0, 1, 4, 9, 16}



**▍27、Dict推导式**



\>>> m = {x: x ** 2for x in range(5)}

\>>> m

{0: 0, 1: 1, 2: 4, 3: 9, 4: 16}



**▍28、Generator推导式**



\# A generator comprehension is the lazy version of a list comprehension.

\>>> m = (x ** 2for x in range(5))

\>>> m

 at 0x108efe408>

\>>> list(m)

[0, 1, 4, 9, 16]



\>>> m = (x ** 2for x in range(5))

\>>> next(m)

0

\>>> list(m)

[1, 4, 9, 16]



**▍29、list推导使用当前值和过往值**



\>>> a = [1, 2, 4,2]

\>>> [y - x for x,y in zip(a,a[1:])]

[1, 2, -2]



**unpacking技巧**



**▍30、从iterable解压缩变量**



\# One can unpack all iterables (tuples, list etc)

\>>> a, b, c = 1, 2, 3

\>>> a, b, c

(1, 2, 3)



\>>> a, b, c = [1, 2, 3]

\>>> a, b, c

(1, 2, 3)



**▍31、交换变量值**



\>>> a, b = 1, 2

\>>> a, b = b, a

\>>> a, b

(2, 1)



**▍32、在不指示所有元素的情况下从iterable解包变量**



\>>> a, *b, c = [1, 2, 3, 4, 5]

\>>> a

1

\>>> b

[2, 3, 4]

\>>> c

5



**▍33、使用splat运算符解包变量**



\>>> deftest(x, y, z):

\>>>      print(x, y, z)

\>>> res = test(*[10, 20, 30])

102030

\>>> res = test(**{'x': 1, 'y': 2, 'z': 3} )

102030

view raw



**Itertools技巧**



**▍34、Flatten iterables**



\>>> a = [[1, 2], [3, 4], [5, 6]]

\>>> list(itertools.chain.from_iterable(a))

[1, 2, 3, 4, 5, 6]



**▍35、从iterables创建笛卡尔积**



\>>> for p in itertools.product([1, 2, 3], [4, 5]):

\>>>      print(''.join(str(x) for x in p))



(1, 4)

(1, 5)

(2, 4)

(2, 5)

(3, 4)

(3, 5)



**▍36、从iterable创建排列**



\>>> for p in itertools.permutations([1, 2, 3, 4]):

\>>>      print(''.join(str(x) for x in p))

123

132

213

231

312

321



**▍37、从iterable创建ngram**



\>>> from itertools import islice

\>>> defn_grams(a, n):

...          z = (islice(a, i, None) for i in range(n))

...         return zip(*z)

...

\>>> a = [1, 2, 3, 4, 5, 6]

\>>> n_grams(a, 3)

[(1, 2, 3), (2, 3, 4), (3, 4, 5), (4, 5, 6)]

\>>> n_grams(a, 2)

[(1, 2), (2, 3), (3, 4), (4, 5), (5, 6)]

\>>> n_grams(a, 4)

[(1, 2, 3, 4), (2, 3, 4, 5), (3, 4, 5, 6)]



**▍38、使用填充组合元组的两个迭代器或使用填充pivot嵌套迭代**



\>>> import itertools as it

\>>> x = [1, 2, 3, 4, 5]

\>>> y = ['a', 'b', 'c']

\>>> list(zip(x, y))

[(1, 'a'), (2, 'b'), (3, 'c')]



\>>> list(it.zip_longest(x, y))

[(1, 'a'), (2, 'b'), (3, 'c'), (4, None), (5, None)]



**▍39、从一个iterable n中创建k个组合**



\>>> import itertools

\>>> bills = [20, 20, 20, 10, 10, 10, 10, 10, 5, 5, 1, 1, 1, 1, 1]

\>>> list(itertools.combinations(bills, 3))

[(20, 20, 20), (20, 20, 10), (20, 20, 10), ... ]



**▍40、在给定函数情况下创建一个迭代的累积结果**



\>>> import itertools

\>>> list(itertools.accumulate([9, 21, 17, 5, 11, 12, 2, 6], min))

[9, 9, 9, 5, 5, 5, 2, 2]



**▍41、创建一个迭代器，只要谓词为True，就从iterable返回元素**



\>>> import itertools

\>>> itertools.takewhile(lambda x: x < 3, [0, 1, 2, 3, 4])

[0, 1, 2]



\>>> it.dropwhile(lambda x: x < 3, [0, 1, 2, 3, 4])

[3, 4]



**▍42、创建一个迭代器，它从iterable中过滤元素，只返回谓词为False的元素**



\>>> import itertools

\# keeping only false values

\>>> list(itertools.filterfalse(bool, [None, False, 1, 0, 10]))

[None, False, 0]



**▍43、创建一个迭代器，使用从迭代的迭代中获得的参数来计算函数**



\>>> import itertools

\>>> import operator

\>>> a = [(2, 6), (8, 4), (7, 3)]

\>>> list(itertools.starmap(operator.mul, a))

[12, 32, 21]



**collections技巧**



**▍44、设置基本操作**



\>>> A = {1, 2, 3, 3}

\>>> A

set([1, 2, 3])

\>>> B = {3, 4, 5, 6, 7}

\>>> B

set([3, 4, 5, 6, 7])

\>>> A | B

set([1, 2, 3, 4, 5, 6, 7])

\>>> A & B

set([3])

\>>> A - B

set([1, 2])

\>>> B - A

set([4, 5, 6, 7])

\>>> A ^ B

set([1, 2, 4, 5, 6, 7])

\>>> (A ^ B) == ((A - B) | (B - A))

True



**▍45、计数器数据结构（无序集合，其中元素存储为字典键，其计数存储为字典值）**



import collections



\>>> A = collections.Counter([1, 1, 2, 2, 3, 3, 3, 3, 4, 5, 6, 7])

\>>> A

Counter({3: 4, 1: 2, 2: 2, 4: 1, 5: 1, 6: 1, 7: 1})

\>>> A.most_common(1)

[(3, 4)]

\>>> A.most_common(3)

[(3, 4), (1, 2), (2, 2)]



**▍46、默认字典结构（字典的子类，在访问不存在的键时检索默认值）**



\>>> import collections

\>>> m = collections.defaultdict(int)

\>>> m['a']

0



\>>> m = collections.defaultdict(str)

\>>> m['a']

''

\>>> m['b'] += 'a'

\>>> m['b']

'a'



\>>> m = collections.defaultdict(lambda: '[default value]')

\>>> m['a']

'[default value]'

\>>> m['b']

'[default value]'



\>>> m = collections.defaultdict(list)

\>>> m['a']

[]



**▍47、有序的dict结构（保持有序字典的子类）**



\>>> from collections import OrderedDict



\>>> d = OrderedDict.fromkeys('abcde')

\>>> d.move_to_end('b')

\>>> ''.join(d.keys())

'acdeb'



\>>> d.move_to_end('b', last=False)

\>>> ''.join(d.keys())

'bacde'



**▍48、Deques结构（Deques是堆栈和队列的概括）**



\>>> import collection

\>>> Q = collections.deque()

\>>> Q.append(1)

\>>> Q.appendleft(2)

\>>> Q.extend([3, 4])

\>>> Q.extendleft([5, 6])

\>>> Q

deque([6, 5, 2, 1, 3, 4])

\>>> Q.pop()

4

\>>> Q.popleft()

6

\>>> Q

deque([5, 2, 1, 3])

\>>> Q.rotate(3)

\>>> Q

deque([2, 1, 3, 5])

\>>> Q.rotate(-3)

\>>> Q

deque([5, 2, 1, 3])



\>>> last_three = collections.deque(maxlen=3)

\>>> for i in range(4):

...         last_three.append(i)

...     print', '.join(str(x) for x in last_three)

...

0

0, 1

0, 1, 2

1, 2, 3

2, 3, 4



**▍49、命名元组结构（创建类元组的对象，这些对象的字段可通过属性查找访问，也可索引和迭代）**



\>>> import collections

\>>> Point = collections.namedtuple('Point', ['x', 'y'])

\>>> p = Point(x=1.0, y=2.0)

\>>> p

Point(x=1.0, y=2.0)

\>>> p.x

1.0

\>>> p.y

2.0



**▍50、使用字典来存储Switch**



\>>> func_dict = {'sum': lambda x, y: x + y, 'subtract': lambda x, y: x - y}

\>>> func_dict['sum'](9,3)

12

\>>> func_dict['subtract'](9,3)

6



**▍51、数据类结构**



\>>> from dataclasses import dataclass



\>>> @dataclass

\>>> classDataClassCard:

\>>>      rank: str

\>>>      suit: str



\>>> queen_of_hearts = DataClassCard('Q', 'Hearts')

\>>> queen_of_hearts.rank

'Q'

\>>> queen_of_hearts

DataClassCard(rank='Q', suit='Hearts')

\>>> queen_of_hearts == DataClassCard('Q', 'Hearts')

True



**其他技巧**



**▍52、生成uuid**



\# This creates a randomized

\#128-bit number that will almost certainly be unique.

\# In fact, there are over 2¹²² possible

\#UUIDs that can be generated.

\#That’s over five undecillion (or 5,000,000,000,000,000,000,000,000,000,000,000,000).



\>>> import uuid

\>>> user_id = uuid.uuid4()

\>>> user_id

UUID('7c2faedd-805a-478e-bd6a-7b26210425c7')



**▍53、使用LRU缓存进行记忆**



import functools



@functools.lru_cache(maxsize=128)

deffibonacci(n):

​    if n == 0:

​        return0

​    elif n == 1:

​        return1

​    return fibonacci(n - 1) + fibonacci(n - 2)



**▍54、Suppression of expressions**



\>>> from contextlib import suppress

\>>> with contextlib.suppress(ZeroDivisionError):

\>>> 10/0

\# No exception raised



**▍55、在需要设置和拆卸时创建上下文管理**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://docs.python.org/2/library/contextlib.html?source=post_page---------------------------*



**▍56、一种处理文件路径的优雅方法（3.4≥）**



\>>> from pathlib import Path

\>>> data_folder = Path("source_data/text_files/)



\# Path calculation and metadata

\>>> file_to_open = data_folder / "raw_data.txt"

\>>> file_to_open.name

"raw_data.txt"

\>>> file_to_open.suffix

"txt"

\>>>file_to_open.stem

"raw_data"



\# Files functions

\>>> f = open(file_to_open)

\>>> f.read()

\# content of the file

\>>> file_to_open.exists()

True



**▍57、将标准操作符实现为类的函数**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://docs.python.org/3/library/operator.html?source=post_page---------------------------*



**▍58、创建装饰器来分离concerns**



\>>>from functools import wraps



\>>>defadd_sandwich(wrapped):

\>>>      @wraps(wrapped)

\>>>     defwrapper(*args, **kwargs):

\>>>         return wrapped(*args, **kwargs) + ' sandwich'

\>>>     return wrapper



\>>>@add_sandwich

\>>>defham():

\>>>     return'ham'



\>>>ham()

'ham sandwich'



**▍59、使用yield创建一个简单的迭代器**



\>>> deffoo(lst):

\>>>     for x in lst:

\>>>         yield x

\>>>         yield x*2



\>>> a = [1, 3]

\>>> list(foo(a))

[1, 2, 3, 6]



**▍60、yield from use cases and tricks**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://stackoverflow.com/questions/9708902/in-practice-what-are-the-main-uses-for-the-new-yield-from-syntax-in-python-3?source=post_page---------------------------*



**彩蛋**



**▍61、Anti-gravity**



import antigravity



antigravity.fly()



**▍62、The Zen of Python**



\>>> import this

The Zen of Python, by Tim Peters

Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren not special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one and preferably only one obvious way to do it.

Although that way may not be obvious at first unless you are Dutch.

Now is better than never.

Although never is often better than *right* now.

If the implementation is hard to explain, it is a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea let us do more of those!



**▍63、另一种很酷彩蛋**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://github.com/OrkoHunter/python-easter-eggs?source=post_page--------------------------*



**理解context的技巧**



**▍64、使用_main_ .py文件显式标记入口点**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://shaneoneill.io/2019/06/12/use-__main__-py/?source=post_page---------------------------*



**▍65、对象属性列表**



\>>> dir()

['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__']

\>>> dir("Hello World")

['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']



**▍66、关于活动对象的附加信息**



![img](https://mp.weixin.qq.com/data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

*地址：*

*https://docs.python.org/3/library/inspect.html?source=post_page---------------------------*



希望以上66个小贴士对你在今天的学习和工作中有所帮助哦！