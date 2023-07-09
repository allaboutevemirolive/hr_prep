

# Rust

```rust
use std::io::{self, BufRead};

/*
 * Complete the 'minimumBribes' function below.
 *
 * The function accepts INTEGER_ARRAY q as parameter.
 */

fn minimumBribes(q: &[i32]) {
    let mut nn: [i32; 100000] = [0; 100000];
    let mut y = 0;
    let n = q.len();

    for j in 0..n {
        nn[j] = q[j];

        // Check current element is less than diff is less than 3
        // Rule: Each element can legally move 2 positions
        if nn[j] - j as i32 > 3 {
            y = -1;
        }
    }

    // If an element needs more than 2 moves, then the list is random
    if y == -1 {
        println!("Too chaotic");
        return;
    }

    let mut yr;
    // We fix element sequence
    for _ in 0..n {
        yr = y;
        for j in 0..n - 1 {
            // If curr element is bigger than next element
            if nn[j] > nn[j + 1] {
                // clone curr
                let x = nn[j];
                // put next element to curr element
                nn[j] = nn[j + 1];
                // put curr element to next element
                nn[j + 1] = x;
                // trace how many change were made
                y += 1;
            }
        }
        if yr == y {
            break;
        }
    }

    println!("{}", y);
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let t = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

    for _ in 0..t {
        let n = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

        let q: Vec<i32> = stdin_iterator.next().unwrap().unwrap()
            .trim_end()
            .split(' ')
            .map(|s| s.to_string().parse::<i32>().unwrap())
            .collect();

        minimumBribes(&q);
    }
}
```