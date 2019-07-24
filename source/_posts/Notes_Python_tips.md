# Notes: Python 小技巧

### **1. enumerate()**

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
```

[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]

```python
list(enumerate(seasons, start=1)) # 下标从1开始
```

[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]



for循环中使用enumerate()

```python
for i, element in enumerate(seasons):
    print(i, element)
```

(0, 'Spring')

(1, 'Summer') 

(2, 'Fall')

(3, 'Winter')



###  **2. zip()**

Combining two iterables

```python
a = [1, 2, 3]
b = ['a', 'b', 'c']
z = zip(a, b)
print(z)
```

[(1, 'a'), (2, 'b'), (3, 'c')]



Pivoting list of tuples

```python
zip(*z)
```

[(1, 2, 3), ('a', 'b', 'c')]



### **3. sorted()**

```python
a = [1, 2, -3, 4]
sorted(a)
```

[-3, 1, 2, 4]



```python
sorted(a, key=abs) # 以参数key的结果作为排序的依据
```

[1, 2, -3]



### **4. 列表扩展**

```python
[1] * 10
```

[1, 1, 1, 1, 1, 1, 1, 1, 1, 1]



### **5. slice() 保存切片**

\# slice(start, end, step)

```python
a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
a_slice = slice(1, 7, 2)
a[a_slice]
```

[1, 3, 5, 7]



### **6. 在列表中查找某项的索引**

```python
a = ["foo", "bar", "baz"]
a.index("baz")
```

2



### **7. 在iterables中查找最大/最小项的索引**

```python
a = [2, 3, 1]
max(enumerate(a), key=lambda x: x[1])[0] # 最大值3对应的索引
```

1



### **8. 旋转iterables中的k个元素**

```python
a = [1, 2, 3, 4, 5, 6]
k = 3
a[-3:] + a[:-3]
```

[4, 5, 6, 1, 2, 3]



### **9. 删除字符串开头/末尾/两端无用的字符**

```python
name = "//Tom//"
print(name.strip("/")) # 删两头
print(name.ltrip("/")) # 删开头
print(name.rtrip("/")) # 删末尾
```

'Tom'

'//Tom'

'Tom//'



### **10. 颠倒iterables的顺序（字符串、列表等）**

\# Reversing string

```python
a = "bcdefg"
a[::-1]
```

'gfedcb'



\# Reversing list

```python
ls = ["a", "b", "c", "d", "e"]
ls[::-1]
```

["e", "d", "c", "b", "a"]



### **11. comprehensions（推导式）技巧**