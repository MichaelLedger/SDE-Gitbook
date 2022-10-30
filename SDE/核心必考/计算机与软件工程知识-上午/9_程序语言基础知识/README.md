## 程序语言基础知识

### 试题放置
题目编号大致为：48-50

### 知识点
#### python语言的特点
跨平台、开源、简单易学、面向对象、可移植性、解释性、开源、高级语言、可扩展性、丰富的库、动态编程等等。

python不是编译型语言，而是解释型语言。

#### python的数据结构
**不可变数据(3个)：Number（数字）、String（字符串）、Tuple（元组）。**

tuple (元组)是一种不可变的、有序的序列结构，其中元素可以重复。

**可变数据(3个)：List（列表）、Dictionary（字典）、Set（集合）。**

Set (集合)的基本功能是进行成员关系测试和删除重复元素。

#### Python语言深度学习
TensorFlow：Tensorflow拥有多层级结构，可部署于各类服务器、PC终端和网页并支持GPU和TPU高性能数值计算，被广泛应用于谷歌内部的产品开发和各领域的科学研究，支持Python语言深度学习。

PyTorch：PyTorch是一个针对深度学习，并且使用GPU和CPU来优化的tensor library（张量库）是由Torch7团队开发，是一个以Python优先的深度学习框架，不仅能实现强大的GPU加速，同时还支持动态的神经网络。

Keras：Keras是一个由Python编写的开源人工神经网络库，可以作为Tensorflow、Microsoft-CNTK和Theano的高阶应用程序接口，进行深度学习模型的设计、调试、评估、应用和可视化。

Matplotlib 是一个 Python 的 2D绘图库，它以各种硬拷贝格式和跨平台的交互式环境生成出版质量级别的图形，**不支持深度学习**。



#### python用pip安装numpy

**numpy是开源的数值计算扩展，可用来存储和处理大型矩阵**，比Python自身的嵌套列表（nested list structure)结构要高效的多。

很多库都是以此库为依赖库的，所以特别重要。最常用的是它的数组功能，`numpy.array([,,,,,])`

安装方法是：首先 `cmd` 下跳到 C:\Python27\Scripts，再使用 `easy_install.exe pip` 安装pip，最后通过 `pip install numpy` 可直接安装numpy。

#### python的List结构

X=[1,2]表示List结构，X*2表示重复2次，运算结果为[1,2,1,2]。

直接赋值：其实就是对象的引用（别名）。

浅拷贝(copy)：拷贝父对象，不会拷贝对象的内部的子对象。

深拷贝(deepcopy)： copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象。

`[ 0 ] * n` 是浅拷贝， 也就是把一个列表重复了 n 次；

`[[0]*n]*m` 这种方式是直接将 `[0]*n` 复制了m遍

`[0 for _ in range(n)]` 才是创建，深拷贝

```
m,n = 3,4
dp1 = [[0] * n ] * m
dp2 = [[0 for _ in range(n) ] for _ in range(m)]
dp3 = [[0] * n for _ in range(m)]
dp1[0][2] = 3
dp2[0][2] = 3
dp3[0][2] = 3
print('dp1:',dp1)
print('dp2:',dp2)
print('dp2:',dp3)
```
结果为：
```
dp1: [[0, 0, 3, 0], [0, 0, 3, 0], [0, 0, 3, 0]]
dp2: [[0, 0, 3, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
dp2: [[0, 0, 3, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
```

#### 引用调用（call by reference）和值调用（call by value）
**通常 Java 中引用数据类型是引用传递（call by reference），基本数据类型是值传递（call by value）**

- 值传递不可以改变原变量的内容和地址 -> 函数调用时是把实参的值传给形参，函数调用结束后形参的值不能带回给实参。

- 引用传递不可以改变原变量的地址，但可以改变原变量的内容 -> 函数调用时是把实参的地址传给形参，也就是说实参和形参共用同一个存储空间，函数调用结束后，形参值改变，同时形参的值就“带回”给了实参。

### 参考
[python用pip安装numpy](https://www.muzhuangnet.com/show/13731.html)
