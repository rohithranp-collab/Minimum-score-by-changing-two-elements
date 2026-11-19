\# 2567. Minimum Score by Changing Two Elements



\- \*\*Difficulty:\*\* Medium

\- \*\*Topics:\*\* Array, Greedy, Sorting

\- \*\*Problem Link:\*\* \[LeetCode - 2567. Minimum Score by Changing Two Elements](https://leetcode.com/problems/minimum-score-by-changing-two-elements/)



\## Problem Summary



Given an integer array `nums`, you may change up to \*\*two\*\* elements to any values:

\- \*\*Low score:\*\* Minimum absolute difference between any two elements.

\- \*\*High score:\*\* Maximum absolute difference between any two elements.

\- \*\*Total score:\*\* `low + high`



Return the minimum possible score after changing two elements.



\## Approach \& Intuition



1\. \*\*Make `low = 0`:\*\* By setting any two elements equal to an existing element, we guarantee a minimum absolute difference of `0`.

2\. \*\*Minimize `high`:\*\* After sorting `nums` in non-decreasing order (`length = n`):

&#x20;  - If `n <= 3`, we can make all elements equal, so the score is `0`.

&#x20;  - Otherwise, changing two elements effectively discards two extreme values, leaving one of three candidate ranges:

&#x20;    - Change two smallest (`nums\[0]`, `nums\[1]`): `nums\[n - 1] - nums\[2]`

&#x20;    - Change two largest (`nums\[n - 1]`, `nums\[n - 2]`): `nums\[n - 3] - nums\[0]`

&#x20;    - Change one smallest and one largest (`nums\[0]`, `nums\[n - 1]`): `nums\[n - 2] - nums\[1]`

&#x20;  - The answer is the minimum of these three values.



\## Python Solution



```python

class Solution(object):

&#x20;   def minimizeSum(self, nums):

&#x20;       """

&#x20;       :type nums: List\[int]

&#x20;       :rtype: int

&#x20;       """

&#x20;       nums.sort()

&#x20;       n = len(nums)



&#x20;       if n <= 3:

&#x20;           return 0



&#x20;       option1 = nums\[n - 1] - nums\[2]

&#x20;       option2 = nums\[n - 3] - nums\[0]

&#x20;       option3 = nums\[n - 2] - nums\[1]



&#x20;       return min(option1, option2, option3)

