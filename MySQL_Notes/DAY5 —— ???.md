# DAY5 —— 

## 垃圾回收机制详解

### 1. 引用计数

```python
x = 10 # 直接引用
print(id(x))
y = x
l = ['a', x] # 间接引用
print(id(l[1]))
# 引用计数：3
```

```python
a = [1, 2, 3]	
b = [1, 2, 3, a]

a[:] = [2, 2, 2]
b
# OUTPUT: [1, 2, 3, [2, 2, 2]]
a = [1, 2, 3]
b
# OUTPUT: [1, 2, 3, [2, 2, 2]]
```

### 2. 标记清除

```python
# 循环引用 -> 导致内存泄漏
l1 = [111, ]
l2 = [222, ]
l1.append(l2)
l2.append(l1)

del l1
del l2
```

在启用标记清除算法时，在栈区扫描，在堆区标记存活。 堆区没有被标记存活的将会被清除。

### 3. 分代回收

* 背景

  基于引用计数的回收机制，每次回收内存，都需要把所有对象的引用计数都遍历一遍，这是非常消耗时间的。于是引入了分代回收来提高回收效率，分代回收采用的是”空间换时间“策略。

* 分代

  在历经多次扫描的情况下，都没有被回收的变量，gc机制就会认为该变量是常用变量，gc对其扫描的频率会降低。

## 与用户交互

#### 接收用户的输入

```python
# 接收用户的输入
username = input("请输入您的账号：")
print(username, type(username))
```

#### 格式化输出

1. ``%``

   ```python
   "my name is %s my age is %s" % ('shanliang', '18')
   
   "my name is %(name)s my age is %(age)s" % ({'name': shanliang, 'age':18})
   ```

2. str.format

   ```python
   "my name is {} my age is {}".format('shanliang', 18)
   "my name is {0} my age is {1}".format('shanliang', 18)
   
   "my name is {name} my age is {age}".format(age=18, name='shanliang')
   ```

3. ``f""``

   ```python
   x = input('your name: ')
   y = input('your age: ')
   res = f'my name is {x}, my age is {y}'
   print(res)
   ```

   

## 基本运算符

### 1. 算数运算符

``+`` , ``-``, ``*``, ``/``, ``//``,``%``, ``**``

###2. 比较运算符

``>``, ``<``, ``>=`` , ``<=`` , ``==``, ``!=``

### 3. 赋值运算符

*  ``=``

* ``+=``, ``-=``, ``*=``, ``/=``, ``//=``, ``**=``, ``%=``

* ```python
  # 链式赋值
  z = y = x = 10
  print(x, y, z)
  print(id(x), id(y), id(z))
  ```

* ```python
  # 交叉赋值
  m, n = n, m
  ```

* ```python
  # 解压赋值
  m0, m1, m2, m3, m4 = [111, 222, 333, 444, 555]
  # 多少都不行
  m0, m1, m2, *_ = [111, 222, 333, 444, 555]
  m0, m1, m2, *aaa = [111, 222, 333, 444, 555]
  # 解压字典默认解压出来的是keys
  m0, m1, m2 = {'a': 1, 'b': 2, 'c': 3}
  # m0 is 'a'; m1 is 'b'; m2 is 'c';
  ```

### 4. 海象运算符

```python
if (n := len(a)) > 10:
  	print(f"List if too long ({n} elements, expected <= 10)")

discount = 0.0
if (mo := re.search(r'(\d+)% discount', advertisement)):
  	discount = float(mo.group(1)) / 100.0
    
while (block := f.read(256)) != '':
  	process(block)
    
[y for x in names if (y := f(x))]
```



