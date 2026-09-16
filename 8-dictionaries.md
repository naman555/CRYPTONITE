# Dictionaries
> In this module, we learn about the dictionary data structure, which allows us to store multiple values in an object and look up the values by their key.

## Code:
```python
name = input("Enter file:")
if len(name) < 1:
    name = "mbox-short.txt"
handle = open(name)

dict = {}
for line in handle:
    if line.startswith("From "):
        sender = line.split()[1]
        dict[sender] = dict.get(sender, 0) + 1

max_sender, max = "", 0
for sender, count in dict.items():
    if count > max:
        max = count
        max_sender = sender


print(max_sender, max)

```

## Concepts Learnt
- Creating and accessing dictionary elements
- Simplifying counting logic with the `.get()` method
- Iterating through dictionary keys and values using `.items()`

## References
- [PY4E](https://www.py4e.com/lessons/dictionary)
