# 选择排序

## 思路

将待排序的数分为两部分，一部分是已排序，另一部分是未排序。

将未排序部分中最小的数放在已排序部分后。

## 过程
![选择排序](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MDY4NjItMjE2YWM1YWZhMmM0YTZkMi5naWY)

## 代码
```cpp
#include <iostream>
using namespace std;

// ------------------------------
void SelectSort(int a[], int len)
{
    int smallestIndex;
    int i, j, temp;
    for (i = 0; i < len - 1; i++)
    {
        smallestIndex = i;
        for (j = i + 1; j < len; j++)
        {
            if (a[j] < a[smallestIndex])
            {
                smallestIndex = j;
            }
        }
        if (smallestIndex != i)
        {
            temp = a[i];
            a[i] = a[smallestIndex];
            a[smallestIndex] = temp;
        }
    }
}

// -------
int main()
{
    int a[6] = {5, 2, 4, 6, 1, 3};
    int len = sizeof(a) / sizeof(a[0]);
    selectSort(a, len);
    for (int i = 0; i < len; i++)
    {
        cout << a[i] << ' ';
    }
    return 0;
}
```
