# 53. Maximum Subarray

## Problem
You are given an integer array `nums`.  
Find the contiguous subarray (containing at least one number) that has the **largest sum**, and return that sum.

---

### Examples
**Example 1**  
Input: `nums = [-2,1,-3,4,-1,2,1,-5,4]`  
Output: `6`  
Explanation: The subarray `[4,-1,2,1]` has the largest sum `6`.  

**Example 2**  
Input: `nums = [1]`  
Output: `1`  
Explanation: The subarray `[1]` has the largest sum `1`.  

**Example 3**  
Input: `nums = [5,4,-1,7,8]`  
Output: `23`  
Explanation: The subarray `[5,4,-1,7,8]` has the largest sum `23`.  

---

### Constraints
- `1 <= nums.length <= 10^5`  
- `-10^4 <= nums[i] <= 10^4`  

---

### Follow-up
If you have solved the **O(n)** solution, try implementing a **divide-and-conquer approach**, which is more subtle.

---

## Solution
### Code (Python)

```python
class Solution(object):
    def maxSubArray(self, nums):
        max_sum = -100001          # Largest subarray sum seen so far
        max_negative_num = -100001 # Track the "least bad" negative number
        sum = 0            # Running sum of the current subarray
        found_positive_num = False # Flag to check if any positive number exists

        for num in nums:
            sum += num

            # If the running sum dips below 0, reset it
            if sum < 0:
                sum = 0
                max_negative_num = max(max_negative_num, num)
            else:
                found_positive_num = True

            # Update the global maximum
            max_sum = max(sum, max_sum)

        # If we saw at least one positive number → return max_sum
        # Otherwise → return the "largest negative number"
        return max_sum if found_positive_num else max_negative_num
```

---

### Key Takeaways
- **`sum`** grows as long as it helps the subarray sum.  
- If **`sum` < 0**, reset (start fresh).  
- **`max_sum`** always tracks the best sum found so far.  
- Handles **all-negative arrays** correctly by returning the least negative element.  
