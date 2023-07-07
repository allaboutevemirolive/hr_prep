


# Rust

```rust
use std::io::{self, BufRead};

fn findZigZagSequence(a: &mut [i32]) {
    a.sort();

    let n = a.len();
    let mid = n / 2;
    a.swap(mid, n - 1);

    let mut st = mid + 1;
    let mut ed = n - 2;
    while st <= ed {
        a.swap(st, ed);
        st += 1;
        ed -= 1;
    }

    for (i, &num) in a.iter().enumerate() {
        if i > 0 {
            print!(" ");
        }
        print!("{}", num);
    }
    println!();
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let test_cases: i32 = stdin_iterator
        .next()
        .unwrap()
        .unwrap()
        .trim()
        .parse()
        .unwrap();

    for _ in 0..test_cases {
        let n: usize = stdin_iterator
            .next()
            .unwrap()
            .unwrap()
            .trim()
            .parse()
            .unwrap();

        let mut a: Vec<i32> = stdin_iterator
            .next()
            .unwrap()
            .unwrap()
            .trim()
            .split_whitespace()
            .map(|s| s.parse().unwrap())
            .collect();

        findZigZagSequence(&mut a);
    }
}
```