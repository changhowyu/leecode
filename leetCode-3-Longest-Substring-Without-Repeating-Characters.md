# Median of Two Sorted Arrays

 ```
Given a string s, find the length of the longest substring without repeating characters.


Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.


```

## java
> 時間複雜度O(log (m+n))，空間複雜度O(1)
   ```java
    class Solution {
       public int lengthOfLongestSubstring(String s) {
           int stringIdx = 0, countLen = 0;
           int stringPassPos[] = new int[128];
           for (int i = 0;i < s.length();i++) {
               stringIdx = Math.max(stringPassPos[s.charAt(i)], stringIdx);
               countLen = Math.max(countLen, i-stringIdx+1);
               stringPassPos[s.charAt(i)] = i + 1;
           }
           return countLen;
       }
    }  
   ```
## php
   ```php
    class Solution {
  
        /**
         * @param String $s
         * @return Integer
         */
        function lengthOfLongestSubstring($s) {
            $stringIdx = 0;$countLen = 0;
            $stringPassPos = [];
            for ($i = 0;$i < strLen($s);$i++) {
                $stringIdx = max($stringPassPos[$s[$i]], $stringIdx);
                $countLen = max($countLen, $i - $stringIdx + 1);
                $stringPassPos[$s[$i]] = $i + 1;
            }
            return $countLen;
        }
    }
   ```
