---
title: "LeetCode Log: ZigZag Conversion"
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

[LeetCode Link](https://leetcode.com/problems/zigzag-conversion/)

The string ```"PAYPALISHIRING"``` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: ```"PAHNAPLSIIGYIR"```

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string s, int numRows);
```

#### Example 1:

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

#### Example 2:

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```

### Methods:

第一行和最后一行都是一样的，有规律可循（ ```gap = 2*numRows - 2``` ），直接把等距离的index的string里面的东西拿出来就好了，麻烦一点的是中间行。

中间行的关键在于要么是和gap余数为行数，要么加上行数能整除gap，找到这个规律就可以直接开写了。

In the first row and the last row, it's easy to find the pattern with the index. Since their gap are the same( ```gap = 2*numRows - 2``` ), hence index modulo gap calculation euqal to 0 will be the condition for first row, and using index modulo gap to get euqal to the number of numRows minus 1 will be the condition for last row.

For the row in the middle, they either modulo gap equals to number of rows or plus the number of rows will modulo gap = 0.

When numRows equal to 3:

```
0	 	4	 	8	 	12
1	3	5	7	9	11	13
2	 	6	 	10	 	 
```

When numRows equal to 4:

```
0	 	 	6	 	 	12
1	 	5	7	 	11	13
2	4	 	8	10	 	 
3	 	 	9	 	 	 
```

### Approach:

#### Python

```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        n = len(s)
        if numRows == 1: return s
        ans = []
        gap = 2*numRows - 2
        
        for i in range(n):
            if i%gap == 0: ans.append(s[i])
                
        for row in range(1, numRows - 1):
            for i in range(n):
                if i%gap == row: 
                    ans.append(s[i])
                elif (i+row)%gap == 0:
                    ans.append(s[i])
                    
        for i in range(n):
            if i%gap == numRows - 1: ans.append(s[i])
                
        return ''.join(ans)
```
