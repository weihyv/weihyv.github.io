# 



## 数据的存储结构:

### 数据的存储结构:

数据的存储结构一般包括三个内容

- 内容存储：存储数据元素的内容(值),每个元素占据独立的可访问的存储区==必须具备==
- 关系存储：直接或间接地存储个数据元素间的逻辑关系==必须具备==
- 附加存储：一般是为了便于运算实现而设置的辅助结点==根据需求设置==

数据的存储结构可用四种==方式==获取:

- 顺序存储:所有节点放到一片连续存储区域,逻辑关系通过物理位置关系间接表示(数组)线性结构
- 连接存储:节点不连续，逻辑关系通过附加的指针来表示，每个元素存储区分两部分，一部分数据，一部分指针。
- 索引存储：存储节点信息的同时，附加索引表，索引中的每一项是索引项，形式为（关键字，地址）关键字标识一个节点的数据项，若每个节点在索引表中都有索引项，称为
- 散列存储

## 数据结构:

### 大O表示法:

- 赋值语句:一个算法所实施的操作数量或步骤数可作为
  独立于具体程序/机器的度量指标。一条赋值语句同时包含了（表达式）计算和（变量）
  存储两个基本资源。除了与计算资源无关的
  定义语句外，主要就是三种控制流语句和赋值语句，
  而控制流仅仅起了组织语句的作用，并不实施处理。

![1627546112336](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627546112336.png)

![1627546181153](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627546181153.png)

==表内数据增长趋势依次递增==

- 大O表示法
  表示了所有上限中最小的那个上限。
- 大𝛀表示法
  表示了所有下限中最大的那个下限。
- 大𝚹表示法
  如果上下限相同，那么就可以用大𝚹表示

![1627546402427](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627546402427.png)

![1627546451878](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627546451878.png)

- 最常用的是：按索引取值和赋值（v =
  a[i], a[i]= v）
  由于列表的随机访问特性，这两个操作执行时间
  与列表大小无关，均为O(1)
- lst.append(v)，执行时间是O(1)
- lst= lst+ [v]，执行时间是O(n+k)，其中k是被加的列表长度
- 字典与列表不同，根据关键码（key）找
  到数据项，而列表是根据位置（index）
  最常用的取值get和赋值set，其性能为O(1)
  另一个重要操作contains(in)是判断字典中是
  否存在某个关键码（key），这个性能也是O(1)

![1627548058102](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627548058102.png)

## 线性结构

- 线性结构是一种有序数据项的集合，其中
  每个数据项都有唯一的前驱和后继，不同线性结构的关键区别在于数据项增减的方式。有的结构只允许数据项从一端添加，而有的结构
  则允许数据项从两端移除

  ## 

### 栈Stack

- 栈stack

  - 一种有次序的数据项集合，在栈中，数据项的加入和移除都仅发生在同一端。
  - 距离栈底越近的数据项，留在栈中的时间
    就越长
    而最新加入栈的数据项会被最先移除。
  - 这种次序通常称为“后进先出LIFO”：
    Last in First out
    这是一种基于数据项保存时间的次序，时间越短的离栈顶越近，而时间越长的离栈底越近。
  - 实例：浏览器的“后退back”按钮，最先back的是最
    近访问的网页
    Word的“Undo”按钮，最先撤销的是最近操作。
  - 但性能有所不同，栈顶首端的版本（左），其
    push/pop的复杂度为O(n)，而栈顶尾端的实现
    （右），其push/pop的复杂度为O(1)

- 抽象数据类型“栈”定义为如下的操作：

  - Stack()：创建一个空栈，不包含任何数据
  - push(item)：将item加入栈顶，无返回值
  - pop()：将栈顶数据项移除，并返回，栈被修改
  - peek()：“窥视”栈顶数据项，返回栈顶的数
    据项但不移除，栈不被修改
  - isEmpty()：返回栈是否为空栈
  - size()：返回栈中有多少个数据项

- HTML/XML文档也有类似于括号的开闭
  标记，这种层次结构化文档的校验、操作
  也可以通过栈来实现

- 第一个左括号（最早打开），就应该匹配
  最后一个右括号（最后遇到）
  这种次序反转的识别，正好符合栈的特性

![1627549077553](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627549077553.png)

!2312](C:\Users\18644\Pictures\2312![2312](C:\Users\18644\Pictures\2312.png).png)



#### 前缀中缀后缀表达式：

- 中缀表达式：A + B	A + B * C	A + B * C + D    
- 前缀表达式：+ A B        + A * B C        + + A * B C D
- 后缀表达式：A B +        A B C * +        A B C * + D +

#### 中缀转后缀：

如果单词是操作数，则直接添加到后缀表达式列表的
末尾
如果单词是左括号“(”，则压入opstack栈顶
如果单词是右括号“)”，则反复弹出opstack栈顶
操作符，加入到输出列表末尾，直到碰到左括号
如果单词是操作符“*/+-”，则压入opstack栈顶

#### 后缀表达式求值：

作为栈结构的结束，我们来讨论“后缀表
达式求值”问题
，跟中缀转换为后缀问题不同，
在对后缀表达式从左到右扫描的过程中，
由于操作符在操作数的后面，
所以要暂存操作数，在碰到操作符的时候
，再将暂存的两个操作数进行实际的计算

仍然是栈的特性：操作符只作用于离它最近的两
个操作数

### 队列Queue

队列是一种有次序的数据集合，其特征是

- 新数据项的添加总发生在一端（通常称为“尾
  rear”端）
- 而现存数据项的移除总发生在另一端（通常称为
  “首front”端）
- 当数据项加入队列，首先出现在队尾，随
  着队首数据项的移除，它逐渐接近队首。
- 新加入的数据项必须在数据集末尾等待，
  而等待时间最长的数据项则是队首
- 这种次序安排的原则称为（FIFO:First-in
  first-out）先进先出
- 不允许数据项直接插入队中，也不允许从中间移
  除数据项
- 将List首端作为队列
  尾端
  List的末端作为队列
  首端
  enqueue()复杂度为
  O(n)
  dequeue()复杂度为
  O(1)

### 双端队列Deque

- 双端队列并不具有内在的LIFO或者
  FIFO特性
- 双端队列Deque是一种有次序的数据集
- 跟队列相似，其两端可以称作“首”“尾”端，
  但deque中数据项既可以从队首加入，也可以从
  队尾加入；数据项也可以从两端移除。
  某种意义上说，双端队列集成了栈和队列的能力
- 如果用双端队列来模拟栈或队列
  需要由使用者自行维护操作的一致性

addFront/removeFr
ont O(1)
addRear/removeRea
r O(n)

List下标0作为
deque的尾端
List下标-1作为
deque的首端

### 采用链表实现无序表

- 虽然列表数据结构要求保持数据项的前后
  相对位置，但这种前后位置的保持，并不
  要求数据项依次存放在连续的存储空间

- 链表实现：节点Node
  - 链表实现的最基本元素是节点Node
  - 每个节点至少要包含2个信息：数据项本身，以
    及指向下一个节点的引用信息
  - 注意next为None的意义是没有下一个节点了，
    这个很重要

- 无序表UnorderedList
  - 设立一个属性head，保存对第一个节点的引用
    空表的head为None
  - 随着数据项的加入，无序表的head始终
    指向链条中的第一个节点
  - 无序表mylist对象本身并不包含数据项（数据项在节点中）
  - 其中包含的head只是对首个节点Node的引用
    判断空表的isEmpty()很容易实现
    -  return self.head == None
  - 添加数据项：
    - 考虑如何实现向无序表中添加数
      据项，实现add方法。由链表结构我们知道
      ：要访问到整条链上的所有数据项，都必须从表头head开始，沿着next链接逐
      个向后查找
      ，所以添加新数据项最快捷的位置是表头，
      整个链表的首位置。

![1627902053080](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627902053080.png)

==定义节点及其属性包含节点数据，结点指向，更新节点数据，更新结点指向。==



![1627902086554](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627902086554.png)

==定义无序表的头指针==

[](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627902129407.png)

![1627902588720](C:\Users\18644\AppData\Roaming\Typora\typora-user-images\1627902588720.png)

==从链表头部插入数据==

```python
class node1:
    def __init__(self, listdata):#定义节点属性，节点对应值，节点下一项索引
        self.data = listdata
        self.next = None

    def getdata(self):#获取节点当前对应值
        return self.data

    def updata(self, Newdata):#更新节点数据
        self.data = Newdata

    def setnext(self, newnext):#更新节点下一项索引
        self.next = newnext


class unorderlist:
    def __init__(self):#创建空列表
        self.head = None

    def add(self, listdata):#添加列表元素
        temp = node1(listdata)
        temp.next = self.head
        self.head = temp

    def size(self):#计算列表长度
        temp = self.head
        count = 0
        while temp != None:
            temp = temp.next
            count += 1
        return count

    def search(self, item):#搜寻元素是否在列表中
        temp = self.head
        find = False
        while not find and temp != None:
            if temp.data == item:
                find = True
            else:
                temp=temp.next
        return find

    def remove(self, item):
        temp = self.head#记录当前节点
        temppre = None#记录前一项节点
        find = False
        while not find:#当要删除的数据在最后，需要记录None,所以不必！=None
            if temp.data == item:
                find = True
            else:
                temppre = temp
                temp = temp.next
        if temppre == None: #要搜寻元素是第一个元素       
            self.head = temp.next    
        else:
            temppre.setnext(temp.next)

M = unorderlist()
M.add(5)
M.add(6)
M.add(7)
print(M.head.next.next.data)
print(M.size())
```

## 递归

- 一种有去有回的逻辑：将大问题转换为小问题并且问题的模式相同，解决途径也相同，并且存在一种简单情况，能够使递归在简单情况退出。

- ```
  f(4)=>4*f(3)
  f(4)=>4*(3*f(2))
  f(4)=>4*(3*(2*f(1)))
  f(4)=>4*(3*(2*(1*f(0))))
  f(4)=>4*(3*(2*1))
  f(4)=>4*(3*2)
  f(4)=>4*6
  f(4)=>24
  
  ```

  

1、进制转换

2、分形树：递归时要返回初始状态，以保证后续问题解决模式与初次相同。从何而起，从何而终。

3、谢尔宾斯基三角形：借助记录每个三角形的三个顶点。根据每个三角形进行画图。

4、汉诺塔：

5、迷宫：注意递归的返回条件，当遇到标记过的地方或者死路结束递归，返回失败。碰到“出口”方格，即“位于边缘的通道”
方格，递归调用结束，返回成功！海龟在四个方向上探索都失败，递归调用结束，
返回失败

### ==递归三定律==

- ### 基本结束条件，解决最小规模问题

- 缩小规模，向基本结束条件演进

- 调用自身来解决已缩小规模的相同问题

问题解决依赖于若干缩小了规模的问题
汇总得到原问题的解

```python
方法一：
#谢尔宾斯基三角形
import turtle
#引入海龟实例对象，初始化海鬼属性
t = turtle
t.pensize(3)
t.penup()
t.goto(-300, -50)
t.pendown()
t.speed(8)
t.color('black', 'black')
#填充黑色的大三角形
t.begin_fill()
for i in range(3):
    t.forward(500)
    t.left(120)
t.end_fill()
#画白色倒三角形
t.color('black', 'white')
t.forward(250)
def white_triangle(l):
    t.begin_fill()
    t.left(60)
    for i in range(3):
        t.forward(l)
        t.left(120)
    t.right(60)
    t.end_fill()
#画谢尔宾斯基三角形
def Sierpinski(n=0):
    if n < 4:
    #设置长度
        l = 250/(2**n)
        #画右侧三角形
        t.forward(l)
        white_triangle(l)
        Sierpinski(n+1)
        #画左侧三角形
        t.backward(2*l)
        white_triangle(l)
        Sierpinski(n+1)
        #画上方三角形
        t.left(60)
        t.penup()
        t.forward(2*l)
        t.pendown()
        t.right(60)
        white_triangle(l)
        Sierpinski(n+1)
        #返回初始位置
        t.penup()
        t.forward(l)
        t.right(120)
        t.forward(2*l)
        t.left(120)
        t.pendown()
white_triangle(250)
Sierpinski(1)
        
#方法二：
import turtle
t = turtle.Turtle()
#定义三角形初始位置
points = {'left': (-200, -100),
          'top': (0, 200),
          'right':(200, -100)}
#画谢尔宾斯基三角形
def sierpinski(n, points):
    colormap = ['blue', 'red', 'green', 'white', 'orange']
    drawTriangle(points, colormap[n])
    if n > 0:
        #记录所有左方三角形三个顶点坐标
        sierpinski(n-1,
                   {'left': points['left'],
                    'top': getMid(points['left'],points['top']),
                    'right': getMid(points['left'], points['right'])})
        #记录所有画上方三角形三个顶点坐标
        sierpinski(n-1,
                   {'left': getMid(points['left'], points['top']),
                    'top': points['top'],
                    'right': getMid(points['top'], points['right'])})
        #记录所有画右方三角形三个顶点坐标
        sierpinski(n - 1,
                   {'left': getMid(points['left'], points['right']),
                    'top': getMid(points['top'], points['right']),
                    'right': points['right']})

#取中点
def getMid(p1, p2):
    return ((p1[0]+p2[0])/2, (p1[1]+p2[1])/2)

#以三角形三个顶点坐标画三角形
def drawTriangle(points, color):
    t.fillcolor(color)
    t.penup()
    t.goto(points['top'])
    t.pendown()
    t.begin_fill()
    t.goto(points['left'])
    t.goto(points['right'])
    t.goto(points['top'])
    t.end_fill()

```

### 优化问题和贪心策略：

优化问题：计算机中许多算法都是为了找到最优解

贪心策略解决找零兑换问题：

- 从最大面值的硬币开始，用尽量多的数量
- 有余额的再到下一最大面值的硬币，还用尽量多的数量，一直到找完为止

##### 找零问题:

假设某次顾客投进$1纸币，买了ȼ37的东西，要
找ȼ63，那么最少数量就是：2个quarter（ȼ25）
、1个dime（ȼ10）和3个penny（ȼ1），一共6个因为这个古怪的国家除了上面3种面值之外，还
有一种【ȼ21】的硬币！贪心策略失效

```python
#方法一:重复数目及多,递归次数极多
#定义找零运算函数:输入零钱列表,找零数目
def recMC(coinvaluelist, change):
    #最小面值一分,最大找零数目为零钱数目
    minCoin = change
    #寻找最优解,零钱数恰好为货币面值:
    if change in coinvaluelist:
        return 1
    else:
        #遍历面值列表,找到比零钱数目小的面值
        for i in [c for c in coinvaluelist if c <= change]:
            #记录所用货币总个数
            numCoin = 1 + recMC(coinvaluelist, change - i)
            if numCoin < minCoin:
                minCoin = numCoin
    return minCoin


print(recMC([1, 5, 10, 25], 63))

#优化方法一:中间结果记录,记忆化,函数值存储技术提高了递归解法的性能
def recMC(coinvaluelist, change, bestlist):
    #最小面值一分,最大找零数目为零钱数目
    minCoin = change
    if change in coinvaluelist:
        #记录最优解
        bestlist[change] = 1
        return 1
    	#当前零钱存在最优解
    elif bestlist[change] > 0:
        return bestlist[change]
    else:
        for i in [c for c in coinvaluelist if c <= change]:
            numCoin = 1 + recMC(coinvaluelist, change - i, bestlist)
            if numCoin < minCoin:
                minCoin = numCoin
                bestlist[change] = minCoin
        return minCoin

#零钱只有1-63这63种清况bestlist[63]为所求结果
print(recMC([1, 5, 10, 25, 21], 63, [0] * 64))


#方法二:辣鸡解法
#记录最小货币量,当前货币量
def coincount(change, bestresult=None, coins=0):
    if bestresult == None:
        bestresult = change
    if change in dict1.keys():
        return coins + 1
    # if coins > bestresult:
    #     return bestresult
    else:
        for i in [c for c in dict1.keys() if c < change]:
            m = coincount(change - i, bestresult, coins + 1)
            if m < bestresult:
                bestresult = m
    return bestresult

print(coincount(63))

```



### 动态规划

- 动态规划算法采用了一种更有条理的方式来得到问题的解.

- 找零兑换的动态规划算法从==最简单的“1分钱找零”的最优解开始==，逐步递加上去
  ，直到我们需要的找零钱数

- 在找零递加的过程中，设法==保持每一分钱的递加都是最优解==，一直加到求解找零钱数, 自然得到最优解

- 递加的过程能保持最优解的==关键是其依赖于更少钱数最优解==的简单计算，而更少钱数的最优解已经得到了。

- 问题的==最优解包含了更小规模子问题的最优解==，这是一个最优化问题能够用动态规划策略解决的==必要条件==。

- 对于找零问题:

  - numcoins = min { 1+numcoins(change-1)

     			       1+numcoins(change-5)

    ​				1+numcoins(change-10)

    ​				1+numcoins(change-21)

    ​				1+numcoins(change-25)}

```
list1 = [1, 5, 10, 15, 21, 25]
coinlist = [0] * 64
coinsused = [0] * 64

def countcoins(change, list1, coinslist, coinsused):
    #从一开始递增,寻找每个钱数的最优解
    for i in range(change + 1):
        newcent = 1
        coins = i
        #遍历货币值,查看减去货币值之后钱数的最优解,找到最优解(只有货币值变化时,最优解会发生突变)
        for m in [c for c in list1 if c <= i]:
            if coinslist[i - m] + 1 < coins:
                coins = coinslist[i - m] + 1
                #记录当前得到最优解时选用的货币
                #for 循环体中的创建的变量,在外部无效.需要在外部初始化
                newcent = m
        #记录每种钱数的最优解
        coinslist[i] = coins
        #记录得到最优解选择的其中一个货币面值
        #如果不初始化,外部无法引用newcent
        coinsused[i] = newcent
    return coinslist[change]

#通过最优解中一个货币面值,再继续查找子规模最优解中的一个货币面值,直到结束
def printcoins(coins, change):
    cent = change
    while cent > 0:
        print(coins[cent])
        cent = cent - coins[cent]


print(countcoins(63, list1, coinlist, coinsused))

```

## 排序与查找

#### 顺序表查找:二分法,算法复杂度是O(log n)

- 这个递归调用使用了列表切片，而切片操作的复
  杂度是O(k)，这样会使整个算法的时间复杂度稍
  有增加；
  当然，我们采用切片是为了程序可读性更好，实
  际上也可以不切片，而只是传入起始和结束的索
  引值即可，这样就不会有切片的时间开销了。

#### 冒泡排序和选择排序算法及分析

选择排序和冒泡排序都是对序列表进行n-1趟排序,每一趟排序比较==n - ( i - 1 )个元素,其中i为第i趟排序== 将该趟排序中的最大(最小)元素放置到该序列表对应位置上

- 冒泡排序是直接两两进行交换,当该趟操作不进行交换时,则证明该趟元素已经按照顺序排列,后续可以不再进行排序,排序结束.
- 选择排序是记录该趟排序



- 冒泡排序的算法思路在于对无序表进行多
  趟比较交换，

- 每趟包括了多次两两相邻比较，并将逆序
  的数据项互换位置，最终能将本趟的最大
  项就位

- 经过n-1趟比较交换，实现整表排序

- 每趟的过程类似于“气泡”在水中不断上
  浮到水面的经过

- 算法过程总需要n-1趟，随着趟数的增加
  ，比对次数逐步从n-1减少到1，并包括可
  能发生的数据项交换

- 比对的时间复杂度是O(n^2^)

- 关于交换次数，时间复杂度也是O(n^2^)，
  通常每次交换包括3次赋值

- 最好的情况是列表在排序前已经有序，交换次数为0

- 最差的情况是每次比对都要进行交换，交换次数等于比对次数

- 平均情况则是最差情况的一半

- 但有一点优势，就是无需任何额外的存储
  空间开销。

- 另外，通过监测每趟比对是否发生过交换
  ，可以提前确定排序是否完成,这也是其它多数排序算法无法做到的,如果某趟比对没有发生任何交换，说明列
  表已经排好序，可以提前结束算法

  ```python
  #改进性能的冒泡排序
  def sortlist(alist):
      #初始化标志变量
      exchange = True
      #列表长度
      passnum = len(alist) - 1
      #n -1趟排序
      while passnum > 0 and exchange:
          ##初始化标志变量
          exchange = False
          for i in range(passnum):
              if alist[i] > alist[i+1]:
                  exchange = True
                  alist[i], alist[i+1] = alist[i+1], alist[i]
          passnum = passnum - 1
  
  alist = [20,30,40,90,50,60,70,80,100,110]
  sortlist(alist)
  print(alist)
  ```

  

选择排序Selection Sort

- 选择排序对冒泡排序进行了改进，保留了
  其基本的多趟比对思路，每趟都使当前最
  大项就位。

- 但选择排序对交换进行了削减，相比起冒
  泡排序进行多次交换，每趟仅进行1次交
  换，记录最大项的所在位置，最后再跟本
  趟最后一项交换
- 选择排序的时间复杂度比冒泡排序稍优
  - 比对次数不变，还是O(n^2^)
  - 交换次数则减少为O(n)

```python
#选择排序
def sortlist(alist):
    longth = len(alist)
    for i in range(longth - 1, 0, -1):
        maxnum = i
        for j in range(i):
            if alist[j] > alist[maxnum]:
                maxnum = j
        alist[i], alist[maxnum] = alist[maxnum], alist[i]


alist = [20, 30, 40, 60, 70, 80, 100, 110, 90, 50]
sortlist(alist)
print(alist)
```

#### 插入排序:

- 插入排序时间复杂度仍然是O(n^2^)，但算
  法思路与冒泡排序、选择排序不同
- 插入排序维持一个已排好序的子列表，其位置始终在列表的前部，然后逐步扩大这个子列表直到全表
- 第1趟，子列表仅包含第1个数据项，将第
  2个数据项作为“新项”插入到子列表的
  合适位置中，这样已排序的子列表就包含
  了2个数据项
- 第2趟，再继续将第3个数据项跟前2个数
  据项比对，并移动比自身大的数据项，空出位置来，以便加入到子列表中
- 经过n-1趟比对和插入，子列表扩展到全表，排序完成
- 插入排序的比对主要用来寻找“新项”的
  插入位置
- 最差情况是每趟都与子列表中所有项进行
  比对，总比对次数与冒泡排序相同，数量
  级仍是O(n^2^)
- 最好情况，列表已经排好序的时候，每趟
  仅需1次比对，总次数是O(n)

```python
#插入排序
def sortlist(alist):
    m = len(alist)
    for i in range(1, m):
        for j in range(i):
            if alist[i] < alist[j]:
                alist.insert(j, alist.pop(i))
alist = [20, 30, 70, 80, 40, 60, 100, 110, 90, 50]
sortlist(alist)
print(alist)

#插入排序
def sortlist(alist):
    m = len(alist)
    for i in range(1, m):
        indexvalue = alist[i]
        position = i
        while position > 0 and alist[position - 1] > indexvalue:
            alist[position] = alist[position - 1]
            position = position -1
        alist[position] = indexvalue


alist = [20, 30, 70, 80, 40, 60, 100, 110, 90, 50]
sortlist(alist)
print(alist)

```

#### 谢尔排序:

我们注意到插入排序的比对次数，在最好的情况
下是O(n)，这种情况发生在列表已是有序的情况
下，实际上，列表越接近有序，插入排序的比对次数就越少

- 从这个情况入手，谢尔排序以插入排序作为基础
  ，对无序表进行“间隔”划分子列表，每个子列表都执行插入排序
- 随着子列表的数量越来越少，无序表的整
  体越来越接近有序，从而减少整体排序的
  比对次数
- 间隔为3的子列表，子列表分别插入排序
  后的整体状况更接近有序
- 最后一趟是标准的插入排序，但由于前面
  几趟已经将列表处理到接近有序，这一趟
  仅需少数几次移动即可完成
