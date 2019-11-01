# 快速排序

## 概述

- 设一个基准点，将比基准点小的放在基准点的左侧，比基准点大的放在基准点的右侧。
- 递归

## 代码

```cpp
#include <stdio.h>

// -------------------------------
void QuickSort(int a[], int low, int high);

// -------
int main()
{
    int a[101];
    int i, n;
    scanf("%d", &n);

    for (i = 0; i < n; i++)
	    scanf("%d", &a[i]);

    QuickSort(a, 0, n - 1);

    for (i = 0; i < n; i++)
	    printf("%d ", a[i]);
}

// ------------------------------
void QuickSort(int a[], int low, int high)
{
    int first, i, j, t;
    first = a[low]; // 基准点
    i = low;
    j = high;

    if (low > high)
	    return;

    while (i != j)
    {
        while (a[j] >= first && i < j)  // 右边的数比基准点大且 i < j 时让 j 的位置一直减
        {
            j--;
        }
        // a[j] 出来的时候肯定是小于 first
        while(a[i] <= first && i < j)
        {
            i++;
        }
        // a[i] 出来的时候肯定大于 first
        // 这是我们交换 a[i] 和 a[j]
        if (i < j)
        {
            t = a[j];
            a[j] = a[i];
            a[i] = t;
        }
    }
    a[low] = a[i];
    a[i] = first;
    // 把基准点的值赋给 a[i] 此时 i == j 则左边都是小于 first
    // 右边都是大于 first
    QuickSort(a, low, i - 1);
    QuickSort(a, i + 1, high);
}
```
