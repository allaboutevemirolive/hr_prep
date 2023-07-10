

# Rust

```rust
use std::io::{self, BufRead};

/*
 * Complete the 'miniMaxSum' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

fn miniMaxSum(arr: &[i32]) {
    let mut sum: i64 = 0;
    let mut min_val = i32::MAX;
    let mut max_val = i32::MIN;

    for &num in arr {
        sum += num as i64;
        min_val = min_val.min(num);
        max_val = max_val.max(num);
    }

    let min_sum = sum - max_val as i64;
    let max_sum = sum - min_val as i64;

    println!("{} {}", min_sum, max_sum);
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let arr: Vec<i32> = stdin_iterator.next().unwrap().unwrap()
        .trim_end()
        .split(' ')
        .map(|s| s.to_string().parse::<i32>().unwrap())
        .collect();

    miniMaxSum(&arr);
}
```





# Java


```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

class Result {

    /*
     * Complete the 'miniMaxSum' function below.
     *
     * The function accepts INTEGER_ARRAY arr as parameter.
     */

    public static void miniMaxSum(List < Integer > arr) {
        long[] m = new long[5];
        for (int i = 0; i < 5; i++) {
            m[i] = arr.get(i);
        }
        Arrays.sort(m);
        long x = 0;
        long y = 0;
        for (int i = 0; i < 4; i++) {
            x += m[i];
        }
        for (int i = 1; i < 5; i++) {
            y += m[i];
        }
        System.out.println(x + " " + y);
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        String[] arrTemp = bufferedReader.readLine().replaceAll("\\s+$", "").split(" ");

        List < Integer > arr = new ArrayList < > ();

        for (int i = 0; i < 5; i++) {
            int arrItem = Integer.parseInt(arrTemp[i]);
            arr.add(arrItem);
        }

        Result.miniMaxSum(arr);

        bufferedReader.close();
    }
}
```