# Remove Duplicates from Sorted Array - Two Pointers Approach

## Problem Statement

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in `nums`.

## Example

**Example 1:**

```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Example 2:**

```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

## Approach Explanation

1. **Two Pointers Approach**

   - Initialize two pointers, `i` and `j`, to the first element of the array `nums`.
   - Iterate through the array using the `j` pointer.
   - If the current element is different from the previous element, increment the `i` pointer and assign the current element to the `i`-th position of the array.
   - Return `i + 1`, which is the number of unique elements in the array.

2. **Return**

   - Return the number of unique elements in the array.

3. **Implementation**

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()==0){
            return 0;

        }
        int i  = 0;
        for(int j = 1;j<nums.size();j++){
            if(nums[i]!=nums[j]){
                i++;
                nums[i] =  nums[j];
            }
        }
        return i+1;

    }
};
```

## Complexity Analysis

### Time Complexity:

The time complexity of this solution is O(N), where N is the size of the input array. The algorithm iterates through the array once.

### Space Complexity:

The space complexity is O(1), as the algorithm uses constant extra space.

## Additional Resources

- [Leetcode - Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

