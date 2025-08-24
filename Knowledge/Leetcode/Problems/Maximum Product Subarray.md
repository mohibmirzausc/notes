# 152. Maximum Product Subarray

## Problem
You are given an integer array `nums`.  
Find the contiguous subarray (containing at least one number) that has the **largest product**, and return that product.  

The test cases are generated so that the answer will fit in a 32-bit integer.  

---

### Examples
**Example 1**  
Input: `nums = [2,3,-2,4]`  
Output: `6`  
Explanation: The subarray `[2,3]` has the largest product `6`.  

**Example 2**  
Input: `nums = [-2,0,-1]`  
Output: `0`  
Explanation: The result cannot be `2`, because `[-2,-1]` is not a contiguous subarray.  

---

### Constraints
- `1 <= nums.length <= 2 * 10^4`  
- `-10 <= nums[i] <= 10`  
- The product of any subarray of `nums` is guaranteed to fit in a **32-bit integer**.  

---

## Solution
### Approach
This solution tracks both the **maximum product (`hi`)** and **minimum product (`lo`)** at each step.  
Why? Because a negative number can flip a small negative product into the largest positive product.  

Steps:
1. Initialize `hi`, `lo`, and `best` to the first element.  
2. Iterate through the array:  
   - If the current number is negative, swap `hi` and `lo`.  
   - Update `hi` as the maximum of `(num, num * hi)`.  
   - Update `lo` as the minimum of `(num, num * lo)`.  
   - Update `best` as the maximum product seen so far.  
3. Return `best`.  

---

### Code (Python)

```python
class Solution(object):
    def maxProduct(self, nums):
        hi = lo = best = nums[0]

        for num in nums[1:]:
            # Swap hi and lo when a negative number flips signs
            if num < 0:
                hi, lo = lo, hi

            # Update current max and min products
            hi = max(num, num * hi)
            lo = min(num, num * lo)

            # Track the best product so far
            best = max(best, hi)

        return best
```

---

### Key Takeaways
- Always track **both max and min products** since negatives can flip results.  
- **Swapping on negative numbers** ensures we don’t miss a large product.  
- Time complexity: **O(n)**, Space complexity: **O(1)**.  
