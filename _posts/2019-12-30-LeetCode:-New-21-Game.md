---
title: "LeetCode Log: New 21 Game"
categories:
  - Algorithm
header:
  overlay_image: "assets/images/post-develop.png"
  overlay_filter: 0.2
excerpt: "Solution and thoughts of problem on LeetCode step by step."
mathjax: "true"
tags:
  - Java
  - Python
---

### Problem Statement

https://leetcode.com/problems/new-21-game/

Alice plays the following game, loosely based on the card game "21".

Alice starts with 0 points, and draws numbers while she has less than K points.  During each draw, she gains an integer number of points randomly from the range [1, W], where W is an integer.  Each draw is independent and the outcomes have equal probabilities.

Alice stops drawing numbers when she gets K or more points.  What is the probability that she has N or less points?

#### Example 1:

```
Input: N = 10, K = 1, W = 10
Output: 1.00000
Explanation:  Alice gets a single card, then stops.
```

#### Example 2:

```
Input: N = 6, K = 1, W = 10
Output: 0.60000
Explanation:  Alice gets a single card, then stops.
In 6 out of W = 10 possibilities, she is at or below N = 6 points.
```

#### Example 3:

```
Input: N = 21, K = 17, W = 10
Output: 0.73278
```

### Methods:

In this situation, the points will fall into three different ranges based on the requirement, and there will be different probability calculations for different points value. 

Firstly, before the points go over the K, then what we need to do is got the probability of each value of points. We can easily store it in the list and update it. 

Secondly, when the points go over the K but the maximum for the points will be K+W. However, the rules said once Alice reaches the K points, she will stop draw numbers. Then, the range for the second situation will be (K, K+W).

Hence, points will not go over K+W, or equal to K+W either, the chance will 0%.


### Approach:

#### Python

```python
class Solution(object):
    def new21Game(self, N, K, W):
        """
        :type N: int
        :type K: int
        :type W: int
        :rtype: float
        """
        if K == 0: 
            return 1
        DP = [1.0] + [0]*N
        mysum = 1.0
        for i in range(1, N+1):
            DP[i] = mysum/W
            # the corresponding value in DP list is the probability when Alice got i points
            if i < K:
                mysum += DP[i]
                # add up the previous probabilities before i is less than k
            if 0 <= i - W < K:
                mysum -= DP[i-W]
                # this is the final situation, when i goes over K but not exceed the K plus W. 
                # Since once go over K, Alice will stop draw. 
                # So we nned to minus the probability of the most recent one, which is the points i minus W.
                
        return sum(DP[K:])
```
