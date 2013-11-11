---
layout: post
title: "LeetCode解题报告: Jump Game"
description: ""
category: "LeetCode"
tags: [greedy]
---
{% include JB/setup %}

## 题目

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:

A = \[2,3,1,1,4\], return true.

A = \[3,2,1,0,4\], return false.


******


## 分析

<pre>
array: 3, 2, 4, 2, 3, 2, 2, 4

       i        i + A[i]
       |        |
index: 0  1  2  3  4  5  6  7
             |           |
             promising   promising + A[promising]
</pre>

考虑当前位置i的下一步所能到达的所有情况\[i, i + A\[i\]\]， 必须从它们中选择一步来跳。
显然应该跳到这样的位置j， 它能使得从它出发再跳A\[j\]步能够达到最远。
也就是说，如果选择跳到j，则它可以保证下一次可跳的范围最大。同时，这个范围包含了其他j'的范围，因为j' + A\[j'\] <= j + A\[j\]。
因此，对于下一轮而言，j位置要比其他j'位置更优，选择更全面。

******


## 代码 (Java):

{% highlight java %}
public class Solution {
    public boolean canJump(int[] A) {
        // IMPORTANT: Please reset any member data you declared, as
        // the same Solution instance will be reused for each test case.
        int i = 0;
        while (i < A.length) {
            int promisingIndex = i;
            for (int j = i; j <= i + A[i] && j < A.length; ++j) {
                promisingIndex = Math.max(promisingIndex, j + A[j]);
            }
            if (promisingIndex >= A.length - 1) {
                return true;
            }
            if (promisingIndex == i) {
                return false;
            }
            i = promisingIndex;
        }
        return false;
    }
}
{% endhighlight %}

