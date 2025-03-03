# [58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/)
```java
class Solution {
    public int lengthOfLastWord(String s) {
        String[] str = s.split(" +"); // The `" +"` in the `split` method serves as a **regular expression** that splits the input string based on one or more spaces
        int res = str[str.length -1].length();
        
        return res;
    }
}
```
# [2103. Rings and Rods](https://leetcode.com/problems/rings-and-rods/)
```java
class Solution {
    public int countPoints(String rings) {
        int[] b = new int[10];
        int[] g = new int[10];
        int[] r = new int[10];

        for(int i = 0; i < rings.length(); i = i + 2){
            if(rings.charAt(i) == 'B'){
                b[rings.charAt(i+1) - '0']++;
            }
            if(rings.charAt(i) == 'G'){
                g[rings.charAt(i+1) - '0']++;
            }
            if(rings.charAt(i) == 'R'){
                r[rings.charAt(i+1) - '0']++;
            }
        }
        int res = 0;
        for(int i = 0 ; i < 10 ; i++){
            if(r[i] > 0 && g[i] >0 && b[i]>0){
                res++;
            }
        }
        return res;
    }
}
```

# [345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)
```java
class Solution {
    public String reverseVowels(String s) {
        int start = 0;
        int end = s.length() -1;
        char[] arr = s.toCharArray();
        while(start < end){
            if(isVowel(arr[start]) && isVowel(arr[end])){
                char temp = arr[start];
                arr[start] = arr[end];
                arr[end] = temp;
                start++;
                end--;
            }
            else if(isVowel(arr[start])){
                end--;
            }else{
                start++;
            }
        }
        return new String(arr);
    }
    private boolean isVowel(char c)
    {
        return "aeiouAEIOU".indexOf(c) != -1;
    }
}
```