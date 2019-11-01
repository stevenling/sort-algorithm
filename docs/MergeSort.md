## 概述

比如 序列 （1， 8， 12 , 14，3， 7， 9， 15）
看做两个序列（1， 8， 12， 14,） （3， 7， 9， 15）左边的下标范围是[low, mid] 右边是[mid+1, high]
然后用 s = low t = mid+1 代表两个序列的起始位置 比较 a[s] 与 a[t] 哪个小就存储在 一个新的数组容器里
然后小的下标值就向前移动继续一直比较 （1， 3， 7， 8， 9， 12， 14 ，15）

## 代码

```cpp
#include<iostream>
using namespace std;

// --------------------------------------------
void Merge(int a[], int low, int mid, int high)//a[low,mid] 和a[mid+1,high]都是有序的  然后归并在一起
{
    // 可以把这拆分的看做两个有序数组
    int k = low, s = low, t = mid + 1;
    int b[100];
    while(s <= mid && t<=high)
    {
        if(a[s] < a[t])
        {
            b[k] = a[s++];
        }
        else
        {
            b[k] = a[t++];
        }
        k++;
    }

     while(s <= mid)
        b[k++] = a[s++];

    while(t <= high)
        b[k++] = a[t++];

    for(int i = low; i <= high; i++)
        a[i] = b[i];
}

// ---------------------------------------
void MergeSort(int a[], int low, int high)
{
    if(low < high)
    {
        int mid = (low + high) / 2;
        MergeSort(a, low, mid);
        MergeSort(a,mid+1, high);
        Merge(a,low,mid, high);
    }
}

// -------
int main()
{
    int n, a[100];
    cin>>n;
    for(int i = 0; i < n; i++)
        cin>>a[i];
    MergeSort(a,0,n-1);
    for(i = 0; i < n; i++)
        cout<<a[i]<<' ';
    return 0;
}
```
