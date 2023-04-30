# 排序

## 一些说在前面的要点
- **稳定性**
    - 在我们以下学过的排序算法中，只有**选择排序**不是稳定的。
    - 稳定性，就是有两个相同的数字，在排序后两个数字的相对位置不变。（前面的在前面，后面的在后面）
- **逆序对**
    - 前面的一个数字大于后面一个数字，这就叫做逆序对。
    - 例如 $5\ 1\ 2\ 3\ 4$ 中，有 $4$ 对逆序对。


## 选择排序

### 简介
**选择排序**，顾名思义，就是选出所有元素中最小的元素，然后再放到前面。这个排序非常好理解，但是，时间复杂度为 $O(n^2)$ ，数据一大就要炸了。（ $n$ 为数组长度）

我们可以使用一个变量来记录其中一个最小数的下标，然后再进行第一个数与最小的数的交换。  
由于不断地将最小的数往前放，最终完成排序。但由于第 $i$ 次遍历之后，第 $i$ 个元素就是最小的元素，因此由 $i + 1$ 个元素开始判断。

### 例子
例如有这样一个数组：

$$
8 \ 5 \ 7 \ 9 \ 2 \ 6
$$

遍历后得知 $2$ 是最小的，与第一个元素 $8$ 进行交换。

$$
{\color{red}2} \ 5 \ 7 \ 9 \ {\color{red}8} \ 6
$$

以此类推：

$$
{\color{green}2} \ {\color{red}5} \ 7 \ 9 \ 8 \ 6 \\
\\ \\
{\color{green}2} \ {\color{green}5} \ {\color{red}6} \ 9 \ 8 \ {\color{red}7} \\
\\ \\
{\color{green}2} \ {\color{green}5} \ {\color{green}6} \ {\color{red}7} \ 8 \ {\color{red}9} \\
\\ \\
{\color{green}2} \ {\color{green}5} \ {\color{green}6} \ {\color{green}7} \ {\color{green}8} \ 9 \\
\\ \\
{\color{green}2} \ {\color{green}5} \ {\color{green}6} \ {\color{green}7} \ {\color{green}8} \ {\color{green}9} \\
$$

### 示例程序
```cpp
#include <cstdio>
using namespace std ;

int n, a[3002] ; 
int main()
{
    scanf("%d", &n) ;
    for(int i = 1; i <= n; i ++)
    {
        scanf("%d", &a[i]) ;
    }
    
    for(int i = 1; i <= n - 1; i ++)
    {
        int th = i ;
        for(int j = i; j <= n; j ++)
        {
            if(a[th] > a[j])
            {
                th = j ;
            }
        }
        int temp = a[i] ;
        a[i] = a[th] ;
        a[th] = temp ;
    }
    
    // printf("\n"); 
    for(int i = 1; i <= n; i ++){printf("%d ", a[i]) ;} 
    printf("\n") ;
    
    return 0 ;
}
```

### 演示网址
演示网址：[`https://visualgo.net/zh/sorting?slide=8`](https://visualgo.net/zh/sorting?slide=8)


## 冒泡排序

### 简介
**冒泡排序**，将前面一个元素和后面一个元素做对比，若前面的元素大于后面的元素即进行交换。时间复杂度也为 $O(n^2)$。

由于不断地将前一个元素大于后一个元素的一组交换，假设数组中有 $n$ 个元素，第 $i$ 次遍历后，第 $n$ 个元素就是最大的数，因此下一次遍历由 $i$ 至 $n - i$ 。

### 例子
还是上面的那个例子，利用冒泡排序：

$$
8 \ 5 \ 7 \ 9 \ 2 \ 6 \ \\ \\
\\ \\
{\color{red}5} \ {\color{red}8} \ 7 \ 9 \ 2 \ 6 \ \\
\\ \\
5 \ {\color{red}7} \ {\color{red}8} \ 9 \ 2 \ 6 \ \\
\\ \\
5 \ 7 \ {\color{red}8} \ {\color{red}9} \ 2 \ 6 \ \\
\\ \\
5 \ 7 \ 8 \ {\color{red}2} \ {\color{red}9} \ 6 \ \\
\\ \\
5 \ 7 \ 8 \ 2 \ {\color{red}6} \ {\color{red}9} \ \\
\\ \\
{\color{red}5} \ {\color{red}7} \ 8 \ 2 \ 6 \ {\color{green}9} \ \\
\\ \\
5 \ {\color{red}7} \ {\color{red}8} \ 2 \ 6 \ {\color{green}9} \ \\
\\ \\
5 \ 7 \ {\color{red}2} \ {\color{red}8} \ 6 \ {\color{green}9} \ \\
\\ \\
5 \ 7 \ 2 \ {\color{red}6} \ {\color{red}8} \ {\color{green}9} \ \\
\\ \\
{\color{red}5} \ {\color{red}7} \ 2 \ 6 \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
5 \ {\color{red}2} \ {\color{red}7} \ 6 \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
5 \ 2 \ {\color{red}6} \ {\color{red}7} \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
{\color{red}2} \ {\color{red}5} \ 6 \ {\color{green}7} \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
2 \ {\color{red}5} \ {\color{red}6} \ {\color{green}7} \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
{\color{red}2} \ {\color{red}5} \ {\color{green}6} \ {\color{green}7} \ {\color{green}8} \ {\color{green}9} \ \\
\\ \\
{\color{green}2} \ {\color{green}5} \ {\color{green}6} \ {\color{green}7} \ {\color{green}8} \ {\color{green}9} \ \\
$$

### 示例程序
```cpp
#include <cstdio>
using namespace std ;

int n, a[3002] ; 
int main()
{
    scanf("%d", &n) ;
    for(int i = 1; i <= n; i ++)
    {
        scanf("%d", &a[i]) ;
    }
    
    for(int j = 1; j <= n - 1; j ++)
    {
        for(int i = 1; i <= n - j; i ++)
        {
            if(a[i] > a[i + 1])
            {
                int t = a[i] ;
                a[i] = a[i + 1] ;
                a[i + 1] = t ;
            }
        }
    }
    
    
    // printf("\n"); 
    for(int i = 1; i <= n; i ++){printf("%d ", a[i]) ;} 
    
    return 0 ;
}
```

### 演示网址
演示网址：[`https://visualgo.net/zh/sorting?slide=7`](https://visualgo.net/zh/sorting?slide=7)


## 插入排序

### 简介
**插入排序**，是在冒泡排序的基础上做的改进。它将整个数列分为两个部分：已排序的与未排序的。

由于一个数本身就没有任何顺序，所以我们可以假设元素 $a[1]$ （假设 $1$ 为数组第一个元素）就是一个已经排列好的数列。  
随后，将 $a[2]$ 插入进已排序好的数列中。若 $a[2] > a[1]$ 则不交换，否则则交换。这就是一个循环的过程。插入进已排列好的数列中时，这个比较就是冒泡排序的过程：
> 将前面一个元素和后面一个元素做对比，若前面的元素大于后面的元素即进行交换。

### 例子
依然是前面那个样例，在这里，我们假设有一个空间是已排序空序列，另一个是未排序序列。

$$
\boxed{
\begin{aligned}
&说明：\\
&? \ 代表未排序序列 \\
&! \ 代表已排序序列 \\
\end{aligned}
}
$$

$$
\begin{aligned}
? \ &8 \ 5 \ 7 \ 9 \ 2 \ 6 \ \\
! \ &[Empty] \\ \\

? \ &5 \ 7 \ 9 \ 2 \ 6 \ \\
! \ &{\color{yellow}8} \\ \\

? \ &7 \ 9 \ 2 \ 6 \ \\
! \ &{\color{yellow}8} \ {\color{yellow}5} \\ \\

? \ &7 \ 9 \ 2 \ 6 \ \\
! \ &{\color{yellow}5} \ {\color{yellow}8} \\ \\

? \ &9 \ 2 \ 6 \ \\
! \ &{\color{yellow}5} \ {\color{yellow}8} \ {\color{yellow}7} \\ \\

? \ &9 \ 2 \ 6 \ \\
! \ &{\color{yellow}5} \ {\color{yellow}7} \ {\color{yellow}8} \\ \\

&...(不再详细演示)
\end{aligned}
$$

### 示例程序
```cpp
#include <cstdio>
using namespace std ;

int a[100010] ;
int main()
{
    int n ;
    scanf("%d", &n) ;
    for(int i = 1; i <= n; i ++)
    {
        scanf("%d", &a[i]) ;
    }
    
    for(int j = 1; j <= n - 1; j ++)
    {
        for(int i = j; i >= 1; i --)
        {
            if(a[i + 1] < a[i])
            {
                int t = a[i] ;
                a[i] = a[i + 1] ;
                a[i + 1] = t ;
            }
            else
            {
                break ;
            }
        }
    }
    
    for(int i = 1; i <= n; i ++)
    {
        printf("%d ", a[i]) ;
    }
    printf("\n") ;
    
    return 0 ;
}
```

可以看到，它比普通冒泡排序快在当前一个元素大于等于后一个元素时会退出循环。但最坏的情况还是 $O(n^2)$ （也是平均情况），因为如果他时一个倒序序列的话，这样排序每次都要从头到尾比较一遍，这和冒泡排序是一样的。

### 演示网址
演示网址：[`https://visualgo.net/zh/sorting?slide=9`](https://visualgo.net/zh/sorting?slide=9)


## 计数排序

### 简介
计数排序需要用到**前缀和**的知识，简单来说就是将每一个数字出现的次数记录到一个数组中（这里称为计数数组），然后再按照这个计数数组将答案数组赋值好。还是比较好理解的。只是也许没有冒泡排序来的码量小。  
计数排序适用于**排序数据量较大**的排序，但数字不能过大。如果数字上限很高的话，计数排序就无能为力了，因为数组不能开太大，否则内存不够用。  
同时，最好不要有**负数**，要不然计数数组要开两倍大，虽说也可以通过处理达到“负下标”的效果，但还是上面说的三个排序比较好。

### 例子
假设有这样一个数组 $a$ ：

$$
8 \ 8 \ 8 \ 5 \ 5 \ 7 \ 5 \ 2 \ 2 \ 6 \ 6 \ 2
$$

统计结果是这样的：  
$8$ 出现了 `3` 次， $5$ 出现了 `3` 次， $7$ 出现了 `1` 次， $6$ 出现了 `2` 次， $2$ 出现了 `3` 次。

那么，就可以将这些数按顺序赋值到答案数组中，然后再输出答案数组。在此处不演示了。~~手都敲酸了~~

### 示例程序

```cpp
#include <cstdio>
using namespace std ;

const int TEMP = 1e7 + 10 ;
int a[TEMP] ;
int b[TEMP], c[TEMP], d[TEMP] ;
int main()
{
    int n ;
    scanf("%d", &n) ;
    for(int i = 1; i <= n; i ++)
    {
        scanf("%d", &a[i]) ;
        b[a[i]] ++ ;
    }
    
    c[0] = b[0] ;
    for(int i = 1; i <= 10000000; i ++)
    {
        c[i] = c[i - 1] + b[i] ;
    }
    
    for(int i = 1; i <= c[0]; i ++)
    {
        d[i] = 0 ;
    }
    for(int i = 1; i <= 10000000; i ++)
    {
        int l = c[i - 1] + 1 ;
        int r = c[i - 1] + b[i] ;
        for(int j = l; j <= r; j ++)
        {
            d[j] = i ;
        }
    }
    
    for(int i = 1; i <= n; i ++)
    {
        printf("%d\n", d[i]) ;
    }
    
    return 0 ;
}
```

### 演示网址
演示网址：[`https://visualgo.net/zh/sorting?slide=15`](https://visualgo.net/zh/sorting?slide=15)


## `<algorithm>` 头文件 `sort()` 排序

这么多排序算法，头都要晕了。为什么不用别人现成的函数来排序呢？看， `C++` 就有一个超级好用的头文件 -> `<algorithm>` ，用它里面的 `sort()` 函数就可以啦！并且，它支持**自定义排序**。

两个重载：
```cpp
template<typename _RandomAccessIterator>
    inline void
    sort(_RandomAccessIterator __first, _RandomAccessIterator __last)
```
```cpp
template<typename _RandomAccessIterator, typename _Compare>
    inline void
    sort(_RandomAccessIterator __first, _RandomAccessIterator __last,
	 _Compare __comp)
```  
想要用的时候，就直接 `sort(&a[0], &a[n])` 或者 `sort(a, a + n)` 就可以了。写排序函数 `cmp` 时，想交换就 `return true` ，否则就 `return false` 。


# THE END
