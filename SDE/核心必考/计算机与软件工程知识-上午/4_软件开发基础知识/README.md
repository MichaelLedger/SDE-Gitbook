## 软件开发基础知识

### 试题放置
题目编号大致为：15-19

### 知识点
#### 软件设计原则
软件设计原则始终强调 **高内聚、低耦合** 的设计原则。

具体包括：

**保持模块的大小适中、尽可能减少调用的深度、多扇入少扇出、单入口单出口、模块的作用域应该在模块之内、功能应该是可以被预测的。**

- 什么是扇入和扇出？

在软件设计中，扇入和扇出的概念是指应用程序模块之间的层次调用情况。

按照结构化设计方法，一个应用程序是由多个功能相对独立的模块所组成。

扇入：是指直接调用该模块的上级模块的个数。扇入大表示模块的复用程序高。

扇出：是指该模块直接调用的下级模块的个数。扇出大表示模块的复杂度高，需要控制和协调过多的下级模块；但扇出过小（总是1）也不好。扇出过大一般是因为缺乏中间层次，应该适当增加中间层次的模块。扇出太小时可以把下级模块进一步分解成若干个子功能模块，或者合并到它的上级模块中去。

设计良好的软件结构，通常顶层扇出比较大，中间扇出小，底层模块则有大扇入。


