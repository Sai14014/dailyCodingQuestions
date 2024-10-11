Problem Statement
Given an unsorted array of integers, find the length of the longest increasing subsequence (LIS).

An increasing subsequence is a subsequence in which the elements are in strictly increasing order. A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.

Sample Input
[10,9,2,5,3,7,101,18]
Sample Output
4
Explanation: The longest increasing subsequence is [2,5,7,101], therefore the length is 4.

Solution
class Solution {
    public int lengthOfLIS(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        
        int[] dp = new int[nums.length];
        dp[0] = 1;
        int maxLen = 1;
        
        for (int i = 1; i < nums.length; i++) {
            dp[i] = 1;
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j] && dp[i] < dp[j] + 1) {
                    dp[i] = dp[j] + 1;
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }
        
        return maxLen;
    }
}
