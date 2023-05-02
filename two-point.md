# 二分

## 二分的意义
**优化**。顾名思义，将一整个**有序的**数列分成两个部分，不断缩小边界，查找某个数字。  
二分的时间复杂度为 $O(log\ 2\ n)$ 。

此时，我们学的还是整数二分。


## 二分的两个模板
二分听起来还简单，但是实现起来~~可能对我来说~~还要多方面考虑。例如，当这样一段二分代码：
```cpp
for(int i = 1; i <= m; i ++)
{
    int x ;
    scanf("%d", &x) ;
    int l = 1, r = m ;
    while(l < r)
    {
        int mid = (l + r) / 2 ;
        if(x > a[mid]) l = mid ;
        else r = mid ;
    }
}
```
它会陷入死循环。所以，我们因该加上什么。
```cpp
for(int i = 1; i <= m; i ++)
{
    int x ;
    scanf("%d", &x) ;
    int l = 1, r = m ;
    while(l < r)
    {
        int mid = (l + r) / 2 ;
        if(x > a[mid]) l = mid + 1 ;
        else r = mid ;
    }
}
```
这是第一个模板。或者：
```cpp
int l = 1, r = n ;
while(l < r)
{
    int mid = (l + r) / 2 ;
    if(k > a[mid]) l = mid + 1 ;
    else r = mid ;
}
```

# THE END