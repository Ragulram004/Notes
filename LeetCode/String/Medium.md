# [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)
```java
class Solution {
    public String intToRoman(int num) {
        int[] nums = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String[] rom = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

        StringBuilder sb = new StringBuilder();

        for(int i = 0 ; i < nums.length;i++){
            while(num >= nums[i]){
                num -= nums[i];
                sb.append(rom[i]);
            }
        }
        return sb.toString();
    }
}
```