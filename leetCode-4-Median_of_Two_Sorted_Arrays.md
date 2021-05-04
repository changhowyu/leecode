# Longest substring without repeating characters

 ```
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
 
Follow up: The overall run time complexity should be O(log (m+n)).
 
 
Example 1:
 
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
 
Example 2:
 
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
 
Example 3:
 
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
 
Example 4:
 
Input: nums1 = [], nums2 = [1]
Output: 1.00000
 
Example 5:
 
Input: nums1 = [2], nums2 = []
Output: 2.00000

```

## java
> 時間複雜度O(n)，空間複雜度O(1)
   ```java
    class Solution {
        public double findMedianSortedArrays(int[] nums1, int[] nums2) {
            int nums1Len = nums1.length;
            int nums2Len = nums2.length;
            
            if(nums1Len == 0 && nums2Len == 0) {
               return 0;
            }
            
            int len = nums1Len + nums2Len, k = len / 2;
            if(len % 2 == 1) { 
               return topK(nums1, nums2, k + 1);
            }
            double val1 = topK(nums1, nums2, k);
            double val2 = topK(nums1, nums2, k + 1);
            return (val1 + val2) / 2;
        }
        
        private int topK(int[] nums1, int[] nums2, int K){
            int nums1Len = nums1.length;
            int nums2Len = nums2.length;
            
            if(nums1Len == 0) {
               return nums2[K - 1];
            }
            if(nums2Len == 0) {
               return nums1[K - 1];
            }
    
            if(K == 1){
                return nums2[0] > nums1[0] ? nums1[0] : nums2[0];
            } else {
                int k = K / 2;
                int l = nums1Len < k ? nums1Len : k;
                int r = nums2Len < k ? nums2Len : k;
                
                if(nums1[l - 1] >= nums2[r - 1]) {
                   return topK(nums1, Arrays.copyOfRange(nums2, r, nums2.length), K - r);
                }
                return topK(Arrays.copyOfRange(nums1, l, nums1.length), nums2, K - l);
            }
        }
    }
   ```
## php
   ```php
    class Solution {
    
        /**
         * @param Integer[] $nums1
         * @param Integer[] $nums2
         * @return Float
         */
        function findMedianSortedArrays($nums1, $nums2) {
            $nums1Len = count($nums1);
            $nums2Len = count($nums2);
            
            if(count($nums1) == 0 && count($nums2) == 0) {
                return 0;
            }
            
            $len = $nums1Len + $nums2Len;
            $k = intval($len / 2);
            
            if($len % 2 == 1) { 
               return $this->topK($nums1, $nums2, $k + 1);
            }
            
            $val1 = $this->topK($nums1, $nums2, $k);
            $val2 = $this->topK($nums1, $nums2, $k + 1);
            return ($val1 + $val2) / 2;
        }
        
        /**
         * @param Integer[] $nums1
         * @param Integer[] $nums2
         * @param Int $K
         * @return Float
         */
        function topK($nums1, $nums2, $K) {
            $nums1Len = count($nums1);
            $nums2Len = count($nums2);
            if($nums1Len == 0) {
               return $nums2[$K - 1];
            }
            if($nums2Len == 0) {
               return $nums1[$K - 1];
            }
    
            if($K == 1){
                return $nums2[0] > $nums1[0] ? $nums1[0] : $nums2[0];
            } else {
                $k = intval($K / 2);
                $l = $nums1Len < $k ? $nums1Len : $k;
                $r = $nums2Len < $k ? $nums2Len : $k;
                
                if($nums1[$l - 1] >= $nums2[$r - 1]) {
                   return $this->topK($nums1, array_slice($nums2, $r, $nums2Len), $K - $r);
                }
                return $this->topK(array_slice($nums1, $l, $nums1Len), $nums2, $K - $l);
            }
        }
    }
   ```
