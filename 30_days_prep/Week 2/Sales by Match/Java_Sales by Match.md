

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int[] freq = new int[101];
        int n = s.nextInt();
        // Acumulate frequency
        for (int i = 0; i < n; i++) {
            int x = s.nextInt();
            freq[x]++;
        }
        int total = 0;
        // Each frequency divide by 2 and acumulate in total
        for (int i = 1; i < 101; i++) {
            total += freq[i] / 2;
        }
        System.out.println(total);
    }
}
```