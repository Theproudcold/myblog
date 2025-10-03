---
title: 力扣 p2918
date: 2025-10-03
draft: false
summary:
tags:
  - 算法
  - 力扣
  - 贪心
showTableOfContents: true
---
> Problem: [2918. 数组的最小相等和](https://leetcode.cn/problems/minimum-equal-sum-of-two-arrays-after-replacing-zeros/description/)

思路

> 可贪心将所有的 0 换为最小正整数 1，根据得出的最小和来进行分类讨论，如果数组和小且没有 0 元素那么无论如何都变不成大的，反正只要有就可以。且因为是**正整数**，**只能变成大的**。

解题过程

> 计算数组和同时统计 0 的个数，进行判断，最后输出两个数组和大的。

复杂度

- 时间复杂度: O(n+m)

- 空间复杂度: O(1) 

Code

```c
long long minSum(int* nums1, int nums1Size, int* nums2, int nums2Size) {
 long long z1 = 0,z2 = 0;
 long long s1 = 0,s2 = 0;
 for(long long i = 0; i < nums1Size; i++) {
 if(nums1[i] == 0) {
            z1++;
        }
 s1 += nums1[i];
    }
    s1 += z1;
 for(long long i = 0; i < nums2Size; i++) {
 if(nums2[i] == 0) {
            z2++;
        }
 s2 += nums2[i];
    }
    s2 += z2;
 if ((s1 < s2 && z1 == 0) || (s1 > s2 && z2 == 0) ) {
 return -1;
    }
 return s1 > s2?s1:s2;
}
```

