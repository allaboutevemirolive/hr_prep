

```py
#!/bin/python3

import sys

# Read the number of elements in the list
n = int(input().strip())

# Read the list of squares
squares = list(
    map(
        int, 
        input().strip().split(' ')
    )
)

# Read the desired sum and the length of subarrays
d, m = input().strip().split(' ')
d, m = [int(d), int(m)]

# Initialize count variable to keep track of subarrays with sum equal to d
count = 0

# Iterate over indices of squares from m to n+1
for i in range(m, n+1):
    # Check if the sum of subarray from i-m to i (excluding i) is equal to d
    if sum(squares[i-m:i]) == d:
        # Increment the count if the condition is satisfied
        count += 1

# Print the count of subarrays with sum equal to d
print(count)
  
```