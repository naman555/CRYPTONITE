# Files
>In this module, we learn file handling in Python. We learn about opening, reading and saving to files. We use iteration to read the contents from these files and perform various actions related to the contents.

## Code
```python
# Use the file name mbox-short.txt as the file name
fname = input("Enter file name: ")
fh = open(fname)
count, average = 0, 0
for line in fh:
    if line.startswith("X-DSPAM-Confidence:"):
        average += float(line[line.find(":") + 1 :].strip())
        count += 1

average /= count
print("Average spam confidence:", average)
```

## Concepts Learnt
- Opening and saving files
- Reading files and iterating through the contents

## References :
- [PY4E](https://www.py4e.com/html3/07-files)
