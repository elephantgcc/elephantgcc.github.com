---
layout: post
title: "LeetCode: Jump Game 解题报告"
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

                i + A[i]
                |
index: 0  1  2  3  4  5  6  7
       |     |           |
       i     pIndex      pIndex + A[pIndex]
</pre>

总体上是一个贪心的过程，每次总是跳这样的一步：如果跳到它这里，它还能保证下一步走到最远。

设当前处在位置i，则可以跳的范围是\[i + 1, i + A\[i\]\]，从这个范围中选择一个最有希望的位置pIndex (promising index)，使得pIndex + A\[pIndex\]最大，然后把i更新为pIndex。继续往后，直到i + A\[i\]超过最后一个元素，已满足可达条件，返回true；如果pIndex并没有比当前的i更大，则说明已经在某个地方停止不前，因此不能跳到最后，返回false。

为什么要选择这样的pIndex？因为它保证了下一步可能到达的范围最远，也就最有可能首先跳到数组的最后。而如果选择其他位置，则它们的下一步一定不如pIndex的下一步远，因此不能做到最快到达数组的最后。


******


## 代码 (Java):

{% highlight java %}
public class Solution {
    public boolean canJump(int[] A) {
        // Start typing your Java solution below
        // DO NOT write main() function
        if (A.length == 0 || A.length == 1) {
            return true;
        }
        int i = 0;
        while (i + A[i] < A.length - 1) {
            int pIndex = i;
            for (int j = i + 1; j <= i + A[i]; ++j) {
                if (j + A[j] > pIndex + A[pIndex]) {
                    pIndex = j;
                }
            }
            if (pIndex == i) {
                return false;
            }
            i = pIndex;
        }
        return true;
    }
}
{% endhighlight %}

