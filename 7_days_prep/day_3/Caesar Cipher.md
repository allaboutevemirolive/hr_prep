


# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'caesarCipher' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts following parameters:
 *  1. STRING s
 *  2. INTEGER k
 */

fn caesarCipher(s: &str, k: i32) -> String {
    let n = s.len();
    let mut builder = String::with_capacity(n);

    for i in 0..n {
        let temp = s.chars().nth(i).unwrap();
        let upper_case = temp.is_uppercase();

        if temp.is_alphabetic() {
            let mut new_char = temp as u8 + (k % 26) as u8;

            if !new_char.is_ascii_alphabetic() || (upper_case && !new_char.is_ascii_uppercase()) {
                new_char -= 26;
            }

            builder.push(new_char as char);
        } else {
            builder.push(temp);
        }
    }

    builder
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let n = stdin_iterator
        .next()
        .unwrap()
        .unwrap()
        .trim()
        .parse::<i32>()
        .unwrap();

    let s = stdin_iterator.next().unwrap().unwrap();

    let k = stdin_iterator
        .next()
        .unwrap()
        .unwrap()
        .trim()
        .parse::<i32>()
        .unwrap();

    let result = caesarCipher(&s, k);

    writeln!(&mut fptr, "{}", result).ok();
}
```

```rust
fn main() {
    // Test the caesarCipher function
    let input = "Hello, World!";
    let key = 3;
    let encrypted = caesarCipher(input, key);
    println!("Encrypted: {}", encrypted);
}
```