---
layout: post
title: "LeetCode: Jump Game"
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



## 分析

aaaa

## 代码

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

