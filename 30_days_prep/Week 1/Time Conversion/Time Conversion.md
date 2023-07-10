
# Rust

```rust
use std::env;
use std::fs::File;
use std::io::{self, BufRead, Write};

/*
 * Complete the 'timeConversion' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING s as parameter.
 */

fn timeConversion(s: &str) -> String {
    let ap = s.chars().nth(s.len() - 2).unwrap();
    let mut time = String::from(&s[..s.len() - 2]);

    if ap == 'A' {
        let hh: i32 = time[..2].parse().unwrap_or(0);
        if hh == 12 {
            time.replace_range(..2, "00");
        }
    } else {
        let hh: i32 = time[..2].parse().unwrap_or(0);
        if hh != 12 {
            let converted = format!("{:02}", hh + 12);
            time.replace_range(..2, &converted);
        }
    }

    time
}

fn main() {
    let stdin = io::stdin();
    let mut stdin_iterator = stdin.lock().lines();

    let mut fptr = File::create(env::var("OUTPUT_PATH").unwrap()).unwrap();

    let s = stdin_iterator.next().unwrap().unwrap();

    let result = timeConversion(&s);

    writeln!(&mut fptr, "{}", result).ok();
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
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'timeConversion' function below.
     *
     * The function is expected to return a STRING.
     * The function accepts STRING s as parameter.
     */

    public static String timeConversion(String s) {
        char ap = s.charAt(s.length() - 2);
        s = s.substring(0, s.length() - 2);
        if (ap == 'A') {
            int hh = Integer.parseInt(s.substring(0, 2));
            if (hh == 12) hh = 0;
            String hour = Integer.toString(hh);
            if (hour.length() == 1) {
                hour = "0" + hour;
            }
            return hour + s.substring(2);
        } else {
            int hh = Integer.parseInt(s.substring(0, 2));
            if (hh != 12) hh += 12;
            String hour = Integer.toString(hh);
            if (hour.length() == 1) {
                hour = "0" + hour;
            }
            return hour + s.substring(2);
        }
    }

}


public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String s = bufferedReader.readLine();

        String result = Result.timeConversion(s);

        bufferedWriter.write(result);
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```


The `timeConversion` method takes a string `s` representing a time in the 12-hour format (e.g., "07:05:45PM") and converts it to the 24-hour format (e.g., "19:05:45").

Here's a step-by-step explanation of how the code works:

1. The method receives the input time string `s`.

2. It extracts the last two characters of `s`, which represent the period of the day (AM or PM). The `charAt` method is used to retrieve the character at the specified index (`s.length() - 2`). It stores the period in the variable `ap`.

3. The variable `s` is updated by removing the last two characters (the period) using the `substring` method. The new `s` value will represent the time without the period.

4. The code then checks the value of `ap`. If it is equal to 'A', it means the time is in the AM period.

5. If `ap` is 'A', the code proceeds to extract the hours from `s`. It parses the substring from index 0 to 2 (excluding index 2) to an integer using `Integer.parseInt`. This represents the hours portion of the time.

6. If the parsed hours value is 12, it means it is 12 AM. In this case, the code sets `hh` (hours) to 0 since it will be represented as 00 in the 24-hour format.

7. The code then converts the modified `hh` value to a string using `Integer.toString`. If the length of the resulting string is 1, it means the hour is a single digit. In this case, the code adds a leading zero to maintain the format.

8. The converted hour (`hour`) is concatenated with the remaining substring of `s` starting from index 2. This represents the minutes and seconds portion of the time.

9. If `ap` is not 'A', it means the time is in the PM period.

10. In the PM case, the code follows a similar process as in the AM case, but with some differences. The hours value (`hh`) is extracted from `s` and parsed to an integer.

11. If the parsed hours value is not 12, it means it is in the afternoon or evening (PM). In this case, the code adds 12 to the hours value to convert it to the 24-hour format.

12. The modified `hh` value is converted to a string, and if the length of the resulting string is 1, a leading zero is added.

13. The converted hour (`hour`) is concatenated with the remaining substring of `s` starting from index 2.

14. The resulting time string is returned, representing the converted time in the 24-hour format.

Overall, the code handles the conversion of a time string from the 12-hour format to the 24-hour format by extracting the period (AM or PM), adjusting the hours accordingly, and concatenating the converted hour with the remaining time components.