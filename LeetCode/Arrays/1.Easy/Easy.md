# [1. Two Sum](https://leetcode.com/problems/two-sum/)
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */

int* twoSum(int*nums, int numsSize, int target, int*returnSize) {
    int *arr = malloc(2*sizeof(int));
    *returnSize = 2;
    for(int i =0;i< numsSize-1;i++){
        for(int j =i+1;j < numsSize;j++){
            if(nums[i] + nums[j] == target){
                arr[0] = i;arr[1]= j;
                return arr;
            }
        }
    }
    return arr;    
}
```
# [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)
```c
int searchInsert(int* nums, int numsSize, int target) { 
	if(target <= nums[0]){ 
		return 0; 
	} 
	for(int i=0;i<numsSize-1;i++){ 
		if(nums[i] == target){ 
			return i+1; 
		} 
		if(nums[i]<=target && nums[i+1]>=target){ 
			return i+1; 
		} 
	} 
	return numsSize;
}
```
# [136. Single Number](https://leetcode.com/problems/single-number/)
```java
class Solution {

    public int singleNumber(int[] nums) {

        int i = 0;

        Arrays.sort(nums);

        for( i = 0 ; i < nums.length -1;i = i+2){

            if(nums[i] != nums[i+1]) return nums[i];

        }

        return nums[nums.length -1];

    }

}
```
# [268. Missing Number](https://leetcode.com/problems/missing-number/)
```java
class Solution {

    public int missingNumber(int[] nums) {

        int len = nums.length, i = 0;

        Arrays.sort(nums);

        for( i = 0;i<len;i++){

            if(nums[i] != i) return i;

        }

        return nums[i-1]+1;

    }

}
```
# [1295. Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)
```java
class Solution {

    public int findNumbers(int[] nums) {

        int count = 0;

        for(int i = 0 ; i < nums.length ; i++){

            int len = (int)Math.log10(nums[i]);

            if(len % 2 == 1) count++;

        }

        return count;

    }

}
```
# [66. Plus One](https://leetcode.com/problems/plus-one/)
```java
class Solution {
    public int[] plusOne(int[] digits) {
        for(int i = digits.length - 1 ; i >=0;i--){
            if(digits[i] != 9){
                digits[i]++;
                break;
            }else{
                digits[i] = 0;
            }
        }
        if(digits[0] == 0){
            int[] res = new int[digits.length+1];
            res[0] = 1;
            return res;
        }
        return digits;
    }
}
```
# [169. Majority Element](https://leetcode.com/problems/majority-element/)
```java
class Solution {
    public int majorityElement(int[] nums) {
       int number = 0;
       int count = 0;
       for(int i= 0; i< nums.length;i++){
        if(count == 0 && number != nums[i]){
            number = nums[i];
            count = 1;
        }else{
            count = (number == nums[i]) ? count+1: count-1;
        }
       }
    return number;
}}
```
# [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;
        int minprice = Integer.MAX_VALUE;
        for(int i = 0 ; i < prices.length ; i++){
            minprice = Math.min(minprice,prices[i]);
            profit = Math.max(profit,prices[i]-minprice);
        }
        return profit;
    }
}
```
# [832. Flipping an Image](https://leetcode.com/problems/flipping-an-image/)
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        for(int[] row : image){
            for(int i = 0 ; i < (image[0].length+1)/ 2 ; i++){
                int temp = row[i] ^ 1;
                row[i] = row[image[0].length - i -1] ^ 1;
                row[image[0].length-i-1] = temp;
            }
        }
        return image;
    }
}
```
# [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)
```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        for(int i = 0 ; i < nums.length;i++){
            nums[i] = nums[i] * nums[i];
        }
        Arrays.sort(nums);
        return nums;
    }
}
```
# [344. Reverse String](https://leetcode.com/problems/reverse-string/)
```java
class Solution {
    public void reverseString(char[] s) {
        int len = s.length;
        int start = 0;
        int end = len - 1;
        while (start<end){
            char temp = s[start];
            s[start] = s[end];
            s[end] = temp;
            start++;
            end--;
        }     
    }
}
```
# 