
# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'lonelyinteger' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY a as parameter.
 */

fn lonelyinteger(a: &[i32]) -> i32 {
    let n = a.len();
    let mut x = 0;
    let mut state;

    for i in 0..n {
        state = true;
        // Iterate left side
        for j in 0..i {
            if a[i] == a[j] {
                state = false;
                break;
            }
        }
        if state {
            // iterate right side/remaining
            for j in i + 1..n {
                if a[i] == a[j] {
                    state = false;
                    break;
                }
            }
            // If left and right didn't contain duplicate
            if state {
                x = a[i];
                break;
            }
        }
    }

    x
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let n = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

    let a: Vec<i32> = stdin_iterator.next().unwrap().unwrap()
        .trim_end()
        .split(' ')
        .map(|s| s.to_string().parse::<i32>().unwrap())
        .collect();

    let result = lonelyinteger(&a);

    writeln!(&mut fptr, "{}", result).ok();
}
```

The code you provided finds the "lonely integer" in an array of integers. The lonely integer is the only element in the array that occurs exactly once, while all other elements occur in pairs.

Here's a step-by-step explanation of how the code works:

1. The function `lonelyinteger` takes an array slice `a` as input and returns an integer.

2. It initializes the variable `n` to the length of the array `a` and `x` to 0. The variable `state` will be used to track if an element is not duplicated.

3. The code enters a loop that iterates over each index `i` in the array from 0 to `n-1`.

4. For each index `i`, it initializes `state` to `true` to assume the element at index `i` is unique.

5. It enters a nested loop that iterates over each index `j` from 0 to `i-1`. This loop checks if any previous element before index `i` is equal to the element at index `i`.

6. If a match is found (`a[i] == a[j]`), it means the element at index `i` is not unique. In this case, the variable `state` is set to `false`, and the loop is broken using the `break` statement.

7. After the inner loop finishes, the code checks if `state` is still `true`. If it is, it means no previous element before index `i` matched the element at index `i`, indicating that the element is unique so far.

8. It enters another nested loop that iterates over each index `j` from `i+1` to `n-1`. This loop checks if any subsequent element after index `i` is equal to the element at index `i`.

9. If a match is found (`a[i] == a[j]`), it means the element at index `i` is not unique. In this case, the variable `state` is set to `false`, and the loop is broken using the `break` statement.

10. After the second inner loop finishes, the code checks if `state` is still `true`. If it is, it means no subsequent element after index `i` matched the element at index `i`, indicating that the element is unique in the entire array.

11. If `state` is still `true` after both inner loops, it means the element at index `i` is the lonely integer. It assigns the value of `a[i]` to the variable `x` and breaks the outer loop using the `break` statement.

12. Once the outer loop finishes or the `break` statement is encountered, the code returns the value of `x`, which represents the lonely integer found in the array.

The code essentially compares each element in the array with all previous elements and subsequent elements to determine if it is unique or not. It keeps track of the `state` variable to decide if an element is duplicated or not. Once it finds the lonely integer, it breaks the loop and returns the value.