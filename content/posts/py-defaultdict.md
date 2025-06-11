+++
date = '2025-06-11T17:13:13+08:00'
draft = false
title = 'PY: defaultdict()'
+++

A `defaultdict` is a subclass of dict that calls a factory function to supply missing values for any requested key.

...
In today's call, I was looking at a simple python solution that will try to count the number of fruits based on types.

Lets take this example. I want to know how many numbers apple in the list.

The typical way:

```
fruit_list = ["apple", "banana", "apple", "orange", "banana", "apple"]
fruit_counts = {}

for fruit in fruit_list:
    if fruit in fruit_counts:
        fruit_counts[fruit] += 1
    else:
        fruit_counts[fruit] = 1

print(fruit_counts)
# Output: {'apple': 3, 'banana': 2, 'orange': 1}
```

We will check the `fruit_counts` dict. If it's there, add more. If not, set it it to 1.

Looks simple, but apparently... There's a way to do this in more pythonic way..

```
from collections import defaultdict

fruit_list = ["apple", "banana", "apple", "orange", "banana", "apple"]
fruit_counts = defaultdict(int) # defaultdict with a default factory of int (which returns 0)

for fruit in fruit_list:
    fruit_counts[fruit] += 1 # If 'fruit' is not in fruit_counts, it defaults to 0, then 1 is added.

print(fruit_counts)
# Output: defaultdict(<class 'int'>, {'apple': 3, 'banana': 2, 'orange': 1})
```

If fruit is already a key in fruit_counts, its current value is incremented by 1.
If fruit is not yet a key in fruit_counts, defaultdict(int) automatically creates fruit_counts[fruit] and initializes its value to 0. Then, 1 is added to it, making its value 1.

From [GeeksforGeeks](https://www.geeksforgeeks.org/defaultdict-in-python/):

- Using `int`: If you use int as the factory function, the default value will be 0 (since int() returns 0).
- Using `list`: If you use list as the factory function, the default value will be an empty list ([]).
- Using `str`: If you use str, the default value will be an empty string ('').

Now... What if I want to start from 100? Apparently... we can! via lambda...

```
from collections import defaultdict

fruit_list = ["apple", "banana", "apple", "orange", "banana", "apple"]

fruit_counts = defaultdict(lambda: 50)

for fruit in fruit_list:
    # If 'fruit' is not in fruit_counts, it defaults to 50, then 1 is added.
    fruit_counts[fruit] += 1

print(fruit_counts)
// defaultdict(<function <lambda> at 0x7f73165e7d30>, {'apple': 53, 'banana': 52, 'orange': 51})
```
