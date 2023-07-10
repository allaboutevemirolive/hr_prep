


```py
n = int(input())
hashmap = {}

# Check occurance
for i in range(n):
    string = input()
    hashmap[string] = 1 if string not in hashmap else hashmap[string] + 1

q = int(input())

# Check occurance for specific query
for j in range(q):
    string = input()
    print(0 if string not in hashmap else hashmap[string])
```



Certainly! The question is asking for a program that can count the occurrences of certain words in a list of input words. Here's a simplified explanation:

1. The program will first ask for the number of input words, let's call it `n`.
2. Next, you'll provide `n` words as input.
3. Then, the program will ask for the number of words you want to search for, let's call it `q`.
4. After that, you'll provide `q` words as queries.
5. Finally, the program will count how many times each query word appears in the input words and give you the results.

For example, let's say we have the following inputs:

Input words: "cat", "dog", "cat", "bird"
Query words: "cat", "dog", "mouse"

The program will count the occurrences of each query word in the input words:

- "cat" appears twice in the input words.
- "dog" appears once in the input words.
- "mouse" does not appear in the input words.

Therefore, the program will output:

2 (for "cat")
1 (for "dog")
0 (for "mouse")

The program essentially helps you find out how many times each query word appears in the given list of input words.