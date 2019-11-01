# 快速排序

## 概述

## 代码

```cpp
#include <stdio.h>

// -------------------------------
void QuickSort(int low, int high);

int a[101];

// -------
int main()
{
    int i, n;
    scanf("%d", &n);

    for (i = 0; i < n; i++)
	    scanf("%d", &a[i]);

    QuickSort(0, n - 1);

    for (i = 0; i < n; i++)
	    printf("%d ", a[i]);
}

// ------------------------------
void QuickSort(int low, int high)
{
    int first, i, j, t;
    // first 基准点
    first = a[low];
    i = low;
    j = high;
    if (low > high)
	        return;
    while (i != j)
    {
        while (a[j] >= first && i < j)  //右边的数比基准点大且i<j时让j的位置一直减
            j--;
        // a[j]出来的时候肯定是小于first
        while (a[i] <= first && i < j)
		            i++;
        // a[i]出来的时候肯定大于first
        // 这是我们交换a[i]和a[j]
        if (i < j)
        {
            t = a[j];
            a[j] = a[i];
            a[i] = t;
        }
    }
    a[low] = a[i];
    a[i] = first;
    //把基准点的值赋给a[i] 此时i == j 则左边都是小于first
    //右边都是大于first
    QuickSort(low, i - 1);
    QuickSort(i + 1, high);
}
```
