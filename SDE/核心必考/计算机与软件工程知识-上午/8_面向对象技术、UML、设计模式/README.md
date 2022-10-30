## 面向对象技术、UML、设计模式

### 试题放置
题目编号大致为：37-47

### 知识点
#### 面向对象(Object-Oriented, OO) 的基本概念
 `面向对象=对象(Object)+分类(Classification)+继承(Inheritance)+通过消息的通信(Communication with Message)`
 
 - 对象：基本的运行时的实体，包括数据（属性）和作用于数据的操作（行为）。所以把一个对象的属性和行为封装为一个整体，封装是一种信息隐蔽技术，使得对象的使用者和生产者分离，使对象的定义和实现分开。
 
 - 消息：对象之间进行通信的一种构造。
 
 - 类：一组大体上相似的对象，描述一组对象的共同行为和属性。类是在对象之上的抽象，对象是类的具体化。
 
 - 继承：父类和子类之间共享数据和方法的机制。
 
 - 多态（Polymorphism）：收到消息，不同的对象收到同一消息的响应结果可以完全不同。
  - 通用多态：参数、包含
  - 特定多态：过载（Overloading）、强制
  
  - 动态绑定（Dynamic Binding）
  把过程调用和响应调用所需要执行的代码加以结合。一个给定的过程调用和代码的结合直到调用时才进行。
  
#### 面向对象分析（Object-Oriented Analys，OOA）
包含5个活动：**认定对象、组织对象、描述对象的相互作用，确定对象的操作、定义对象的内部信息**。

#### 面向对象设计 (Object-Oriented Design, OOD)
OOD是将OOA所创建的分析模型转化为设计模型，目的是定义系统构造蓝图。

设计原则：
-五大原则：
 - 单依原则（Simgle Responsibility Principle, SPR）
 - 开放-封闭原则（Open & Close Principle, OCP）
 - 里氏替换原则（Liskov Substituion Principle, LSP）
 - 依赖倒置原则（Dependence Inversion Principle, DIP）
 - 接口分离原则（Interface Segregation Principle, ISP）
 - 其他
 - 重用发布等价原则（Release Reuse Equivalency Priniple, REP）
 - 共同封闭原则（Common Closure Principle, CCP）
 - 共同重用原则（Common Reuse Principle, CRP）
 - 无环依赖原则（Arcycle Dependencies Principle, ADP）
 - 稳定依赖原则（Stable Dependencies Principle, SDP）
 - 稳定抽象原则（Stable Abstractions Principle, SAP）
