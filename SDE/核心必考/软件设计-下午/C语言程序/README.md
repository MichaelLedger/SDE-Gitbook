## C语言程序

### 试题放置
第四大题的一部分

### HelloWorld
```
#include <stdio.h>
 
int main()
{
    /* 我的第一个 C 程序 */
    printf("Hello, World! \n");
 
    return 0;
}
```
实例解析：

所有的 C 语言程序都需要包含 `main()` 函数。 代码从 `main()` 函数开始执行。

`/* ... */` 用于注释说明。

`printf()` 用于格式化输出到屏幕。`printf()` 函数在 `"stdio.h"` 头文件中声明。

`stdio.h` 是一个头文件 (标准输入输出头文件) , `#include` 是一个预处理命令，用来引入头文件。 当编译器遇到 `printf()` 函数时，如果没有找到 `stdio.h` 头文件，会发生编译错误。

`return 0;` 语句用于表示退出程序。

### 基本语法

#### C 的令牌（Token）
C 程序由各种令牌组成，令牌可以是关键字、标识符、常量、字符串值，或者是一个符号。

- 在 C 程序中，分号是语句结束符。也就是说，每个语句必须以分号结束。它表明一个逻辑实体的结束。

- C 语言有两种注释方式：

(1) 以 // 开始的单行注释，这种注释可以单独占一行。

(2) /* */ 这种格式的注释可以单行或多行。

您不能在注释内嵌套注释，注释也不能出现在字符串或字符值中。

- C 标识符是用来标识变量、函数，或任何其他用户自定义项目的名称。一个标识符以字母 A-Z 或 a-z 或下划线 _ 开始，后跟零个或多个字母、下划线和数字（0-9）。

C 标识符内不允许出现标点字符，比如 @、$ 和 %。

C 是区分大小写的编程语言。

- C 中的关键字即保留字不能作为常量名、变量名或其他标识符名称。

- C 中的空格

只包含空格的行，被称为空白行，可能带有注释，C 编译器会完全忽略它。

在 C 中，空格用于描述空白符、制表符、换行符和注释。

空格分隔语句的各个部分，让编译器能识别语句中的某个元素（比如 int）在哪里结束，下一个元素在哪里开始。

### 数据类型
基本类型：

它们是算术类型，包括两种类型：整数类型和浮点类型。

枚举类型：

它们也是算术类型，被用来定义在程序中只能赋予其一定的离散整数值的变量。

void 类型：
类
型说明符 void 表明没有可用的值。

派生类型：

指针类型、数组类型、结构类型、共用体类型和函数类型。

### enum(枚举)
`enum season {spring, summer=3, autumn, winter};`

没有指定值的枚举元素，其值为前一元素加 1。也就说 spring 的值为 0，summer 的值为 3，autumn 的值为 4，winter 的值为 5

### 指针
学习 C 语言的指针既简单又有趣。通过指针，可以简化一些 C 编程任务的执行，还有一些任务，如动态内存分配，没有指针是无法执行的。所以，想要成为一名优秀的 C 程序员，学习指针是很有必要的。

正如您所知道的，每一个变量都有一个内存位置，每一个内存位置都定义了可使用 & 运算符访问的地址，它表示了在内存中的一个地址。

```
#include <stdio.h>
 
int main ()
{
    int var_runoob = 10;
    int *p;              // 定义指针变量
    p = &var_runoob;
 
   printf("var_runoob 变量的地址： %p\n", p);
   return 0;
}
```

指针也就是内存地址，指针变量是用来存放内存地址的变量。就像其他变量或常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。

在变量声明的时候，如果没有确切的地址可以赋值，为指针变量赋一个 NULL 值是一个良好的编程习惯。赋为 NULL 值的指针被称为空指针。

NULL 指针是一个定义在标准库中的值为零的常量。地址为 `0x0`。

在大多数的操作系统上，程序不允许访问地址为 0 的内存，因为该内存是操作系统保留的。然而，内存地址 0 有特别重要的意义，它表明该指针不指向一个可访问的内存位置。但按照惯例，如果指针包含空值（零值），则假定它不指向任何东西。

#### 指针的算术运算
C 指针是一个用数值表示的地址。因此，您可以对指针执行算术运算。可以对指针进行四种算术运算：`++、--、+、-`。

指针的每一次递增，它其实会指向下一个元素的存储单元。

指针的每一次递减，它都会指向前一个元素的存储单元。

指针在递增和递减时跳跃的字节数取决于指针所指向变量数据类型长度，比如 int 就是 4 个字节。

我们喜欢**在程序中使用指针代替数组，因为变量指针可以递增，而数组不能递增**，数组可以看成一个指针常量。下面的程序递增变量指针，以便顺序访问数组中的每一个元素：

```
#include <stdio.h>
 
const int MAX = 3;
 
int main ()
{
   int  var[] = {10, 100, 200};
   int  i, *ptr;
 
   /* 指针中的数组地址 */
   ptr = var;
   for ( i = 0; i < MAX; i++)
   {
 
      printf("存储地址：var[%d] = %p\n", i, ptr );
      printf("存储值：var[%d] = %d\n", i, *ptr );
 
      /* 指向下一个位置 */
      ptr++;
   }
   return 0;
}
```

### 函数指针
函数指针是指向函数的指针变量。

通常我们说的指针变量是指向一个整型、字符型或数组等变量，而函数指针是指向函数。

函数指针可以像一般函数一样，用于调用函数、传递参数。

函数指针变量的声明：`typedef int (*fun_ptr)(int,int); // 声明一个指向同样参数、返回值的函数指针类型`

```
#include <stdio.h>
 
int max(int x, int y)
{
    return x > y ? x : y;
}
 
int main(void)
{
    /* p 是函数指针 */
    int (* p)(int, int) = & max; // &可以省略
    int a, b, c, d;
 
    printf("请输入三个数字:");
    scanf("%d %d %d", & a, & b, & c);
 
    /* 与直接调用函数等价，d = max(max(a, b), c) */
    d = p(p(a, b), c); 
 
    printf("最大的数字是: %d\n", d);
 
    return 0;
}
```

#### 回调函数
函数指针变量可以作为某个函数的参数来使用的，回调函数就是一个通过函数指针调用的函数。
简单讲：回调函数是由别人的函数执行时调用你实现的函数。

> 你到一个商店买东西，刚好你要的东西没有货，于是你在店员那里留下了你的电话，过了几天店里有货了，店员就打了你的电话，然后你接到电话后就到店里去取了货。在这个例子里，你的电话号码就叫回调函数，你把电话留给店员就叫登记回调函数，店里后来有货了叫做触发了回调关联的事件，店员给你打电话叫做调用回调函数，你到店里去取货叫做响应回调事件。

实例中 populate_array() 函数定义了三个参数，其中第三个参数是函数的指针，通过该函数来设置数组的值。

实例中我们定义了回调函数 getNextRandomValue()，它返回一个随机值，它作为一个函数指针传递给 populate_array() 函数。

populate_array() 将调用 10 次回调函数，并将回调函数的返回值赋值给数组。

```
#include <stdlib.h>  
#include <stdio.h>
 
void populate_array(int *array, size_t arraySize, int (*getNextValue)(void))
{
    for (size_t i=0; i<arraySize; i++)
        array[i] = getNextValue();
}
 
// 获取随机值
int getNextRandomValue(void)
{
    return rand();
}
 
int main(void)
{
    int myarray[10];
    /* getNextRandomValue 不能加括号，否则无法编译，因为加上括号之后相当于传入此参数时传入了 int , 而不是函数指针*/
    populate_array(myarray, 10, getNextRandomValue);
    for(int i = 0; i < 10; i++) {
        printf("%d ", myarray[i]);
    }
    printf("\n");
    return 0;
}
```

### 结构体
```
struct tag { 
    member-list
    member-list 
    member-list  
    ...
} variable-list;
```
```
//此声明声明了拥有3个成员的结构体，分别为整型的a，字符型的b和双精度的c
//同时又声明了结构体变量s1
//这个结构体并没有标明其标签
struct 
{
    int a;
    char b;
    double c;
} s1;
 
//此声明声明了拥有3个成员的结构体，分别为整型的a，字符型的b和双精度的c
//结构体的标签被命名为SIMPLE,没有声明变量
struct SIMPLE
{
    int a;
    char b;
    double c;
};
//用SIMPLE标签的结构体，另外声明了变量t1、t2、t3
struct SIMPLE t1, t2[20], *t3;
 
//也可以用typedef创建新类型
typedef struct
{
    int a;
    char b;
    double c; 
} Simple2;
//现在可以用Simple2作为类型声明新的结构体变量
Simple2 u1, u2[20], *u3;
```

#### 指向结构的指针
您可以定义指向结构的指针，方式与定义指向其他类型变量的指针相似，如下所示：
`struct Books *struct_pointer;`

现在，您可以在上述定义的指针变量中存储结构变量的地址。为了查找结构变量的地址，请把 & 运算符放在结构名称的前面，如下所示：
`struct_pointer = &Book1;

**为了使用指向该结构的指针访问结构的成员，您必须使用 `->` 运算符**，如下所示：
`struct_pointer->title;`

```
#include <stdio.h>
#include <string.h>
 
struct Books
{
   char  title[50];
   char  author[50];
   char  subject[100];
   int   book_id;
};
 
/* 函数声明 */
void printBook( struct Books *book );
int main( )
{
   struct Books Book1;        /* 声明 Book1，类型为 Books */
   struct Books Book2;        /* 声明 Book2，类型为 Books */
 
   /* Book1 详述 */
   strcpy( Book1.title, "C Programming");
   strcpy( Book1.author, "Nuha Ali"); 
   strcpy( Book1.subject, "C Programming Tutorial");
   Book1.book_id = 6495407;
 
   /* Book2 详述 */
   strcpy( Book2.title, "Telecom Billing");
   strcpy( Book2.author, "Zara Ali");
   strcpy( Book2.subject, "Telecom Billing Tutorial");
   Book2.book_id = 6495700;
 
   /* 通过传 Book1 的地址来输出 Book1 信息 */
   printBook( &Book1 );
 
   /* 通过传 Book2 的地址来输出 Book2 信息 */
   printBook( &Book2 );
 
   return 0;
}
void printBook( struct Books *book )
{
   printf( "Book title : %s\n", book->title);
   printf( "Book author : %s\n", book->author);
   printf( "Book subject : %s\n", book->subject);
   printf( "Book book_id : %d\n", book->book_id);
}
```

### 共用体
共用体是一种特殊的数据类型，允许您在相同的内存位置存储不同的数据类型。您可以定义一个带有多成员的共用体，但是**任何时候只能有一个成员带有值**。共用体提供了一种使用相同的内存位置的有效方式。

为了定义共用体，您必须使用 union 语句，方式与定义结构类似。union 语句定义了一个新的数据类型，带有多个成员。

```
union [union tag]
{
   member definition;
   member definition;
   ...
   member definition;
} [one or more union variables];
```

共用体占用的内存应足够存储共用体中最大的成员。

```
#include <stdio.h>
#include <string.h>
 
union Data
{
   int i;
   float f;
   char  str[20];
};
 
int main( )
{
   union Data data;        
 
   data.i = 10;
   data.f = 220.5;
   strcpy( data.str, "C Programming");
 
   printf( "data.i : %d\n", data.i);
   printf( "data.f : %f\n", data.f);
   printf( "data.str : %s\n", data.str);
 
   return 0;
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```
data.i : 1917853763
data.f : 4122360580327794860452759994368.000000
data.str : C Programming
```
在这里，我们可以看到共用体的 i 和 f 成员的值有损坏，因为**最后赋给变量的值占用了内存位置**，这也是 str 成员能够完好输出的原因。

### 位域
如果程序的结构中包含多个开关量，只有 TRUE/FALSE 变量。在这种情况下，C 语言提供了一种更好的利用内存空间的方式。如果您在结构内使用这样的变量，您可以定义变量的宽度来告诉编译器，您将只使用这些字节。
```
struct 位域结构名 
{
    type [member_name] : width ;
    //...
};
```
type: **只能为 int(整型)，unsigned int(无符号整型)，signed int(有符号整型) 三种类型**。

member_name: 位域的名称。

width: 位域中位的数量。宽度必须小于或等于指定类型的位宽度。

```
#include <stdio.h>
#include <string.h>
 
/* 定义简单的结构 */
struct
{
  unsigned int widthValidated;
  unsigned int heightValidated;
} status1;
 
/* 定义位域结构 */
struct
{
  unsigned int widthValidated : 1;
  unsigned int heightValidated : 1;
} status2;
 
int main( )
{
   printf( "Memory size occupied by status1 : %d\n", sizeof(status1));
   printf( "Memory size occupied by status2 : %d\n", sizeof(status2));
 
   return 0;
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```
Memory size occupied by status1 : 8
Memory size occupied by status2 : 4
```

由于字节对齐原则，上面的结构中，status 变量将占用 4 个字节的内存空间，但是只有 2 位被用来存储值。

#### 字节对齐
其实字节对齐的细节和具体编译器实现相关，但一般而言，满足三个准则：

1) 结构体变量的首地址能够被其最宽基本类型成员的大小所整除；

2) 结构体每个成员相对于结构体首地址的偏移量都是成员大小的整数倍，如有需要编译器会在成员之间加上填充字节；例如上面第二个结构体变量的地址空间。

3) 结构体的总大小为结构体最宽基本类型成员大小的整数倍，如有需要编译器会在最末一个成员之后加上填充字节。

四个基本概念:

1. 数据类型自身的对齐值：
对于char型数据，其自身对齐值为1，对于short型为2，对于int,float类型，其自身对齐值为4，对于double型，其自身对齐值为8，单位字节。
2. 结构体或者类的自身对齐值：其成员中自身对齐值最大的那个值。
3. 指定对齐值：#pragma pack (value)时的指定对齐值value。
4. 数据成员、结构体和类的有效对齐值：自身对齐值和指定对齐值中小的那个值。

### typedef
C 语言提供了 typedef 关键字，您可以使用它来为类型取一个新的名字。
`typedef unsigned char BYTE;`
您也可以使用 typedef 来为用户自定义的数据类型取一个新的名字。
```
#include <stdio.h>
#include <string.h>
 
 typedef struct Books
 {
    char  title[50];
    char  author[50];
    char  subject[100];
    int   book_id;
 } Book;
 
int main( )
{
   Book book;
 
   return 0;
}
```

#### `typedef` vs `#define`
`#define` 是 C 指令，用于为各种数据类型定义别名，与 `typedef` 类似，但是它们有以下几点不同：

- `typedef` 仅限于为类型定义符号名称，`#define` 不仅可以为类型定义别名，也能为数值定义别名，比如您可以定义 1 为 ONE。

- `typedef` 是由编译器执行解释的，`#define` 语句是由预编译器进行处理的。

```
#include <stdio.h>
 
#define TRUE  1
#define FALSE 0
 
int main( )
{
   printf( "TRUE 的值: %d\n", TRUE);
   printf( "FALSE 的值: %d\n", FALSE);
 
   return 0;
}
```

### 输入 & 输出
当我们提到输入时，这意味着要向程序填充一些数据。输入可以是以文件的形式或从命令行中进行。C 语言提供了一系列内置的函数来读取给定的输入，并根据需要填充到程序中。

当我们提到输出时，这意味着要在屏幕上、打印机上或任意文件中显示一些数据。C 语言提供了一系列内置的函数来输出数据到计算机屏幕上和保存数据到文本文件或二进制文件中。

C 语言把所有的设备都当作文件。所以设备（比如显示器）被处理的方式与文件相同。以下三个文件会在程序执行时自动打开，以便访问键盘和屏幕。

标准文件|文件指针|设备
:-:|:-:|:-:
标准输入|stdin|键盘
标准输出|stdout|屏幕
标准错误|stderr|您的屏幕

C 语言中的 I/O (输入/输出) 通常使用 printf() 和 scanf() 两个函数。

scanf() 函数用于从标准输入（键盘）读取并格式化， printf() 函数发送格式化输出到标准输出（屏幕）。

```
#include <stdio.h>      // 执行 printf() 函数需要该库
int main()
{
    printf("Hello World!");  //显示引号中的内容
    return 0;
}
```

### 参考
[C 语言教程](https://www.runoob.com/cprogramming/c-tutorial.html)
