# 顺序查找

## 基本原理
对于任意一个序列以及一个给定的元素，将给定元素与序列中元素依次比较，直到找出与给定关键字相同的元素，或者将序列中的元素与其都比较完为止。

## 代码实现
### Java
```
package search;
/*
*  顺序查找
* des 要查找的元素
* i 保存当前元素的下标
*/
public class OrderSearch {
    public static int ordersearch(int[] arry,int des){
        int i=0;
        for(;i<=arry.length-1;i++){
            if(des==arry[i])
            return i;
        }
        return -1;
    }
    public static void main(String[] args){
        int[] a=new int[]{2,3,5,6,7,3,};
        System.out.println(ordersearch(a,3));
    }
}
```
### C
```
int sq_search(keytype keyp[],int n,keytype key)
{
int i;
for(i=0; i<n; i++)
if(key[i] == key)
return i;//查找成功
return -1;//查找失败
}
```
### C++
```
int Seqsch(ElemType A[ ],int n,KeyType K) {
//从顺序表A的n个元素中顺序查找关键字为K的元素，若成功返回其下标，否则返回-1
    int i;
    for( i=0;i<n;i++){
        if(A[i].key==K)
        break;
    }
    if(i<=n-1) //查找成功返回下标，否则返回-1
        return i;
    else return -1;
}
```
### python
```
# 最基本的查找算法，
# 基本原理：
# 对于任意一个序列以及一个给定元素，将给定元素与序列中元素依次比较，直到找出与给定关键字相同的数为止
 
import random
Range = 10
Length = 5
flag = 0
pos = -1
 
list = random.sample(range(Range),Length)
goal = random.randint(0,Range)
print('search ',goal,', in list:',list)
 
for i in range(Length):
    if list[i] == goal:
        flag = 1
        pos = i
        break
 
if flag:
    print('find in ',pos+1,'th place')
else:
    print('not found')
```
### php
```
function seq_sch($array, $n, $k) {
    for($i=0; $i<$n; $i++) {
        if( $array[$i]==$k)　break; 　
    }
    if ($i<$n) {
        return $i;
    }
    else{
        return -1;
    } 　
}
```
