# 堆排序

## 代码

```cpp
// 构造一个最大堆，然后反着输出去
#include<stdio.h>

int h[101];
int n;

// --------------------
void Swap(int x, int y)
{
    int t;
    t = h[x];
    h[x] = h[y];
    h[y] = t;
}

// 需要向下调整的编号 需要的是最大堆 父节点小于子节点都要调整
// -----------------
void SiftDown(int i)
{
    int t, flag = 0;
    while(i*2 <= n && flag == 0)
    {
        if(h[i] < h[i * 2]) // 父节点小于左儿子
            t = i*2;        // t 记录左儿子的下标
        else
            t = i;          // if父节点大于左儿子 t 还是 i本身
        if(i*2+1<=n)
        {
            if(h[t] < h[2*i+1])//目前的下标与右儿子去比较
                t = 2*i+1;
        }
        //此时的t记录的就是值最大的下标 儿子中找个最大的
        if(t!=i)//如果不是本身，那么就进行交换
        {
            Swap(t,i);
            i = t; //把t赋给i继续向下调整 t是目前值最大的下标  交换后 t就成为父节点
        }
        else
            flag = 1;//t 就是i了  说明父节点值大于两个儿子的值  已调整完毕
    }
}

// ---------
void Creat()
{
    int i;
    for(i = n/2;i>=1;i--)//叶节点不需要调整 从叶节点上一层开始调整 直到根节点
    {
        SiftDown(i);
    }
}

// ------------
void headsort()
{
    while(n>1)
    {
        Swap(1,n);//h[1]原来是最大的 现在与h[n]交换 一步步固定当前最大的数
        n--;
        SiftDown(1);
    }
}

// -------
int main()
{
    int i, num, sum = 0, j = 1;
    scanf("%d",&num);
    for(i=1; i<=num; i++)
        scanf("%d",&h[i]);
    n  = num;
    Creat();
    headsort();
    for(i = 1; i <= num; i++)
        printf("%d ",h[i]);
}
```
