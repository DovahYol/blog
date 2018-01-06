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