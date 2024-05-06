# 3Sum - Two Pointer Approach

## Problem Statement

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

## Example

**Example 1:**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation:
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

**Example 2:**

```
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```

**Example 3:**

```
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```

## Approach Explanation

1. **Two Pointer Approach**

   - Sort the input array `nums` in non-decreasing order.
   - Iterate through the array using a variable `i` as the first pointer.
   - For each iteration, set `j` as the second pointer to the element next to `i`, and `k` as the third pointer to the last element of the array.
   - If the sum of the elements at indices `i`, `j`, and `k` is greater than 0, decrement `k`.
   - If the sum is less than 0, increment `j`.
   - If the sum is equal to 0, add the triplet to the result and increment `j` and decrement `k` until the next unique element is found.
   - Skip duplicates by checking if the current number is the same as the previous number.

2. **Return**

   - Return the result vector containing all unique triplets.

3. **Implementation**

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n = nums.size();
        vector<vector<int>>ans;
        for(int i =0; i<n-1 ;i++){

            if(i > 0 && nums[i] == nums[i-1]) continue;
            int a = nums[i];
            int t = -a;
            int end = n-1;
            int start = i+1;
            while(end > start){
                if(nums[start]+nums[end] == t ){
                    ans.push_back({nums[i],nums[start],nums[end]});
                    while(start < end && (nums[start] == nums[start+1])) start++;
                    while(start < end && (nums[end]==nums[end-1]))end--;
                    start++;
                    end--;
                }
                else if(nums[start]+nums[end] > t){
                    end --;
                }
                else{
                    start++;

                }
           }
        }

         return ans;
    }
};
```

## Complexity Analysis

### Time Complexity:

The time complexity of this solution is O(N^2), where N is the size of the input array. The algorithm iterates through the array once and uses a two-pointer approach to find the triplets.

### Space Complexity:

The space complexity is O(1), as the algorithm uses constant extra space.

## Additional Resources

- [Leetcode - 3Sum](https://leetcode.com/problems/3sum/description/)
- [Fraz's Tutorial on 3Sum Algorithm](https://youtu.be/TeegtfmEhTY?si=Kk_-7zjroXUaFWm7)