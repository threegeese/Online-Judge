---
title: "Prime Number - C"
date: 2019-10-27T15:21:04+08:00
tags: [Online Judge, Algorithms, Basic]
---

<p class="diy-info">
使用 C 语言编写一个函数，该函数接收一个整数，判断这个数是否是素数。
</p>

{{< highlight C "linenos=table, hl_lines=3 8 12, linenostart=10" >}}
bool isPrime (int N) {
    if (N <= 3) {
        return N > 1;
    }

    // 不在 6 的倍数两侧的一定不是素数
    if (N % 6 != 1 && N % 6 != 5) {
        return false;
    }
    // 在 6 的两侧的也不一定是素数，如 25,49
    for (int i=5; i*i<=N; i+=6) {
        if (N % i == 0 || N % (i+2) == 0) {
            return false;
        }
    }
    return true;
}
{{< /highlight >}}

``` C
// 判断一个int类型的数是否是素数
// 大于 3 的素数只分布在 6n-1 和 6n+1 两数列中.(n 为非 0自然数)
bool isPrime (int N) {
    if (N <= 3) {
        return N > 1;
    }

    // 不在 6 的倍数两侧的一定不是素数
    if (N % 6 != 1 && N % 6 != 5) {
        return false;
    }
    // 在 6 的两侧的也不一定是素数，如 25,49
    for (int i=5; i*i<=N; i+=6) {
        if (N % i == 0 || N % (i+2) == 0) {
            return false;
        }
    }
    return true;
}
```