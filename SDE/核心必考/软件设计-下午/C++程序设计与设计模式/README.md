## C++程序设计与设计模式

###  试题放置
第五大题 (**最后两题选做一题**)

### 简介
C++ 是一种高级语言，它是由 Bjarne Stroustrup 于 1979 年在贝尔实验室开始设计开发的。C++ 进一步扩充和完善了 C 语言，是一种面向对象的程序设计语言。C++ 可运行于多种平台上，如 Windows、MAC 操作系统以及 UNIX 的各种版本。

### 面向对象
面向对象的三个基本特征是：封装、继承、多态

#### 封装
隐藏具体的内部实现细节，仅向外部提供简单的接口

优点：
- 减少耦合：可以独立地开发、测试、优化、使用、理解和修改
- 减轻维护的负担：可以更容易被程序员理解，并且在调试的时候可以不影响其他模块

#### 继承
继承就是在父类的基础上，作出扩展，定义一个子类，而子类跟父类的关系就是is a的关系。

子类比父类拥有更丰富的功能，子类中只需定义与父类的不同之处即可。

#### 多态

多态性可以简单地概括为“一个接口，多种方法”

多态类型： 

a、编译时多态性：通过模板和重载函数实现（子类实现父类中的同名函数，但是接口不一样称为覆盖(override)，或者称为重写） 

b、运行时多态性：通过虚函数实现

#### 面向过程 VS 面向对象
面向过程：为了解决一个问题，分析出解决这个问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候一个一个依次调用就可以了；

而面向对象是站在一个抽象的角度去解决问题，把构成问题事务分解成各个对象，建立对象的目的不是为了完成一个步骤，而是为了描叙某个事物在整个解决问题的步骤中的行为。

### 面向对象设计七大原则
#### 简述
原则都是前人总结出来的经验，遵循这些原则，让我们开发的程序更加健壮易维护。

**七大原则之间并不是相互孤立的，彼此间存在着一定关联，一个可以是另一个原则的加强或是基础。**

违反其中的某一个，可能同时违反了其余的原则。**开闭原则是面向对象的可复用设计的基石**。其他设计原则是实现开闭原则的手段和工具。

一般地，可以把这七个原则分成了以下两个部分:
- **设计目标**: 开闭原则、里氏代换原则、迪米特原则
- **设计方法**: 单一职责原则、接口分隔原则、依赖倒置原则、组合/聚合复用原则

1. 单一职责原则(Single Responsibility Principle, SRP): 一个类只负责一个功能领域中的相应职责
2. 依赖倒置原则(Dependece Inversion Principle, DIP): 抽象不应该不依赖于细节，细节应该依赖于抽象
3. 接口隔离原则(Interface Segregation Principle, ISP): 使用多个专门的接口，而不是用单一的总接口
4. 组合/聚合复用原则(Composite Reuse Principle, CARP): 尽量使用对象组合，而不是继承来达到复用的目的。
5. 迪米特原则(Law of Demeter, LOD): 一个软件实体应当尽可能少地与其他实体发生相互作用
6. 里氏替换原则(Liskov Substitution Prinicple, LSP): 所有引用其（基类）父类的地方都能够透明的引用其子类
7. 开闭原则(Open-Closed Principle, OCP): 对于扩展是开放(open for extension)，对于更改是封闭的(closed for modification)

### 循环
循环类型|描述
-|-
while 循环|当给定条件为真时，重复语句或语句组。它会在执行循环主体之前测试条件。
for 循环|多次执行一个语句序列，简化管理循环变量的代码。
do...while 循环|除了它是在循环主体结尾测试条件外，其他与 while 语句类似。
嵌套循环|您可以在 while、for 或 do..while 循环内使用一个或多个循环。

控制语句|描述
-|-
break 语句|终止 loop 或 switch 语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。
continue 语句|引起循环跳过主体的剩余部分，立即重新开始测试条件。
goto 语句|将控制转移到被标记的语句。但是**不建议在程序中使用 goto 语句**。

一般情况下，C++ 程序员偏向于使用 `for(;;)` 结构来表示一个无限循环。

您可以按 `Ctrl + C` 键终止一个无限循环。

#### goto
goto 语句允许把控制无条件转移到同一函数内的被标记的语句。

**注意**：在任何编程语言中，都不建议使用 goto 语句。因为它使得程序的控制流难以跟踪，使程序难以理解和难以修改。任何使用 goto 语句的程序可以改写成不需要使用 goto 语句的写法。

```
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   int a = 10;

   // do 循环执行
   LOOP:do
   {
       if( a == 15)
       {
          // 跳过迭代
          a = a + 1;
          goto LOOP;
       }
       cout << "a 的值：" << a << endl;
       a = a + 1;
   }while( a < 20 );
 
   return 0;
}
```
goto 语句一个很好的作用是退出深嵌套例程。
```
for(...) {
   for(...) {
      while(...) {
         if(...) goto stop;
         .
         .
         .
      }
   }
}
stop:
cout << "Error in program.\n";
```
消除 goto 会导致一些额外的测试被执行。一个简单的 break 语句在这里不会起到作用，因为它只会使程序退出最内层循环。

### 类 & 对象
C++ 在 C 语言的基础上增加了面向对象编程，C++ 支持面向对象程序设计。类是 C++ 的核心特性，通常被称为用户定义的类型。

类用于指定对象的形式，它包含了数据表示法和用于处理数据的方法。类中的数据和方法称为类的成员。函数在一个类中被称为类的成员。

```
#include <iostream>
 
using namespace std;
 
class Box
{
   public:
      double length;   // 长度
      double breadth;  // 宽度
      double height;   // 高度
      // 成员函数声明
      double get(void);
      void set( double len, double bre, double hei );
};
// 成员函数定义
double Box::get(void)
{
    return length * breadth * height;
}
 
void Box::set( double len, double bre, double hei)
{
    length = len;
    breadth = bre;
    height = hei;
}
int main( )
{
   Box Box1;        // 声明 Box1，类型为 Box
   Box Box2;        // 声明 Box2，类型为 Box
   Box Box3;        // 声明 Box3，类型为 Box
   double volume = 0.0;     // 用于存储体积
 
   // box 1 详述
   Box1.height = 5.0; 
   Box1.length = 6.0; 
   Box1.breadth = 7.0;
 
   // box 2 详述
   Box2.height = 10.0;
   Box2.length = 12.0;
   Box2.breadth = 13.0;
 
   // box 1 的体积
   volume = Box1.height * Box1.length * Box1.breadth;
   cout << "Box1 的体积：" << volume <<endl;
 
   // box 2 的体积
   volume = Box2.height * Box2.length * Box2.breadth;
   cout << "Box2 的体积：" << volume <<endl;
 
 
   // box 3 详述
   Box3.set(16.0, 8.0, 12.0); 
   volume = Box3.get(); 
   cout << "Box3 的体积：" << volume <<endl;
   return 0;
}
```

### 继承
面向对象程序设计中最重要的一个概念是继承。继承允许我们依据另一个类来定义一个类，这使得创建和维护一个应用程序变得更容易。这样做，也达到了重用代码功能和提高执行效率的效果。

当创建一个类时，您不需要重新编写新的数据成员和成员函数，只需指定新建的类继承了一个已有的类的成员即可。这个已有的类称为基类，新建的类称为派生类。

继承代表了 is a 关系。例如，哺乳动物是动物，狗是哺乳动物，因此，狗是动物，等等。
```
// 基类
class Animal {
    // eat() 函数
    // sleep() 函数
};


//派生类
class Dog : public Animal {
    // bark() 函数
};
```

#### 访问控制和继承
派生类可以访问基类中所有的非私有成员。因此基类成员如果不想被派生类的成员函数访问，则应在基类中声明为 private。

我们可以根据访问权限总结出不同的访问类型，如下所示：
访问|public|protected|private
-|-|-|-
同一个类|yes|yes|yes
派生类|yes|yes|no
外部的类|yes|no|no

**一个派生类继承了所有的基类方法，但下列情况除外**：
- 基类的构造函数、析构函数和拷贝构造函数。

- 基类的重载运算符。

- 基类的友元函数。

### 重载运算符和重载函数
C++ 允许在同一作用域中的某个函数和运算符指定多个定义，分别称为函数重载和运算符重载。

重载声明是指一个与之前已经在该作用域内声明过的函数或方法具有相同名称的声明，但是它们的参数列表和定义（实现）不相同。

当您调用一个重载函数或重载运算符时，编译器通过把您所使用的参数类型与定义中的参数类型进行比较，决定选用最合适的定义。选择最合适的重载函数或重载运算符的过程，称为**重载决策**。

```
#include <iostream>
using namespace std;
 
class printData
{
   public:
      void print(int i) {
        cout << "整数为: " << i << endl;
      }
 
      void print(double  f) {
        cout << "浮点数为: " << f << endl;
      }
 
      void print(char c[]) {
        cout << "字符串为: " << c << endl;
      }
};
 
int main(void)
{
   printData pd;
 
   // 输出整数
   pd.print(5);
   // 输出浮点数
   pd.print(500.263);
   // 输出字符串
   char c[] = "Hello C++";
   pd.print(c);
 
   return 0;
}
```

#### 重载运算符
重载的运算符是带有特殊名称的函数，函数名是由关键字 operator 和其后要重载的运算符符号构成的。与其他函数一样，重载运算符有一个返回类型和一个参数列表。

对象作为参数进行传递，对象的属性使用 `this` 运算符进行访问。
```
实例
#include <iostream>
using namespace std;
 
class Box
{
   public:
 
      double getVolume(void)
      {
         return length * breadth * height;
      }
      void setLength( double len )
      {
          length = len;
      }
 
      void setBreadth( double bre )
      {
          breadth = bre;
      }
 
      void setHeight( double hei )
      {
          height = hei;
      }
      // 重载 + 运算符，用于把两个 Box 对象相加
      Box operator+(const Box& b)
      {
         Box box;
         box.length = this->length + b.length;
         box.breadth = this->breadth + b.breadth;
         box.height = this->height + b.height;
         return box;
      }
   private:
      double length;      // 长度
      double breadth;     // 宽度
      double height;      // 高度
};
// 程序的主函数
int main( )
{
   Box Box1;                // 声明 Box1，类型为 Box
   Box Box2;                // 声明 Box2，类型为 Box
   Box Box3;                // 声明 Box3，类型为 Box
   double volume = 0.0;     // 把体积存储在该变量中
 
   // Box1 详述
   Box1.setLength(6.0); 
   Box1.setBreadth(7.0); 
   Box1.setHeight(5.0);
 
   // Box2 详述
   Box2.setLength(12.0); 
   Box2.setBreadth(13.0); 
   Box2.setHeight(10.0);
 
   // Box1 的体积
   volume = Box1.getVolume();
   cout << "Volume of Box1 : " << volume <<endl;
 
   // Box2 的体积
   volume = Box2.getVolume();
   cout << "Volume of Box2 : " << volume <<endl;
 
   // 把两个对象相加，得到 Box3
   Box3 = Box1 + Box2;
 
   // Box3 的体积
   volume = Box3.getVolume();
   cout << "Volume of Box3 : " << volume <<endl;
 
   return 0;
}
```

### 多态
多态按字面的意思就是多种形态。当类之间存在层次结构，并且类之间是通过继承关联时，就会用到多态。

C++ 多态意味着调用成员函数时，会根据调用函数的对象的类型来执行不同的函数。

```
#include <iostream> 
using namespace std;
 
class Shape {
   protected:
      int width, height;
   public:
      Shape( int a=0, int b=0)
      {
         width = a;
         height = b;
      }
      int area()
      {
         cout << "Parent class area :" <<endl;
         return 0;
      }
};
class Rectangle: public Shape{
   public:
      Rectangle( int a=0, int b=0):Shape(a, b) { }
      int area ()
      { 
         cout << "Rectangle class area :" <<endl;
         return (width * height); 
      }
};
class Triangle: public Shape{
   public:
      Triangle( int a=0, int b=0):Shape(a, b) { }
      int area ()
      { 
         cout << "Triangle class area :" <<endl;
         return (width * height / 2); 
      }
};
// 程序的主函数
int main( )
{
   Shape *shape;
   Rectangle rec(10,7);
   Triangle  tri(10,5);
 
   // 存储矩形的地址
   shape = &rec;
   // 调用矩形的求面积函数 area
   shape->area();
 
   // 存储三角形的地址
   shape = &tri;
   // 调用三角形的求面积函数 area
   shape->area();
   
   return 0;
}
```

### 数据抽象
数据抽象是指，只向外界提供关键信息，并隐藏其后台的实现细节，即只表现必要的信息而不呈现细节。

数据抽象是一种依赖于**接口和实现分离**的编程（设计）技术。

让我们举一个现实生活中的真实例子，比如一台电视机，您可以打开和关闭、切换频道、调整音量、添加外部组件（如喇叭、录像机、DVD 播放器），但是您不知道它的内部实现细节，也就是说，您并不知道它是如何通过缆线接收信号，如何转换信号，并最终显示在屏幕上。

因此，我们可以说电视把它的内部实现和外部接口分离开了，您无需知道它的内部实现原理，直接通过它的外部接口（比如电源按钮、遥控器、声量控制器）就可以操控电视。

C++ 编程而言，C++ 类为数据抽象提供了可能。它们向外界提供了大量用于操作对象数据的公共方法，也就是说，外界实际上并不清楚类的内部实现。

在 C++ 中，我们使用类来定义我们自己的抽象数据类型（ADT）。您可以使用类 iostream 的 cout 对象来输出数据到标准输出，如下所示：

```
#include <iostream>
using namespace std;
 
int main( )
{
   cout << "Hello C++" <<endl;
   return 0;
}
```
在这里，您不需要理解 `cout` 是如何在用户的屏幕上显示文本。您只需要知道公共接口即可，`cout` 的底层实现可以自由改变。

**数据抽象的好处**
- 类的内部受到保护，不会因无意的用户级错误导致对象状态受损。

- 类实现可能随着时间的推移而发生变化，以便应对不断变化的需求，或者应对那些要求不改变用户级代码的错误报告。

### 数据封装
所有的 C++ 程序都有以下两个基本要素：

- 程序语句（代码）：这是程序中执行动作的部分，它们被称为函数。

- 程序数据：数据是程序的信息，会受到程序函数的影响。

封装是面向对象编程中的把数据和操作数据的函数绑定在一起的一个概念，这样能避免受到外界的干扰和误用，从而确保了安全。数据封装引申出了另一个重要的 OOP 概念，即数据隐藏。

数据封装是一种把数据和操作数据的函数捆绑在一起的机制，数据抽象是一种仅向用户暴露接口而把具体的实现细节隐藏起来的机制。

C++ 通过创建类来支持封装和数据隐藏（public、protected、private）。我们已经知道，类包含私有成员（private）、保护成员（protected）和公有成员（public）成员。默认情况下，在类中定义的所有项目都是私有的。

把一个类定义为另一个类的友元类，会暴露实现细节，从而降低了封装性。理想的做法是尽可能地对外隐藏每个类的实现细节。

### 接口（抽象类）
接口描述了类的行为和功能，而不需要完成类的特定实现。

C++ 接口是使用抽象类来实现的，抽象类与数据抽象互不混淆，数据抽象是一个把实现细节与相关的数据分离开的概念。

**如果类中至少有一个函数被声明为纯虚函数，则这个类就是抽象类。** 纯虚函数是通过在声明中使用 "= 0" 来指定的。
```
class Box
{
   public:
      // 纯虚函数
      virtual double getVolume() = 0;
   private:
      double length;      // 长度
      double breadth;     // 宽度
      double height;      // 高度
};
```

设计抽象类（通常称为 ABC）的目的，是为了给其他类提供一个可以继承的适当的基类。抽象类不能被用于实例化对象，它只能作为接口使用。如果试图实例化一个抽象类的对象，会导致编译错误。

因此，如果一个 ABC 的子类需要被实例化，则必须实现每个虚函数，这也意味着 C++ 支持使用 ABC 声明接口。如果没有在派生类中重写纯虚函数，就尝试实例化该类的对象，会导致编译错误。

可用于实例化对象的类被称为**具体类**。

### PS
#### Objective-C中的重载和重写详解
重载、重写和隐藏三者在编程语言中的定义

重载（overload）：

函数名相同,函数的参数列表不同(包括参数个数和参数类型)，至于返回类型可同可不同。重载既可以发生在同一个类的不同函数之间，也可发生在父类子类的继承关系之间，其中发生在父类子类之间时要注意与重写区分开。

重写（override）：

发生于父类和子类之间，指的是子类不想继承使用父类的方法，通过重写同一个函数的实现实现对父类中同一个函数的覆盖，因此又叫函数覆盖。注意重写的函数必须和父类一模一样，包括函数名、参数个数和类型以及返回值，只是重写了函数的实现，这也是和重载区分开的关键。

隐藏：

重载和重写区分开后，隐藏又有可能会跟前两者混在一起。当然OC中也没有隐藏，典型的C++中有，通过虚函数和父子类之间的函数重载进行区分，此处不再讨论。其中重载和重写是针对函数的，而隐藏除了函数还会针对成员变量。隐藏发生在父类和子类之间，隐藏指的是父类的同名函数或变量在子类中隐藏，其中只要函数同名就隐藏，不管参数相同与否。在子类中父类的同名函数或变量不可见，但在父类中依然存在。

Swift是基于C语言和OC语言优化后更加完善的新型语言，摆脱了C的兼容性限制，采用安全的编程模式并且增加了一些新的特性使编程更加有趣、友好，适应语言发展的趋势和期望。函数重载作为多态性的一个部分在Swift中是支持的，可能也是考虑到要弥补OC中不完全支持函数重载的这一缺陷。

OC不完全支持重载，因为OC学习者应该会发现同一个类中不允许定义函数名相同且参数个数相同的两个函数，无论参数类型和返回值类型相同与否。但是说完全不支持也太绝对，因为OC中允许定义函数名相同但参数个数不同的两个函数，也就是说OC支持参数个数不同的函数重载。这从OC中Runtime定义Method的方式就可以看出端倪，忽略参数名称。

### 参考
[C++ 教程](https://www.runoob.com/cplusplus/cpp-tutorial.html)

[面向对象的3个基本特征](https://blog.csdn.net/speargod/article/details/101022333)

[面向对象设计七大原则](https://blog.csdn.net/SeeyouMT/article/details/113846110)

[Objective-C中的重载和重写详解](https://www.nhooo.com/note/qadjne.html)
