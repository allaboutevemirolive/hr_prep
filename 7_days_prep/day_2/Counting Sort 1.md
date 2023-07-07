

# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'countingSort' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

fn countingSort(arr: &[i32]) -> Vec<i32> {
    let mut count = vec![0; 100];

    for &nbr in arr {
        count[nbr as usize] += 1;
    }

    count
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let n = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

    let arr: Vec<i32> = stdin_iterator.next().unwrap().unwrap()
        .trim_end()
        .split(' ')
        .map(|s| s.to_string().parse::<i32>().unwrap())
        .collect();

    let result = countingSort(&arr);

    for i in 0..result.len() {
        write!(&mut fptr, "{}", result[i]).ok();

        if i != result.len() - 1 {
            write!(&mut fptr, " ").ok();
        }
    }

    writeln!(&mut fptr).ok();
}
```



Explain to me how does this code works

```rust
fn countingSort(arr: &[i32]) -> Vec<i32> {
    let mut count = vec![0; 100];

    for &nbr in arr {
        count[nbr as usize] += 1;
    }

    count
}
```

The code you provided implements the Counting Sort algorithm to count the occurrences of each element in an input array. Here's how the code works:

1. The `countingSort` function takes an array slice `arr` as input and returns a vector `count` containing the counts of each element.

2. It initializes a vector `count` with a length of 100, filled with 0 values. The size 100 assumes that the input array contains values ranging from 0 to 99.

3. It iterates over each element `nbr` in the input array using a for loop.

4. For each element `nbr`, it uses the value as an index into the `count` vector and increments the count at that index.

   - Since `nbr` is of type `i32`, it needs to be converted to `usize` to use it as an index. This is done using the `nbr as usize` expression.

   - By incrementing `count[nbr as usize]`, the code keeps track of how many times each element appears in the input array.

5. After iterating over all elements in the input array, the `count` vector contains the counts of each element.

6. The `count` vector is returned from the function as the result.

The counting sort algorithm avoids the comparison step by using an auxiliary count array to keep track of the frequency of each element. By iterating over the input array and updating the count array accordingly, we obtain the count of each element. The resulting count array provides information about the occurrence of each element in the input array.

Note that in the provided code, the range of values is assumed to be between 0 and 99 since the count vector has a length of 100. The code can be modified to handle a different range of values if needed.