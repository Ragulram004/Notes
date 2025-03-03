# [485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int left = 0; 
        int right = 0;int n = 0;int maxlen = 0;
        while(right < nums.length){
            if(nums[right] == 1){
                maxlen = Math.max(maxlen,right-left+1);
            }else{
                left = right + 1;
            }
            right = right +1;
        }
        return maxlen;
    }
}
```
# [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int left = 0;
        int right = k - 1;
        int sum =0;
        int maxlen = 0;
        int maxsum = 0;
        for(int i = 0; i < k; i++){
            sum += nums[i];
        }
        maxsum = sum;
        while( right < nums.length -1){
            sum -= nums[left];
            sum += nums[++right];
            if(maxsum < sum){
                maxsum = sum;
            }
            left++;
        }
        return (double) maxsum/k;
    }
}
```
# [1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)
```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int left =0 ; int right = 0; int zero = 0 ; int maxlen = 0;
        while(right < nums.length){
            if(nums[right] == 0){
                zero += 1;
            }
            if(zero > k){
                if(nums[left] == 0){
                    zero -= 1;
                }
                left += 1;
            }else{
                maxlen = Math.max(maxlen, right - left +1);
            }
            right += 1;
        }
        return maxlen;
    }
}
```

