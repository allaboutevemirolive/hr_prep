


# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, Read, Write};

fn super_digit(n: &str, k: i32) -> i32 {
    if n.len() == 1 {
        n.parse().unwrap()
    } else {
        let np: i32 = n.chars().map(|c| c.to_digit(10).unwrap() as i32).sum();
        super_digit(&(np * k).to_string(), 1)
    }
}

fn main() {
    let mut input = String::new();
    io::stdin().read_to_string(&mut input).unwrap();

    let mut lines = input.lines();
    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let first_multiple_input: Vec<&str> = lines
        .next()
        .unwrap()
        .trim()
        .split_whitespace()
        .collect();

    let n = first_multiple_input[0];
    let k = first_multiple_input[1].parse::<i32>().unwrap();

    let pSum = super_digit(n, 1);
    let result = super_digit(&(pSum * k).to_string(), 1);

    writeln!(&mut fptr, "{}", result).expect("Error writing to file");
}
```