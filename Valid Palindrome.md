# 125. Valid Palindrome

## Problem Statement

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

## Example

**Example 1:**

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**

```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**Example 3:**

```
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

## Constraints

- `1 <= s.length <= 2 * 10^5`
- `s` consists only of printable ASCII characters.

## Approach Explanation

1. **Two Pointer Approach**

   - Initialize two pointers `left` and `right` at the beginning and end of the string `s`, respectively.
   - Iterate through the string using the two pointers.
   - If the character at the `left` pointer is not an alphanumeric character, increment the `left` pointer.
   - If the character at the `right` pointer is not an alphanumeric character, decrement the `right` pointer.
   - If the lowercase characters at the `left` and `right` pointers are not equal, return `false`.
   - If the pointers meet or cross each other, return `true`.

2. **Return**

   - Return `true` if the string is a palindrome, or `false` otherwise.

3. **Implementation**

```cpp
class Solution {
public:
    bool isPalindrome(string s) {

        int left  = 0,right = s.size()-1;
        if(s.empty()){
            return false;
        }
        while(left < right){
            if(!isalnum(s[left])){
                left++;

            }
            else if(!isalnum(s[right])){
                right--;
            }
            else if(tolower(s[left]) != tolower(s[right])){
                return false;
            }
           else{ left++;
            right--;
           }
        }

        return true;
    }
};
```

## Complexity Analysis

### Time Complexity:

The time complexity of this solution is O(N), where N is the size of the input string. The algorithm iterates through the string once using two pointers.

### Space Complexity:

The space complexity is O(1), as the algorithm uses constant extra space.

## Additional Resources

- [Leetcode - Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
