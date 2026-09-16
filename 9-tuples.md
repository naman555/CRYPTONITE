# Tuples
> In this module, we learn about tuples, which are a data structure similar to lists but are immutable. Tuples are more efficient than lists and are commonly used for multiple assignment and sorting dictionaries by value.

## Code
```python
name = input("Enter file:")
if len(name) < 1:
    name = "mbox-short.txt"
handle = open(name)

hours = {}

for line in handle:
    if line.startswith("From "):
        hour = line.split()[5][0:2]
        hours[hour] = hours.get(hour, 0) + 1

lst = sorted([(hour,count) for (hour,count) in hours.items()])
for hour, count in lst:
    print(hour, count)
```

## Concepts Learnt
- Differences between lists and tuples (immutability)
- Tuple assignment and multiple variable assignment
- Using tuples to sort dictionaries by value instead of key
- How Python compares tuples (element by element, left to right)

## References
- [PY4E](https://www.py4e.com/lessons/tuples)
