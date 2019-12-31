---
title: "LeetCode Log: Broken Calculator"
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

https://leetcode.com/problems/broken-calculator/

On a broken calculator that has a number showing on its display, we can perform two operations:

* Double: Multiply the number on the display by 2, or;

* Decrement: Subtract 1 from the number on the display.

Initially, the calculator is displaying the number X.

Return the minimum number of operations needed to display the number Y.

#### Example 1:

```
Input: X = 2, Y = 3
Output: 2
Explanation: Use double operation and then decrement operation {2 -> 4 -> 3}.
```

#### Example 2:

```
Input: X = 5, Y = 8
Output: 2
Explanation: Use decrement and then double {5 -> 4 -> 8}.
```

#### Example 3:

```
Input: X = 1024, Y = 1
Output: 1023
Explanation: Use decrement operations 1023 times.
```

### Methods:

If X was more than Y, then we only can use decrement operation for X minus Y times. If Y was more than Y, we can use the backward solution. 

The main methods is to reduce the Y by decrement operation or double operation based on if Y become odd or even number, count on times for every cycle before the Y less than X.

And don't forget to add on the gap if last step is decrement operation.

### Approach:

#### Python

```python
class Solution(object):
    def brokenCalc(self, X, Y):
        """
        :type X: int
        :type Y: int
        :rtype: int
        """
        ans = 0
        while Y > X:
            ans += 1
            if Y % 2 == 1: Y += 1
            else: Y /= 2
        return ans + X - Y
```

#### Java

```java
class Solution {
    public int brokenCalc(int X, int Y) {
        int ans = 0;
        while (Y > X){
            ans ++;
            if (Y % 2 == 1)
                Y++;
            else
                Y /= 2;
        }
        return ans + X - Y;
    }
}
```
