
## 思路
外循环和之前一样，每相邻两个数都比较，最小的就沉在最右边，内循环的范围一次一次减少。
代码，因为一个一个沉下去的就是排好的，相邻元素顺序错误我们就交换。

## 过程

![冒泡排序](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MDY4NjItNjE1ZDcyN2QxMWZjYTRiYS5naWY)

## 代码
```c
#include <stdio.h>
int main()
{
    int a[100], i, n, j, temp, max, k; // n 为需要排序的数的数量

    scanf("%d", &n);

    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n - 1 - i; j++) // 一次外循环结束沉淀一个数比较的那些数就减少
        {
            if (a[j] < a[j + 1]) // 后面一个数大于前面的则交换
            {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }

    for (i = 0; i < n; i++)
        printf("%d ", a[i]);
}
```
