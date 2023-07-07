


# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'gridChallenge' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING_ARRAY grid as parameter.
 */

fn gridChallenge(grid: &[String]) -> String {
    for i in 0..grid.len() {
        let mut chars: Vec<char> = grid[i].chars().collect();
        chars.sort();
        let sorted_row: String = chars.into_iter().collect();

        if i > 0 {
            let prev_sorted_row = &grid[i - 1];
            for j in 0..prev_sorted_row.len() {
                if sorted_row.chars().nth(j).unwrap() < prev_sorted_row.chars().nth(j).unwrap() {
                    return "NO".to_string();
                }
            }
        }
    }

    "YES".to_string()
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let t = stdin_iterator
        .next()
        .unwrap()
        .unwrap()
        .trim()
        .parse::<i32>()
        .unwrap();

    for _ in 0..t {
        let n = stdin_iterator
            .next()
            .unwrap()
            .unwrap()
            .trim()
            .parse::<i32>()
            .unwrap();

        let mut grid: Vec<String> = Vec::with_capacity(n as usize);

        for _ in 0..n {
            let grid_item = stdin_iterator.next().unwrap().unwrap();
            grid.push(grid_item);
        }

        let result = gridChallenge(&grid);

        writeln!(&mut fptr, "{}", result).ok();
    }
}
```


___
___


Explain to me how does this code works

```rust
fn gridChallenge(grid: &[String]) -> String {
    for i in 0..grid.len() {
        let mut chars: Vec<char> = grid[i].chars().collect();
        let sorted_row: String = chars.into_iter().collect();

        if i > 0 {
            let prev_sorted_row = &grid[i - 1];
            for j in 0..prev_sorted_row.len() {
                // Check if current char is lexically smaller than upper char
                if sorted_row.chars().nth(j).unwrap() < prev_sorted_row.chars().nth(j).unwrap() {
                    return "NO".to_string();
                }
            }
        }
    }

    "YES".to_string()
}
```

Certainly! Let's break down how the code works:

The function `gridChallenge` takes a slice of strings `grid` as input and returns a string.

1. The function iterates over each row of the `grid` using a `for` loop and the index `i`. The loop variable `i` represents the index of the current row.

2. For each row, the characters of the row are collected into a `Vec<char>` by calling `.chars().collect()`. This allows us to perform operations on the characters of the row.

3. The collected characters are then transformed back into a string using `.into_iter().collect()` and stored in the variable `sorted_row`. This creates a string representing the current row with its characters in lexicographically sorted order.

4. If the index `i` is greater than 0 (meaning it's not the first row), the function compares each character of the current `sorted_row` with the corresponding character of the previous row (`prev_sorted_row`). It does this by iterating over the length of `prev_sorted_row` using a `for` loop and the index `j`.

5. Inside the loop, the function checks if the character at index `j` of `sorted_row` is less than the character at the same index of `prev_sorted_row`. If it is, it means that the current row is not in lexicographic order compared to the previous row. In this case, the function immediately returns the string "NO".

6. If the loop completes without returning "NO" for any row, it means that all the rows are in lexicographic order. In this case, the function returns the string "YES" indicating that the grid satisfies the lexicographic order condition.

So, the function essentially checks whether each row of the grid is lexicographically greater than or equal to the previous row. If any row violates this condition, it returns "NO". Otherwise, it returns "YES" indicating that the grid is in lexicographic order.