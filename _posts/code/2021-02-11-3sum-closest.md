---
title: 16. 3Sum Closest
date: 2021-02-10 09:36:00 PST
category: code
---

### Problem Statement

```
Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

```
### Input

Example 1:

```
  Input: nums = [-1,2,1,-4], target = 1
  Output: 2
  Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

```

Constraints:

```

    3 <= nums.length <= 10^3
    -10^3 <= nums[i] <= 10^3
    -10^4 <= target <= 10^4


```

1. Key

```
  Same as 3 sum but we have to compare 3 conditions <, >, == with target and return closest difference.

    return target - diff

```

2. Solution

```
class Solution {
    public int threeSumClosest(int[] nums, int target) {

        Arrays.sort(nums);
        //Here we have to return a integer(3sum closest to target)
        //So we find the difference at each sum we calculate

        int diff = Integer.MAX_VALUE;
        int size = nums.length;
        int res = Integer.MAX_VALUE;

        //for each element of array we will iterate over 2 separate numbers for sum
        for(int i =0; i< size; i++){
            int lo = i+1;
            int hi = size-1;

            while(lo < hi){
                int sum = nums[i] + nums[lo] + nums[hi];
                if(Math.abs(target - sum) < Math.abs(diff)){
                    diff = target - sum;
                    res = sum;
                }
                else if(sum < target){
                    lo++;
                }
                else{
                    hi--;
                }
            }
        }
        return target - diff;

    }
}
```
