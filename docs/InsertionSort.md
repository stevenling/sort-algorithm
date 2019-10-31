# 插入排序

## 思路

将待排序的数分为两部分，一部分是已排序，另一部分是未排序。

将未排序的数一个一个和已排序的数比较，插入到合适的位置。

## 过程

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MDY4NjItNmE4YTVmMmM5NjkyZWI1Yy5naWY)

## 代码
```cpp
#include<iostream>
using namespace std;

// ---------------------
void insertSort(int a[])
{
	int i, temp, j, len;
	len = 6;
	for(j = 1; j < len; j++)
	{
		temp = a[j];
		i = j - 1;
		while(i >= 0 && a[i] > temp)
		{
			a[i+1] = a[i];
			i--;
		}
		a[i+1] = temp;
	}
}

// -------
int main()
{
	int a[6]={5,2,4,6,1,3};
	insertSort(a);
	for(int i = 0; i < 6; i++)
	{
		cout<<a[i]<<' ';
	}
	return 0;
}
```
