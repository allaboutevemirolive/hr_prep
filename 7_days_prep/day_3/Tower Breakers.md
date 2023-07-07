


# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'towerBreakers' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER m
 */

fn towerBreakers(n: i32, m: i32) -> i32 {
    if m != 1 && n % 2 == 1 {
        1
    } else {
        2
    }
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let t = stdin_iterator.next().unwrap().unwrap().trim().parse::<i32>().unwrap();

    for _ in 0..t {
        let first_multiple_input: Vec<String> = stdin_iterator.next().unwrap().unwrap()
            .split(' ')
            .map(|s| s.to_string())
            .collect();

        let n = first_multiple_input[0].trim().parse::<i32>().unwrap();

        let m = first_multiple_input[1].trim().parse::<i32>().unwrap();

        let result = towerBreakers(n, m);

        writeln!(&mut fptr, "{}", result).ok();
    }
}
```



The question seems compilcated but why the solution is easy like below?

```rust
fn towerBreakers(n: i32, m: i32) -> i32 {
    if m != 1 && n % 2 == 1 {
        1
    } else {
        2
    }
}
```

Although the problem statement may seem complicated, the actual solution logic provided is relatively simple. Let's break it down:

The solution is implemented in the `towerBreakers` function, which takes two integer parameters: `n` (the number of towers) and `m` (the height of each tower). It returns an integer value representing the winner of the game.

The logic of the function is as follows:

1. If `m` is not equal to 1 (meaning the height of the tower is not already 1) and `n` is an odd number, then Player 1 wins the game. In this case, the function returns 1.
2. In all other cases, Player 2 wins the game. The function returns 2.

The reason this solution works is that it takes advantage of the game rules and the fact that both players play optimally. 

If the height of the tower (`m`) is not 1 and the number of towers (`n`) is odd, then Player 1 can always make a move that reduces the height of a tower to 1. This forces Player 2 to eventually have no possible moves and lose the game. Therefore, Player 1 wins.

In all other cases, Player 1 doesn't have an immediate winning move, so Player 2 wins the game.

Overall, the solution is simple because it leverages the properties of the game and optimal play to determine the winner based on the given inputs.

