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
# [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m -1;
        int j = n -1;
        int k = m+n  -1;
        
        while(i>= 0 && j >= 0){
            if(nums1[i] > nums2[j]){
                nums1[k--] = nums1[i--];
            }else{
                nums1[k--] = nums2[j--];
            }
        }
        while(j>=0){
            nums1[k--] = nums2[j--];
        }
    }
}
```
# [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)
```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
     List<List<Integer>> rows = new ArrayList<List<Integer>>();
     ArrayList<Integer> row = new ArrayList<Integer>();
     for(int i= 0 ; i < numRows;i++){
        row.add(0,1);
        for(int j = 1; j <row.size()-1;j++){
            row.set(j,row.get(j)+row.get(j+1));
        }
        rows.add(new ArrayList<Integer>(row));
     }   
     return rows;
    }
}
```
# [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int[] ans = new int[nums1.length];
        for(int i = 0; i<nums1.length ; i++){
            for(int j = 0; j < nums2.length;j++){
                if(nums1[i] == nums2[j]){
                    int k;
                    for(k = j; k < nums2.length ; k++){
                        if(nums2[j] < nums2[k]){
                            ans[i] = nums2[k];
                            break;
                        }
                    }
                    if(k == nums2.length){
                        ans[i] = -1;
                    }
                }
            }
        }
        return ans;
    }
}
```
# [908. Smallest Range I](https://leetcode.com/problems/smallest-range-i/)
```java
class Solution {
    public int smallestRangeI(int[] nums, int k) {
        int min = Arrays.stream(nums).min().getAsInt();
        int max = Arrays.stream(nums).max().getAsInt();

        for(int i = 0; i < k ; i++){
            min = min +1;
            max = max -1;
            if (min > max || min == max) return 0;
        }
        return max - min;

    }
}
```
# [1051. Height Checker](https://leetcode.com/problems/height-checker/)
```java
class Solution {
    public int heightChecker(int[] heights) {
        int res = 0;
        int[] sorArr = Arrays.copyOf(heights,heights.length);
        Arrays.sort(sorArr);
        for(int i = 0 ; i < heights.length ; i++){
            if(sorArr[i] != heights[i]) res++;
        }
        return res;
    }
}
```
# [1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)
```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int wealth = Integer.MIN_VALUE;
        for(int i = 0 ; i < accounts.length ; i++){
            int sum = 0;
            for(int j = 0 ; j < accounts[0].length;j++){
                sum += accounts[i][j];
                if(sum > wealth){
                    wealth = sum;
                }
            }
        }
        return wealth;
    }
}
```
# 