## java数组元素交换的四种方法

对于两种变量的交换，我发现四种方法，下面我用Java来演示一下。

1、利用第三个变量交换数值，简单的方法。
```
class TestEV
//创建一个类
{
    public static void main(String[] args)
    {
        int x =5,y=10;     //定义两个变量
        int temp = x;　　　 //定义第三临时变量temp并提取x值
        x = y;　　　　　　　　//把y的值赋给x
        y = temp;　　　　　　//然后把临时变量temp值赋给y
        System.out.println("x="+x+"y="+y);
    }
}
```

2、可以用两个数求和然后相减的方式进行数据交换,弊端在于如果 x 和 y 的数值过大的话，超出 int 的值会损失精度，故**不推荐使用**！
```
class TestEV
//创建一个类
{
    public static void main(String[] args)
    {
        int x =5,y=10;    //定义两个变量
        x = x + y;        //x(15) = 5 + 10；
        y = x - y;        //y(5) = x(15) - 10;
        x = x - y;        //x(10) = x(15) - y(5)
        System.out.println("x="+x+"y="+y);
    }
} 
```

3、利用位运算的方式进行数据的交换，利用的思想原理是：

一个数异或同一个数两次，结果还是那个数，而且不会超出int范围
```
class TestEV
//创建一个类
{
    public static void main(String[] args)
    {
        int x =5,y=10; //定义两个变量
        x = x^y;
        y = x^y;  //y=(x^y)^y
        x = x^y;  //x=(x^y)^x
        System.out.println("x="+x+"y="+y);
    }
}
```

4、最为简单的，在打印输出的时候直接交换变量
```
class TestEV
//创建一个类
{
    public static void main(String[] args)
    {
        int x =5,y=10; //定义两个变量
        System.out.println("x="+y+"y="+x); //直接在输出的时候交换
    }
}
```

#### 参考
[两个变量交换的四种方法（Java）](https://www.cnblogs.com/Brad-Lee/p/5808299.html)
