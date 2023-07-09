

# Java

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        String str = "{[()]}";
        boolean res = isBalanced(str);
        System.out.println(res);
    }
    public static boolean isBalanced(String s) {
        // check
        if (s == null || s.length() % 2 != 0) return false;
        Stack < Character > stack = new Stack < Character > ();
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            // If open
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            // If close
            } else if (c == ')' || c == '}' || c == ']') {
                if (!stack.isEmpty()) {
                    // Consume last item in vector
                    char latestOpenP = stack.pop();

                    // Compare consumed with current char
                    // If coupled, it is okay
                    if (latestOpenP == '(' && c != ')') {
                        return false;
                    } else if (latestOpenP == '{' && c != '}') {
                        return false;
                    } else if (latestOpenP == '[' && c != ']') {
                        return false;
                    }
                } else {
                    return false;
                }
            }
        }

        // If empty, then all char coupled
        // else !balanced
        return stack.isEmpty();
    }
}
```