# 18. 4Sum

## Problem Statement

Given an array `nums` of `n` integers, return an array of all the unique quadruplets `[nums[a], nums[b], nums[c], nums[d]]` such that:

- `0 <= a, b, c, d < n`
- `a`, `b`, `c`, and `d` are distinct.
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in any order.

## Example

**Example 1:**

```
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

**Example 2:**

```
Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
```

## Constraints

- `1 <= nums.length <= 200`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`

## Approach Explanation

1. **Two Pointer Approach**

   - Sort the input array `nums` in non-decreasing order.
   - Iterate through the array using a variable `i` as the first pointer.
   - For each iteration, set `j` as the second pointer to the element next to `i`.
   - Initialize two more pointers `left` and `right` to the element next to `j` and the last element of the array, respectively.
   - If the sum of the elements at indices `i`, `j`, `left`, and `right` is greater than `target`, decrement `right`.
   - If the sum is less than `target`, increment `left`.
   - If the sum is equal to `target`, add the quadruplet to the result and increment `left` and decrement `right` until the next unique element is found.
   - Skip duplicates by checking if the current number is the same as the previous number.

2. **Return**

   - Return the result vector containing all unique quadruplets.

3. **Implementation**

```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        int n = nums.size();
        for(int i = 0; i < n - 3; i++) {
            if(i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            for(int j = i + 1; j < n - 2; j++) {
                if(j > i + 1 && nums[j] == nums[j - 1]) {
                    continue;
                }
                int left = j + 1;
                int right = n - 1;
                while(left < right) {
                    long long int sum = static_cast<long long int>(nums[i]) + nums[j] + nums[left] + nums[right];
                    if(sum == target) {
                        ans.push_back({nums[i], nums[j], nums[left], nums[right]});
                        while(left < right && nums[left] == nums[left + 1]) left++;
                        while(left < right && nums[right] == nums[right - 1]) right--;
                        left++;
                        right--;
                    } else if(sum < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }
        return ans;
    }
};
```

## Complexity Analysis

### Time Complexity:

The time complexity of this solution is O(N^3), where N is the size of the input array. The algorithm iterates through the array twice using two nested loops and uses a two-pointer approach to find the quadruplets.

### Space Complexity:

The space complexity is O(1), as the algorithm uses constant extra space.

## Additional Resources

- [Leetcode - 4Sum](https://leetcode.com/problems/4sum/description/)
- [Ayushi Sharma](https://www.youtube.com/watch?v=OZdOHiodh_c)