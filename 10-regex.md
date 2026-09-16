# Regular Expressions
> In this module, we learn how to use regular expressions to search for patterns in strings and extract data from them. This provides a powerful way to parse strings without writing complex string logic.

## Code:
```python
import re

with open("regex_sum_2466085.txt") as file:
    content = file.read()

lst = re.findall("[0-9]+", content)
sum = 0
for i in lst:
    sum += int(i)
print(sum)
```

## Concepts Learnt
- Learnt important regex patterns
- Importing and using the `re` module
- Using `re.search()` for boolean pattern matching
- Using `re.findall()` to extract matching substrings into a list

## References
- [PY4E](https://www.py4e.com/lessons/regex)
