# 153. Find Minimum in Rotated Sorted Array

## Problem
Suppose an array of length `n` sorted in ascending order is rotated between `1` and `n` times.  

For example, the array `nums = [0,1,2,4,5,6,7]` might become:  
- `[4,5,6,7,0,1,2]` if it was rotated 4 times.  
- `[0,1,2,4,5,6,7]` if it was rotated 7 times.  

Notice that rotating an array `[a[0], a[1], ..., a[n-1]]` once results in `[a[n-1], a[0], a[1], ..., a[n-2]]`.  

Given the sorted rotated array `nums` of **unique elements**, return the **minimum element** of this array.  

You must write an algorithm that runs in **O(log n)** time.  

---

### Examples
**Example 1**  
Input: `nums = [3,4,5,1,2]`  
Output: `1`  
Explanation: The original array was `[1,2,3,4,5]` rotated 3 times.  

**Example 2**  
Input: `nums = [4,5,6,7,0,1,2]`  
Output: `0`  
Explanation: The original array was `[0,1,2,4,5,6,7]` rotated 4 times.  

**Example 3**  
Input: `nums = [11,13,15,17]`  
Output: `11`  
Explanation: The original array was `[11,13,15,17]` rotated 4 times.  

---

### Constraints
- `n == nums.length`  
- `1 <= n <= 5000`  
- `-5000 <= nums[i] <= 5000`  
- All integers of `nums` are **unique**  
- `nums` is sorted and rotated between `1` and `n` times  

---

## Solution

### Approach
We use **binary search** to find the minimum element.  
- If the leftmost value is less than the rightmost → the subarray is already sorted → return `nums[l]`.  
- Otherwise, compute `mid = (l + r) // 2`.  
  - If `nums[mid] > nums[r]`, then the minimum is in the **right half**.  *(explanation below)*
  - Else, the minimum is in the **left half**, including `mid`.  
- Continue until `l == r`.  

---

### Code (Python)
```python
class Solution(object):
    def findMin(self, nums):
        l, r = 0, len(nums)-1

        while l < r:
            if nums[l] < nums[r]:  # Already sorted
                return nums[l]

            mid = (l + r) // 2

            if nums[mid] > nums[r]:
                l = mid + 1
            else:
                r = mid

        return nums[l]
```

---

### Key Takeaways
- This is a **binary search** problem, so the runtime is **O(log n)**.  

- Key check:  
  - If `nums[mid] > nums[r]` → go right: because the domain of that subsection of the array is  (-inf, r) & (mid, inf). 
  - Else → go left (including `mid`): because the domain of that subsection would be (mid, r).

- NOTE: Looking at the domains help show which side will contain the lesser item. Since it is sorted we can take advantage of this. 

---
