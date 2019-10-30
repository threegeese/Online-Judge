---
title: "最大公因数、最小公倍数 - C"
date: 2019-10-29T20:17:20+08:00
tags: [Online Judge, Algorithms, Basic]
draft: true
---

<div class="diy-info">
编写两个函数，一个求最大公因数，一个求最小公倍数。<br/>
</div>

> 最大公因数（highest common factor）也称最大公约数（greatest common divisor）。<br/>
> 最小公倍数（least common multiple）。

> 最大公因数最小为 1。不讨论 0 的情况，因为 0 没有意义。<br/>
> 两个数的最大公因数与它们的绝对值的最大公因数相同。

> 两个数的最大公约数与最小公倍数的乘积等于这两个数的积。<br/>
> 负数的没有最小公倍数。

{{< highlight C "linenos=table, hl_lines=0, linenostart=1" >}}
// 递归实现求两个数的最大公约数
// 欧几里得算法，gcd(a, b) = gcd(b, a mod b)
int GCD (int a, int b)
{
    if (a == 0 || b == 0) return 0;
    if (a < 0) a = -a;
    if (b < 0) b = -b;
    return a % b == 0 ? b : GCD(b, a % b);
}

// 
int GCD (int a, int b)
{
    if (a == 0 || b == 0) return 0;
    if (a < 0>) a = -a;
    if (b < 0) b = -b;
    while((a %= b) && (b %= a));
	return a + b;
}

// 更相减损法求两个数的最大公约数
// 可半者半之，不可半者，副置分母、子之数，以少减多，更相减损，求其等也。以等数约之。 - 《九章算术》
int GCD(int x, int y)
{
    if(x == 0 || y == 0) return 0;
    if (x < 0>) x = -x;
    if (y < 0>) y = -y;
    while (1)
        if (x > y) x -= y;
        else if(x < y) y -= x;
        else return x;
}

// 二进制欧几里得算法
// https://en.wikipedia.org/wiki/Binary_GCD_algorithm
unsigned int gcd(unsigned int u, unsigned int v)
{
    // simple cases (termination)
    if (u == v) return u;
    if (u == 0 || v == 0) return 0;

    // look for factors of 2
    if (~u & 1) // u is even
        if (v & 1) // v is odd
            return gcd(u >> 1, v);
        else // both u and v are even
            return gcd(u >> 1, v >> 1) << 1;

    // u is odd, v is even
    if (~v & 1) return gcd(u, v >> 1);

    // reduce larger argument
    if (u > v) return gcd((u - v) >> 1, v);

    return gcd((v - u) >> 1, u);
}
{{< /highlight >}}


{{< highlight C "linenos=table, hl_lines=0, linenostart=1" >}}
// 两个数的最大公约数与最小公倍数的乘积等于这两个数的积
int LCM (int a,int b)
{
    return (a * b) / GCD(a, b);
}

//不调用外部函数求最小公倍数
int LCM (int x,int y)
{
    int tmp, product = x * y;
    if (x < y) {
        tmp = x;
        x = y;
        y = tmp;
    }

    while(1) {
        if((tmp = x % y) == 0)
            return product / y;
        else {
            x = y;
            y = tmp;
        }
    }
}
{{< /highlight>}}