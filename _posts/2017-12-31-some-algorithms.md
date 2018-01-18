---
layout: post
title: "一些算法常识"
tags: ['online judge']
---
### #1
>辗转相除法求gcd
```cpp
int gcd(unsigned int a, unsigned int b)
{
    while(a != b)
    {
        if(a>b) a -= b;
        else b -= a;
    }
    
    return a;
}
```
### #2
>要计算只包含加法、减法和乘法的整数表达式除以正整数n的余数，可以在每步计算之后对n取余，结果不变。

>输入n,计算 S=1!+2!+3!+...+n!的末6位（不含前导0）。n<=10^6。例如：输入:10，输出37919
```cpp
#include <stdio.h>
#include <time.h>
int main(){
    const int MOD = 1000000;
    int i; unsigned n, S = 0;
    scanf("%u", &n);
    int factorial = 1;
    for (i = 1; i <= n; i++) {
        factorial = (factorial * i % MOD);
        S = (S + factorial) % MOD;
    }
    printf("%d\n", S);
    printf("Time used = %.21f\n", (double)clock() / CLOCKS_PER_SEC);
    return 0;
}
```

### #3 Maximum Subarray
Kadane's algorithm(Dynamic Programming)
```python
def max_subarray(A):
    max_ending_here = max_so_far = A[0]
    for x in A[1:]:
        max_ending_here = max(x, max_ending_here + x)
        max_so_far = max(max_so_far, max_ending_here)
    return max_so_far
```

### #4 最大生成树问题
[灌溉](https://nanti.jisuanke.com/t/34)
```cpp
#include<cstdio>
#include<cstring>
#include<algorithm>
using namespace std;

struct node
{
    int u,v,cost;
}p[10005];

int pre[105];
int fin(int x)
{
    if(x==pre[x])
    {
        return x;
    }
    else
    {
        return pre[x]=fin(pre[x]);
    }
}

void join(int x,int y)
{
    int t1=fin(x);
    int t2=fin(y);
    if(t1!=t2)
    {
        pre[t1]=t2;
    }
}

bool cmp(node a,node b)
{
    return a.cost<b.cost;
}

int main()
{
    int n;
    while(~scanf("%d",&n))
    {
        for(int i=0;i<=n;i++)
        {
            pre[i]=i;
        }
        int num,sum=0;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
            {
                scanf("%d",&num);
                if(i!=j)
                {
                    p[sum].u=i;
                    p[sum].v=j;
                    p[sum++].cost=num;
                }
            }
        }
        sort(p,p+sum,cmp);
        int re=0,ss=0;
        for(int i=0;i<sum;i++)
        {
            if(fin(p[i].u)!=fin(p[i].v))
            {
                join(p[i].u,p[i].v);
                ss++;
                re+=p[i].cost;
            }
            if(ss==n-1)
            {
                break;
            }
        }
        printf("%d\n",re);
    }
    return 0;
}
```

### #5 四舍五入
```cpp
float a;
a += 0.5;
```