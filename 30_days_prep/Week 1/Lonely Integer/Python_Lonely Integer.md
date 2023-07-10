

```py
def lonelyinteger(a):
    a = sorted(a)
    if len(a) < 3:
        # means there is only one unique integer in the list
        return a[0]
    # checks if the first element of the sorted list (a[0]) is different from the second element (a[1])
    # If they are different, it means the first element is the lonely integer, so the function returns a[0]
    elif a[0] != a[1]:
        return a[0]
    else:
        # retrieves a portion of a list a starting from the index 2 (inclusive)
        return lonelyinteger(a[2:])

if __name__ == '__main__':
    a = int(input())
    b = map(int, input().strip().split(" "))
    print(lonelyinteger(b))
```