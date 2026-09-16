# Lists
> In this module, we learn about lists. Lists can store more than one item in a variable and we can iterate through them and slice them to process data safely.

## Code
```python
fname = input("Enter file name: ")
file = open(fname)
lst = list()

for line in file:
    words = line.split()
    line.startswith
    for word in words:
        if word not in lst:
            lst.append(word)
lst.sort()
print(lst)
```

```python
fname = input("Enter file name: ")
if len(fname) < 1:
    fname = "mbox-short.txt"

fh = open(fname)
count = 0

for line in fh:
    if line.startswith("From "):
        print(line.split()[1])
        count += 1
print("There were", count, "lines in the file with From as the first word")
```

## Concepts Learnt
- Creation and indexing of lists
- Common built-in list functions
- `in` / `not in` for membership checks

## References
- [PY4E](https://www.py4e.com/html3/08-lists)
