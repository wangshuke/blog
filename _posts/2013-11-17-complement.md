---
layout: post
title: 为什么要用补码表示负数11111111111111111111111111111111111111111111111111111111
tags: 补码 computer
categories: common
---

抛开二进制不谈，我们先来看看10进制

假设世界上没有负号且数字最大只有3位，我们要把 `0～999` 分成两部分，一部分表示负数，一部分表示正数，而且不影响他们的运算规律，应当如何去做？

首先，最大的负数加上一等于零，那么用999表示最大的负数再合适不过，现在需要正负数各一半，那么正数部分应当为 `0 ～ 499`，负数部分应当为 `500～999`，我们暂时把这些表示负数的数字成为`对照数字`。

验证一下，`18 - 5 = 18 + 995 = 1013 = 13`

有没有一种计算方法可以方便地找出`-5`与`995`的关系呢？

有，那就是`999 - 5 + 1`

---

将这个规律推及到二进制中

假设二进制数只有8位，那么8个1代表最大的负数，将这些数分为正负各一半，那么正数部分应该为 `0 ～ 01111111`，负数部分应当为 `10000000  ～ 11111111`。

验证一下，`00010010 - 00000101 = 00010010 + 11111011 = 00001101`

与十进制同理，`-00000101`的对照数字可以用相同方法计算出来，`11111111 - 00000101 + 1`

等等，我们发现了一个特性，这真是一个神奇的特性！

`11111111 - 00000101` 等于`00000101` 按位取反！

现在，我们已经总结出了一点经验，在二进制中，负数的对照数字等于它的数值位按位取反再加一。

对于一个二进制负数来说，它是有符号的，因此他的第一位为符号位，剩余的为数值位，那么完整的表述就是负数的对照数字为`符号位不变，数值位按位取反再加一`，这个对照数字就是`补码`。

---

最后回答一下标题中的问题，显而易见，使用补码的好处就是，可以用加法来计算减法，从而简化电路设计。



