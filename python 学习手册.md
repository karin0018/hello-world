# python 学习手册

[菜鸟教程 - python教程][https://www.runoob.com/python3/python3-tutorial.html] 学习笔记 

2020.1. 

## 基础语法 + 基本数据结构

- python 保留字

    ```python
    import keyword
    keyword.kwlist #输出当前版本的所有关键字
    ```
    
- 数字类型：支持复数 complex

- 字符串：不可更改内容；单双引号使用完全相同 "\" 转义字符 "r"让反斜杠不发生转义；

- 集合 set ： 由一个或数个形态各异的大小整体组成的，**基本功能**是进行成员关系测试和删除重复元素。 

    > 可以进行集合的数学运算 交 并 差 对称差 等

- 元组 tuple : 元素不能修改 ```(a,b,’karin’) ```

- 字典 dictionary ： 无序的对象集合，字典中元素通过键来存取，而不是偏移存取；

    > { key : value }
    
    ```python
    demodict = {} #创建空字典
    
    demodict['one'] = "value"
    demodict[2] = "value2"
    tinydict = {'name' : 'karin','code' : '1'}
    
    dict() # 构造函数，可以直接从键值对序列中创建字典
    ```
    
- python 默认文件编解码方式为 ```utf-8```

### 数字

- 基本数学运算符：```"**" 乘幂 ; "//" 取整除- 向下（小）取整 "!=" 比较两个引用变量的值是否相等   ```

- **数学函数** import math：abs(x)--数字绝对值;max(x1,x2,x3,…)–返回最大值；
  
    ```python
    := #海象运算符，可在表达式内部为变量赋值
    if(n := len(a)) > 10:
        print(f "List is too long({n} elements,expected <= 10)")
    ```
    
- 成员运算符:```in ：特定序列中找到值返回真 / not in```
  
- 身份运算符：``` is: 判断两个标识符是不是引用自同一个对象```

- 逻辑运算符优先级 ： not and or;

- **随机数函数**：random( ) –随机生成下一个实数，在[0,1) 范围内

    ```python
    import random
    random.choice(range(10)) #从序列元素中随机挑选一个元素
    random.shuffle(lst) #将序列的所有元素随机排序
    random.uniform(x,y)#随机生成下一个实数，在[x,y]范围内
    ```
    
- 还包括 **三角函数**， 和一些数学常量

### 字符串

```python
* 重复输出
[:] 按位置截取字符串，左闭右开 原则
in 在
r/R 原始字符串--不识别转义字符

#字符串格式化输出
print("My name is %s, I'm %d years old" % ('karin',10))

"""python 三引号 
允许一个字符串跨多行，字符串中可以包含换行符，制表符以及其他字符"""

f + 'string' #格式化字符串,表达式用{}括起来

>>> w = {'name': 'Runoob', 'url': 'www.runoob.com'}
>>> f'{w["name"]}: {w["url"]}'
'Runoob: www.runoob.com'
>>>x = 1
>>>print(f'{x+1=}') #可以用 = 拼接运算结果
2

str.count(string,sub) # 查看子串 sub 在主串中出现的次数
```

### 列表 List

>序列都可以进行的操作包括索引，切片，加，乘，检查成员。
>       创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。

```python
list1 = []
# 内置方法
list1.append('apple') # 向末尾添加新元素
list1.pop() # 堆栈使用，后进先出

queque =[] # 队列使用 比较慢
queue.append()
queque.popleft()


\.count(obj) #统计某个对象的出现次数
\.extend(seq) # 在列表末尾一次性追加另一个序列的多个值
\.index(obj) # 第一个匹配项的索引值
\.insert(index,obj) # 插入列表
\.remove(obj) # 移除第一个匹配元素
\.reverse() #反向列表中的元素
\.sort() #排序
\.clear() #清空
list2 = list1.copy() # list2 == list1

del list1[0] # 删除第一个元素
len(list1) #元素个数
```

### 元组 Tuple --不可修改

- 与列表类似，不同之处在于元组的元素**不能修改** -- 元组指向的内存中的内容不可改变；

- 小括号，中间元素用 " , " 隔开

- 使用索引访问，可截取，不可修改元素，使用 del 删除整个 tuple ；

### 字典 Dictionary --可变容器

- 以键值对的形式添加新内容；
- 通过对应的键值访问字典中的值；
- 修改和删除都通过 ```dict['key’] = value  \ del dict['key]``` 的方式进行；
- ABOUT **键**
    - 只能出现一次；
    - 必须不可变；故可以由数字，字符串，元组充当，但列表不行；

- ABOUT **值**：比较自由，可是任何的 python 对象（包括标准的和用户自定义的）；

    ```python
    # 内置方法
    dict1 = {}
    dict.clear() # 删除所有元素
    dict.fromkeys(seq) # 创建一个新的字典，以序列seq中的元素做字典的键，None 为默认值
\.get(key ,default=None) # 返回指定键的值
    \.items() #以列表返回可遍历的键值对元组数组
    \.keys()
    \.values()
    \.setdefault(key,default=None) #和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default
    \.update(dict2)
    \.pop(key)
    \.popitem()
    '''format_map 提取所需信息'''
    >>>phonebook = {'beth': '2345', 'alice': '2323'}
    >>>print("alice's phone number is {alice}.".format_map(phonebook))
    alice's phone number is 2323.
    ```
    
### 集合

```python
parame = set() #创建一个空集合
parame\.add(x)
\.update(x)
\.remove(x)
\.discard(x)
\.pop(x) #随机删除
set.intersection() #交集
\.union() #并集
```

- 去重功能;
- 交 &，差 - ，并 + ，对称差 ^ ;

- [更多内置函数和方法](https://www.runoob.com/python3/python3-set.html)

### 循环

- 循环语句可以有 else 子句，它在穷尽列表(以for循环)或条件变为 false (以while循环)导致循环终止时被执行，但循环被 break 终止时不执行。
- for循环可以遍历任何序列的项目，如一个列表或者一个字符串。

### 迭代器与生成器
- 访问元素的一种方式，可以记住遍历位置的对象；
- 只能前进不可后退，基本方法： ```iter()#创建迭代器 next() #遍历```

### 函数
- 参数：

    必需参数，

    关键字参数（调用时：a=3)，

    默认参数（函数默认 def fuc(a=3) )，

    不定长参数  ( 加 * ，以元组形式存放所有未命名的变量参数；加 ** ，以字典形式导入；单独出现 * 后的参数必须用关键字传入 ）；

-  lambda 函数：

    有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数；``` lambda arg1,arg2,…: expression```
### 模块
- __name__属性：代表在模块被引入时，模块中的某一程序块不执行；
```python
#!/usr/bin/python3
# Filename: using_name.py
# 每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。

if __name__ == '__main__':
   print('程序自身在运行')
else:
   print('我来自另一模块')
```

- dir() 函数：可以找到模块内定义的所有**名称**。以字符串列表的形式返回；如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称；

### 文件读取

```python
f.read()
f.readline()
f.readlines()

f.write(string)
f.tell()
f.seek()
f.close()

 with open('/tmp/foo.txt', 'r') as f:
...     read_data = f.read()
```

### pickle 模块

实现了基本的数据序列和反序列化。

pickle模块的序列化操作：将程序中运行的对象信息保存到文件中去，永久存储。

pickle模块的反序列化操作：能够从文件中创建上一次程序保存的对象。

```python
pickle.dump(obj,file,protocol) # 写入文件 file
pickle.load() # 加载文件
```

### python 异常

- try / except…else
- try - finally
- raise - 抛出异常
- 用户自定义异常：异常类继承自 Exception 类；

## 面向对象编程

- 类：描述具有相同的属性和方法的对象的集合，对象是类的实例；

- 方法：类中定义的函数；

### 1. 类

操作：属性引用  obj.name + 实例化

```python
def __init__(self): #在类实例化时会自动调用 ， 可以有参数
    '''python 中的特殊方法 -- 构造方法'''
    self.data = []
```
类的方法与普通的函数相比只有一个区别：额外的第一个参数名称是 self – 代表类的对象实例；

```python
self #类的实例化对象
self.__class__ # 指向类

#类定义
class people:
    #定义基本属性
    name = ""
    age = 0
    # 定义私有属性，私有属性在类外部无法直接访问
    __weight = 0
    # 定义构造方法（函数），在对象初始化时执行
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print( self.name," said : I'm" + self.age +" years old. ")
        
#实例化类
p = people('karin','20','60')

```

### 继承

支持类的继承和派生；

如果在子类中需要父类的构造方法就需要显式地调用父类的构造方法，或者不重写父类的构造方法。

子类不重写 __init__，实例化子类时，会自动调用父类定义的 __init__。

如果重写了__init__ 时，要继承父类的构造方法，可以使用 super 关键字：

```python
super(子类，self).__init__(参数1，参数2，....)

父类名称.__init__(self,参数1，参数2，...)
```

```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))


# 单继承 
class student(people):# class DerivedClassName(BaseClassName):
    grade = '' #定义子类的特殊属性
    def __init__ (self,n,a,w):
        #调用父类的构造函数。
        people.__init__(self,n,a,w)
        self.grade = g
    #覆盖父类的方法--重新编写
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 

# 多继承 有限的支持多继承形式
class DerivedClassName(Base1,Bae2,Base3):
    '''需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。'''
    
# 方法重写
'''
如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法
'''
#!/usr/bin/python3
 
class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')
 
class Child(Parent): # 定义子类
   def myMethod(self):
      print ('调用子类方法')
 
c = Child()          # 子类实例
c.myMethod()         # 子类调用重写方法
super(Child,c).myMethod() #用子类对象调用父类已被覆盖的方法
```

