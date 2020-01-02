---
title: "LeetCode Log: Valid Palindrome"
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

[LeetCode Link](https://leetcode.com/problems/valid-palindrome/)

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

#### Example 1:

```
Input: "A man, a plan, a canal: Panama"
Output: true
```

#### Example 2:

```
Input: "race a car"
Output: false
```

### Methods:

Using regex to find all letters(to lowercase) in a string into a list, then try to match it with reversed one. 


### Approach:

#### Python

```python
import re

class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        s = ''.join(re.findall("[a-zA-Z0-9]+", s)).lower()

        return s == s[::-1]      
```
