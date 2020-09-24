# DAY4 —— 变量与基本数据类型

* 变量就是可以变化的量，指事物的某种状态
* 为了让计算机能够像人一样记忆事物的某种状态

## 常量

不变的量： python语法中没有constant的概念， 但是在程序的开发过程中会涉及到常量的概念

变量名全部为大写代表常量，这只是一种**约定**、规范

## 变量的内存管理

### 垃圾回收机制

* 垃圾——引用计数为0

```python
#引用计数增加
x = 10 # 10的引用计数为1
y = x # 10的引用计数为2
z = y # 10的引用计数为3
#引用计数减少
del x # 10的引用计数为2
del y # 10的引用计数为1

z = 12345 # 10的引用计数为0 -> 垃圾
# z 变为指向 12345
```

## 变量有三大组成部分

1. 变量名 -> 是指向等号右侧值的内存地址的，用来访问等号右侧的值
2. 赋值符号 -> 将变量值的内存地址绑定给变量名
3. 变量值 -> 代表记录的事物的状态

见名知意 > 简短

## 变量值的三个重要特征

* ID： 反映的是变量值的内存地址

  id()

* Type： 不同类型的值表示记录不同的状态

  type()

* Value： 值本身

### is 与 ==

* is： 比较左右两个值身份id是否相等
* ==： 比较左右两个值是否相等

```python
x = "info: python"
y = "info: python"
print(x == y)
# OUTPUT: True
# actually,  code "a is b" equals "id(a) == id(b)"
print(x is y)
# OUTPUT: False

m = 10
n = 10
print(m == n)
# OUTPUT: True
print(m is n)
# OUTPUT: True
```

* 小整数池（[-5, 256]）： 从python解释器启动那一刻开始，就会在内存中实现申请一系列内存空间存放好常用的整数。

* id不同的情况下，值有可能相同；id相同的情况下，值一定相等

## 基本数据类型

### 数字类型（int & float）

#### 整形 —— int

```python
age = 18
print(type(age))
# OUTPUT: <class 'int'>
```

#### 浮点型 —— float

```python
salary = 3.3
print(type(salary))
# OUTPUT: <class 'float'>
```

#### Operators

* Division ( / ) always returns a float

  ```python
  17 / 3
  # OUTPUT: 5.666666666666667
  ```

* get an integer result(discarding any fractional result) use ``//``

  note that, the result will not return the floor

  ```python
  17 // 3
  # OUTPUT: 5
  -1 // 2
  # OUTPUT: 0
  ```

* Calculate the remainder use ``%``

  ```python
  17 % 3
  # OUTPUT: 2
  ```

* Calculate powers ``**``

  ```python
  5 ** 2
  # OUTPUT: 25
  ```

### 字符串类型

```python
'a'
"a"
'''a''' """a"""
```

* 字符串相加效率极低

```python
word = 'Python'
word[0]
# OUTPUT: 'P'
word[5]
# OUTPUT: 'n'

word[-1]
# OUTPUT: 'n'
word[-6]
# OUTPUT: 'P'
```

* Note that since -0 is the same as 0, negative indices strat from -1

```python
word[0:2]
# OUTPUT: 'Py'
word[2:5]
# OUTPUT: 'tho'
word[:2]
# OUTPUT: 'Py'
word[4:]
# OUTPUT: 'on'
word[4:42]
# OUTPUT: 'on'
word[42:]
# OUTPUT: ''
```

* Python strings cannot be changed -- they are **immutable**.

```python
word[0] = 'J'
# OUTPUT: 
# Traceback (most recent call last):
# 	File "<stdin>", line1, in <module>
# TypeError: 'str' object does not support item assignment

'J' + word[1:]
# OUTPUT: 'Jython'
```

### 列表类型

 ```python
cubes = [1, 8, 27, 64, 125]
cubes.append(216)
cubes
# OUTPUT: [1, 8, 27, 64, 125, 216]
 ```



````python
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
# replace some values
letters[2:5] = ['C', 'D', 'E']
letters
# OUTPUT: ['a', 'b', 'C', 'D', 'E', 'f', 'g']
# now remove them
letters[2:5] = []
letters
# OUTPUT: ['a', 'b', 'f', 'g']
````

### 字典类型

### 布尔类型

## 其他

* ReformatCode Command+Option+L

