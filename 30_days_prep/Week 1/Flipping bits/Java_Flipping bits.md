


```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        // represented by a signed long integer
        long max = Integer.MAX_VALUE;
        max = max * 2 + 1;
        for (int i = 0; i < n; i++) {
            // ~ operator performs a bitwise complement operation on the value, which flips all the bits
            // & operator performs a bitwise AND operation between the complemented value and max
            System.out.println(~in.nextLong() & max);
        }
    }
}
```