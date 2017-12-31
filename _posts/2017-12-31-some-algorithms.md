---
layout: post
title: "一些算法常识"
tags: ['online judge']
---
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
