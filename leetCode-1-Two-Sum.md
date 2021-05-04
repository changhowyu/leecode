# Two-Sum

 ```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].

Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]

Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]

```

## java
> 時間複雜度O(n)，空間複雜度O(n)
   ```java
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer, Integer> lookingFor = new HashMap<>();
            for (int i = 0; i < nums.length; i++) {
                if (!lookingFor.containsKey(target - nums[i])) {
                    lookingFor.put(nums[i], i);
                    continue;
                }
                return new int[] { lookingFor.get(target - nums[i]), i };
            }
            throw new IllegalArgumentException("No two sum solution");
        }
    }
   ```
## php
   ```php
    class Solution {
        /**
         * @param Integer[] $nums
         * @param Integer $target
         * @return Integer[]
         */
        function twoSum($nums, $target) {
            $lookingFor = [];
            foreach ($nums as $key=>$num) {
                if (!array_key_exists($target - $num, $lookingFor)) {
                    $lookingFor[$num] = $key;
                    continue;
                }
                return [$lookingFor[$target - $num], $key];
            }
        }
    }
   ```
