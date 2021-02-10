---
title: 3. Longest Substring Without Repeating Characters
date: 2021-02-10 07:20:00 PST
category: code
---

### Problem Statement

```
Given a string s, find the length of the longest substring without repeating characters.
```
### Input

Example 1:

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

```

Example 2

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

Example 3

```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

Example 4
```
Input: s = ""
Output: 0
```
Note:

```

    0 <= s.length <= 5 * 104
    s consists of English letters, digits, symbols and spaces.

```

1. Key

```
Sliding Window
Keep adding to a string until you see a same character.
When you see a same character get the index of it the current string.
Remove everything before that character including the character -> substring from the index+1 to length of the current string.
Keep track of longest substring.
```

2. Solution

```
class Solution {
    public int lengthOfLongestSubstring(String s) {

        String longest = "";
        String current = "";
        Set<Character> seen = new HashSet<Character>();

        for(int i = 0; i<s.length(); i++){
            Character curr = s.charAt(i);
            if(!seen.add(curr) && !current.isEmpty()){
                int delPos = current.indexOf(curr);
                current = current.substring(delPos+1,current.length());
            }
            seen.add(curr);
            current += s.charAt(i);

            if(current.length() > longest.length()){
                longest = current;
            }
        }
        return longest.length();

    }
}
```
