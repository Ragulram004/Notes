# [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();
        int itr = 0;
        if(s.length() <=1 )return false;
        while( itr < s.length()){
            if(s.charAt(itr) == '('){
                st.push(')');
            }else if(s.charAt(itr) == '['){
                st.push(']');
            }else if(s.charAt(itr) == '{'){
                st.push('}');
            }else{
                if( st.isEmpty() || s.charAt(itr) != st.pop()){
                    return false;
                }
            }
            itr++;
        }
        return st.isEmpty();
    }
}
```
# [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> st = new Stack<>();
        for(String c : tokens){
            if(c.equals("+") || c.equals("-") || c.equals("/") || c.equals("*") ){
                int num2 = st.pop();
                int num1 = st.pop();
                switch(c){
                    case "+":
                        st.push(num1 + num2);
                        break;
                    case "-":
                        st.push(num1 - num2);
                        break;
                    case "/":
                        st.push(num1 / num2);
                        break;
                    case "*":
                        st.push(num1 * num2);
                        break;
                }
            }else{
                st.push(Integer.parseInt(c)); 
            }
        }
        return st.peek();
    }
}
```
# [155. Min Stack](https://leetcode.com/problems/min-stack/)
```java
class MinStack {
    private Stack<Integer> st;
    private Stack<Integer> min;

    public MinStack() {
        st = new Stack<>();
        min = new Stack<>();
    }
    
    public void push(int val) {
        st.push(val);
        if(min.isEmpty() || min.peek() >= val){
            min.push(val);
        }
    }
    
    public void pop() {
        if(st.peek().equals(min.peek())){
            min.pop();
        }
        st.pop();
    }
    
    public int top() {
        return st.peek();
    }
    
    public int getMin() {
        return min.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```