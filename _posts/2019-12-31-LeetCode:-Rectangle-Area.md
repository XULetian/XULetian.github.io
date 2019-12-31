---
title: "LeetCode Log: Rectangle Area"
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

https://leetcode.com/problems/rectangle-area/

Find the total area covered by two rectilinear rectangles in a 2D plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.

#### Example 1:

```
Input: A = -3, B = 0, C = 3, D = 4, E = 0, F = -1, G = 9, H = 2
Output: 45
```

### Methods:

The question asks you if you can find out the overlapped area, so as long as you can classify the situation into two positions: intersect or disjoint, and then calculate each area, we will be fine.

### Approach:

#### Python

```python
class Solution(object):
    def computeArea(self, A, B, C, D, E, F, G, H):
        """
        :type A: int
        :type B: int
        :type C: int
        :type D: int
        :type E: int
        :type F: int
        :type G: int
        :type H: int
        :rtype: int
        """
        area = (C-A)*(D-B) + (G-E)*(H-F)
        x, y = (min(C, G) - max(A, E)), (min(D, H) - max(B, F))
        if x > 0 and y > 0: return area - x*y
        else: return area
```

#### Java

```java
class Solution {
    public int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {

    int area = (D - B) * (C - A) + (G - E) * (H - F);

    int up = Math.min(D, H);
    int down = Math.max(B, F);
    int right = Math.min(G, C);
    int left = Math.max(A, E);

    if (up > down && right > left) {
      return area - (right - left) * (up - down);
    }else{
            return area;
        }
    }
}
```
