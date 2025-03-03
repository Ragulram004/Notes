# [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode result = new ListNode(0);
        ListNode ptr = result;

        int carry = 0;
        while(l1 != null || l2 != null){
            int sum = 0+carry;
            if(l1 != null){
                sum += l1.val;
                l1 = l1.next;
            }
            if(l2 != null){
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10;
            sum = sum % 10;
            ptr.next = new ListNode(sum);
            ptr = ptr.next;
        }
        if(carry == 1) ptr.next = new ListNode(1);
        return result.next;
    }
}

```
# [48. Rotate Image](https://leetcode.com/problems/rotate-image/)
```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for(int i = 0 ; i < (n+1)/2;i++){
            for(int j = 0 ; j < n/2;j++){
                int temp = matrix[n-1-j][i];

                matrix[n-1-j][i] = matrix[n-1-i][n-1-j];

                matrix[n-1-i][n-1-j] = matrix[j][n-1-i];
                
                matrix[j][n-1-i] = matrix[i][j];
                
                matrix[i][j] = temp;
            }
        }
    }
}
```