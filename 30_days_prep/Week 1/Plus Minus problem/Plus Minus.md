
# Rust

```rust
use std::io::{self, BufRead};

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

fn plusMinus(arr: &[i32]) {
    let mut positives = 0;
    let mut negatives = 0;
    let mut zeros = 0;
    let len = arr.len();

    if len > 0 && len <= 100 {
        for &elem in arr {
            if elem > 0 {
                positives += 1;
            } else if elem < 0 {
                negatives += 1;
            } else {
                zeros += 1;
            }
        }
    }

    println!("{}", positives as f64 / len as f64);
    println!("{}", negatives as f64 / len as f64);
    println!("{}", zeros as f64 / len as f64);
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let n = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

    let arr: Vec<i32> = stdin_iterator.next().unwrap().unwrap()
        .trim_end()
        .split(' ')
        .map(|s| s.to_string().parse::<i32>().unwrap())
        .collect();

    plusMinus(&arr);
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
     * Complete the 'plusMinus' function below.
     *
     * The function accepts INTEGER_ARRAY arr as parameter.
     */

    public static void plusMinus(List < Integer > arr) {
        int positives = 0, negatives = 0, zeros = 0;
        int len = arr.size();

        if (len > 0 && len <= 100) {
            for (int elem: arr) {
                if (elem > 0) {
                    positives++;
                } else if (elem < 0) {
                    negatives++;
                } else {
                    zeros++;
                }
            }
        }

        System.out.println((double) positives / len);
        System.out.println((double) negatives / len);
        System.out.println((double) zeros / len);
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        String[] arrTemp = bufferedReader.readLine().replaceAll("\\s+$", "").split(" ");

        List < Integer > arr = new ArrayList < > ();

        for (int i = 0; i < n; i++) {
            int arrItem = Integer.parseInt(arrTemp[i]);
            arr.add(arrItem);
        }

        Result.plusMinus(arr);

        bufferedReader.close();
    }
}
```