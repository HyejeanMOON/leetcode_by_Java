

Given an unsorted array of integers, find the length of longest increasing subsequence.

Example:
```
Input: [10,9,2,5,3,7,101,18]
Output: 4 
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4. 
```
Note:

There may be more than one LIS combination, it is only necessary for you to return the length.
Your algorithm should run in O(n2) complexity.
Follow up: Could you improve it to O(n log n) time complexity?


Difficulty:Medium  
Total Accepted:139.5K  
Total Submissions:357K  
Related Topics:Binary Search, Dynamic Programming

!

### 解题思路
http://www.cnblogs.com/grandyang/p/4938187.html  
这道题让我们求最长递增子串Longest Increasing Subsequence的长度，简称LIS的长度。我最早接触到这道题是在LintCode上，可参见我之前的博客Longest Increasing Subsequence 最长递增子序列，那道题写的解法略微复杂，下面我们来看其他的一些解法。首先来看一种动态规划Dynamic Programming的解法，这种解法的时间复杂度为O(n2)，类似brute force的解法，我们维护一个一维dp数组，其中dp[i]表示以nums[i]为结尾的最长递增子串的长度，对于每一个nums[i]，我们从第一个数再搜索到i，如果发现某个数小于nums[i]，我们更新dp[i]，更新方法为dp[i] = max(dp[i], dp[j] + 1)，即比较当前dp[i]的值和那个小于num[i]的数的dp值加1的大小，我们就这样不断的更新dp数组，到最后dp数组中最大的值就是我们要返回的LIS的长度。
#### Scala
```Scala
object Solution {
    def lengthOfLIS(nums: Array[Int]): Int = {
        if(nums.isEmpty) return 0
        var len = nums.length
        var dp = new scala.collection.mutable.ArrayBuffer[Int]()
        var res = 0
        for(i <- 0 until len) dp=dp:+1
        for(i <- 0 until len){
            for(j <- 0 until i){
                if(nums(i)>nums(j)) dp(i) = scala.math.max(dp(i),dp(j)+1)             
            }
            res = scala.math.max(res,dp(i))
        }
        res   
    }
}
```
```Java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int len = nums.length;
        if(len==0) return 0;
        int[] dp = new int[len];
        for(int i=0; i<len; i++) dp[i] = 1;
        int res = 0;
        for(int i=0; i<len; i++){
            for(int j=0; j<i; j++){
                if(nums[i]>nums[j]) dp[i] = Math.max(dp[i],dp[j]+1);        
            }
            res=Math.max(res,dp[i]);
        }
        return res;
    }
}
```